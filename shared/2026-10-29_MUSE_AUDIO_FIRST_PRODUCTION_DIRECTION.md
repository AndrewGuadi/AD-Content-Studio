# Muse production direction — clean voice first
Date: 2026-10-29
Owner request: review two unpublished reels and direct Muse, prioritizing **no extra background sound**. Founder explicitly confirms Muse has access to an approved high-quality clone of his voice.

## Evidence / status
- Source: Muse's repository inventory and archive manifest, not playback.
- Target drafts: A-002 "Start With One Job" (reported 80.4s); B-003 "What Your Wi-Fi Is Doing All Day" (reported 82.9s).
- GPT attempted the six-archive access route, including direct access to A/B ZIP URLs; playback files were not retrievable with tools in this chat. **No claim of listening or visual inspection is made.**
- This file is a revision brief, not approval to publish and not a QC-pass certificate.

## Nonnegotiable audio specification
1. **Narration ONLY** in the final video. **NO music beds, atmospheric tracks, room tone layers, ambience, whooshes, stingers, transition sound effects, typewriter noises or UI clicks.** Silence outside spoken narration. If visual footage includes recorded ambient audio, strip/mute its source audio before mixing.
2. Use Andrew's already-approved voice clone, not any alternate speaker. Do not train a new voice model from public photos/reels or imply Andrew personally recorded words he didn't review. Obtain his per-item approval for final clone rendition.
3. Generate narration from final approved script, one sentence/phrase at a time if necessary; preserve natural intonation, micro-pauses, and consistent pronunciation. Re-render awkward lines instead of pitch-bending or aggressive denoising.
4. Use one isolated narration stem; disable background generation and any automatic soundtrack defaults in video tools; strip all generated-video audio streams before muxing voice.
5. Keep clear headroom: suggested peak <= -1 dBTP, integrated loudness around -16 LUFS for stereo social export (or platform-equivalent, after an actual loudness measurement). Avoid clipping, pumping and harsh sibilance.
6. Validate with listening **and measurable tests**. Run ffprobe to inspect streams (expect exactly one audio stream). Use ffmpeg loudnorm/ebur128 or equivalent to inspect integrated loudness; inspect no-speech intervals, sample background to confirm near-silence, and manually audition intro, middle and ending with headphones. Automatic silence threshold is a diagnostic, not proof: very faint noise or music may be audible.
7. Captions must match actual final narration and screen timing. Make one review copy with narration isolated, and one ordinary final preview (same audio); do not add a soundtrack after approval.
8. Report whether the voice clone is accurate, with any hard-to-pronounce words called out. In B-003 say "Wi-Fi" consistently; clarify "router" versus "wireless access point" correctly.

## Example deterministic export approach
Source: narration.wav (single authorized voice track); visuals.mp4 (source may have audio). Example only; inspect actual media characteristics before use.

```bash
ffmpeg -i visuals.mp4 -i narration.wav -map 0:v:0 -map 1:a:0 \
  -c:v libx264 -crf 18 -preset medium -pix_fmt yuv420p \
  -af "loudnorm=I=-16:TP=-1.5:LRA=9" -c:a aac -b:a 192k \
  -ar 48000 -movflags +faststart final_narration_only.mp4
ffprobe -v error -show_entries stream=index,codec_type,codec_name \
  -of json final_narration_only.mp4
ffmpeg -i final_narration_only.mp4 -filter_complex "ebur128=peak=true" -f null -
```
Do not use the example blindly if audio/video duration doesn't match. Enforce full voice coverage, no trimmed words and clean ending. The best quality choice may be a two-pass loudness correction.

## Required Muse response
For **each** episode return: final playable MP4; isolated voice WAV/FLAC; final narration transcript; SRT; 3–5 screenshots including first, main explanation and closing frames; codec/duration; measured loudness, max peak; confirmation that every non-narration audio source was removed; list of any glitches or uncertain pronunciations. Mark status 'ready for founder review', never 'published'.
