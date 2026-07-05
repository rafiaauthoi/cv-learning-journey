# Stage 1: Webcam Feed

## Goal

Get a live webcam feed showing on screen in the browser. No tracking, no AI, no libraries. Just proving the camera can be accessed and displayed.

## Concept

Browsers have a built in API called `getUserMedia` that asks the user for permission to access their camera, then returns a live video stream. That stream gets attached to a `<video>` element, and the browser handles the rendering automatically.

This is the foundation every later stage builds on. Landmark detection, gesture logic, and visual overlays all start with this same video feed.

## How to run it

No installs needed for this stage, it is plain HTML and JavaScript.

1. Open this folder in VS Code.
2. Right click `index.html` and open it with a live server, or simply double click the file to open it in your browser.
3. Allow camera access when the browser prompts you.
4. You should see your own webcam feed on the page.

If you have the "Live Server" extension installed in VS Code, right click `index.html` and choose "Open with Live Server" for a smoother experience with auto reload.

## What to notice

Open your browser's developer console (F12) while this is running. Nothing is being logged yet, but this is the same video stream that Stage 2 will feed into MediaPipe to detect hand landmarks. Understanding that the raw video is just a stream of frames is the key idea to carry forward.

## Status

Complete.