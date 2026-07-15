# Newsletter Notes

A small Claude Code skill that reads the newsletters in your inbox and turns each one into a clean, structured note you keep. It is the first step of building a second brain: stop reading to keep up, start reviewing.

## Why

The volume of writing worth reading now outpaces anyone's ability to hold onto it. You save more, subscribe to more, and end up with an archive you never reopen. This skill hands the reading to Claude and leaves you with notes you can review and search.

## What you need

- Claude Code
- A connected email source (a Gmail connection is the common one)
- A folder to write notes into (any folder works; Obsidian users can use their vault)

## Install

1. Create the folder `.claude/skills/newsletter-notes/` in your project or home directory.
2. Copy `SKILL.md` into it.
3. In Gmail, create a label called `Newsletters` and apply it to the newsletters you want processed. A Gmail filter can do this automatically for known senders.

## Use

Ask Claude:

> Process my newsletters from this week.

The skill reads them, skips the promotions, and writes one note per issue into a `Newsletter Notes` folder. Each note carries the source, the date, a faithful summary, and a line on why it matters.

## Example output

```
# Evaluating Models Is Getting Even Harder

**Source:** The Information, AI Agenda (Stephanie Palazzolo)
**Date:** July 14, 2026

## Summary

Judging how good AI is at various tasks is getting harder as models improve.
The obvious reason is benchmark saturation. The subtler one, surfaced at ICML:
models can now work a single task for hours or days, so measuring their
performance takes hours or days too.

## Why it matters

Evaluation is the bottleneck for trusting agentic systems. If judging output
takes as long as producing it, eval design becomes core product work.
```

## Where this goes next

This is the intake step. The real value shows up in what accumulates over months, when the notes start to compound. I write about that in my newsletter, Shifting Ground.

## Credit

Built by Rupa Chaturvedi at HCAI Institute.

## License

MIT. Use it, change it, share it.
