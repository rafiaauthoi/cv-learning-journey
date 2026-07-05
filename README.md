# cv-learning-journey

A hands-on log of learning motion sensing and computer vision, starting from zero experience, built stage by stage using open source tools only.

## Why this exists

This repo documents the process of learning webcam based interaction, hand and face tracking, and gesture driven visuals and sound. Each stage is a small, working example that builds on the one before it. The goal is to end up with real interactive projects that can be used for showcases & workshops, and to leave behind a clear trail other developers can follow to learn the same skills.

## Tools used

All tools in this repo are free and open source. No paid services or APIs are used at any stage.

- MediaPipe (hand and face landmark detection)
- Canvas API (drawing and visual overlays)
- Tone.js (sound generation)

## Stages

Each folder is a self contained step. Open any folder's own README for setup instructions.

- `stage-1-webcam-feed` - getting a live camera feed into the browser
- `stage-2-mediapipe-hands` - detecting hand landmarks in real time
- `stage-3-canvas-overlay` - drawing visuals on top of the video feed
- `stage-4-gesture-logic` - turning raw coordinates into gestures
- `stage-5-sound-mapping` - mapping hand movement to sound
- `stage-6-face-tracking` - detecting and overlaying face landmarks
- `stage-7-combined-demo` - combining tracking, visuals, and sound into one interactive demo

## Status

Complete. All 7 stages are done.

## For WMU Developer Club members

Feel free to clone this and follow along stage by stage. If a stage grows into a full standalone project, it will get its own separate repo, and it will be linked here.