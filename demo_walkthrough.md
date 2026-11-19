# Safe Web Application Security Lab — Demo Walkthrough

## Purpose
Demonstrate the module workflow **Identify → Test → Fix → Document** using only a local training application or an intentionally provided sandbox.

## Safety rules
- Use only your own local lab or a system for which you have explicit written permission.
- Use fake accounts and sample data only.
- Do not scan public websites or access other people's accounts or information.
- Do not upload passwords, tokens, private records or screenshots containing personal data.

## Demo 1 — Access control
**Identify:** A record page should allow only its owner or an authorized role.  
**Test:** Create two dummy accounts (User A and User B) and one sample record owned by User A. Sign in as User B and check whether the application denies access to User A's record.  
**Fix:** Add a server-side ownership/role check before returning the record.  
**Retest:** User A can access the record; User B receives an access-denied response.  
**Document:** Record the expected result, observed result, fix and retest result. If no lab app is available, present this as a test plan rather than claiming it was executed.

## Demo 2 — Safe database query handling
**Identify:** Review whether database queries use parameters.  
**Test:** Inspect the source code for string concatenation of untrusted input into a query. Use code review or a local toy application only.  
**Fix:** Use parameterized queries or a safe ORM.  
**Retest:** Confirm that input is passed as a parameter and cannot change query structure.  
**Document:** Include a short before/after code review note. Do not use a production database.

## Demo 3 — Session cookie settings
**Identify:** Session cookies should be configured securely.  
**Test:** In the local lab, inspect the response's `Set-Cookie` header.  
**Fix:** Configure `Secure`, `HttpOnly`, an appropriate `SameSite` value, HTTPS, session rotation and logout invalidation.  
**Retest:** Confirm the expected cookie attributes and logout behavior.  
**Document:** Record the header attributes without copying the cookie value or session identifier.

## Demo 4 — Safe error handling
**Identify:** User-facing errors should not reveal internal details.  
**Test:** Cause a normal validation error using safe sample input in the local lab.  
**Fix:** Return a generic message and keep diagnostic details in protected logs.  
**Retest:** Confirm that the response does not expose stack traces, file paths or secrets.  
**Document:** Record the safe response and the retest outcome.

## Demo presentation script
“First, I identify the feature and its security requirement. Next, I test it only in a local or authorized sandbox using dummy data. If I find a weakness, I apply a defensive fix and repeat the same check. Finally, I document the evidence, impact, recommendation and retest result. This process helps improve application security without affecting real users or systems.”

## Evidence checklist
- [ ] Screenshot of the local lab or code review (hide all private values).
- [ ] Screenshot or note showing the expected test result.
- [ ] Screenshot or note showing the defensive fix.
- [ ] Retest result.
- [ ] Short conclusion and limitations.

**Important:** Do not tick evidence items or write “passed” until you have actually completed them.
