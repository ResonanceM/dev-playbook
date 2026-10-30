# Security & Authentication Architecture

---

## 🔒 Session Tokens: HttpOnly Cookies vs LocalStorage

| Storage Method | XSS Vulnerability | CSRF Vulnerability | Senior Recommendation |
| :--- | :--- | :--- | :--- |
| **LocalStorage** | ❌ High risk (JS accessible) | ✅ Safe | **Do NOT store auth tokens here** |
| **HttpOnly, SameSite Cookies** | ✅ Protected from JS theft | ⚠️ Needs CSRF Protection (`SameSite=Lax/Strict`) | **Industry Standard** |

---

## 🔗 Essential Resources & Repositories
* [Lucia Auth](https://github.com/lucia-auth/lucia) — Flexible session handling library.
* [NextAuth.js / Auth.js](https://github.com/nextauthjs/next-auth) — Complete web framework authentication.
