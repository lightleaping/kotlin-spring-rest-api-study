# Practice 02 – POST API with @RequestBody

This module demonstrates how to handle HTTP POST requests in Spring Boot using `@RequestBody` and Kotlin `data class`.

---

## 📌 Covered Topics

- `@PostMapping` to handle POST requests
- `@RequestBody` to bind JSON payloads
- Using `@JsonNaming` to support snake_case JSON keys
- Returning Kotlin objects as JSON responses
- Testing POST endpoints with Talend API Tester

---

## 🛠️ Endpoint Summary

### 1. `POST /api/post-mapping`
Returns a simple string.
```kotlin
@PostMapping("/post-mapping")
fun postMapping(): String
```
---
2. POST /api/request-mapping
   Uses @RequestMapping as an alternative to @PostMapping.
```kotlin
@RequestMapping(method = [RequestMethod.POST], value = ["/request-mapping"])
fun requestMapping(): String
```
---
3. POST /api/post-mapping/object
   Receives a JSON object and maps it to a Kotlin data class using @RequestBody.
```kotlin
@PostMapping("/post-mapping/object")
fun postMappingObject(@RequestBody userRequest: UserRequest): UserRequest
```

📦 Data Class – UserRequest
```kotlin
@JsonNaming(PropertyNamingStrategy.SnakeCaseStrategy::class)
data class UserRequest (
var name: String? = null,
var age: Int? = null,
var email: String? = null,
var address: String? = null,
var phoneNumber: String? = null
)
```
Accepts snake_case JSON (e.g., phone_number)

Uses nullable types to prevent deserialization errors

* PropertyNamingStrategy: deprecated -> PropertyNamingStrategies 사용

🧪 Testing with Talend API Tester
1. Method: POST

2. URL: http://localhost:8080/api/post-mapping/object

3. Headers:
```pgsql
Content-Type: application/json
```
4. JSON Body:
```json
{
"name": "Soojin",
"age": 26,
"email": "soojin@example.com",
"address": "Seoul",
"phone_number": "010-1234-5678"
}
```
✅ Response:
Status: 200 OK
Body:
        
```json
{
"name": "Soojin",
"age": 26,
"email": "soojin@example.com",
"address": "Seoul",
"phoneNumber": "010-1234-5678"
}
```
🧠 What I Learned
How to map a JSON request to a Kotlin object

How to design a data class with snake_case compatibility

How to test POST endpoints and handle response structure