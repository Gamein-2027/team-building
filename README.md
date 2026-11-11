# Gamein 2026 - Team-Building Microservice

[![Java](https://img.shields.io/badge/Java-21%20LTS-orange.svg)](https://openjdk.org/projects/jdk/21/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Author](https://img.shields.io/badge/Author-ARASH%20ESLAMI-informational)](https://github.com/arashae)

The **team-building** microservice manages participant team registration, invitations, matchmaking, and roster formation prior to the start of Gamein 2026.

---

## 📌 Features

- **Team Formation & Invites**: Create teams, invite members via email/SMS, and manage roster roles.
- **Matchmaking**: Connects solo participants with open teams.
- **Stateless Operation**: Authenticates all requests using signed Bearer JWT tokens.
- **Virtual Threads & HikariCP**: Tuned for high concurrency during registration peaks.

For complete developer specifications, refer to [**`AGENTS.md`**](./AGENTS.md).

---

## 🚀 Build & Run

```bash
# Compile with Java 21
./gradlew compileJava

# Build executable fat JAR
./gradlew bootJar

# Run service locally
./gradlew bootRun
```

Default port: `8085` (context path `/team`).
