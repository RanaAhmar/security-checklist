# Web Application Security Checklist 🛡️🔐

[![Sponsored by Stackaura](https://img.shields.io/badge/Sponsored_by-Stackaura_&_Ahmar_Hussain-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://www.stackaura.com/)
[![Security Checklist](https://img.shields.io/badge/Security-Checklist-ea2c2f.svg?style=for-the-badge&logo=owasp)](https://www.stackaura.com/)

A comprehensive, no-nonsense security checklist for modern web applications. Don't deploy your next Next.js, Node, or Python app without verifying these critical security vectors.

---

<div align="center">
  <h3>Sponsored by <a href="https://www.stackaura.com/">Stackaura</a> & Ahmar Hussain</h3>
  <p>Building secure, scalable, and resilient software systems.</p>
  <a href="https://www.stackaura.com/"><img src="https://img.shields.io/badge/Visit_Stackaura-Black?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Visit Stackaura" /></a>
</div>

---

## 🛑 Why do you need this?

Data breaches in 2025 are expensive. If you are handling user data, JWTs, or connecting to external APIs, you are a target. This checklist distills the OWASP Top 10 into actionable, framework-agnostic steps that you can verify in an afternoon.

## ✅ The Checklist

### 1. Authentication & Authorization
- [ ] **Strong Passwords:** Enforce minimum length (12+ chars), complexity, and check against `HaveIBeenPwned` APIs.
- [ ] **MFA Supported:** Provide Time-based One-Time Passwords (TOTP) for all user accounts.
- [ ] **Rate Limiting:** Implement strict rate limiting on `/login`, `/register`, and `/forgot-password` endpoints.
- [ ] **Session Invalidation:** Ensure tokens/sessions are aggressively invalidated on logout and password change.
- [ ] **Principle of Least Privilege:** APIs should verify role permissions on *every* request, not just in UI.

### 2. Data Security & Cryptography
- [ ] **HTTPS Only:** Enforce HSTS (HTTP Strict Transport Security). Never serve content over HTTP.
- [ ] **Secure Storage:** Hash passwords using Argon2id or bcrypt (with appropriate cost factors). Never use MD5/SHA-1.
- [ ] **Environment Variables:** Never commit `.env` files. Ensure cloud secrets (AWS Parameter Store, Vercel Env) are scoped correctly.

### 3. API Security
- [ ] **CORS Configuration:** Explicitly define `Access-Control-Allow-Origin`. Never use `*` in production if passing credentials.
- [ ] **Input Validation:** Use schema validation (Zod, Joi, Pydantic) on **all** incoming request bodies, params, and headers.
- [ ] **IDOR Protection:** Verify the user making the request actually owns the requested resource ID (Insecure Direct Object Reference).

### 4. Client-Side Security (Frontend)
- [ ] **XSS Protection:** Use frameworks (React/Vue/Svelte) that escape HTML by default. Avoid `dangerouslySetInnerHTML`.
- [ ] **CSP Headers:** Implement a strict Content Security Policy to prevent loading unauthorized scripts.
- [ ] **Cookie Flags:** JWTs/Sessions stored in cookies must have `HttpOnly`, `Secure`, and `SameSite=Strict` flags.

## 📦 Automation Tools

The `/scripts` directory contains tools to automate these checks:
- `csp-evaluator.js`: Tests your domains Content Security Policy.
- `jwt-auditor.py`: Checks if your JWTs are overly permissive or lack expiration dates.

## 🤝 Contributing

Security is an evolving field. If you spot an inaccuracy or want to add a critical check, please open a PR! We welcome contributions from red-teamers and application developers alike.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
*Maintained with ❤️ by Ahmar Hussain and [Stackaura](https://www.stackaura.com/). Stay secure.*
