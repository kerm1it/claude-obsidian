# X / Twitter Sub-Processor

Use this sub-processor when ingesting a public X/Twitter status URL whose host is `twitter.com`, `www.twitter.com`, `x.com`, or `www.x.com`, and whose path matches `/[screen_name]/status/[tweet_id]`.

Purpose: turn a tweet, media tweet, or X Article into a clean immutable source file under `.raw/articles/`, download media assets into `.raw/assets/twitter/[tweet-id]/`, then return to the main `wiki-ingest` Single Source Ingest flow.

This workflow is inspired by Microsoft MarkItDown PR #1708, which uses the FXTwitter API to obtain structured tweet and X Article data.

---

## When To Use

Run this before ordinary URL ingestion when:

- URL host is `twitter.com`, `www.twitter.com`, `x.com`, or `www.x.com`
- URL path contains `/status/[tweet_id]`
- The tweet is public enough for FXTwitter to resolve it

If FXTwitter fails or returns incomplete data, fall back to ordinary URL ingestion or ask the user for an exported copy / screenshot.

---

## Extraction Contract

Input:

- X/Twitter status URL
- Current ingest date, used for the `.raw/articles/` filename and `fetched` field

Output:

- `.raw/articles/twitter-[tweet-id]-[YYYY-MM-DD].md`
- Frontmatter:

```markdown
---
source_url: [url]
fetched: [YYYY-MM-DD]
source_type: tweet
tweet_id: "[tweet-id]"
author_name: "[display name]"
author_handle: "[screen_name]"
published: "[created_at]"
assets_dir: ".raw/assets/twitter/[tweet-id]"
---
```

Body:

```markdown
# [title]

## Tweet

[tweet text or article body]

## Media

[downloaded images, cover images, video thumbnails, and remote video links]

## Stats

| 浏览 | 点赞 | 转发 | 收藏 | 评论 |
|------|------|------|------|------|
| ...  | ...  | ...  | ...  | ...  |
```

---

## Fetch Strategy

Extract `screen_name` and `tweet_id` from the original URL, then request:

```text
https://api.fxtwitter.com/[screen_name]/status/[tweet_id]
```

Use a desktop browser `User-Agent`. Parse the JSON response and use the top-level `tweet` object.

Do not rely on scraped Twitter/X HTML as the primary path; it is frequently incomplete, login-gated, or script-heavy.

---

## Tweet Fields To Extract

For ordinary tweets:

- `tweet.author.name`
- `tweet.author.screen_name`
- `tweet.text`
- `tweet.created_at`
- `tweet.likes`
- `tweet.retweets`
- `tweet.replies`
- `tweet.views`
- `tweet.bookmarks`
- `tweet.media.all[]` for photos
- `tweet.media.videos[]` for videos and thumbnails

For X Articles, prefer `tweet.article`:

- `article.title`
- `article.preview_text`
- `article.cover_media`
- `article.content.blocks`
- `article.content.entityMap`
- `article.media_entities`

Convert Draft.js-like article blocks into Markdown:

- `header-two` -> `##`
- `header-three` -> `###`
- `blockquote` -> Markdown blockquote
- `unordered-list-item` -> `-`
- `ordered-list-item` -> `1.`
- `code-block` -> fenced code block
- `unstyled` -> paragraph
- `atomic` media entities -> downloaded image links
- `LINK` entities -> Markdown links
- `Bold` inline styles -> `**bold**`

---

## Asset Download Rules

Download media into:

```text
.raw/assets/twitter/[tweet-id]/
```

Photos:

- Use each photo URL from `tweet.media.all[]` where `type == "photo"`.
- Name files deterministically with index + URL hash, e.g. `tw_img_001_ab12cd34ef56.jpg`.

X Article images:

- Download cover image from `article.cover_media.media_info.original_img_url` when present.
- Download embedded article images by mapping `atomic` media entity IDs through `article.media_entities`.

Videos:

- Do not download full video files by default.
- Download video thumbnails when available.
- Include the remote video URL in Markdown as a plain link.

Use paths relative to the source article file. For `.raw/articles/twitter-[tweet-id]-[date].md`, use:

```markdown
![图片1](../assets/twitter/[tweet-id]/tw_img_001_ab12cd34ef56.jpg)
```

If media download fails, keep the remote URL and record the failure under `## Extraction Notes`.

---

## Slug Rule

Use the tweet id as the stable slug:

```text
https://x.com/example/status/1234567890
=> twitter-1234567890
```

Save as:

```text
.raw/articles/twitter-[tweet-id]-[YYYY-MM-DD].md
```

---

## Quality Gate

Before returning to the main ingest flow:

- Confirm the source file exists in `.raw/articles/`.
- Confirm the author, handle, tweet id, and source URL are recorded.
- Confirm media Markdown links resolve to `.raw/assets/twitter/[tweet-id]/` when media was downloaded.
- Confirm the body contains either tweet text, X Article content, or a useful media/video description.
- If FXTwitter returns no `tweet` object, stop this sub-processor and use ordinary URL fallback.

After the quality gate passes, proceed with Single Source Ingest on the saved `.raw/articles/` file.
