Email Verifier v1.2.4

GitHub Pages
------------
- index.html is the browser version and can be hosted directly on GitHub Pages.
- Browser mode checks syntax, domain/DNS mail routing, disposable/role signals, provider hints, and suggestions.
- Deep verification can use either a Reacher SaaS API key or a self-hosted Reacher shared secret.
- Bulk import supports TXT, CSV, and XLSX (Excel) files. XLSX files are processed locally in the browser.
- Verification reports can be exported as XLSX, CSV, or JSON. Single and bulk results are supported.

Windows desktop verifier
------------------------
- EmailVerifier-Portable.exe is a self-contained Windows 64-bit GUI application.
- It performs DNS and SMTP verification directly from the user's computer.
- It supports TXT, CSV, and XLSX imports, plus XLSX/CSV/JSON report export.
- It includes Light and Dark themes with readable native list/drop-down colors.
- No installer, Docker, server, or API account is required for local verification.
- It binds only to 127.0.0.1 while running and uses a temporary authenticated browser session.
- No email message is sent.
- Outbound SMTP port 25 may be blocked by some networks; blocked/ambiguous SMTP checks are reported as Unknown rather than incorrectly reported as invalid.

Build
-----
- Go 1.23+
- GOOS=windows GOARCH=amd64 CGO_ENABLED=0 go build -trimpath -buildvcs=false -ldflags="-s -w -H=windowsgui -buildid=" -o EmailVerifier-Portable.exe .
- The desktop source package includes web/index.html so the embed directive and build command work directly from the source root.

Upstream reference
------------------
- Reacher: https://github.com/reacherhq/check-if-email-exists
- The desktop application is an independent implementation of the local-verification concept and is not the official Reacher binary.

Privacy and limitations
-----------------------
- Browser-only verification cannot directly prove an individual mailbox exists because normal browser JavaScript cannot open arbitrary SMTP TCP connections.
- Deep API verification sends the full address to the configured verification service.
- Local desktop verification performs SMTP checks from the user's own network.

Programmed by Naser AlWatani
Version: 1.2.4
