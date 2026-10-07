Email Verifier v1.2.5 — GitHub Pages Package

Upload the contents of this folder to your GitHub Pages site.

Files
-----
- index.html                 Main browser application.
- EmailVerifier-Portable.exe Windows portable deep-verification application.

The browser application performs browser-safe syntax/domain/DNS checks and can optionally use a configured remote verification API. The portable Windows application performs local DNS and SMTP verification without requiring a hosted verification server.

The portable application's XLSX report export bug in v1.2.4 has been fixed in v1.2.5. Numeric SMTP response codes are now handled correctly by the XLSX export endpoint.

No email message is sent during verification.
