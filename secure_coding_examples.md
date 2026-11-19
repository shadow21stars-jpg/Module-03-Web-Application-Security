# Secure Coding Examples (Defensive)

These small examples show safer coding patterns. Adapt them to your framework and review official documentation before production use.

## 1. Parameterized database query (Python DB-API style)

```python
# Safer: the value is passed separately as data.
cursor.execute(
    "SELECT id, display_name FROM users WHERE email = ?",
    (email,)
)
```

The placeholder syntax differs by database driver. Follow the driver documentation. Avoid constructing SQL by joining user input into query text.

## 2. Server-side authorization (pseudocode)

```text
record = load_record(record_id)

if current_user is not authenticated:
    return 401

if current_user is not record.owner and current_user.role is not "admin":
    return 403

return record
```

The permission check must happen on the server, not only by hiding a link or button in the browser.

## 3. Session cookie configuration (conceptual)

```text
Set-Cookie: session=<random-session-id>;
            Secure;
            HttpOnly;
            SameSite=Lax
```

Use HTTPS. The actual cookie configuration belongs in the server framework's session settings. Never publish real session values.

## 4. Safe error response

```json
{
  "error": "The request could not be completed."
}
```

Keep technical diagnostic details in protected server logs. Do not return stack traces, secrets or internal file paths to users.
