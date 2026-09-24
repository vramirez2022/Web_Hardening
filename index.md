---
layout: default
---

# 🛡️ Production Web Application Hardening & Edge Security

![Security Headers Grade](https://img.shields.io/badge/SecurityHeaders.com-A%2B_Rating-brightgreen?style=for-the-badge&logo=securityscorecard)
![HTTPS Enforced](https://img.shields.io/badge/HTTPS-Enforced_via_HSTS-blue?style=for-the-badge&logo=letsencrypt)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

## 📌 Executive Summary

This repository documents the production security hardening for my live web application. By configuring defense-in-depth controls at both the HTTP application layer and the network edge, the application mitigates critical web vulnerabilities—including Cross-Site Scripting (XSS), Clickjacking, MIME-sniffing, and SSL/TLS downgrade attacks—achieving a **Top-Tier (A / A+) rating** on independent security audits.

---

## 🚀 Key Technical Implementations

### 1. HTTP Security Headers & Policy Enforcement

- **Strict-Transport-Security (HSTS)**
  - Enforced full HTTPS communication with a 1-year (`max-age=31536000`) policy, `includeSubDomains`, and `preload` directives to prevent SSL stripping and man-in-the-middle (MitM) attacks.
- **Content Security Policy (CSP)**
  - Implemented restrictive, least-privilege asset-loading rules (`default-src 'self'`, `object-src 'none'`, `frame-ancestors 'none'`) to stop unauthorized script execution and prevent Cross-Site Scripting (XSS).
- **Clickjacking & Framing Defense**
  - Configured `X-Frame-Options: DENY` combined with CSP `frame-ancestors 'none'` to block UI redressing and framing attacks via invisible `<iframe>` elements.
- **Drive-by Download & Sniffing Protection**
  - Implemented `X-Content-Type-Options: nosniff` to enforce strict MIME-type interpretation across modern browsers.
- **Privacy & Information Leakage Mitigation**
  - Set `Referrer-Policy: strict-origin-when-cross-origin` to protect user navigation privacy and restricted browser API capabilities via `Permissions-Policy`.

---

### 2. Edge Security & Infrastructure Isolation

- **End-to-End Encryption:** Enforced TLS 1.2/1.3 standards across all origin and client connections.
- **Automated Edge Header Injection:** Configured response header injection at the serverless CDN edge via proxy transform rules, ensuring zero latency impact and consistent enforcement across all static assets.

---

### 3. Validation & Security Auditing

- Conducted continuous external security scans using industry-recognized tools, including **SecurityHeaders.com** and **Mozilla Observatory**, consistently achieving an **A / A+ Grade**.
