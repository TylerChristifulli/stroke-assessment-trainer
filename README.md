Stroke Assessment Trainer (Experimental), v2
============================================

WHAT IT IS
A 3D patient that responds to exam commands (smile, raise eyebrows, close eyes tight,
follow my finger, look left/right, "can you hear me", swallow). A toggle switches between
a normal patient and a left hemisphere stroke (right facial droop with forehead sparing,
leftward gaze deviation, can't look right past midline). Commands can be spoken, tapped
or typed. Webcam finger tracking lets the patient follow the learner's fingertip.

Visual fields (camera): say "look at my nose" (or tap Visual fields). He fixates on center.
Hold your hand up in one of his four quadrants and wiggle a finger ("tell me when you see it
move") or hold up 1 to 4 fingers after asking "how many fingers?". In stroke mode he has a right
homonymous hemianopia: nothing in his right field is seen. Each stimulus is written to the exam log.

He also talks. Ask his name, where he is, what day it is, what happened, whether anything
hurts, or have him repeat "You can't teach an old dog new tricks". In stroke mode his
answers are slow, slurred and word-finding (dysarthria with expressive aphasia). His mouth
is lip-synced to the recorded clips.

FILES
  index.html        the trainer page
  patient_glb.txt + textures   the patient model, textures and room backdrop (about 13 MB)
  voice/            22 recorded answers: <line>_normal.mp3 and <line>_stroke.mp3
Keep everything in the same folder. Open index.html.
To change a line, replace its mp3 (same name) and edit the matching text in LINES in
index.html so the captions match. voice/lipsync.json holds the mouth timing for each
clip (made with Rhubarb Lip Sync from the audio). A replaced clip needs its timing
regenerated; until then it falls back to rougher letter-based lip sync.
A missing clip falls back to the browser voice.

HOSTING NOTES FOR THE SANDBOX
1. Serve it over HTTPS. Browsers only allow the microphone and camera on secure pages.
2. If the sandbox shows it inside an iframe, the iframe needs camera and mic permission:
     <iframe src=".../index.html" allow="camera; microphone; autoplay; fullscreen"
             style="width:100%;aspect-ratio:16/10;border:0"></iframe>
   Without the allow attribute the page still works with tap and typed commands.
   Browsers block sound until the learner interacts with the page, so a standalone page
   shows one "Start exam" button. Inside an iframe with autoplay allowed, after the learner
   has clicked into the cartridge, Chrome skips that button and he can talk right away.
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
