# Stage 3: Canvas Overlay

## Goal

Draw a glowing dot on top of the video feed that follows the index fingertip in real time, turning raw coordinates from Stage 2 into an actual visual.

## Concept

A `<canvas>` element is placed directly on top of the `<video>` element using CSS positioning (`position: absolute`, both at `top: 0, left: 0`, same width and height). This makes them stack perfectly, so anything drawn on the canvas appears to sit on top of the live video.

The coordinates coming from MediaPipe are 0 to 1, relative to the frame size, not actual pixel positions. To draw at the correct spot, each coordinate gets multiplied by the canvas width or height:

pixelX = x * canvas.width
pixelY = y * canvas.height

Every frame, two things happen in order:

1. `ctx.clearRect()` wipes the previous frame's dot off the canvas. Without this step, dots would pile up and leave a trail instead of tracking cleanly.
2. A new dot gets drawn at the current fingertip position.

This clear then redraw pattern is the standard approach for any real time canvas animation, not just this project.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Allow camera access when prompted.
4. Wait for the model to load, then move your hand in front of the camera.
5. A glowing pink dot should appear directly on your index fingertip and follow it as you move.

## What to notice

Move your hand quickly and watch whether the dot keeps up. Some lag is normal since detection takes a small amount of processing time per frame. This same drawing technique, glow gradient plus solid core, is the visual foundation for the neon HUD concept planned for the festival demo. Stage 7 will expand this into a fuller effect with particles and multiple points tracked at once.

## Status

Complete.