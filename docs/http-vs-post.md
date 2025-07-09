# GET vs POST in REST API

This document explains the difference between the GET and POST HTTP methods in a REST API context.

---

## 🔍 Purpose

| Method | Use Case |
|--------|----------|
| **GET** | Retrieve (read-only) data from the server |
| **POST** | Send data to the server to create a new resource |

---

## ⚙️ Technical Differences

| Property | GET | POST |
|----------|-----|------|
| Request Body | ❌ Not allowed | ✅ Yes, required |
| Safe | ✅ Yes | ❌ No |
| Idempotent | ✅ Yes | ❌ No |
| Visible Parameters | ✅ In URL (`?name=...`) | ❌ In body (not visible in URL) |
| Used For | Read-only data fetch | Resource creation, form submission |

---

## 🧪 Example – Kotlin Spring Boot

### GET with `@RequestParam`

```kotlin
@GetMapping("/search")
fun search(@RequestParam keyword: String): String {
    return "Searching for: $keyword"
}
```

POST with @RequestBody
```kotlin
@PostMapping("/user")
fun createUser(@RequestBody user: UserRequest): UserResponse {
    return UserResponse(user.name, user.age)
}
```

✅ Summary
Use GET when the request does not change server state and is intended to fetch data.

Use POST when you are submitting new data to the server.

GET is safe and idempotent, while POST is neither.

GET data appears in the URL, whereas POST data is sent in the body (typically as JSON).

🧠 Best Practices
Avoid sending sensitive data via GET (URL is logged and cached).

Use POST for operations like registration, login, and form submission.

Combine POST with @Valid and DTOs for data validation (in later stages).

🔗 Related Concepts
none.
---


