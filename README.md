# 📈 Stock Trading Platform – Backend

This repository contains the backend logic for a real-time stock trading application, enabling secure transactions, real-time price updates, wallet management, and background processing using a robust event-driven architecture.

---

## 🔧 Tech Stack

- **Node.js & Express.js** – Backend REST API
- **PostgreSQL** – Primary data store for user data, orders, and transactions
- **Redis (via Docker)** – Used for caching, real-time Pub/Sub messaging, and order book storage
- **BullMQ (Redis-based)** – Message queue system to handle background jobs
- **Stripe + Webhooks** – Handles dummy payment flows and wallet top-ups
- **Nodemailer** – For automated email notifications
- **Docker** – Used to containerize Redis and related services

---

## 🧠 Key Features

### 🎯 Core Functionality
- Full support for user registration, login, and secure authentication using JWT.
- Buy/sell stock orders with automatic order matching and partial fulfillment support.
- Maintains user wallet balance, transaction history, and order statuses.
- Logs critical system events and financial activities for auditability.

### 🔁 Event-Driven Components

- **Message Queues (BullMQ)**:
  - Enables asynchronous processing of order books and email delivery.
  - Ensures scalability and decoupling of time-intensive operations.

- **Worker Services**:
  - **Price Calculation Worker**: Recalculates stock prices based on market depth and updates Redis cache.
  - **Mail Worker**: Handles delivery of signup confirmations, purchase receipts, and wallet operation alerts.

- **Redis Pub/Sub**:
  - Publishes live stock price updates.
  - Subscribed by WebSocket server for broadcasting to users in real-time.

### 💳 Stripe Webhook Integration
- Integrated with **Stripe** for handling dummy payments and wallet recharges.
- Uses **webhooks** to:
  - Validate completed transactions
  - Automatically credit user wallets
  - Maintain payment logs and transaction consistency

---

## 📁 Project Modules Overview

- `controllers/` – Handles route logic for users, orders, wallets, and Stripe webhooks.
- `workers/` – Background processing logic for pricing and emails.
- `queues/` – Job definitions and BullMQ handlers.
- `services/` – Business logic for transaction execution and wallet updates.
- `utils/` – Utility functions including Redis clients and Pub/Sub emitters.

---

## 🔗 Related Repositories

- **🖥 Frontend Repository:** [[CLick here](https://github.com/Moksh05/stocks-frontend)]
- **🔌 WebSocket Server:** [[click here](https://github.com/Moksh05/stocks-wss)]

---

## 📽️ Demo Video

Watch a full demo of the platform here: [[click here](https://drive.google.com/file/d/10fpMmQsDQGQ1KLfmnIkQbeSUF07oP_R1/view?usp=sharing)]

---
