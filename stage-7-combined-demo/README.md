# Stage 7: Combined Demo

## Goal

Combine everything from Stages 1 through 6 into one experience with two distinct modes: an idle ambient state that looks alive on its own, and an active state that responds directly to hand gestures with visuals and sound.

## Concept

### State machines

A state machine is a program that is always in exactly one "mode" at a time, with clearly different behavior in each mode. This stage has two states:

- **Idle**: triggered when no hand is detected. Ambient particles drift and pulse using sine wave based animation, purely decorative, meant to catch attention from a distance.
- **Active**: triggered the moment a hand is detected. Ambient particles stop, fingertip glow dots appear, a pinch triggers a short synth note, and raising the hand triggers a HUD text flash.

Switching modes each frame is just a single check:

```javascript
const handFound = results.landmarks && results.landmarks.length > 0;
if (!handFound) {
  // idle behavior
} else {
  // active behavior
}
```

Every other stage's technique feeds into one branch or the other.

### Triggering sound once, not repeatedly

A pinch might be held for many frames in a row. Without extra logic, that would fire the sound dozens of times per second while pinched. The fix is tracking the previous frame's pinch state (`wasPinching`) and only triggering sound the instant a pinch begins, when it was not pinching last frame but is pinching now:

```javascript
if (isPinching && !wasPinching) {
  synth.triggerAttackRelease(frequency, "8n");
}
wasPinching = isPinching;
```

This "trigger once on change, not on every frame while true" pattern applies to almost any one-shot reaction to a held gesture, not just sound.

### Ambient particle animation

Idle particles use `Math.cos` and `Math.sin` for smooth wandering motion, and a separate sine wave tied to `performance.now()` for a gentle pulsing size effect. This is a common lightweight technique for ambient background animation without needing a physics library.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Click "Start Demo" first, this is required before audio will work.
4. Allow camera access when prompted.
5. With no hand in frame, watch the idle particles drift and pulse.
6. Move your hand into frame, particles stop and fingertip dots appear.
7. Pinch thumb and index together to trigger a synth note.
8. Raise your hand up to trigger the "ENERGY CHARGED" HUD flash.

## What to notice

This is the closest version yet to an actual festival table demo. The idle state is what a passerby sees from a distance, calm, glowing, clearly alive. The active state is what rewards someone who actually steps up and puts their hand in frame. This two state pattern, ambient state plus a reactive state, is worth reusing for the final showcase build, along with tuning the specific colors, particle count, and thresholds to match Specter's visual identity.

## Status

Complete.