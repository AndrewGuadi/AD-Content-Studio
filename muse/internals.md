# How Muse structures things internally

So collaborators can read Muse's notes without guessing at its system.

## Goals

- A goal is a durable outcome with a timeframe (e.g. "Instagram operations
  for Authentic Dynamics"). Each goal has a workspace with a `GOAL.md`
  (Muse's notes on the goal) and two folders:
  - `files/` — documents the user asked for, shown to the user as the goal's
    documents.
  - `hidden_files/` — internal bookkeeping: run logs, watermarks, seen
    lists, check logs. Never user-facing.
- Goals stay open until the outcome is resolved; one finished step does not
  close a goal.

## Content

- Series live in per-series folders with one folder per episode containing
  the package (script, caption, cover plan), the video, the subtitles file,
  the cover image, and the caption text.
- Production pipeline: script from sourced material → cloned-voice narration
  (chunked, resumable) → assembly (stills spine; generated motion clips can
  be swapped in later without rebuilding narration or captions) → QC
  (frame grabs, caption-vs-narration check) → staged for approval.
- Publishing is approval-shaped: every feed post and every story needs its
  own tap. After any publish attempt, Muse verifies the live account before
  logging success — an interrupted call may still have landed.
- The publish log records verified publishes only, plus explicit NOT-POSTED
  entries for declined items, so "declined" is never confused with "pending."

## Interactions

- Main chat is the primary conversation. Approvals arrive as cards the user
  taps; a card left untapped parks the work, and a late tap still releases it.
- Scheduled work runs on crons (e.g. the SnowFight challenge reviewer, every
  3 hours through the Oct 30 deadline). Each run reports to the main chat.
- Proactive messages only go out in Andrew's window (09:00–21:30 local) and
  only when genuinely new and worth interrupting for.
- Memory: a curated long-term file plus dated daily notes. Memory never
  grants permission to act and never holds credentials.

## How to read Muse's files here

- `understanding.md` — what Muse believes and is acting on. Correct it when
  wrong; Muse updates it from corrections.
- `content-inventory.md` — the running track of created and accessible
  content. This is the file to check for "what exists and what's its status."
- `activity-log.md` — what Muse did in this repo, newest first.
