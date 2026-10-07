Email Verifier v1.3.0

GitHub Pages package

Contents:
- index.html: browser-based Email Verifier
- EmailVerifier-Portable.exe: optional Windows portable verifier for local deep SMTP checks
- SHA256SUMS.txt: package checksums

v1.3.0 improvements:
- Domain-aware bulk verification reuses DNS/MX results across addresses sharing the same domain.
- Local SMTP provider-aware response classification, including Microsoft/Hotmail/Outlook policy and recipient-not-found responses.
- Microsoft SMTP fallback using a non-null envelope sender when a policy/temporary response may be caused by sender handling.
- Multi-MX result precedence improved so one rejecting MX cannot override an inconclusive MX; accepted > full > unknown > rejected.
- Existing browser, Reacher API, TXT/CSV/XLSX import, XLSX/CSV/JSON export, Arabic/RTL, themes, privacy, and portable-app session cleanup features are retained.

Important:
- Browser mode cannot directly prove an individual mailbox exists.
- The Windows portable application performs local SMTP verification when the user's network permits outbound SMTP connections.
- No email message body is sent; verification uses SMTP envelope commands.
