---
name: merge-meeting-notes
description: Merges multiple AI-generated summaries or transcripts from the same meeting (e.g. Gemini, Granola, Otter) into one unified, deduplicated note saved to this repo.
version: "1.0.0"
category: productivity
tags:
  - meeting
  - notes
  - merge
  - summary
  - transcript
---

# Merge Meeting Notes

## Overview

When the same meeting was captured by multiple AI note-takers (Gemini, Granola, Otter, etc.), this skill merges all sources into a single authoritative note — deduplicating content, filling gaps, flagging conflicts, and saving the result in the correct repo path.

## How to Use

Provide the meeting context and each source clearly labelled:

> "Use the merge-meeting-notes skill.
> Meeting: [company/client/project], [date]
> **Granola:** [paste]
> **Gemini:** [paste]"

You can include as many sources as you have. The labels can be anything (Granola, Gemini, Otter, Manual, etc.).

## Merge Process

### Step 1 — Read all sources in full before writing anything

For each source, identify:
- Topics and sections covered
- Action items and their owners
- Decisions made
- Unique details not in other sources
- Any contradictions with other sources

### Step 2 — Resolve conflicts

| Situation | Rule |
|---|---|
| Different timestamps/dates | Prefer the more specific one |
| "Someone" vs a named person | Prefer the named person |
| Contradicting facts | Include both with a `⚠️ Conflict:` note |
| Action item in only one source | Include it — union of all sources |
| Same point worded differently | Pick the clearest wording, don't duplicate |

### Step 3 — Write the merged note

Use the repo's note format — `###` headings, bullet lists per section:

```markdown
### [Topic]

- Key point from any source
- Another key point

### [Another Topic]

- ...

### Next Steps

- [ ] [Action] - [Owner]
- [ ] [Action] - [Owner]

---

> Merged from: [Source 1], [Source 2], ...
> Transcript links:
> - [Source 1 name]: [URL if provided]
> - [Source 2 name]: [URL if provided]
```

### Step 4 — Suggest the file path

Derive the correct path from the meeting details:

```
{company}/{client}/{project}/YYYY/MM/DD-MM-YYYY_meeting-description.md
```

Present the suggested path and ask the user to confirm before saving.

## Quality Checklist

Before presenting output, verify:
- [ ] No action item is listed twice
- [ ] Every named person's commitments are captured
- [ ] `⚠️ Conflict:` markers appear wherever sources disagree
- [ ] "Merged from" footer lists all sources
- [ ] All transcript URLs are collected in the footer (if provided)
- [ ] File path follows `DD-MM-YYYY` date format
- [ ] All `###` sections use sentence-style headings consistent with existing notes in the repo
