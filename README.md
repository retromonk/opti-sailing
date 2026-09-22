# opti-sailing

Live site: https://retromonk.github.io/opti-sailing/

The site is deployed to GitHub Pages by `.github/workflows/pages.yml` on every push to `main`.

## Shared high scores (coin run)

The coin run has an arcade-style top-ten board with three-letter initials. Out of the box
scores are kept in the browser only; to share one board across every device, connect a
free Firebase project:

1. Go to https://console.firebase.google.com, **Add project** (Analytics can be off).
2. **Build → Firestore Database → Create database**, production mode, any region.
3. **Rules** tab: paste the contents of [`firestore.rules`](firestore.rules) and **Publish**.
   These let anyone read the board and add one well-formed score, and nothing else.
4. **Project settings (gear) → Your apps → Web (`</>`)**, register the app (no hosting needed)
   and copy the `firebaseConfig` values.
5. Paste `apiKey`, `authDomain`, `projectId` and `appId` into `window.FIREBASE_CONFIG`
   near the top of `index.html`, then push to `main`. The site redeploys and the board goes live.

The Firebase web keys are meant to be public; the rules above are what protects the data.
