# Infinity Gaminig Cafe Manager

Mobile-friendly manager for four PS5 stations. Uses Firebase Authentication for owner sign-in and Cloud Firestore to sync the app state. A local browser copy is also retained as a fallback.

## First-time Firebase setup

1. In Firebase Console, open **Authentication → Sign-in method** and enable **Email/Password**.
2. Under **Authentication → Users**, create the owner account with the email address you will use in the app. The owner UID must match the UID in `firestore.rules`.
3. Open **Firestore Database → Rules**, paste the contents of `firestore.rules`, and click **Publish**.
4. Host this folder on HTTPS (GitHub Pages, Netlify, or Vercel). Open the site on your phone and sign in using the Firebase Auth email/password.

The app stores its cafe state at `cafes/infinity-gaminig-cafe/app/state`. If that cloud document is empty on the first sign-in, the current browser's existing local data is uploaded. Afterward, successful app changes write the state to Firestore and refresh the local cache.

## Features

- Dashboard reports: today, yesterday, last 7 days, last month, custom dates; items, station revenue, customer sessions, station usage, recent activity.
- Sessions: four PS5 timers, optional customer name, manual minutes, item sales, session totals, 5-minute and time-up voice reminders.
- Keep the page open and the phone awake with volume enabled for reminders.

## Notes

Firebase Web configuration is public client configuration. Firestore rules protect the records using the owner UID. Do not add service-account JSON, private keys, or Admin SDK credentials. This app writes one state document for the cafe; it is intended for a single operator and should be exported/backed up periodically as usage grows.
