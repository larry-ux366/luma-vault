# Luma

Minimal password storage backed by the owner's private Google Sheet and an owner-only Apps Script deployment.

- Add: Title, User Name, PW, Personal/Work.
- Search icon: enter Master PW, then choose a Title from the dropdown. All matching entries are displayed.
- Eye icons reveal/hide passwords; copy/edit/delete use icons.
- On first search, the owner creates the Master PW (12+ characters). This must be set by the owner, not by an agent.
- Master verification uses a salted PBKDF2-SHA256 proof (600,000 iterations), hashed again server-side. Protected reads require a short-lived server session. Five failures trigger a five-minute cooldown; sessions expire after 15 minutes and the UI locks after five minutes idle.

The Master PW gates this app's read/edit/delete operations. It does not encrypt the underlying Sheet. Passwords remain readable to the Sheet owner in Google Sheets. Adding a new record still requires the owner's Google session but does not require the search unlock.

GitHub Pages is a small entry page that opens the Google-protected app. No account data/passwords are committed. The prior browser-local app remains at `local-vault.html` for backup; its records are not automatically migrated.

Validation: JavaScript syntax and mocked server checks for lock enforcement, master verification, legacy rows, category saving, stale edits and session revocation. No live account records modified for tests.

## Device fingerprint unlock
After unlocking with Master PW, select the fingerprint icon to enroll this device. A top-level GitHub Pages bridge uses a platform passkey with required user verification and the WebAuthn PRF extension to encrypt the password-derived unlock proof using AES-GCM. Only the encrypted proof and credential metadata are retained in this browser. Message exchange is pinned to the deployed Apps Script sandbox origin, the popup window, and a per-request nonce. Master PW remains the fallback. Unsupported PRF providers fail closed; they do not enable fingerprint unlock. The OS may use fingerprint, face verification or device PIN.

This is device/browser-specific convenience unlock, not a replacement for the owner-only Google account requirement. Clearing browser data requires enrollment again. An Apps Script sandbox-origin change requires updating the pinned bridge origin before re-enrollment. Authenticator behavior was tested with mocks; actual phone passkey enrollment requires the user's participation.
