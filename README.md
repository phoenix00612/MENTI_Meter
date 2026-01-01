# Mentimeter Clone – Backend

This repository contains the **Spring Boot backend** for the Mentimeter Clone project.
It exposes RESTful APIs for core application logic, implements secure authentication using JWT, and enables real-time quiz interactions via WebSockets (STOMP).

🔗 **Repository:** [https://github.com/phoenix00612/MENTI_Meter](https://github.com/phoenix00612/MENTI_Meter)

---

## ✨ Key Features

### 🔹 RESTful API Layer

* Well-structured APIs for managing **users, quizzes, sessions, attempts, and analytics**
* Clean controller–service–repository separation

### 🔐 Authentication & Security

* Secured using **Spring Security**
* Stateless authentication with **JSON Web Tokens (JWT)**

### ⚡ Real-Time Communication

* **WebSocket (STOMP)** based real-time quiz flow
* Supports:

  * Joining live sessions
  * Starting quizzes
  * Moving to next questions
  * Submitting answers
  * Live leaderboard updates

### 🗄️ Database & Persistence

* Uses **Spring Data MongoDB**
* Stores:

  * Users
  * Quizzes & questions
  * Live sessions
  * Participant attempts and scores

### 🤖 AI-Powered Quiz Generation

* Integrates with **Google Gemini AI via Vertex AI**
* Automatically generates quiz questions from text input

### 🧠 Session Management

* Creates real-time quiz sessions with **unique join codes**
* Tracks participant state, responses, and scoring in real time

### 🕒 Asynchronous Quizzes

* Supports quiz sharing via public links
* Allows participants to attempt quizzes asynchronously
* Stores all attempts for analytics and review

---

## 🛠️ Tech Stack

### Backend

* **Java 17**
* **Spring Boot**

  * Spring Web (REST APIs)
  * Spring Security (JWT-based authentication)
  * Spring WebSocket (STOMP)
  * Spring Data MongoDB

### Database & Tools

* **MongoDB** – NoSQL data storage
* **Maven** – Dependency management
* **Lombok** – Boilerplate reduction
* **jjwt** – JWT creation and validation
* **Google Cloud Vertex AI** – Gemini AI integration

---

## ⚙️ Setup & Installation

### 1️⃣ Prerequisites

* JDK 17 or later
* Apache Maven
* MongoDB (local or cloud instance)

### 2️⃣ Clone the Repository

```bash
git clone https://github.com/phoenix00612/MENTI_Meter.git
cd MENTI_Meter
```

### 3️⃣ Configure Environment Variables

The application **requires environment variables** to function correctly.
You may define them in your OS environment or via `application.properties` (do **not** commit secrets).

Required variables:

* `JWT_SECRET_KEY` – Secure random string for signing JWTs
* `GCP_PROJECT_ID` – Google Cloud project ID (Vertex AI)
* `spring.data.mongodb.uri` – MongoDB connection URI

  * Local example:

    ```
    mongodb://localhost:27017/mentimeter_db
    ```
  * Cloud example:

    ```
    mongodb+srv://user:password@cluster.mongodb.net/mentimeter_db
    ```

### 4️⃣ Build the Project

```bash
mvn clean install
```

### 5️⃣ Run the Application

```bash
mvn spring-boot:run
```

The server starts on **port 8080** by default.

---

## 📡 API Overview

### Authentication

* `/auth/register` – User registration
* `/auth/login` – User login & JWT generation

### Quiz Management

* `/api/quizzes/**` – Create, update, delete, and fetch quizzes

### Live Sessions

* `/api/sessions/**` – Create and manage real-time quiz sessions

### Asynchronous Quizzes

* `/api/share/**` – Share quizzes via link and submit attempts

### AI Quiz Generation

* `/api/ai/generate-quiz-from-text` – Generate quizzes using Gemini AI

### WebSockets

* `/ws/**` – STOMP WebSocket endpoint for real-time interactions
