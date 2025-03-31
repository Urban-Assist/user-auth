# 🛠️ USER-AUTH

Welcome to the **User-Auth Microservice**! This service is the gatekeeper of your application, handling all user-related operations like authentication, registration, and profile management. Think of it as the bouncer at the club, but way friendlier (and with fewer tattoos). 🎉

---

## 🌟 Overview

### Key Features

- **User Registration**: Sign up users with email verification. No bots allowed! 🤖
- **Authentication**: Secure login with JWT tokens. Your data is safe with us! 🔒
- **OAuth2 Integration**: Login with Google. Because who remembers passwords anyway? 😅
- **Role-Based Access Control**: Admins, users, and providers—everyone gets their own VIP section. 🏷️
- **Email Notifications**: Sends welcome and verification emails. We even say "Hi" to your inbox! 📧
- **RabbitMQ Integration**: Seamless communication with other services. 🐇📬

---

## 🚀 Getting Started

### Prerequisites

Before you dive in, make sure you have the following:

- **Node.js** (v20 or higher) 🟢
- **Java** (JDK 17) ☕
- **Docker** 🐳
- **Kubernetes** (Optional, but recommended) ☸️
- **MySQL** (v8.0 or higher) 🐬

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/user-auth.git
   ```
2. Navigate to the project directory:
   ```bash
   cd user-auth
   ```
3. Install dependencies for the Node.js admin service:
   ```bash
   cd admin && npm install
   ```

---

## 🏃 Running Steps

### Local Development

1. Start the MySQL database.
2. Configure environment variables in `.env` files (refer to the **Environment Variables** section below).
3. Run the Node.js admin service:
   ```bash
   npm start
   ```
4. Build and run the Spring Boot service:
   ```bash
   ./mvnw spring-boot:run
   ```

### Testing

Run tests to ensure everything is working:
```bash
npm test
```

---

## 🐳 Docker + ☸️ Kubernetes

### Docker

1. Build the Docker image for the admin service:
   ```bash
   docker build -t user-auth-admin ./admin
   ```
2. Build the Docker image for the Spring Boot service:
   ```bash
   docker build -t user-auth .
   ```
3. Run the containers:
   ```bash
   docker-compose up
   ```

### Kubernetes

1. Apply the Kubernetes manifests:
   ```bash
   kubectl apply -f k8s/
   ```
2. Check the status of the deployments:
   ```bash
   kubectl get pods
   ```

---

## 📡 API Endpoints

### Public Endpoints
- **POST** `/auth-api/public/register`: Register a new user.

### Example Request

```bash
curl -X POST http://localhost:8080/auth-api/public/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "SecurePassword123",
    "firstname": "user123",
    "lastname": "user654",
    "role": "userrole"
  }'
```

- **POST** `/auth-api/public/authenticate`: Authenticate a user.

```bash
curl -X POST http://localhost:8080/auth-api/public/authenticate \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "SecurePassword123"
  }'
```

- **GET** `/auth-api/public/email-verification`: Verify email using a token.

```bash
curl -X GET "http://localhost:8080/auth-api/public/email-verification?token=your_verification_token"
```

### Secured Endpoints
- **GET** `/auth-api/user/profile`: Get user profile (requires JWT).

```bash
curl -X GET http://localhost:8080/auth-api/user/profile \
  -H "Authorization: Bearer <JWT_TOKEN>"
```

- **GET** `/auth-api/admin/dashboard`: Admin-only access.

```bash
curl -X GET http://localhost:8080/auth-api/admin/dashboard \
  -H "Authorization: Bearer <ADMIN_JWT_TOKEN>"
```

---

## 🛠️ Tech Stack

- **Backend**: Spring Boot (Java)
- **Frontend**: None (API-only service)
- **Database**: MySQL
- **Messaging**: RabbitMQ
- **Authentication**: JWT, OAuth2 (Google)
- **Containerization**: Docker
- **Orchestration**: Kubernetes

---

## 🌍 Contributions of This Service

This microservice is the backbone of user management in the Urban Assist ecosystem. It ensures:

- Secure and scalable user authentication.
- Seamless integration with other microservices via RabbitMQ.
- A delightful user experience with email notifications.

---

## 🔧 Required Environment Variables

### 🔑 Authentication & User Management

#### `AUTH_SERVER_PORT`

-  **Description**: The port for running the authentication & user management server.

-  **Example**:

```bash

AUTH_SERVER_PORT=8080

```

---

### 🏛️ Database Configuration

#### `DB_URL`

-  **Description**: The database connection URL.

-  **Example**:

```bash

DB_URL="your url"

```

#### `DB_USERNAME`

-  **Description**: Your database username.

-  **Example**:

```bash

DB_USERNAME="admin"

```

#### `DB_PASSWORD`

-  **Description**: Your database password.

-  **Example**:

```bash

DB_PASSWORD="securepassword123"

```

---

### 📧 Email Server Configuration

#### `EMAIL_SERVER_URL`

-  **Description**: The URL of the email server used for sending notifications related to user registration.

-  **Example**:

```bash

EMAIL_SERVER_URL="http://email.server/mail/send"

```

---

## 📜 User Flow Diagrams

### 📝 User Registration Flow

![User Registration Flow](./assets/user_registration_flow.png)

### 🔐 User Authentication Flow

![User Authentication Flow](./assets/user_authentication_flow.png)

---

## ✅ Next Steps

🎯 Once the environment variables are set, you can proceed with:

1. Starting the authentication service.

2. Launching the application backend & frontend.

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add your feature"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/your-feature-name
   ```
5. Open a pull request.

---

## 🎉 Fun Zone

![Funny GIF](https://media.giphy.com/media/3o7abldj0b3rxrZUxW/giphy.gif)

"Coding is like humor. If you have to explain it, it’s bad." 😄

---

## 📞 Need Help?

- 📧 **Email**: vaibhavpatel162002@gmail.com
- 🌐 **Website**: [Home Repair Support]([https://homerepairapp.com](http://advancedweb-vm4.research.cs.dal.ca/))
- 🗨️ **Community**: [Join our Discord](https://discord.gg/homerepair)

🚀 **Happy Coding** 🚀.
