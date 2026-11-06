# Säkerhet och Autentisering (Web Security)

---

## 🔒 Tokens: HttpOnly Cookies vs. LocalStorage

| Lagringsmetod | XSS-sårbarhet (Stöld via JS) | CSRF-risk | Senior rekommendation |
| :--- | :--- | :--- | :--- |
| **LocalStorage / SessionStorage** | ❌ Hög risk (åtkomlig via skript) | ✅ Säker | **Använd aldrig för känsliga auth-tokens** |
| **HttpOnly, SameSite Cookies** | ✅ Skyddad mot JS-stöld | ⚠️ Kräver SameSite-skydd | **Branschstandard för moderna webbappar** |

---

## 🛡️ OWASP Top 10 viktiga åtgärder
1. **Sanering:** Använd `DOMPurify` för att förhindra Stored XSS vid rendering av användargenererad HTML.
2. **CSP (Content Security Policy):** Lås ned vilka domäner som får exekvera skript via HTTP-huvuden.
3. **CORS:** Tillåt aldrig `Access-Control-Allow-Origin: *` i produktion tillsammans med autentiseringsuppgifter.
