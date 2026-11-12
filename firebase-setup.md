# Firebase setup for Infinity Gaminig Cafe

The app is configured for Firebase project `infinitygammingcafe`. The web configuration is included in the client app and also documented in `firebase-config.js`.

## Required Firebase console steps

1. **Authentication → Sign-in method:** enable Email/Password.
2. **Authentication → Users:** create the owner account. Confirm its UID is `fERrZIKffsQYapVSWYmj4flTHuP2` (the UID already supplied).
3. **Firestore Database → Rules:** paste `firestore.rules` and click **Publish**.
4. Deploy the app folder to an HTTPS static host and sign in with the owner email/password.

The app uses `cafes/infinity-gaminig-cafe/app/state` as its single Firestore document. First successful login uploads this browser's saved data if no cloud document exists. After that, changes are saved to Firestore. Use one operator at a time; this whole-state document is not designed for concurrent multi-device edits.

Do not put service-account JSON, private keys, or Admin SDK credentials in the app or Git.
