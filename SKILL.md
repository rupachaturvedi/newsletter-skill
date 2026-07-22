---
name: newsletter-skill
description: Use when the user wants to process, triage, or catch up on the newsletters in their inbox, clear a newsletter backlog, or turn newsletters into notes they can keep. Reads recent newsletter emails and writes one short, structured note per issue, so reading turns into something searchable instead of an unread pile. Triggers on phrases like "process my newsletters", "catch me up on my newsletters", "turn my newsletters into notes", "clear my newsletter backlog", or "what came in this week".
---

# Newsletter Skill

Turn the newsletters sitting in your inbox into a clean, structured note per issue. This is the first step of a second-brain practice. It hands the triage and filing to Claude, so your reading time goes to the substance and you keep a note of what mattered.

## What counts as a newsletter

By default, process emails that carry the Gmail label `Newsletters`. Reference the label by name, which is more reliable than a label ID on some mail connectors. If that label does not exist, ask the user which they prefer:

- A label they apply to newsletters (recommended, most reliable)
- A list of sender addresses or domains to treat as newsletters
- Gmail's `Updates` category as a fallback

Only process the range the user asks for. Default to the last 7 days, unread first. If there are more than about 25, report the count and confirm before writing notes. Some publications send several emails a day, so group by sender when you report the count, so the user sees the real volume.

## Get clean text out of the email first

Newsletter emails are HTML and often very large. Do not read the raw message end to end, it will be mostly markup.

- If the message has a plaintext body, use it.
- Otherwise take the HTML body, drop the `<script>` and `<style>` blocks, strip the remaining tags, decode HTML entities, and delete the invisible preheader padding many senders inject (zero-width and soft-hyphen characters). Work from the resulting text.
- The real content usually sits near the top: a title, an author, a date, and the opening paragraphs. That is enough for a faithful summary.

## For each newsletter

1. Read the extracted text, not the raw HTML.
2. Skip anything with no substance: receipts, event reminders, and issues that are mostly a subscribe or upgrade pitch. Some publications send frequent upsell emails that tease a paywalled report. If the lede carries one real signal, capture that in a line, then move on. Track what you skipped so you can report it.
3. Extract:
   - **Source**: the publication or author (for example "The Information, AI Agenda" or "Lenny's Newsletter").
   - **Date**: the send date.
   - **Link**: the canonical link to the issue if one is present, otherwise leave it blank. Do not use tracking links.
   - **Summary**: 2 to 4 sentences on what the issue actually says. Be faithful. Do not add hype, do not editorialize, do not use marketing language.
   - **Why it matters**: 1 to 2 lines on why this might be worth returning to. If nothing stands out, say so plainly.

## Write each note as a markdown file

- Output folder: `./Newsletter Notes/`, created if missing, or a folder the user names. Obsidian users can point this at their vault.
- Filename: `YYYY-MM-DD - {Source} - {Short Title}.md`
- Note format:

```
---
date: YYYY-MM-DD
source: {Source}
url: {link}
---

# {Title}

**Source:** {Source}
**Date:** {Month DD, YYYY}
**Link:** {url}

## Summary

{2 to 4 sentence faithful summary}

## Why it matters

{1 to 2 lines}
```

## After processing

Print a short recap: how many issues you turned into notes, how many you skipped and why, and any theme you noticed showing up across more than one issue. Keep it to a few lines.

## Rules

- Faithful over impressive. The value is an accurate record, not a clever one.
- One note per issue. Do not merge unrelated newsletters into a single note.
- No invented links. If there is no canonical URL, leave the field blank.
- Do not add tags, scores, or categories beyond the fields specified here. Keep the note tight.
