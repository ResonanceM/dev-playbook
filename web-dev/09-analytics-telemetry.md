# Analys, Produkttelemetri och GDPR-efterlevnad

För att mäta om nya funktioner skapar affärsvärde krävs en ren och disciplinerad event-taxonomi.

---

## 📐 Event Taxonomy (Navngivningsstandard)

Använd konsekvent **[Entity] [Action]** med tillhörande egenskaper:

```json
// ✅ Rekommenderad struktur
Event: "checkout_button_clicked"
Properties: {
  "user_id": "usr_9982",
  "plan_type": "enterprise",
  "currency": "SEK",
  "value": 4995
}
```

---

## 🛡️ Integritet och GDPR
* **Samtyckeshantering:** Ladda aldrig tunga analys- eller spårningsskript (Google Analytics, Mixpanel, Meta Pixel) innan användaren har gett aktivt samtycke via en Consent Management Platform (CMP).
* **Anonymisering:** Hasha IP-adresser och undvik att skicka känsliga personuppgifter i custom properties.
