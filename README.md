# DevMatch 🚀

> **Developer Networking & Matchmaking Platform**  
> A Tinder-style matchmaking platform built specifically for developers to connect, explore peer profiles, send collaboration requests, and expand their tech network.

[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express-5.x-lightgrey.svg)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green.svg)](https://www.mongodb.com/)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)

---

## 🌐 Live Links

- **Live Demo (Frontend):** [https://dev-tinder-front-end-6vd2.vercel.app/](https://dev-tinder-front-end-6vd2.vercel.app/)
- **Backend API (Render):** [https://devtinder-backend.onrender.com](https://devtinder-backend.onrender.com)
- **Frontend Repository:** [github.com/divy6976/DevTinder-FrontEnd](https://github.com/divy6976/DevTinder-FrontEnd)

---

## 📌 Project Overview

**DevMatch** solves the challenge of formal and awkward networking in the developer ecosystem. By combining the simplicity of swipe-based matching with developer-centric profile data, DevMatch allows developers to:

- Showcase technical skills, bios, and project interests.
- Discover other developers without seeing duplicate profiles or existing connections.
- Send connection requests (`interested` / `ignored`).
- Review and accept incoming requests to unlock direct connections for projects, hackathons, or mentorship.

---

## ✨ Features

- **🔍 Smart Developer Feed:** Paginated discovery algorithm that filters out the logged-in user, existing connections, and already reviewed requests.
- **🤝 Connection Request Flow:** Seamless request dispatching (`interested` / `ignored`) and review management (`accepted` / `rejected`).
- **🔐 Secure Authentication:** Stateless JWT session management backed by HTTP-Only cookies with SameSite/Secure attributes and bcrypt password hashing.
- **👤 Profile Management:** Full profile customization including skills, bio, age, gender, and avatar URL with input sanitization and schema-level validation.
- **🛡️ Field-Level Privacy:** Whitelisted projection (`USER_SAFE_FIELDS`) to prevent sensitive user fields (passwords, emails) from being exposed in public feeds.
- **🌐 Cross-Origin Support:** Robust CORS configuration supporting cross-site credentials for smooth frontend-backend communication.

---

## 🛠️ Tech Stack

- **Runtime:** [Node.js](https://nodejs.org/) (v18+)
- **Framework:** [Express.js](https://expressjs.com/) (v5.1.0)
- **Database & ODM:** [MongoDB Atlas](https://www.mongodb.com/atlas) with [Mongoose](https://mongoosejs.com/) (v8.18.0)
- **Authentication & Security:** JSON Web Tokens (`jsonwebtoken`), `bcrypt`, `cookie-parser`, `validator`
- **Deployment:** [Render](https://render.com/) (Backend Web Service), [Vercel](https://vercel.com/) (Frontend Client)

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher)
- [MongoDB Atlas](https://www.mongodb.com/atlas) account or a local MongoDB database

### 1. Clone the Repository

```bash
git clone https://github.com/divy6976/DevMatch-Backend.git
cd DevMatch-Backend
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory:

```env
PORT=7777
MONGODB_URI=your_mongodb_connection_string
CLIENT_URL=http://localhost:5173
```

### 4. Start the Application

```bash
# Development mode (with auto-restart via nodemon)
npm run dev

# Production mode
npm start
```

The API will be available at `http://localhost:7777`.

---

## 📡 API Endpoints Overview

### 🔐 Authentication (`/`)
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/signup` | Register a new developer account |
| `POST` | `/login` | Authenticate credentials and receive secure JWT cookie |
| `POST` | `/logout` | Clear authentication cookie and end session |

### 👤 Profile (`/profile`)
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/profile/view` | Fetch current user's profile details |
| `PATCH` | `/profile/edit` | Update allowed profile fields (about, skills, age, etc.) |
| `POST` | `/profile/password` | Change password with current password verification |

### 🤝 Connection Requests (`/request`)
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/request/send/:status/:toUserId` | Send request (`interested` or `ignored`) |
| `POST` | `/request/review/:status/:requestId` | Review received request (`accepted` or `rejected`) |

### 👥 Connections & Feed (`/user`)
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/user/feed` | Paginated feed of new developer profiles |
| `GET` | `/user/requests/received` | List all incoming pending requests |
| `GET` | `/user/connections` | List all accepted developer connections |

---

## 👨‍💻 Author

**Divy**
- GitHub: [@divy6976](https://github.com/divy6976)

---

## 📄 License

This project is licensed under the [ISC License](LICENSE).
