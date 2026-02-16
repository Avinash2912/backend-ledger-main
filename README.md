Bank Transaction System (Backend)
An industry-grade banking backend architecture built with Node.js, Express, and MongoDB. This project implements a Ledger-based financial system, ensuring data consistency, auditability, and security for financial transactions.

🚀 Key Features
Ledger-Based Accounting: Implements double-entry bookkeeping. Balances are derived from transaction history rather than stored as static values to ensure 100% data integrity.

Transaction Idempotency: Prevents duplicate payments using unique idempotency keys, ensuring that retried requests do not result in double debits.

Secure Authentication: User registration and login using JWT (JSON Web Tokens) stored in HTTP-only cookies and password hashing with bcrypt.

System User Hierarchy: Dedicated administrative "System User" for controlled operations like initial account funding.

Automated Notifications: Integration with Nodemailer and Google Cloud Gmail API to send real-time email alerts for transactions and registration.

Advanced MongoDB Queries: Utilizes Aggregation Pipelines for high-performance balance calculation and complex data retrieval.

🛠 Tech Stack
Runtime: Node.js

Framework: Express.js

Database: MongoDB (Atlas)

ODM: Mongoose

Security: JWT, bcrypt, Cookie-parser

Utilities: Dotenv (Environment Management), Nodemailer (Email Service), Nodemon (Development)

📂 Project Structure
Plaintext
src/
├── config/             # Database & environment configurations
├── controllers/        # Business logic for Auth, Accounts, and Transactions
├── middlewares/        # JWT Verification, System User checks, Error handling
├── models/             # Mongoose Schemas (User, Account, Transaction, Ledger, Blacklist)
├── routes/             # API Endpoints
├── services/           # External services (Email/Nodemailer)
├── app.js              # Express app configuration
└── server.js           # Server entry point
⚙️ Setup & Installation
Clone the repository:

Bash
git clone https://github.com/yourusername/bank-backend.git
cd bank-backend
Install dependencies:

Bash
npm install
Environment Variables:
Create a .env file in the root directory and add the following:

Code snippet
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
EMAIL_USER=your_gmail
EMAIL_CLIENT_ID=your_google_client_id
EMAIL_CLIENT_SECRET=your_google_client_secret
EMAIL_REFRESH_TOKEN=your_google_refresh_token
Run the application:

Bash
# For development
npm run dev

# For production
npm start
📝 API Endpoints (Brief)
Authentication
POST /api/v1/auth/register - Create a new account.

POST /api/v1/auth/login - Secure login with cookie-based JWT.

POST /api/v1/auth/logout - Blacklist token and clear cookies.

Transactions
POST /api/v1/transactions/transfer - Initiate a credit/debit transaction.

GET /api/v1/transactions/balance - Get derived balance via Aggregation Pipeline.

POST /api/v1/transactions/system/initial-funds - (Admin only) Add initial balance.

🛡 Security Practices
Password Hashing: Uses salt rounds with bcrypt.

Route Protection: Custom middleware to intercept unauthorized requests.

JWT Blacklisting: Handles secure logout by invalidating tokens.

Input Validation: Regex-based email validation and schema constraints.
