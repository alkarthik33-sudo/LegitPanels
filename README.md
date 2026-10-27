# Access Key Portal

A minimal dark access-key page with server-side validation and a basic admin console. It is a generic licensing starter, not tied to any third-party service.

## What it includes

- Public key input, paste button, and verify button
- Node.js + Express backend
- Key generation, expiry, and revocation in the admin console
- Only SHA-256 hashes of access keys are stored
- Keys are shown only once when created
- JSON file storage (`data/keys.json`)

## Run locally

1. Install Node.js 18 or newer on a computer or hosting service.
2. Copy `.env.example` to `.env`.
3. Set `ADMIN_PASSWORD` to a long, unique password (at least 16 characters).
4. Install dependencies and start:

   ```bash
   npm install
   npm start
   ```

5. Open `http://localhost:3000`.
6. Open `http://localhost:3000/admin.html` to create keys.

The server refuses to start if `ADMIN_PASSWORD` is missing or too short. On a hosting platform, set it in the platform's environment-variable settings; do not upload a real `.env` file.

## Android / Acode note

Acode can edit these files and preview the static HTML, but the backend API needs a running Node.js server. For a public website, deploy the project to a Node.js host that supports persistent storage. If the host's filesystem is ephemeral, keys may disappear after redeploy/restart; use a managed database for production.

## Before public launch

This is a starter, not a hardened production service. Add HTTPS, request rate limiting, persistent admin sessions with secure cookies, CSRF protection if using cookies, backups, and a managed database. Do not use it to validate third-party keys or claim it unlocks software that your server does not control. The current public endpoint only verifies whether a key is valid; connect it only to features or services you own or are authorized to manage.
