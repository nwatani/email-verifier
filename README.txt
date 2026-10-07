Email Verifier v1.2.7 — GitHub Pages Package

Upload the contents of this folder to your GitHub Pages site.

Files
-----
- index.html                 Main browser application.
- EmailVerifier-Portable.exe Windows portable deep-verification application.

The browser application performs browser-safe syntax/domain/DNS checks and can optionally use a configured remote verification API. The portable Windows application performs local DNS and SMTP verification without requiring a hosted verification server.

The portable application monitors the browser session with heartbeats and automatically closes after the browser is closed. A browser-close signal normally triggers shutdown after a short grace period; heartbeat cleanup provides a fallback, while multiple open tabs are tracked independently and active verification requests are allowed to finish.

No email message is sent during verification.
