# Penalty Shootout: Soccer Rules Showdown

A single-page, no-build static game. Answer soccer rules questions to take
penalty kicks against an AI keeper across 5 regulation rounds and sudden
death, with an early-elimination check the moment a comeback becomes
mathematically impossible.

## Project structure

```
/index.html       game (markup, CSS, and JS all in one file)
/videos/          make_1-3.mp4, miss_1-3.mp4 kick-moment clips
/README.md
```

## The kick flow

1. Pick an answer — it highlights neutral (no right/wrong color yet).
   Correctness is locked in immediately but not revealed.
2. A "Take Your Kick" ball appears. Swipe up (or just tap) to strike it —
   built on the Pointer Events API, so mouse drag and touch swipe share one
   code path. Swipe direction only steers which corner the ball visually
   heads toward; it never changes whether the kick is a make or a miss.
3. A random clip plays from `/videos/make_*.mp4` or `/videos/miss_*.mp4`
   (muted, with tap-to-unmute) matching the locked-in outcome. "GOAL!" or
   "SAVED!" text overlays in the final couple seconds of the clip.
4. The feedback panel (result + rules explanation) appears after the clip
   ends, then play continues to the AI's kick as before.

If a video file is missing or fails to load, the game skips it silently and
goes straight to the feedback panel — see `videos/README.md` for the
expected filenames.

## Running locally

No build step. Just serve the folder statically, e.g.:

```
python3 -m http.server 8080
```

then open `http://localhost:8080/`.

## Deploying

Static hosting (Netlify, etc.) with no build command and publish directory
set to the repo root. The CSS `transform: scale(...)` fit works from any
real `https://` origin; local `content://` file preview quirks on mobile are
expected and not a target for this build.

## Constraints this build respects

- Vanilla JS/CSS only, no npm or build tools.
- No dependencies that would break inside a Storyline 360 web object iframe.
- Video files are linked assets under `/videos`, never inlined as base64.
