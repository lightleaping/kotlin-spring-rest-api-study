# JSON to Kotlin Object Binding in Spring Boot

## 🧩 Tools

- Jackson (default JSON library in Spring Boot)
- Kotlin `data class`
- `@RequestBody` annotation
- `@JsonNaming` for snake_case mapping

---

## ✅ Key Techniques

### 1. Snake Case Handling

```kotlin
@JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy::class)
data class UserRequest(
    val phoneNumber: String? = null
)
```

JSON input:
```json
{
"phone_number": "010-1234-5678"
}
```


2. Null Safety in Kotlin
   Kotlin properties should be nullable or have default values

Avoid val age: Int without = 0 or ? = null

3. Common Pitfalls
   Missing Content-Type: application/json

Field name mismatch between JSON and data class

Missing default/null values → 400 error or empty binding

🧠 Best Practices

Use @JsonProperty for precise key mapping if needed

Always test with tools like Talend or Postman

Include proper error handling when using @RequestBody