# 📓 Journal App

A secure and intelligent journal web application developed using **Spring Boot**, **MongoDB**, and **Spring Security**, with integrated support for weather info, sentiment analysis, email notifications, and Redis caching.

---

## ✨ Features

- 🔐 User Registration, Login with JWT Authentication
- 📝 Create, View, and Delete Journal Entries
- 💬 Weekly Sentiment Analysis via Kafka
- 📧 Email Notifications
- 🌦️ Get Real-Time Weather Updates
- 🚀 Admin Dashboard and Role-Based Access
- 🧠 Redis Caching for Performance Optimization
- 🔒 Password Hashing using BCrypt

---

## 📁 Modules & Packages

### 📦 Controllers

- **`JournalEntryController`**  
  Handles journal entry CRUD operations.

- **`UserController`**  
  Handles user registration and login logic.

- **`PublicController`**  
  Exposes public APIs like weather updates.

- **`AdminController`**  
  Exposes admin-level APIs and functionality.

- **`GoogleAuthController`**  
  Supports Google-based authentication.

---

## 🔧 Services

### 📨 `EmailService`

Sends email notifications using JavaMailSender.

```java
sendEmail(String to, String subject, String body)
Paste your rich text content here. You ca

### 📔 `JournalEntryService`

Handles CRUD operations for journal entries and maps them to users.

java

CopyEdit

`saveEntry(JournalEntry journalEntry, String userName) deleteById(ObjectId id, String userName)`

* * *

### 💾 `RedisService`

Caches weather data using Redis and handles serialization/deserialization of objects.

java

CopyEdit

`<T> T get(String key, Class<T> entityClass) void set(String key, Object o, Long ttl)`

* * *

### 💬 `SentimentConsumerService`

Consumes the Kafka topic `weekly-sentiments` and dispatches emails with the sentiment analysis report.

java

CopyEdit

`@KafkaListener(topics = "weekly-sentiments", groupId = "weekly-sentiment-group") void consume(SentimentData sentimentData)`

* * *

### 👤 `UserDetailsServiceImpl`

Implements Spring Security’s `UserDetailsService` to load user credentials.

java

CopyEdit

`UserDetails loadUserByUsername(String username)`

* * *

### 👥 `UserService`

Handles user registration, assigns roles, encrypts passwords, and saves data in MongoDB.

java

CopyEdit

`boolean saveNewUser(User user) void saveAdmin(User user) void saveUser(User user) User findByUserName(String userName)`

* * *

### 🌦️ `WeatherService`

Calls REST API for weather info and caches it using Redis.

java

CopyEdit

`WeatherResponse getWeather(String city)`

* * *

## 🗃️ Database

* *   Uses **MongoDB** for storing journal entries and users.
*     
* *   Every user has a one-to-many mapping with journal entries.
*     

* * *

## 🛡️ Security

* *   Secured with **Spring Security** and **JWT**.
*     
* *   **BCrypt** used for password encryption.
*     
* *   **Role-Based Access Control (RBAC)** for `USER` and `ADMIN` roles.
*     

* * *

## 🌐 External Integrations

* *   🔗 **Kafka**: For consuming weekly sentiment data.
*     
* *   🌐 **Weather API**: For fetching weather data.
*     
* *   📧 **JavaMailSender**: For sending email notifications.
*     
* *   🧠 **Redis**: For caching external API responses.
*     

* * *

## 🧪 Run Locally

### 🛠️ Prerequisites

* *   MongoDB
*     
* *   Redis
*     
* *   Kafka
*     

### ▶️ Run the Application

bash

CopyEdit

`./mvnw spring-boot:run`

* * *

## 🧪 API Endpoints

> Sample endpoints for testing (secured with JWT)

Method

Endpoint

Description

POST

`/api/users/register`

Register a new user

POST

`/api/users/login`

User login to get JWT

GET

`/api/entries`

Get user's journal entries

POST

`/api/entries`

Create new journal entry

DELETE

`/api/entries/{id}`

Delete journal entry

GET

`/api/public/weather?city=London`

Get weather info for city

GET

`/api/admin/users`

Admin: List all users

* * *

## 🧑‍💻 Author

**Ashwin Kumar**  
Built with ❤️ for journaling, productivity, and self-reflection.

n paste directly from Word or other rich text sources.
