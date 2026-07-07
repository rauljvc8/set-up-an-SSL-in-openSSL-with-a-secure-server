# Setting Up a Secure Server with SSL/TLS Using OpenSSL

**Network Security Lab · 4Geeks Academy**
Author: Raúl Velásquez

## Overview

Configured a Debian server to serve content over HTTPS using a self-signed SSL/TLS certificate generated with OpenSSL, then verified the full chain — key, certificate, and Apache configuration — with an automated validation script.

## What I Did

1. **Generated a 2048-bit RSA private key** with OpenSSL (`openssl genrsa`).
2. **Created a Certificate Signing Request (CSR)** containing the server's public key and organization details.
3. **Self-signed the CSR** to produce a valid X.509 certificate (`openssl x509 -req`), valid for 365 days.
4. **Configured Apache's SSL virtual host** to point to the certificate and private key, matching the `ServerName` to the certificate's Common Name.
5. **Enabled the SSL module and site** (`a2enmod ssl`, `a2ensite default-ssl`) and reloaded Apache.
6. **Updated the local hosts file** to resolve the test domain and verified the HTTPS connection in-browser.
7. **Ran an automated verification script** to confirm the full setup end-to-end.

## Verification Results

| Check | Result |
|---|---|
| Apache service | ✅ Running |
| SSL module | ✅ Enabled |
| Certificate file | ✅ Found at `/etc/ssl/certs/myserver.crt` |
| Private key file | ✅ Found at `/etc/ssl/private/myserver.key` |
| Certificate validity | ✅ Valid — Common Name (CN): `mi-dominio.com` |
| Certificate expiry | ✅ 364 days remaining |

## Skills Demonstrated

- Public-key cryptography fundamentals (private key / CSR / certificate chain)
- OpenSSL certificate generation and self-signing
- Apache HTTPS/TLS virtual host configuration
- Linux service management (`systemctl`, `a2enmod`, `a2ensite`)
- End-to-end validation of a security configuration

## Repository Contents

| File | Description |
|---|---|
| `report.json` | Output of the automated validation script confirming the SSL setup |
| `assets/` | Supporting lab resources |

---
Academic project — Cybersecurity Program, 4Geeks Academy.
