EMAIL VERIFIER — GITHUB PAGES + PORTABLE WINDOWS VERIFIER

FILES
-----
index.html
    The GitHub Pages browser version. It performs browser-safe checks and includes
    a Download for Windows button for deep local verification.

EmailVerifier-Portable.exe
    Native 64-bit Windows portable application. Double-click it to launch the local
    verifier. It requires no installer, Docker, Rust, Node.js, or hosted server.

HOW TO PUBLISH ON GITHUB PAGES
------------------------------
1. Upload index.html to the root of your GitHub Pages site.
2. Upload EmailVerifier-Portable.exe to the same directory as index.html.
3. Open the GitHub Pages URL.
4. Users who need individual mailbox confirmation can download the Windows app.

HOW THE WINDOWS APP WORKS
-------------------------
The executable starts a temporary HTTP interface on 127.0.0.1 only and opens the
local interface in the user's default browser. Verification is performed locally
from the user's PC using DNS and SMTP connections. It does NOT expose a server to
the Internet and does NOT send email content.

NETWORK REQUIREMENTS
--------------------
SMTP verification normally requires outbound TCP port 25. Some corporate, ISP,
VPN, antivirus, or firewall configurations block SMTP. In that case the application
reports Unknown rather than incorrectly reporting the mailbox as invalid.

CATCH-ALL
---------
The optional catch-all test checks a deliberately random recipient on the same
mail domain. It sends SMTP envelope commands only; no message body is transmitted.
Catch-all domains cannot reliably confirm individual mailbox existence.

SECURITY / SMARTSCREEN
----------------------
The portable EXE is unsigned. Windows SmartScreen may therefore display a warning
when it is downloaded from the Internet. If you distribute it through your own
organization, code-signing the executable is recommended.

The application binds only to 127.0.0.1 and uses a per-launch random local token.
It has no analytics or telemetry.

LIMITATIONS
-----------
Some providers deliberately prevent SMTP mailbox enumeration or return ambiguous
responses. Even a successful SMTP probe is a strong signal, not an absolute legal
or technical guarantee of future deliverability.

REACHER RELATIONSHIP
--------------------
The desktop verifier follows the same core local verification concept as Reacher:
syntax -> DNS/MX -> SMTP -> recipient assessment -> optional catch-all check.
It is an independent implementation and is NOT the official Reacher executable.
The upstream Reacher project currently has a v0.11.8 release, but its current
release workflow has Windows publishing disabled. If exact upstream Reacher engine
parity is required, build the official CLI from the upstream source on Windows
instead of treating this executable as an official Reacher binary.

SHA-256
-------
EmailVerifier-Portable.exe
65a59fee479cf9b8f8509294e039278c4f0df86284a70f80434b88af0821e2d2

SOURCE BUILD
------------
Source is included separately in the provided source package. The Windows build
command is:

GOOS=windows GOARCH=amd64 CGO_ENABLED=0 go build -trimpath -buildvcs=false \
  -ldflags="-s -w -H=windowsgui -buildid=" \
  -o EmailVerifier-Portable.exe .

API settings support both Reacher SaaS Authorization API keys and self-hosted Reacher x-reacher-secret credentials.
