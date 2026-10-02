# Medical History Timeline (self-hosted)
Anyone can read. Only your account can add, edit or delete. Data lives in Firebase Firestore (free Spark plan is enough). Photos are resized and stored inside each event, so no paid Storage is needed.

## Setup (about 10 minutes)
1. console.firebase.google.com > Add project.
2. Project settings > Your apps > Web (</>) > register. Copy the config into `firebase-config.js`.
3. Build > Firestore Database > Create database (production mode).
4. Build > Authentication > Get started > Sign-in method > Email/Password > Enable.
5. Authentication > Users > Add user (your email and a strong password). Copy that user's UID.
6. Put the UID in `OWNER_UID` in `firebase-config.js` and in `firestore.rules`.
7. Firestore > Rules: paste `firestore.rules` and Publish. This step is what actually enforces owner-only editing.
8. Authentication > Settings > User actions: turn off "Enable create (sign-up)" so nobody else can register.
9. Host the folder anywhere static (Firebase Hosting, Netlify Drop, GitHub Pages, Cloudflare Pages).
10. Authentication > Settings > Authorized domains: add your site's domain.

Open the site, press "Owner sign in", and add events. Visitors see them live, read-only.

## Notes
- The Firebase config values are not secrets; the security rules protect the data.
- Existing entries from the claude.ai version are not transferred. Re-enter them.
- Medical data is sensitive. Anyone with the URL can read it. Keep the URL private or ask for a login-gated read version.
