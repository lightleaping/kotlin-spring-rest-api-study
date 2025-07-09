# REST API Overview

This document summarizes the key principles of REST and related HTTP concepts.

---

## 🔷 What is REST?

REST (Representational State Transfer) is an architectural style for designing networked applications. It defines a set of constraints for building scalable web services.

### Key REST Principles:

- **Client-Server**: Separate user interface concerns from data storage concerns.
- **Stateless**: Each request from the client must contain all the information needed.
- **Cacheable**: Responses must define themselves as cacheable or not.
- **Layered System**: Architecture can be composed of multiple layers (e.g. load balancer, proxy).
- **Uniform Interface**: A consistent interface across APIs.
- **Code on Demand (optional)**: Server can send code (like JavaScript) to be executed by the client.

---

## 🔸 HTTP Methods and CRUD Mapping

| HTTP Method | Description | CRUD Action | Safe | Idempotent |
|-------------|-------------|-------------|------|------------|
| GET         | Retrieve resource | Read | ✅ | ✅ |
| POST        | Create resource | Create | ❌ | ❌ |
| PUT         | Update/replace resource | Update | ❌ | ✅ |
| DELETE      | Delete resource | Delete | ❌ | ✅ |

---

## 🔸 URI Design Best Practices

- Use plural nouns for resources: `/users`, `/posts`
- Use nouns, not verbs: `/products` instead of `/getAllProducts`
- Use path parameters for specific resources: `/users/123`
- Use query parameters for filtering, paging: `/users?page=1&size=10`

---

## 🔸 HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 OK | Successful request |
| 201 Created | New resource created |
| 400 Bad Request | Invalid request format |
| 401 Unauthorized | Authentication required |
| 404 Not Found | Resource not found |
| 500 Internal Server Error | Server failed to process |

---

## 🧠 Summary

REST is stateless, resource-based, and relies on HTTP methods and status codes for communication.  
Designing clean URIs and choosing the correct HTTP verbs are key to building proper REST APIs.
