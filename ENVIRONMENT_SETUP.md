# Local Environment Setup & Troubleshooting Documentation

## 1. Environment Overview
* **Application:** Invoice Ninja (v5-stable)
* **Architecture:** Headless deployment (Laravel PHP backend API + pre-compiled React frontend)
* **Infrastructure:** Docker Compose (Nginx, PHP-FPM, MySQL 8, Redis)
* **Primary Objective:** Establish a secure local deployment for vulnerability testing and remediation.

## 2. Deployment Challenges & Remediation

### Issue 1: "Blank Page" / Silent Failure on Application Boot
**Symptom:** Accessing `http://localhost:8000/login` resulted in a completely blank page (White Screen of Death). The Nginx access logs showed `200 OK` status codes, but the browser received 0 bytes. The F12 Developer Console showed no frontend JavaScript errors.
**Root Cause:** A cryptographic failure. The Laravel application requires a base64 encryption key (`APP_KEY`) to encrypt cookies and secure session states. Because the variable was entirely missing from the `.env` file, the PHP engine crashed fatally during the boot sequence before it could render an error page or send logs to the browser.
**Remediation:**
1. Manually injected the `APP_KEY=` variable into the `.env` file.
2. Executed the internal container command to generate a secure cipher: `docker exec -it invoiceninja-app-1 php artisan key:generate`
3. Flushed the corrupted application configuration cache: `php artisan optimize:clear`

### Issue 2: 500 Internal Server Error Post-Merge
**Symptom:** After pulling the stabilized `v5-stable` branch containing the vulnerability fixes, the application threw a 500 Server Error reporting `Unsupported cipher or incorrect key length.`
**Root Cause:** Standard security configuration management. Git `.gitignore` rules correctly prevented the transfer of the teammate's `.env` file to prevent credential leakage. Consequently, the local environment attempted to boot with an out-of-sync or missing configuration state, defaulting to incorrect database hosts (`127.0.0.1` instead of the Docker `db` network alias) and an invalid cipher.
**Remediation:**
1. Copied the safe template: `cp .env.example .env`
2. Updated DB connection strings to utilize Docker internal network routing (`DB_HOST=db`).
3. Forced a cryptographic key regeneration to match the new state: `php artisan key:generate --force`
4. Re-established file ownership for the storage directories bridging Windows and the Linux container: `chmod -R 775 storage bootstrap/cache`

### Issue 3: OAuth Integration & Headless UI Limitations
**Symptom:** Implemented the Google OAuth 2.0 configuration (Client ID and Secret) within the backend `.env` file, but the visual "Login with Google" button did not appear on the React frontend.
**Root Cause:** Invoice Ninja utilizes a statically compiled React frontend Docker image. While the Laravel backend securely registered the OAuth variables and opened the authentication routes, the frontend UI components require a full Node.js source recompilation to visually expose third-party login buttons.
**Remediation:** Verified the backend implementation via direct routing. Navigating manually to the backend authentication endpoint (`http://localhost:8000/auth/google`) successfully intercepts the request and redirects to the Google secure sign-in portal, confirming the OpenID connect implementation is functional at the API layer.

## 3. Current State
The local deployment is stable, the database is migrated, and the backend is actively routing OAuth requests.