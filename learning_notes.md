# Learning Notes — Web Application Security

## 1. How a web application works
A web application usually has:
- **Client:** browser or mobile app used by the user.
- **Server:** receives requests, applies business rules and sends responses.
- **Database:** stores information such as accounts and records.

### HTTP request and response lifecycle
1. A user enters a URL or clicks a link.
2. The browser sends an HTTP request to the server.
3. The server checks the request, identity and permissions.
4. The server may read or update database information.
5. The server sends an HTTP response with a status code, headers and sometimes a body.
6. The browser displays the result.

Common methods: `GET` reads information, `POST` submits information, `PUT/PATCH` updates information, and `DELETE` requests deletion. HTTPS protects data while it travels between browser and server.

## 2. Cookies and sessions
- A **cookie** is a small piece of data stored by the browser and sent with matching requests.
- A **session** is server-side information used to remember a user's state between requests.
- A session cookie commonly contains a random session identifier; the server uses it to find the session data.

Good practices:
- Use HTTPS.
- Set session cookies with `Secure`, `HttpOnly`, and an appropriate `SameSite` value.
- Use unpredictable session IDs.
- Regenerate the session ID after login or privilege changes.
- Expire sessions and invalidate them on logout.
- Do not store passwords or sensitive personal data in cookies.

## 3. Authentication vs authorization
| Term | Meaning | Example |
|---|---|---|
| Authentication | Confirms who the user is | Sign in with an account |
| Authorization | Checks what the user is allowed to do | Only an administrator can manage users |

A user being logged in does not mean they can access every record or feature. Check permissions on the server for every protected action.

## 4. OWASP Top 10:2025
The current OWASP Top 10 release is the 2025 edition. It is an awareness list of major web application security risks.

1. **A01 Broken Access Control:** users can perform actions or view data outside their permissions.
2. **A02 Security Misconfiguration:** unsafe defaults, exposed debug features, unnecessary services or incorrect security settings.
3. **A03 Software Supply Chain Failures:** risk from compromised or untrusted dependencies, build systems or distribution processes.
4. **A04 Cryptographic Failures:** sensitive information is not properly protected with suitable cryptography.
5. **A05 Injection:** untrusted input is treated as a command or query instead of data.
6. **A06 Insecure Design:** security requirements and abuse cases were not considered during design.
7. **A07 Authentication Failures:** weaknesses in login, identity verification, or account/session handling.
8. **A08 Software or Data Integrity Failures:** software or data is accepted without sufficient integrity verification.
9. **A09 Security Logging and Alerting Failures:** important events are not logged, monitored or alerted on appropriately.
10. **A10 Mishandling of Exceptional Conditions:** errors and unusual conditions are handled unsafely, such as failing open or exposing sensitive details.

## 5. Secure coding practices
- Validate input on the server using allow-lists and sensible limits.
- Use parameterized database queries.
- Encode output for the correct context to reduce cross-site scripting risk.
- Enforce authorization on every protected server-side request.
- Store passwords using a modern password-hashing algorithm with a unique salt.
- Keep frameworks and dependencies supported and updated.
- Store secrets outside source code.
- Use HTTPS and secure cookie settings.
- Show users generic error messages; keep useful details in protected logs.
- Log security-relevant events without recording passwords, tokens or unnecessary personal data.
- Review changes and run security tests before release.

## 6. Security testing workflow
**Identify → Test → Fix → Retest → Document**
- Identify the asset, scope and possible risk.
- Test only in an authorized sandbox with safe test data.
- Record evidence and impact without exposing private information.
- Apply a fix.
- Repeat the same check to confirm the issue is resolved.
- Document the result, limitations and remaining risks.

## 7. Key takeaway
Web application security means protecting user data and making sure every request is correctly validated, authenticated, authorized, processed and monitored.
