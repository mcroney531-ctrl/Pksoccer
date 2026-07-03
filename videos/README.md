# Video assets

Drop the kick-moment clips here using these exact filenames — `index.html`
picks one at random from the matching pool for every kick:

- `make_1.mp4` through `make_5.mp4` — goal clips (all 5 in place)
- `miss_1.mp4`, `miss_2.mp4`, `miss_3.mp4` — save/miss clips (still placeholders)

Notes:

- Clips play muted (autoplay policy) with a tap-to-unmute button; keep the
  make/miss moment readable without sound.
- The "GOAL!"/"SAVED!" text overlay appears in the last ~1.5s of the clip
  (or on end), so trim clips so the outcome is visually clear by then.
- Any aspect ratio works — clips are shown `object-fit: cover` fullscreen
  over the stage.
- If a file listed above is missing, the game fails silently and skips
  straight to the feedback panel, so it's safe to ship without all six
  clips in place.
