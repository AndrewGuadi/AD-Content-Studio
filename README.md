# AD Content Studio

The shared working repo for Authentic Dynamics content. This is where content
plans, briefs, and tracking live so that everyone building on it — Andrew,
Muse, and other collaborators — works from the same picture.

## Layout

- `muse/` — Muse's section. Its understanding of the work, its running
  content inventory, how it structures things internally, and its activity log.
- `collaborators/` — where other contributors drop notes, briefs, and
  material. See `collaborators/README.md` for the convention.
- `content/` — (created on demand) briefs and packages for content in
  production. Finished media files themselves are NOT stored here; they live
  in Muse's workspace and on Instagram once published. This repo tracks
  metadata, status, and links — not binaries.

## Rules that apply to everything in here

- Nothing here is published to Instagram, deleted, or sent to followers
  without Andrew's explicit per-item approval. A plan or a draft is never
  approval to publish.
- No invented creative direction. Content is built from sourced material:
  Andrew's transcripts, packages, published lines, and verified facts.
  (Bounded exception: the two reels commissioned Oct 29, 2026, where Andrew
  explicitly told Muse to use its own spin.)
- No decision-grade claim about social performance is made on a partial
  picture. Organic insights alone are not the full picture — paid activity
  must be included or the gap stated plainly.
- This repo is public. Never put credentials, tokens, private account IDs,
  or non-public personal details in it.

## How Muse stays in sync with this repo

There is no push webhook into Muse — GitHub cannot wake Muse directly.
The working mechanism is a scheduled check: Muse pulls the repo on a
schedule, diffs against the last commit it has seen, reads anything new
(especially in `collaborators/`), updates its inventory and activity log,
and reports what changed. A watcher schedule is proposed in
`muse/activity-log.md` and is set up only once Andrew confirms the interval.
Until then, Muse checks this repo whenever Andrew points at it.
