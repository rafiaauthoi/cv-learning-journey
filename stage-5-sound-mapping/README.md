# Stage 5: Sound Mapping

## Goal

Turn hand position into sound. Vertical hand movement controls pitch, horizontal hand movement controls volume, creating a basic theremin style instrument controlled entirely by hand tracking.

## Concept

### Tone.js

Tone.js is a free, open source library built on top of the browser's native Web Audio API. It handles the complicated parts of audio (oscillators, timing, scheduling) so a usable synthesizer can be built in a few lines instead of dozens.

### The browser audio rule

Browsers refuse to play any sound until a real user interaction happens first, usually a click. This is a deliberate anti-annoyance policy across all browsers, not something specific to this project. That is why this stage has a "Start Audio" button. `Tone.start()` must be called inside that click handler, calling it any other way will silently fail.

### Mapping coordinates to sound

The key technique here is range mapping, taking a number in one range and converting it proportionally into a different range:

mapRange(value, inMin, inMax, outMin, outMax)

Wrist y-position (0 to 1, top to bottom) gets mapped to frequency (1000 Hz down to 130 Hz), with the direction flipped so a higher hand produces a higher pitch. Wrist x-position (0 to 1, left to right) gets mapped to volume in decibels (-40 dB to -5 dB).

This same `mapRange` function is reusable for almost anything: coordinates to color, coordinates to rotation, coordinates to size. It is one of the most useful small tools in this entire skill set.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Click "Start Audio" first. This step cannot be skipped or reordered.
4. Allow camera access when prompted.
5. Move your hand up and down to change pitch, left and right to change volume.

## What to notice

If no sound plays, check that "Start Audio" was clicked before anything else, and check your system volume. If the pitch changes feel jumpy rather than smooth, that is normal for this simple version, small tracking noise gets amplified into audible pitch jitter. Smoothing that out (for example, averaging the last few positions) is a common next improvement but is intentionally left out of this stage to keep the core concept clear.

## Status

Complete.