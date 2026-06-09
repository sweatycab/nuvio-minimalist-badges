# Nuvio Minimalist Badges

A clean badge icon set for the Nuvio Android TV app, with regex-based detection for resolution, source quality, dynamic range, codecs, audio, and channels.

## How it works

Two pieces work together. The AIOStreams formatter runs server-side and emits the stream's title/description — including invisible Unicode tokens for dynamic range (DV / HDR10+ / HDR / SDR) so those are detected reliably rather than guessed from the filename. Nuvio then runs the badge regex (from the JSON below) against that description and displays the matching badges.

## Setup

1. Add the formatter code in AIOStreams. Set your Title template to the contents of `title-template.txt`, and your Description template to the contents of `description-template.txt` (copy that file exactly — it contains invisible characters that must be preserved). If you run your own description template, add the `dynamic-range-block.txt` snippet somewhere inside it to get the dynamic-range tokens.

2. Add a badge set to Nuvio. Import whichever style suits you:
   - `badges-white.json` — white icons
   - `badges-white-no-codecs.json` — white, without codec badges
   - `badges-mixed.json` — mixed colour
   - `badges-mixed-no-codecs.json` — mixed, without codec badges

3. Disable Nuvio's built-in size badge for a consistent look — the description template already includes size, so the built-in one is redundant and clutters the row.
