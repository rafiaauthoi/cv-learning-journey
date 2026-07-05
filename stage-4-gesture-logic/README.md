# Stage 4: Gesture Logic

## Goal

Turn raw fingertip coordinates into actual detected gestures. This stage adds pinch detection (thumb tip touching index tip) and raise detection (hand lifted above a height threshold).

## Concept

A gesture is just math applied to coordinates, compared against a threshold.

### Pinch detection

The distance between two points is calculated using the standard distance formula:

distance = sqrt((x2 - x1)^2 + (y2 - y1)^2)

This is applied to the thumb tip (landmark 4) and index tip (landmark 8). When that distance drops below `PINCH_DISTANCE_THRESHOLD` (currently 0.05), the fingers are considered close enough together to count as a pinch.

### Raise detection

The wrist's y-coordinate (landmark 0) is checked directly. Remember that y=0 is the top of the frame and y=1 is the bottom, so a smaller y-value means the hand is positioned higher. If wrist y drops below `RAISE_Y_THRESHOLD` (currently 0.4), the hand counts as raised.

### The general pattern

Every gesture in this stage follows the same three steps:

1. Pull the relevant landmark coordinates.
2. Run simple math on them (distance, comparison, angle, whatever fits).
3. Compare the result to a threshold and trigger a state change.

This pattern is reused for essentially any gesture you will build later, including more complex ones.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Allow camera access when prompted.
4. Try pinching your thumb and index finger together. The status panel below the video should say "Pinch: detected" and the fingertip dots should turn from pink to cyan.
5. Try raising your hand above roughly chest height. The status panel should say "Raise: detected."

## What to notice

The thresholds (`PINCH_DISTANCE_THRESHOLD` and `RAISE_Y_THRESHOLD`) are tunable numbers, not fixed rules. If pinch detection feels too sensitive or not sensitive enough, adjust `PINCH_DISTANCE_THRESHOLD` up or down and refresh. Same for the raise height. Tuning thresholds by trial and error is completely normal in gesture based projects, there is no universally correct number, only what feels right for the specific camera angle and use case.

## Status

Complete.