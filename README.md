
# 🏦 Bank Transaction System – Backend

A **production-style banking backend** built using **Node.js, Express, and MongoDB**, designed with a **ledger-based accounting architecture** similar to real-world financial systems.  
This project focuses on **data consistency, auditability, and transactional safety**.

It demonstrates how modern backend systems handle **secure transactions, idempotent APIs, and derived balances** instead of relying on error-prone stored values.

---

## 💡 Why this project matters

Most demo banking projects store balances directly, which leads to data inconsistency and poor auditability.  
This system follows a **ledger-first design**, where:

- All money movement is recorded as immutable transactions  
- Balances are calculated from the ledger  
- Every transaction is traceable and auditable  
- Duplicate requests are safely handled  

This reflects **real-world financial backend patterns** used in fintech and payment systems.

---

## 🚀 Core Features

- **Ledger-Based Accounting (Double Entry)**  
  Credits and debits are recorded separately. Balances are derived using MongoDB aggregation pipelines.

- **Idempotent Transactions**  
  Prevents double debit/credit on retries using idempotency keys.

- **Secure Authentication**  
  JWT stored in HTTP-only cookies + bcrypt for password hashing.

- **Role-Based System User**  
  Dedicated system/admin user for privileged operations like initial funding.

- **Email Notifications**  
  Real-time alerts via Nodemailer (Gmail OAuth).

- **Production-Style Architecture**  
  Clean separation of routes, controllers, services, and middlewares.

---

## 🛠 Tech Stack

**Node.js · Express · MongoDB (Atlas) · Mongoose · JWT · bcrypt · Nodemailer · dotenv**

---

## 🧠 Architecture (High-Level)



Client
│
▼
API Routes (Express)
│
▼
Controllers
│
▼
Services  ───────► External Services (Email)
│
▼
Models (Mongoose)
│
▼
MongoDB (Ledger + Transactions + Users)



---

## 🧩 Ledger Flow (Transaction Lifecycle)


Client Request
│
▼
Validate & Authenticate
│
▼
Check Idempotency Key
│
▼
Create Ledger Entries (Debit + Credit)
│
▼
Store Transaction Record
│
▼
Derive Balance using Aggregation
│
▼
Send Email Notification



---

## 🔁 Idempotency Flow



Client Retry Request
│
▼
Check Idempotency Key
│
┌────┴─────┐
│ Exists?  │
└────┬─────┘
│
Yes  ▼       No
Return Old    Process Transaction
Response      Save Idempotency Key



---

## 🧪 API Endpoints (Brief)

### 🔐 Authentication
- `POST /api/v1/auth/register`  
- `POST /api/v1/auth/login`  
- `POST /api/v1/auth/logout`  

### 💸 Transactions
- `POST /api/v1/transactions/transfer`  
- `GET  /api/v1/transactions/balance`  
- `POST /api/v1/transactions/system/initial-funds`  

---

## 🔐 Security & Reliability

- Password hashing using bcrypt  
- JWT auth with HTTP-only cookies  
- Token blacklisting on logout  
- Input validation & schema constraints  
- Idempotent APIs for transaction safety  

---

## 📌 What this project demonstrates

- Understanding of **financial system design**  
- Designing **safe, retryable APIs**  
- Applying **ledger-based data modeling**  
- Writing **production-grade backend architecture**  
- Handling **security, auth, and transactional consistency**  

---

## 📝 Project Explanation (For Resume / Portfolio)

This project is a backend system designed to simulate how real financial platforms handle money movement securely and reliably.

Instead of storing user balances directly, the system follows a ledger-based approach where every credit and debit is recorded as an immutable transaction. Balances are calculated dynamically from transaction history using MongoDB aggregation pipelines, ensuring auditability and preventing data inconsistency.

To handle real-world issues like API retries and duplicate requests, idempotent transaction endpoints were implemented to prevent double debits or credits. The system also includes secure authentication using JWT with HTTP-only cookies, role-based access for privileged operations, and email notifications for transaction events.

This project demonstrates practical backend system design patterns used in fintech platforms, focusing on transactional safety, security, and production-ready architecture.

---

## 🧠 Future Scope

- Rate limiting  
- Redis-based idempotency  
- Event-driven notifications  
- OpenAPI (Swagger) documentation  
- Distributed locks for high concurrency  
```

---

