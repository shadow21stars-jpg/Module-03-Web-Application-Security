# Remediation Recommendations

These recommendations correspond to the illustrative training scenarios in the vulnerability report.

| Priority | Area | Recommendation | Verification |
|---|---|---|---|
| 1 | Access control | Enforce server-side role and ownership checks on every protected request. Deny access by default. | Test permitted and denied actions with separate test accounts. |
| 2 | Database access | Use parameterized queries or a safe ORM. Never build SQL by concatenating untrusted input. | Code review and safe tests with ordinary sample inputs. |
| 3 | Session security | Use HTTPS, random session IDs, `Secure`, `HttpOnly` and suitable `SameSite` cookie settings. Rotate IDs after login and invalidate on logout. | Inspect local response headers and test logout/session expiry. |
| 4 | Error handling | Show generic messages to users; store diagnostic details in access-controlled logs. | Trigger a safe error and inspect the response and protected log. |
| 5 | Configuration | Disable production debug mode, remove default accounts and unnecessary services, and review security headers. | Configuration review before deployment. |
| 6 | Dependencies | Maintain an inventory, update supported packages and review dependency changes. | Dependency review and automated checks in the development pipeline. |
| 7 | Monitoring | Record authentication and authorization events without logging passwords or session tokens. Configure useful alerts. | Verify events are recorded and alerts reach the responsible team. |

## General secure development checklist
- [ ] Validate input on the server.
- [ ] Encode output for its display context.
- [ ] Apply least privilege.
- [ ] Protect sensitive data in transit and at rest.
- [ ] Store passwords using a suitable password-hashing function.
- [ ] Keep dependencies and frameworks updated.
- [ ] Keep secrets out of source control.
- [ ] Handle errors safely.
- [ ] Log security events without exposing secrets.
- [ ] Retest after every security fix.

## Final recommendation
Make security part of design, coding, testing and maintenance. Fix confirmed high-impact issues first, then retest and document the evidence.
