---
name: create-blog-post
description: "Use when asked to create a blog post for the Maturity Model site, including a Practitioners Call archive post from an issue created with the Practitioners Call post form."
argument-hint: "The issue number, or the post type plus its inputs"
user-invocable: true
disable-model-invocation: false
---

# Create a Blog Post

Create one post under `docs/blog/` and list it in the blog index.

## Post types

Every post has a `type` in its front matter. The type decides the template and the inputs.

| Type | Use for | Inputs | Template |
|---|---|---|---|
| `archive` | One recorded Practitioners Call | Practitioners Call post issue form | [Archive post](#archive-post) |

Add a new type by adding a row here and a template section below. Do not invent a type that is not in the table.

## Rules for every post

- All facts come from the issue (or the user). Never invent people, credentials, quotes, dates or links. Leave a section out rather than guess.
- File name: `docs/blog/YYYY-MM-DD-<slug>.md`, using the event date for `archive` and the publish date otherwise.
- Add the post at the top of its type's list in `docs/blog/index.md` (newest first) and to `docs/blog/toc.yml` (newest first).
- Run `git diff --check`, check that every relative link resolves, and open a PR that says `Fixes #<issue>` and lists anything left out for lack of evidence.

## Archive post

### Inputs

Session date, topic, speakers, speaker plugs, recording URL, slides link, transcript, links mentioned.

- Do not fetch the YouTube transcript or watch the video. The transcript is pasted into the issue. If it is missing, stop and ask for it in the issue.
- The session date is the date of the call, not the upload date.
- Speaker plugs come only from the issue, never from the transcript.
- Check the recording ID against existing archive posts and the legacy archive page; do not create a duplicate.

### Chapters

Build chapters only from timestamps in the transcript (YouTube's copied transcript has `m:ss` lines; `.vtt` has cue times). Aim for 5–10 chapters at real topic shifts. Each links to `https://www.youtube.com/watch?v=<ID>&t=<seconds>s`. Without timestamps, omit Chapters and say so in the PR.

### Summary

Summarise the main presentation, not the community news at the start or the closing housekeeping. Follow Step 3 of the `update-practitioners-calls-archive` skill: original, source-grounded, opinions attributed to the speaker, no padding. Tags use the existing competency names.

### Template

```markdown
---
title: "<Topic>"
type: archive
date: <YYYY-MM-DD of the session>
ms.date: <MM/DD/YYYY today>
author: <GitHub handle of the issue author>
ms.topic: overview
ms.service: microsoft-365
ms.collection: M365Community
description: "Practitioners Call, <Month YYYY>: <one sentence on what the session covered>."
---

# <Topic>

Practitioners Call, <D Month YYYY> · **Speaker(s):** <a href="<profile>" target="_blank"><Name, credentials></a>

> [!Video https://www.youtube-nocookie.com/embed/<ID>]

## Chapters

- [00:00](https://www.youtube.com/watch?v=<ID>&t=0s) <Chapter title>

## Summary

<Paragraphs.>

## Key takeaways

- <3–5 bullets>

## Presentation

<a href="<slides URL>" target="_blank">Slides (<format>)</a>

## About the speakers

### <Name, credentials>

<a href="<profile URL>" target="_blank">LinkedIn</a> · <other public profiles from the issue>

- <Plug: what it is> – <a href="<URL>" target="_blank"><title></a>

## Links

- Competencies discussed: [<Competency>](../competencies/<file>.md)
- <Resources mentioned, from the issue>

`<Existing tag>`, `<Existing tag>`

[← All posts](index.md)
```
