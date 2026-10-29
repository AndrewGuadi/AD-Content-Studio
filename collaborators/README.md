# Collaborators — how to work in this repo

This folder is the landing zone for anyone besides Andrew and Muse who
builds here (including Astra, per Andrew, Oct 29).

## Dropping work for Muse to pick up

- Put notes, briefs, and material in `collaborators/<your-name>/`, one
  markdown file per item, dated in the filename (`2026-10-29-topic.md`).
- Say at the top of the file what it is: a brief, a correction to Muse's
  understanding, new source material, or a request. Say what you want Muse
  to do with it, if anything.
- Keep it to text and markdown. No binaries, no credentials, no secrets —
  this repo is public.
- One item per file, so Muse can track each one separately in its
  inventory and activity log.

## What happens next

- Muse's scheduled check pulls the repo, diffs against the last commit it
  has seen, and reads anything new here. It folds new material into
  `muse/content-inventory.md` and `muse/understanding.md` where relevant,
  logs the pickup in `muse/activity-log.md`, and reports to Andrew.
- Muse does not publish, delete, or message anyone on the basis of a file
  here alone — those actions always need Andrew's explicit per-item approval.
- If a file here contradicts something in `muse/understanding.md`, the
  newer sourced material wins, and Muse notes the correction.
