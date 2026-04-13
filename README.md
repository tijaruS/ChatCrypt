# ChatCrypt

> End-to-end encrypted messaging — because your conversations are nobody else's business.

![JavaScript](https://img.shields.io/badge/JavaScript-99%25-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express)

---

## Overview

ChatCrypt is a full-stack encrypted messaging application with a clean separation between backend and frontend. Messages are encrypted on the client before being sent, ensuring the server never sees plaintext content. Built with a Node.js/Express REST API backend and a lightweight JavaScript frontend.

## Features

- **End-to-end encryption** — Messages encrypted client-side before transmission
- **User authentication** — Register, login, and session management via REST API
- **Real-time messaging** — WebSocket-based live message delivery
- **Separate architecture** — Decoupled backend and frontend for clean boundaries
- **Responsive frontend** — Works across desktop and mobile browsers

## Architecture

```
ChatCrypt/
├── backend/
│   ├── routes/         # Auth, messaging API routes
│   ├── middleware/      # Auth guards, error handling
│   ├── models/          # User and message schemas
│   └── server.js        # Express app + WebSocket setup
├── frontend/
│   ├── index.html       # Entry point
│   ├── app.js           # Client logic, encryption, WebSocket client
│   └── style.css        # UI styles
└── package.json
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js |
| Framework | Express.js |
| Real-time | WebSocket (ws) |
| Encryption | Web Crypto API (AES-GCM) |
| Frontend | Vanilla JavaScript |

## Getting Started

### Prerequisites

- Node.js 18+

### Installation

```bash
# Clone the repo
git clone https://github.com/tijaruS/ChatCrypt.git
cd ChatCrypt

# Install root dependencies
npm install

# Install backend dependencies
cd backend && npm install && cd ..

# Install frontend dependencies
cd frontend && npm install && cd ..
```

### Running the App

```bash
# Start the backend server
cd backend
npm start
# Server runs on http://localhost:5000

# Open frontend/index.html in your browser
# or serve it with:
cd frontend
npx serve .
```

### Environment Variables

Create a `.env` file in the `backend/` directory:

```env
PORT=5000
JWT_SECRET="your-jwt-secret"
```

## How Encryption Works

1. On registration, a key pair is derived from the user's credentials using the Web Crypto API
2. Before sending, each message is encrypted with AES-GCM using the recipient's public key
3. The backend stores and forwards only ciphertext — it never processes plaintext
4. The recipient's client decrypts on receipt using their private key

## Author

**Surajit Das** — [@tijaruS](https://github.com/tijaruS)
