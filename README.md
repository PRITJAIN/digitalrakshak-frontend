# DigitalRakshak - Frontend (React + Vite + TypeScript)

Features in this scaffold:
- SOS button with auto GPS acquisition
- Nearest rescue station selection (local data; replace with server/Firestore list if needed)
- Loud alarm (Web Audio API)
- Live voice recording (MediaRecorder) and upload to Firebase Storage
- Alert object stored in Firestore (includes location, nearest station, recording URL)
- Attempt to call parents using `tel:` link (mobile browsers only; user gesture required)

Important notes:
- Browsers restrict auto-calls and autoplay audio. The SOS button click is used as the required user gesture.
- For upload and alerts we use Firebase (Firestore + Storage). Provide your Firebase config in `src/firebase.ts`.
- MediaRecorder outputs WebM/Opus in most modern browsers. iOS Safari may behave differently.

Setup
1. Clone repo and install dependencies:
   npm install

2. Create a Firebase project and enable:
   - Firestore (in Native mode)
   - Storage

3. Add Firebase config to `src/firebase.ts` (replace placeholders).

4. Run the dev server:
   npm run dev

Usage
- Open the app in a mobile device (or desktop with media & geolocation permissions).
- Tap SOS, allow location and microphone, confirm and proceed.
- The app will:
  - Acquire GPS
  - Compute nearest station
  - Start alarm and recording
  - Create an alert in Firestore and upload the recorded audio
  - Attempt to call the first parent number (opens dialer)

Files
- `src/data/stations.json` contains sample station coordinates. Replace with real station data or fetch from Firestore.

Security & Next steps
- Add authentication to identify users.
- Replace local station list with a secured Firestore collection.
- Add Cloud Functions to notify authorities via SMS/voice (Twilio) or call bridging.
- Add UI for contact management and settings (parents' numbers).
- Add PWA support and use push notifications.
