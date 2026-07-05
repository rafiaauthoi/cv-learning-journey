# Stage 2: MediaPipe Hands

## Goal

Detect a hand in the webcam feed and read out real coordinates for key points, like the wrist and fingertips, updating live as the hand moves.

## Concept

MediaPipe provides a pretrained hand landmark model, meaning it already learned what hands look like from a large training set. Nothing gets trained here, the model is simply loaded and used.

For every video frame, the model returns 21 landmark points per detected hand. Each point has:

- x: horizontal position, 0 to 1, relative to the frame width
- y: vertical position, 0 to 1, relative to the frame height
- z: rough depth, relative to the wrist

This stage only reads three of those 21 points for clarity: the wrist, the index fingertip, and the thumb tip. Stage 4 will use the distance between fingertip points to detect gestures like a pinch.

The model runs fully in the browser using WebAssembly. No account, no API key, no server calls, no cost. It is open source under the Apache 2.0 license.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Allow camera access when prompted.
4. Wait a moment for the model to load, then move your hand in front of the camera.
5. You should see live coordinates for your wrist, index tip, and thumb tip updating on screen.

An internet connection is required the first time you run this, since the model file and MediaPipe library load from a CDN rather than being installed locally. Once cached by the browser, it may load faster on repeat visits.

## What to notice

Try moving your hand closer to and farther from the camera and watch how the numbers shift. Try touching your thumb tip to your index tip and watch how close their x and y values get. That closeness is exactly what "pinch detection" measures, which becomes useful starting in Stage 4.

## Status

Complete.