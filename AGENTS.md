# Team-Building Microservice Guide (AGENTS.md)

## 📌 Overview
The **team-building** service manages pre-competition and onboarding workflows: participant team creation, invitations, matchmaking, roster approvals, and team profile state.

- **Directory**: `F:\projects\Gamein-2022\team-building`
- **Port**: Default host port `8085` (container port `8080`)
- **Context Path**: `/team`
- **Tech Stack**: Spring Boot 3.3.5, Java 21 (Virtual Threads enabled), Gradle 8.10.2, PostgreSQL 16, Redis, Jakarta Persistence (Hibernate 6).

---

## 🏗️ Architecture & Decoupled State
- **Stateless Operation**: Authenticates participant requests using signed JWT tokens.
- **Email & SMS Notifications**: Integrates with Kavenegar SMS gateway and SMTP relays for team invite verification codes.
- **Connection Optimization**: Configured with **HikariCP** and Virtual Threads to handle registration traffic spikes prior to game launch.

---

## 📁 Key Packages & Files

| Package / File | Purpose |
| :--- | :--- |
| [`controllers.InitController`](file:///F:/projects/Gamein-2022/team-building/src/main/java/gamein2/team/controllers/InitController.java) | Request validation, auth extraction, and exception handling advice. |
| [`kernel.entity.Team`](file:///F:/projects/Gamein-2022/team-building/src/main/java/gamein2/team/kernel/entity/Team.java) | Team entity representing roster membership and team profile. |
| [`kernel.entity.TeamOffer`](file:///F:/projects/Gamein-2022/team-building/src/main/java/gamein2/team/kernel/entity/TeamOffer.java) | Participant invitation requests and join offers. |
| [`kernel.util.JwtUtils`](file:///F:/projects/Gamein-2022/team-building/src/main/java/gamein2/team/kernel/util/JwtUtils.java) | JWT validation and decoding. |
| [`application.properties`](file:///F:/projects/Gamein-2022/team-building/src/main/resources/application.properties) | Configuration for Virtual Threads, SMS API keys, and database connection pool. |

---

## ⚙️ Configuration & Concurrency

```properties
server.port=8080
server.servlet.context-path=/team

spring.threads.virtual.enabled=true
spring.jpa.open-in-view=false

# HikariCP Connection Pool
spring.datasource.hikari.maximum-pool-size=30
spring.datasource.hikari.minimum-idle=10
spring.datasource.hikari.connection-timeout=5000
```

---

## 🚀 Build & Run

```bash
# Compile and check Java 21 compatibility
./gradlew compileJava

# Build executable fat JAR
./gradlew bootJar

# Run service locally
./gradlew bootRun
```
Executable JAR is placed at: `build/libs/team-building-0.0.1-SNAPSHOT.jar`.
