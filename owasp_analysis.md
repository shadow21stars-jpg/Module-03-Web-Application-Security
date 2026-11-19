# OWASP Top 10:2025 Analysis

## Introduction
The OWASP Top 10 is an awareness document that helps developers understand important web application security risks. This analysis uses the current OWASP Top 10:2025 categories.

## Category analysis

| ID | Risk | Simple explanation | Defensive controls |
|---|---|---|---|
| A01 | Broken Access Control | A user can access another user's data or a feature they are not allowed to use. | Enforce server-side authorization on every request; deny by default; test roles and ownership. |
| A02 | Security Misconfiguration | An application has unsafe settings or unnecessary exposed features. | Remove defaults, disable debug mode in production, set secure headers, review configuration. |
| A03 | Software Supply Chain Failures | A dependency, build tool or software distribution process may be untrusted or compromised. | Use trusted sources, pin and review dependencies, scan packages, protect build credentials. |
| A04 | Cryptographic Failures | Sensitive information is not properly protected. | Use HTTPS, approved modern cryptography, secure key management and suitable password hashing. |
| A05 | Injection | Input is interpreted as part of a database query or other command. | Parameterized queries, safe APIs, server-side validation and context-aware output encoding. |
| A06 | Insecure Design | Security was not built into the application's requirements and design. | Threat model important features, define security requirements, apply least privilege and abuse-case testing. |
| A07 | Authentication Failures | Login or session controls can be weak. | Use secure authentication libraries, rate-limit login attempts, protect recovery flows and manage sessions safely. |
| A08 | Software or Data Integrity Failures | Software or data is trusted without verifying its source or integrity. | Verify signatures and checksums where appropriate, protect CI/CD pipelines and validate trusted updates. |
| A09 | Security Logging and Alerting Failures | Suspicious activity is not recorded or acted on. | Log important security events, protect logs, monitor patterns and configure actionable alerts. |
| A10 | Mishandling of Exceptional Conditions | Unexpected errors or unusual states are handled in an unsafe way. | Fail safely, validate state transitions, handle errors consistently and avoid exposing internal details. |

## Three important examples
### 1. Broken Access Control
**Scenario:** A normal user attempts to open an administrator-only page.  
**Risk:** Unauthorized access or changes to protected information.  
**Prevention:** Check the user's role and resource ownership on the server for every request. Hiding a button in the interface is not sufficient.

### 2. Injection
**Scenario:** An application builds a database query by joining user input directly into a query string.  
**Risk:** Input may change the meaning of the query.  
**Prevention:** Use parameterized queries so user input remains data, not executable query syntax.

### 3. Authentication Failures
**Scenario:** Sessions remain active after logout or session identifiers are not refreshed after login.  
**Risk:** An old or exposed session may remain useful.  
**Prevention:** Use secure session management, rotate session identifiers at important authentication events, and invalidate sessions on logout.

## Conclusion
The OWASP Top 10:2025 shows that security is broader than preventing one type of attack. Teams should protect access, configuration, dependencies, data, authentication, integrity, logging and error handling throughout the software lifecycle.

## Official references
- OWASP Top 10:2025: https://owasp.org/Top10/2025/
- OWASP Top 10 project: https://owasp.org/www-project-top-ten/
