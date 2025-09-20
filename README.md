# Invoice Issuer Microservices Platform

> **Tech Stack:** NestJS · TypeScript · Docker · PostgreSQL · RabbitMQ · Redis · MinIO · MongoDB

A distributed microservices system for issuing and delivering electronic invoices (NFe), designed with **clean architecture** and **event-driven communication**. Each service is independent, allowing scalability, maintainability, and testability.

---

## 🎯 Motivation

The motivation behind this project is to simulate a **real-world, business-critical system** for handling electronic invoices (NFe).  
It demonstrates how independent services collaborate to solve a complex workflow: **authentication, tax calculation, PDF generation, storage, and email delivery**.

This project allowed me to:  
- Apply **microservices and clean architecture** (Hexagonal + DDD lite)  
- Explore **asynchronous communication** with RabbitMQ  
- Integrate with services like **MinIO (S3)** for file storage and **SMTP** for notifications  
- Build a modular, maintainable, and production-ready system  

---

## 🧩 Features

- **Auth Service:** JWT authentication, login, registration  
- **User Service:** CRUD for users and companies  
- **Invoice Service:** Create and manage invoices  
- **Tax Service:** Calculate taxes (ISS, ICMS) automatically  
- **PDF Service:** Generate PDFs of invoices and store in MinIO  
- **Notification Service:** Send invoice emails to clients  
- **Audit Service:** Track all events and store logs in MongoDB  
- **Optional API Gateway:** Route requests, handle authentication, and rate limiting  

---

## 🛠 Tech Stack

| Layer                 | Technology                          |
|-----------------------|-------------------------------------|
| Backend Framework      | NestJS + TypeScript                 |
| Databases             | PostgreSQL (Invoices, Users), MongoDB (Logs) |
| Cache                  | Redis                                |
| Messaging Queue        | RabbitMQ                             |
| PDF Generation         | Puppeteer or PDFKit                  |
| File Storage           | MinIO (S3 compatible)               |
| Email                  | Mailhog / Nodemailer                 |
| Containerization       | Docker + Docker Compose             |
| Documentation          | Swagger                             |
| Authentication         | JWT + Refresh Token                  |

---

## 🏗 Architecture Overview

Each microservice follows **Hexagonal Architecture (Ports & Adapters)**:

Controllers / Adapters
│
Application Layer (Use Cases)
│
Domain Layer (Entities, Business Rules)
│
Infrastructure Layer (Database, Messaging, Storage)


**Event-driven flow example:**  
`Invoice Created → Tax Calculation → PDF Generation → Notification → Audit Logging`

---

## 🚀 Getting Started

### Prerequisites
- Docker & Docker Compose
- Node.js v18+
- npm or yarn

### Run the project
```bash
git clone https://github.com/yourusername/nfe-microservices.git
cd nfe-microservices
docker-compose up -d

Access services via ports defined in docker-compose.yml

Swagger UI available at http://localhost:{service_port}/docs

MinIO Console at http://localhost:9001 (user: minio / password: minio123)

cd apps/auth-service
npm install
npm run test

📄 Project Structure
apps/
├── auth-service/
├── user-service/
├── invoice-service/
├── tax-service/
├── pdf-service/
├── notification-service/
└── audit-service/
libs/
docker-compose.yml
README.md
.env

📂 Contribution

Contributions are welcome! Feel free to fork, open issues, or create pull requests.