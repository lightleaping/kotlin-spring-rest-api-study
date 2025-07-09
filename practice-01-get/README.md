# Practice 01 – GET API with Spring Boot + Kotlin

This module demonstrates how to build basic RESTful GET endpoints using Kotlin and Spring Boot.

---

## 🧩 Covered Topics

- `@RestController` and `@RequestMapping`
- `@GetMapping` for GET requests
- `@RequestParam` for query parameters
- `@PathVariable` for path parameters
- Automatic object binding with data classes

---

## 🛠️ Endpoints Tested

### 1. `GET /api/hello`

Returns a simple greeting.

```kotlin
@GetMapping("/hello")
fun hello(): String = "Hello Kotlin Spring Boot!"
```

2. GET /api/query?name=Soojin&age=26
Handles query parameters using @RequestParam.

```
@GetMapping("/query")
fun queryParam(@RequestParam name: String, @RequestParam age: Int): String
```

3. GET /api/user/Soojin/26
Handles path variables using @PathVariable.

```
@GetMapping("/user/{name}/{age}")
fun pathVariable(@PathVariable name: String, @PathVariable age: Int): String
```

4. GET /api/object?name=Soojin&age=26
Maps multiple query parameters into a Kotlin data class.

```
data class UserRequest(val name: String, val age: Int)

@GetMapping("/object")
fun queryObject(userRequest: UserRequest): String
```


🧪 How to Test
Test using Talend API Tester (Chrome Extension):
→ Talend API Tester

Ensure that:

The server is running (./gradlew bootRun)

Requests return expected responses

🧠 What I Learned
How to build basic RESTful GET APIs

The difference between @RequestParam and @PathVariable

Kotlin's data class works great for parameter binding

Talend API Tester helps quickly validate REST endpoints