# Security & Authentication Architecture

---

## 🔒 Session Tokens: HttpOnly Cookies vs LocalStorage

| Storage Method | XSS Vulnerability | CSRF Vulnerability | Senior Recommendation |
| :--- | :--- | :--- | :--- |
| **LocalStorage / SessionStorage** | ❌ High risk (JS accessible) | ✅ Safe | **Do NOT store auth tokens here** |
| **HttpOnly, SameSite Cookies** | ✅ Protected from JS theft | ⚠️ Needs CSRF Protection (`SameSite=Lax/Strict`) | **Industry Standard for Web Apps** |

---

## 🛡️ OWASP Top 10 Web Security Essentials
1. **Content Security Policy (CSP):** Restrict script execution sources via HTTP headers.
2. **CORS (Cross-Origin Resource Sharing):** Never use `Access-Control-Allow-Origin: *` in production with credentials.
3. **Input Sanitization:** Sanitize user HTML inputs using `DOMPurify` to prevent Stored XSS.

---

## 🔗 Essential Resources & Repositories
* [Lucia Auth](https://github.com/lucia-auth/lucia) — Simple, flexible session handling library.
* [NextAuth.js / Auth.js](https://github.com/nextauthjs/next-auth) — Complete authentication for Next.js and web frameworks.
* [OWASP Top Ten Official](https://owasp.org/www-project-top-ten/) — The standard awareness document for developers.
