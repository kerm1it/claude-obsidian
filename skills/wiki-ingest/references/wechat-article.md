# WeChat Article Sub-Processor

Use this sub-processor when ingesting a WeChat public-account article whose URL host is `mp.weixin.qq.com`, especially links shaped like `https://mp.weixin.qq.com/s/<id>`.

Purpose: turn WeChat's script-heavy article HTML into a clean immutable source file under `.raw/articles/`, download article images into `.raw/assets/wechat/[slug]/`, then return to the main `wiki-ingest` Single Source Ingest flow.

---

## When To Use

Run this before ordinary URL ingestion when:

- URL host is `mp.weixin.qq.com`
- The user provides a WeChat public-account article link
- Generic WebFetch returns noisy HTML, script output, or no usable prose

If this sub-processor cannot extract a non-empty article body, fall back to ordinary URL ingestion or ask the user for an exported copy.

---

## Extraction Contract

Input:

- WeChat article URL
- Current ingest date, used for the `.raw/articles/` filename and `fetched` field

Output:

- `.raw/articles/[slug]-[YYYY-MM-DD].md`
- Frontmatter:

```markdown
---
source_url: [url]
fetched: [YYYY-MM-DD]
title: "[extracted title]"
account: "[extracted public-account name]"
published: [YYYY-MM-DD]
assets_dir: ".raw/assets/wechat/[slug]"
---
```

Body:

```markdown
# [extracted title]

[cleaned article prose]
```

---

## Fetch Strategy

Fetch the article HTML with `curl`, not generic WebFetch:

- Use `-L --compressed -sS`
- Use a desktop browser `User-Agent`
- Use `Accept-Language: zh-CN,zh;q=0.9,en;q=0.8`
- If the first response looks like a captcha / verification page, retry with mobile browser user agents and `Referer: https://mp.weixin.qq.com/`.
- Save to a temp file such as `/tmp/wechat-article.html`

Reason: WeChat often includes the full article body in the initial HTML under `#js_content`, but generic fetchers may return noisy script-heavy output or fail to surface the body.

Captcha / verification indicators include: `环境异常`, `captcha`, `appmsgcaptcha`, and `验证后即可继续`.

---

## Fields To Extract

Check the HTML for these fields:

```bash
rg -n "msg_title|js_content|nickname|ct =" /tmp/wechat-article.html | sed -n '1,80p'
```

Expected fields:

- `var msg_title = ...` — article title
- `var nickname = ...` — public-account name
- `var ct = "..."` — Unix publish timestamp
- `id="js_content"` — article body HTML

Convert `ct` to `YYYY-MM-DD` for `published`.

Fallback selectors:

- Title: `h1#activity-name`, `h1.rich_media_title`, then `soup.title`
- Account: `a#js_name`, `span.rich_media_meta_nickname`
- Author: `span#js_author_name`, then rich media meta text
- Date: `em#publish_time`, then `meta[property="article:published_time"]`

---

## Image Download Rules

Download article images into:

```text
.raw/assets/wechat/[slug]/
```

Process every `<img>` inside `#js_content` unless it is a `data:` URL:

- Prefer `data-src`; fall back to `src`.
- Resolve protocol-relative URLs by prepending `https:`.
- Resolve relative URLs against the page URL.
- Request images with a desktop browser `User-Agent` and `Referer: [article-url]`.
- Guess extension from `Content-Type`, then URL path; default to `.jpg`.
- Name files deterministically with index + URL hash, e.g. `img_001_ab12cd34ef56.jpg`.
- Skip downloading if the target file already exists.

Replace the image URL in Markdown with a path relative to the source article file. For `.raw/articles/[slug]-[date].md`, use:

```markdown
![alt](../assets/wechat/[slug]/img_001_ab12cd34ef56.jpg)
```

If an image fails to download, keep the original remote URL and record the failure under `## Extraction Notes`.

---

## Body Cleaning Rules

Extract the inner HTML of `#js_content`, then:

- Treat `br`, `p`, `section`, headings, blockquotes, and list items as paragraph breaks.
- Decode HTML entities, including numeric entities.
- Strip remaining tags.
- Collapse repeated whitespace inside a line.
- Preserve paragraph breaks.
- Preserve downloaded images as Markdown image links into `.raw/assets/wechat/[slug]/`.
- If image OCR matters, run Image / Vision Ingestion for those downloaded files and link the results from the source summary.

The resulting body should be mostly article prose, not JavaScript, CSS, navigation, comments, or ad boilerplate.

---

## Slug Rule

For `/s/<id>` links, use the article id lowercased as the slug:

```text
https://mp.weixin.qq.com/s/L11cw9ecXrmwbX4CV5P9yA
=> l11cw9ecxrmwbx4cv5p9ya
```

Save as:

```text
.raw/articles/[slug]-[YYYY-MM-DD].md
```

---

## Quality Gate

Before returning to the main ingest flow:

- Confirm the source file exists in `.raw/articles/`.
- Confirm downloaded images exist in `.raw/assets/wechat/[slug]/` when the article contains images.
- Confirm Markdown image links are relative and resolve from the source file.
- Confirm the title/account/published fields were extracted when present.
- Confirm body length is non-trivial and content is human-readable prose.
- If `#js_content` is missing or empty, stop this sub-processor and use the ordinary URL fallback.
- If important article content is only inside images, run Image / Vision Ingestion for the downloaded images and link the results from the source summary.

After the quality gate passes, proceed with Single Source Ingest on the saved `.raw/articles/` file.
