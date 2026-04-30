# 📦 Spring Cloud Config Repository

This repository serves as a **centralized configuration store** for microservices using **Spring Cloud Config Server**.

It contains environment-specific and service-specific configuration files that are fetched at runtime by microservices.

---

## 🚀 Purpose

* Centralize configuration management
* Avoid hardcoding configs inside services
* Enable dynamic updates without redeploying services

---

## 📁 Repository Structure

```
.
├── application.yml        # Common configurations (shared across services)
├── address.yml           # Config for address-service
├── employee.yml          # Config for employee-service
```

---

## ⚙️ How It Works

1. Config Server connects to this repository
2. Microservices fetch configuration using:

   ```
   http://<config-server-url>/<application-name>/<profile>
   ```

Example:

```
http://localhost:8888/employee/default
```

---

## 🔗 Naming Convention

| File Name       | Service Name     |
| --------------- | ---------------- |
| application.yml | Shared config    |
| employee.yml    | employee-service |
| address.yml     | address-service  |

---

## 🛠️ Usage in Microservices

Add the following in your microservice:

### `bootstrap.yml` (or application.yml in newer versions)

```yaml
spring:
  application:
    name: employee
  config:
    import: "optional:configserver:http://localhost:8888"
```

---

## ⚠️ Important Notes

* ❌ Do NOT store sensitive data (passwords, API keys) in this public repository
* ✔ Use environment variables or a secure vault (e.g., HashiCorp Vault)

---

## 🌱 Future Improvements

* Add environment-based configs (`dev`, `prod`)
* Integrate secure config management
* Enable config refresh with `/actuator/refresh`

---

## 👨‍💻 Maintainer

Managed for microservices configuration in Spring Boot ecosystem.
