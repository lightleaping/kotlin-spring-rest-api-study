# 🟧 Practice 02 – POST API with @RequestBody

This module demonstrates how to receive and bind JSON request bodies in a Spring Boot application using Kotlin and `@RequestBody`.

---

## 🎯 Objectives

- Handle HTTP POST requests using `@PostMapping`
- Map JSON data to Kotlin `data class` using Jackson
- Support `snake_case` JSON using `@JsonNaming`
- Test using Talend API Tester

---

## 📁 Files

| File | Description |
|------|-------------|
| `PostApiController.kt` | Defines multiple POST endpoints |
| `UserRequest.kt` | Kotlin `data class` used for JSON mapping |

---

## 🛠️ Endpoints

### 1. `POST /api/post-mapping`

Returns a plain string response.

```kotlin
@PostMapping("/post-mapping")
fun postMapping(): String
```
2. POST /api/request-mapping
   Same as above, using @RequestMapping instead of @PostMapping.

```kotlin
@RequestMapping(method = [RequestMethod.POST], value = ["/request-mapping"])
fun requestMapping(): String
```
3. POST /api/post-mapping/object
   Receives JSON and maps to UserRequest object.
```kotlin
@PostMapping("/post-mapping/object")
fun postMappingObject(@RequestBody userRequest: UserRequest): UserRequest
```
📦 UserRequest Data Class
```kotlin
@JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy::class)
data class UserRequest(
var name: String? = null,
var age: Int? = null,
var email: String? = null,
var address: String? = null,
var phoneNumber: String? = null
)
```
Supports snake_case JSON keys (e.g., phone_number)

Uses null-safe properties for easier binding

🧪 Test with Talend API Tester
POST → http://localhost:8080/api/post-mapping/object
Header → Content-Type: application/json
Body:

```json
{
"name": "Soojin",
"age": 26,
"email": "soojin@example.com",
"address": "Seoul",
"phone_number": "010-1234-5678"
}
```
✅ Expected Response:
```json
{
"name": "Soojin",
"age": 26,
"email": "soojin@example.com",
"address": "Seoul",
"phoneNumber": "010-1234-5678"
}
```
### ❗ Troubleshooting Notes

| Status | Issue                                             | Cause                             | Fix                                |
|--------|---------------------------------------------------|-----------------------------------|-------------------------------------|
| 405    | Used `@GetMapping` instead of `@PostMapping`     | HTTP method mismatch              | Use `@PostMapping` for POST requests |
| 404    | Endpoint not found                                | Forgot to save file before run    | Save files before restarting server |
| 400    | JSON parsing failed                               | Missing comma `,` in request body | Carefully check JSON syntax         |

📚 What I Learned
How to map request body to a Kotlin object using @RequestBody

How Jackson and @JsonNaming help bridge JSON <-> Kotlin

Talend is useful for simulating real API clients

Common pitfalls with request types, file saving, and JSON formatting
