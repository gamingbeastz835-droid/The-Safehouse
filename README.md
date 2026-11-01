# THE SAFEHOUSE — Version 2

Responsive dark/purple messaging-community starter built with vanilla HTML/CSS/JS, Firebase Authentication and Cloud Firestore. Designed to edit from Android using Spck Editor and deploy on GitHub Pages.

## Version 2 features
- Google sign-in and profile display name/about field
- Direct messages and group chats
- Firestore live message updates
- Friend requests and friend list
- Server creation, general channels, channel messages
- Invite codes to join servers
- Typing indicator and basic seen receipts for direct/group messages
- Unread badge data model and responsive mobile navigation

## Setup

1. Create a Firebase project at https://console.firebase.google.com/
2. Add a Web app and copy its config into `firebase-config.js`.
3. Authentication → Sign-in method → enable Google.
4. Authentication → Settings → Authorized domains: add `YOUR_GITHUB_USERNAME.github.io`.
5. Create Firestore Database.
6. Firestore → Rules: publish the complete `firestore.rules` included here.
7. In Spck Editor create/open a project and add `index.html`, `styles.css`, `app.js`, `firebase-config.js`.
8. Preview locally. For OAuth, use your deployed HTTPS URL after adding the GitHub Pages domain in Firebase.
9. Create GitHub repository `the-safehouse`, upload the four site files to the repository root.
10. Repository Settings → Pages → Deploy from branch → `main` → `/ (root)`.
11. Website URL: `https://YOUR_GITHUB_USERNAME.github.io/the-safehouse/`.

## Important limitations / production hardening

This is a substantial functional starter, not a finished audited production messaging service. It is not end-to-end encrypted. The invite-code join flow is a basic convenience mechanism; for production, move invite validation and membership changes into a trusted Cloud Function to prevent abuse and add expiry, revocation, usage limits and rate limiting. Current public profile reads expose display names/emails to signed-in users so email lookup works; do not store sensitive information in user profile documents. Firestore rules should be tested in Firebase Emulator before launch. The first version does not include image/file upload, push notifications, voice/video calls, message editing/deletion, robust presence, spam prevention, user blocking/reporting, admin moderation, privacy policy or account deletion workflow.

### Notes
- Firestore may request composite indexes; follow the Firebase console link in any index error.
- Google sign-in popup behavior can differ in mobile browser previews; test the deployed HTTPS site.
- GitHub Pages hosts static files only; Firebase provides authentication and realtime database services.
- Firebase web config is not an admin secret. Never put service-account JSON or private admin credentials in frontend code.
