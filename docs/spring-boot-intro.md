# Spring Boot – Introduction & Structure

This document explains what Spring Boot is and how a typical Kotlin + Spring Boot application is structured and executed.

---

## 🚀 What is Spring Boot?

Spring Boot is a framework that simplifies the setup and development of production-ready Spring applications. It eliminates the need for manual configuration by providing default setups and embedded servers.

---

## ✅ Key Features

- **Auto Configuration** – Automatically configures components based on dependencies.
- **Standalone Applications** – No need to deploy to an external server.
- **Embedded Servers** – Uses Tomcat, Jetty, or Undertow out of the box.
- **No XML** – Uses annotations instead of verbose XML files.
- **Fast Development** – Minimal setup and quick start.

---

## 📁 Project Structure (Kotlin + Spring Boot)

```css
src/
└── main/
    ├── kotlin/
    │       └── com/
    │           └── example/
    │                 └── mvc/
    │                     ├── MvcApplication.kt
    │                     └── controller/
    │                              └── GetApiController.kt
    └── resources/
              ├── application.yml
              └── static/
```
## 🧩 Main Class – Entry Point

```kotlin
@SpringBootApplication
class MvcApplication

fun main(args: Array<String>) {
    runApplication<MvcApplication>(*args)
}
```

@SpringBootApplication
This is a meta-annotation that includes:

@Configuration

@EnableAutoConfiguration

@ComponentScan

It tells Spring Boot:
→ "This is the entry point and configuration base of the application."

runApplication<>()
Starts the Spring Boot application

Initializes the Spring context

Starts the embedded web server

✅ Summary
Spring Boot allows Kotlin developers to start building web applications quickly and with minimal configuration. The combination of annotations and default behavior helps reduce boilerplate code and improves productivity.
---
