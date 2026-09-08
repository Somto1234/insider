# BET INSIDER — Firebase VIP System

## What is included
- Google-only user authentication
- Admin authorization for `bobiorah80@gmail.com` via Firebase custom claim
- No public/default admin PIN
- Weekly and monthly VIP plan support
- Paystack automatic payment functions (NGN)
- Manual payment proof submission and admin approval
- User-bound activation codes
- VIP game image upload/storage and protected signed URLs
- Firestore + Storage security rules
- Admin panel with payment/plan/game management

## Firebase setup
1. In Firebase Console, open **Authentication → Sign-in method** and enable **Google**.
2. In **Authentication → Settings → Authorized domains**, add your deployed website domain. Keep `localhost` for local testing.
3. Confirm the Firebase web configuration in `Index.html` matches your Firebase Web App.
4. Install Firebase CLI and log in.
5. From this project directory, install Functions dependencies:
   `cd functions && npm install`
6. The admin account is configured in `functions/.env`:
   `ADMIN_EMAIL=bobiorah80@gmail.com`
7. Add your Paystack secret only to `functions/.env` (never to frontend code):
   `PAYSTACK_SECRET_KEY=sk_live_...`
8. Deploy rules/functions/hosting with Firebase CLI.

## Important
- The Firebase Web API key in the frontend is not a password/secret. Do not expose service-account private keys.
- Paystack secret keys must remain server-side.
- VIP games are returned only through the authenticated callable function and their images use short-lived signed URLs.
- Normal users do not get an Admin navigation item or admin dashboard access.
- The frontend does not create the public Firestore document anymore, so a missing `public/main` document does not trigger a false "real-time connection lost" state.

## Local test
Serve the folder through a local web server (for example VS Code Live Server) rather than opening the HTML file directly. Use the exact authorized local domain shown in Firebase Authentication.
