---
name: summarize-meeting
description: >
  Summarize meeting notes or transcripts into decisions, action items with
  owners/deadlines, and unanswered questions. Use when the user invokes
  /summarize-meeting, pastes meeting notes/transcripts, or asks in natural
  language to summarize a meeting and list everyone's action items.
---

# Summarize meeting

Reusable workflow for turning raw meeting notes or a transcript into a
consistent, scannable summary. Activate with `/summarize-meeting` or a natural
request such as: "Please summarize this meeting and list everyone's action items."

## Required inputs

Ask only for what is missing before summarizing:

1. **Meeting material** — notes, transcript, or recording summary (required).
2. **Meeting context** (optional but helpful) — title, date, attendees.
3. **Focus** (optional) — e.g. decisions only, one workstream, or one owner.

If the material is empty or clearly incomplete, ask one clarifying question and
stop. Do not invent attendance, decisions, or owners.

## Steps

1. Read the full material once. Prefer what was said over what you infer.
2. Extract **confirmed decisions** only when the notes state them as decided,
   agreed, approved, or locked. Put softer ideas under suggestions.
3. Extract **action items** with owner and deadline when present. If owner or
   deadline is missing, leave the cell as `TBD` — never guess a person or date.
4. List **unanswered questions** still open at the end of the meeting.
5. Write a short summary (see output template). Keep it under 150 words.
6. Run the quality checklist below before returning the result.

## Output template

Use this shape every time:

```markdown
# Meeting summary

**Meeting:** <title or "Untitled">
**Date:** <date or "Unknown">
**Attendees:** <names, or "Not listed">

## Summary

<≤150 words. What the meeting was about and what moved forward. Plain language.>

## Confirmed decisions

- <decision>
- <decision>

(If none: `_No confirmed decisions recorded._`)

## Suggestions (not decided)

- <suggestion or proposal still open>

(If none: omit this section.)

## Action items

| Action | Owner | Deadline |
| --- | --- | --- |
| <task> | <name or TBD> | <date or TBD> |

(If none: `_No action items recorded._`)

## Unanswered questions

- <open question>

(If none: `_None noted._`)
```

## Quality checklist

Before returning output, verify:

- [ ] Decisions are correct and only include confirmed ones (not suggestions).
- [ ] Action items are present when the notes contain them.
- [ ] Owners and deadlines are filled when stated; otherwise `TBD`.
- [ ] Action items are always in a **table** (never a bullet list).
- [ ] Summary is under **150 words**.
- [ ] Confirmed decisions are separated from suggestions.
- [ ] Output is easy to skim on a phone or in chat.

## Hard constraints

- Do not invent facts, attendees, decisions, owners, or deadlines.
- Do not merge "we should" / "maybe" into Confirmed decisions.
- Do not add filler commentary, motivational closers, or hashtags.
- Keep terminology from the notes when it is domain-specific; otherwise prefer
  plain everyday words.
- One idea per sentence in the Summary section.

## Improve through conversation

If the user corrects the result, update future runs in this chat to match — for
example:

- Always put action items in a table.
- Keep the summary under 150 words.
- Separate confirmed decisions from suggestions.

Treat those corrections as standing rules for the rest of the session unless the
user reverses them.
