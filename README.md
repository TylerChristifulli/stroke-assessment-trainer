Stroke Assessment Trainer (Experimental), v1
============================================

WHAT IT IS
A 3D patient that responds to exam commands (smile, raise eyebrows, close eyes tight,
follow my finger, look left/right, "can you hear me", swallow). A toggle switches between
a normal patient and a left hemisphere stroke (right facial droop with forehead sparing,
leftward gaze deviation, can't look right past midline). Commands can be spoken, tapped
or typed. Webcam finger tracking lets the patient follow the learner's fingertip.

FILES
  index.html        the trainer page
  patient_glb.txt + textures   the patient model, textures and room backdrop (about 12 MB)
Keep both files in the same folder. Open index.html.

HOSTING NOTES FOR THE SANDBOX
1. Serve it over HTTPS. Browsers only allow the microphone and camera on secure pages.
2. If the sandbox shows it inside an iframe, the iframe needs camera and mic permission:
     <iframe src=".../index.html" allow="camera; microphone; fullscreen"
             style="width:100%;aspect-ratio:16/10;border:0"></iframe>
   Without the allow attribute the page still works with tap and typed commands.
3. The page loads these at runtime, so the sandbox's security policy must allow them:
     cdn.jsdelivr.net          three.js (3D engine) and MediaPipe (hand tracking)
     storage.googleapis.com    the MediaPipe hand-tracking model (only when the camera is used)
   Voice uses the browser's built-in speech recognition (Chrome sends audio to Google's
   speech service; Safari uses Apple's). Firefox has no speech recognition, so voice is
   unavailable there; buttons and typing still work.
4. No server code, database or login is needed. Nothing is stored or uploaded by the page.

BROWSER SUPPORT
  Chrome / Edge (desktop):  everything
  Safari (Mac, iPad):       everything; speech recognition can be less accurate
  Firefox:                  no voice; buttons, typing and camera work
  Phones:                   works, but the layout stacks and the model is heavy for older devices
