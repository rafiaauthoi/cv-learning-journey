# Stage 6: Face Tracking

## Goal

Detect a face in the webcam feed and overlay a sci-fi style scanning effect, a bounding box with corner brackets plus a simplified wireframe mesh over the jawline, eyes, and lips.

## Concept

MediaPipe's Face Landmarker works the same way as the hand model from Stage 2, a pretrained model that returns coordinates for every video frame. The difference is scale: it returns 478 points per face instead of 21 points per hand, covering the entire face structure in detail.

### Why not draw all 478 points

Drawing every single point as a dot would look like visual noise rather than a clean effect. Instead, this stage picks a small, meaningful subset of landmark indices, ones that trace the jawline, eyes, and lips, and connects them with lines to form a simplified wireframe. This is a common technique in face tracking projects: use only the landmarks relevant to the effect you want, not the entire dataset every time.

### The bounding box scan effect

`drawScanBox` loops through every landmark to find the minimum and maximum x and y values, which defines a rectangle tightly containing the whole face. Corner brackets are drawn at the rectangle's corners instead of a full outline, which is a common design shorthand for "scanning" or "targeting" in sci-fi interfaces.

## How to run it

1. Open this folder in VS Code.
2. Right click `index.html` and choose "Open with Live Server."
3. Allow camera access when prompted.
4. Face the camera directly. You should see a bounding box with pink corner brackets around your face, plus a wireframe outline tracing your jaw, eyes, and lips.

## What to notice

Try tilting your head or turning to the side and watch how the mesh and box adjust to follow the new angle. Try moving closer and farther from the camera and watch the box resize accordingly. This scanning effect is the visual foundation for the "character scan" project idea, and pairs well with the glow dot technique from Stage 3 if you want to add extra flourishes later, like glowing dots at the eye corners.

## Status

Complete.