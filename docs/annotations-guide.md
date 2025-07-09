# Spring Boot REST API – Common Annotations

This document summarizes frequently used annotations in Spring Boot REST API development using Kotlin.

---

## 🧩 Core REST API Annotations

| Annotation | Description |
|------------|-------------|
| `@RestController` | Combines `@Controller` and `@ResponseBody`. Declares a class as a REST controller. |
| `@RequestMapping` | Maps a base URL path for a class or method. |
| `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` | HTTP method-specific shortcuts for `@RequestMapping`. |
| `@RequestParam` | Extracts query parameters from the URL (e.g., `?name=soojin`). |
| `@PathVariable` | Extracts variables from the URL path (e.g., `/user/{id}`). |
| `@RequestBody` | Automatically maps JSON body to a Kotlin data class. |
| `@ResponseBody` | Converts return values to JSON. (Implicit in `@RestController`) |
| `@ResponseEntity` | Allows custom HTTP status and response body. |
| `@ResponseStatus` | Sets response status code directly on method without using `ResponseEntity`. |

---

## 🔧 Jackson JSON Annotations (for `@RequestBody` and `@ResponseBody`)

| Annotation | Description |
|------------|-------------|
| `@JsonProperty("json_field")` | Maps a JSON field name to a Kotlin property. |
| `@JsonNaming` | Applies naming strategies (e.g., snake_case) for all properties in a class. |

---

## 📦 Example Usage

```kotlin
@RestController
@RequestMapping("/api")
class UserController {

    @GetMapping("/hello")
    fun hello(): String = "Hello"

    @GetMapping("/user/{id}")
    fun getUser(@PathVariable id: Int): String = "User ID: $id"

    @GetMapping("/query")
    fun search(@RequestParam keyword: String): String = "Search: $keyword"

    @PostMapping("/user")
    fun createUser(@RequestBody user: UserRequest): ResponseEntity<UserResponse> {
        return ResponseEntity.status(HttpStatus.CREATED).body(
            UserResponse(user.name, user.age)
        )
    }
}
```

🧠 Notes
@RestController automatically applies @ResponseBody.

Use @RequestParam for short parameters like filters, and @RequestBody for larger data payloads.

@PathVariable is useful for accessing specific resources like /users/1.

ResponseEntity gives you full control over the response structure.

🔗 References
Spring Boot Official Docs
(
🧠 Notes
@RestController automatically applies @ResponseBody.

Use @RequestParam for short parameters like filters, and @RequestBody for larger data payloads.

@PathVariable is useful for accessing specific resources like /users/1.

ResponseEntity gives you full control over the response structure.

🔗 References
Spring Boot Official Docs
https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/
Jackson Annotations
https://fasterxml.github.io/jackson-annotations/javadoc/2.12/
---