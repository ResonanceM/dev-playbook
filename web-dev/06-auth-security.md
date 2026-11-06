# Authentication, Authorization, and Web Application Security

Security is a system property. Apply defense in depth and verify controls on the server, not only in the UI.

## Authentication versus authorization

- **Authentication (AuthN):** establishes who or what is making a request.
- **Authorization (AuthZ):** determines whether that principal may perform this action on this resource in this context.

A valid session does not imply permission to access every object. Enforce object-level authorization on every relevant server operation.

## Session and token guidance

For browser sessions, prefer well-maintained framework/provider implementations. Cookie-based sessions should generally use `Secure`, `HttpOnly`, and an appropriate `SameSite` policy. Rotate session identifiers after authentication or privilege changes; expire and revoke sessions on logout and security events.

For OAuth/OIDC, use Authorization Code with PKCE for public clients, validate issuer/audience/signature/state/nonce as applicable, and follow provider guidance. Avoid storing long-lived bearer tokens in browser-accessible storage when a secure cookie-based design is suitable.

## Common web risks

- Broken access control and IDOR.
- Injection (SQL, command, template, LDAP).
- Cross-site scripting (XSS).
- Cross-site request forgery (CSRF).
- Server-side request forgery (SSRF).
- Insecure deserialization and unsafe file handling.
- Security misconfiguration and exposed secrets.
- Vulnerable dependencies and build pipeline compromise.
- Insufficient logging and abuse detection.

Use parameterized queries, context-aware output encoding, strict input validation, CSRF defenses where applicable, safe URL allowlists for outbound requests, and least privilege.

## Browser defenses

Use a carefully tested Content Security Policy, HSTS, appropriate framing restrictions, secure referrer policy, and restrictive permissions policy. CSP is defense-in-depth, not a replacement for preventing XSS.

## Secrets and data

- Store secrets in a managed secret store; never commit them.
- Rotate credentials and scope them narrowly.
- Encrypt traffic in transit and sensitive data at rest.
- Classify data; minimize collection and retention.
- Redact tokens, passwords, personal data, and payment data from logs.
- Define deletion, export, and access workflows where required.

## Secure development lifecycle

Threat-model meaningful changes, scan dependencies and artifacts, review authorization paths, test abuse cases, patch vulnerabilities, and maintain an incident process. Security scanners provide signals, not proof of safety.

## Review checklist

- [ ] Authentication flow follows current provider guidance.
- [ ] Authorization is enforced server-side per object/action.
- [ ] Session cookies and token lifetimes are appropriate.
- [ ] CSRF, XSS, injection, and SSRF are considered.
- [ ] Secrets and sensitive data are not logged or exposed.
- [ ] Rate limits and abuse controls protect costly endpoints.
- [ ] Dependencies, containers, and CI pipeline are monitored.
- [ ] Security incidents have owners and response procedures.
