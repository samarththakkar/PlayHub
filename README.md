<div align="center">
  <!-- <img src="https://via.placeholder.com/150x150.png?text=PlayZen" alt="PlayZen Logo" width="150" height="150" /> -->
  <h1>PlayZen 🎬</h1>
  <p><em>A production-grade, full-stack YouTube clone built with React, Node.js, Express, and MongoDB</em></p>
  
  <!-- Badges -->
  <p>
    <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
    <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js" />
    <img src="https://img.shields.io/badge/Express.js-404D59?style=for-the-badge" alt="Express.js" />
    <img src="https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB" />
    <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
  </p>
</div>

---

## 📖 Table of Contents

- [About the Project](#-about-the-project)
- [Key Features](#-key-features)
- [Visuals & Screenshots](#-visuals--screenshots)
- [Tech Stack](#-tech-stack)
- [Project Architecture](#-project-architecture)
- [API Endpoints](#-api-endpoints)
- [Getting Started (Setup)](#-getting-started)
- [Database Models](#-database-models)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🚀 About the Project

**PlayZen** is a highly scalable and feature-rich video-sharing platform inspired by YouTube. It offers a complete ecosystem including real video uploads, secure OAuth login, a robust recommendation engine, Shorts (vertical videos), community tweets, dynamic playlists, and real-time-like notifications. 

Built with modern web development standards in mind, this project demonstrates best practices in RESTful API design, database modeling, and responsive frontend architecture.

---

## ✨ Key Features

### 🔐 Authentication & User Management
- **Email/Password** registration with OTP verification (via Brevo).
- **Google & Facebook OAuth 2.0** login (Passport.js).
- **JWT-based Security** with access & refresh tokens stored securely in HTTP-only cookies.
- Password recovery via OTP.
- Profile customization: Avatar & cover image upload with crop support (Cloudinary).
- Comprehensive user channel profiles with real-time subscriber counts.

### 🎥 Video & Shorts Ecosystem
- Upload standard videos and **Shorts** with dynamic thumbnail generation (Multer + Cloudinary).
- Detailed video pages with accurate view tracking.
- Content Management: Publish, unpublish, and delete functionalities.
- Creator **Studio Dashboard** for managing uploads.

### 🤝 Social & Community Features
- Polymorphic **Like / Unlike** system for videos, comments, and tweets.
- **Subscribe / Unsubscribe** mechanics for channels.
- Nested **Comments** on videos.
- **Tweets (Community Posts)** to engage with subscribers.
- In-app **Notifications** for interactions.

### 🔍 Discovery & Recommendations
- Full-text intelligent **Search** across videos.
- **Recommendation Engine** based on user interests.
- Dedicated **Subscriptions Feed**.
- Browse by specific **Categories**.

### 📚 Personalized Library
- **Watch History**: Auto-tracked viewing history.
- **Watch Later**: Save videos to your personal queue.
- **Watch Progress**: Seamlessly resume videos where you left off.
- **Liked Videos**: Dedicated collection of all your liked content.
- **Playlists**: Create, manage, and curate collections.

---

## 📸 Visuals & Screenshots

*(Replace the placeholder images below with actual screenshots of your application to make the README more engaging!)*

<div align="center">
  <img src="https://via.placeholder.com/800x400.png?text=Home+Page+Dashboard" alt="Home Page Screenshot" width="800" />
  <br/>
  <em>Home Page & Recommendations Feed</em>
</div>

<br/>

<div align="center">
  <img src="https://via.placeholder.com/400x300.png?text=Video+Player" alt="Video Player" width="400" />
  <img src="https://via.placeholder.com/400x300.png?text=Creator+Studio" alt="Creator Studio" width="400" />
  <br/>
  <em>Video Player (Left) and Creator Studio Dashboard (Right)</em>
</div>

---

## 🛠️ Tech Stack

| Layer | Technology | Description |
|-------|------------|-------------|
| **Frontend** | React 19, Vite, Tailwind CSS v4 | Ultra-fast UI and styling |
| **Routing** | React Router v7 | Seamless client-side navigation |
| **State/API** | Custom Hooks, Axios | `useFetch`, `useAuth`, `useLike`, etc. |
| **Icons & UI** | Lucide React, react-hot-toast | Scalable icons and notifications |
| **Image Handling**| react-easy-crop, react-image-crop | Client-side image adjustments |
| **Backend** | Node.js, Express 5 | Robust and highly scalable server |
| **Database** | MongoDB, Mongoose | NoSQL flexible data storage |
| **Pagination** | mongoose-aggregate-paginate-v2 | Efficient database aggregations |
| **Authentication**| JWT, bcrypt, Passport.js | Secure user sessions and OAuth |
| **File Storage** | Multer, Cloudinary | Efficient media handling and cloud storage |
| **Email/OTP** | Brevo (via nodemailer/axios) | Transactional emails and verification |

---

## 📁 Project Architecture

```text
PlayZen/
├── backend/
│   ├── src/
│   │   ├── config/          # Passport OAuth & general configurations
│   │   ├── controllers/     # Core business logic (Video, User, Like, etc.)
│   │   ├── models/          # 13+ Mongoose schemas (User, Video, Playlist, etc.)
│   │   ├── routes/          # Express route definitions
│   │   ├── middlewares/     # JWT verification, Multer upload handling
│   │   ├── utils/           # Custom Error handlers, API Responders, Cloudinary logic
│   │   ├── db/              # Database connection logic
│   │   ├── app.js           # Express app setup and middleware registration
│   │   └── index.js         # Server entry point
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── pages/           # Core Pages (Home, Watch, Profile, Search, etc.)
│   │   ├── components/      # Reusable UI (VideoCard, Header, Sidebar, Modal)
│   │   ├── hooks/           # Custom logic encapsulation
│   │   ├── services/        # Centralized API service layer
│   │   ├── context/         # Global state (AuthContext)
│   │   ├── utils/           # Helper functions (formatDate, avatarUtils)
│   │   ├── layouts/         # Structural wrappers (MainLayout, AuthLayout)
│   │   └── main.jsx         # React application entry
│   └── package.json
│
└── package.json             # Root package for concurrent execution
```

---

## ⚙️ API Endpoints

A quick glance at the primary RESTful resources exposed by the backend:

| Resource | Base Path | Description |
|---|---|---|
| **Users** | `/api/v1/users` | Registration, login, profile, avatars |
| **Videos** | `/api/v1/videos` | Upload, update, delete, fetch videos |
| **Playlists** | `/api/v1/playlists` | Create and manage custom playlists |
| **Tweets** | `/api/v1/tweets` | Community text posts |
| **Likes** | `/api/v1/likes` | Toggle likes for videos, comments, tweets |
| **Comments** | `/api/v1/comments` | Add, update, delete comments |
| **Subscriptions**| `/api/v1/subscriptions` | Channel subscribe/unsubscribe logic |
| **Notifications**| `/api/v1/notifications` | Fetch user activity notifications |
| **Watch Progress**| `/api/v1/watch-progress` | Sync video playback time |
| **Search** | `/api/v1/search` | Full-text query endpoint |
| **Watch History**| `/api/v1/watch-history` | User viewing records |
| **Watch Later** | `/api/v1/watch-later` | Queue management |

---

## 💻 Getting Started

Follow these steps to set up the project locally on your machine.

### Prerequisites
Make sure you have the following installed and configured:
- **Node.js** (v18 or higher)
- **MongoDB** (Local instance or MongoDB Atlas URI)
- **Cloudinary Account** (For media storage)
- **Google Cloud Console Project** (For Google OAuth 2.0)
- **Brevo Account** (For sending OTP emails)

### 1. Clone the Repository

```bash
git clone https://github.com/samarththakkar/PlayZen.git
cd PlayZen
```

### 2. Install Dependencies

You can install dependencies for both the frontend and backend simultaneously if you wish, or navigate to each directory:

```bash
# Install root dependencies (concurrently)
npm install

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install
```

### 3. Environment Variables Configuration

#### Backend `.env`
Create a `.env` file inside the `backend/` directory:

```env
PORT=8000
MONGODB_URI=your_mongodb_connection_string
CORS_ORIGIN=http://localhost:5173
CLIENT_URL=http://localhost:5173

# JWT Secrets
ACCESS_TOKEN_SECRET=your_access_token_secret_string
ACCESS_TOKEN_EXPIRY=1d
REFRESH_TOKEN_SECRET=your_refresh_token_secret_string
REFRESH_TOKEN_EXPIRY=10d

# Cloudinary Setup
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# OAuth Setup
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# Email / OTP
BREVO_API_KEY=your_brevo_api_key
```

#### Frontend `.env`
Create a `.env` file inside the `frontend/` directory:

```env
VITE_API_BASE_URL=http://localhost:8000
```

### 4. Run the Application

You can run the entire stack from the root directory using concurrently (defined in the root `package.json`):

```bash
# Make sure you are in the root directory (/PlayZen)
npm run dev
```

Alternatively, run them separately:
- **Backend:** `cd backend && npm run dev`
- **Frontend:** `cd frontend && npm run dev`

🎉 The frontend should now be running at **`http://localhost:5173`** and the backend API at **`http://localhost:8000`**.

---

## 🗄️ Database Models Overview

The application is powered by a robust schema design using **13+ Mongoose models**:

- `User` — Authentication, profile details, total watch history, OAuth IDs.
- `Video` — Video metadata, file URLs, view counts, duration, and owner refs.
- `Subscription` — Maps subscribers to channels with notification preferences.
- `Likes` — Polymorphic design handling likes for videos, comments, and tweets.
- `Comments` — Nested comments with parent/child relationships on videos.
- `Playlists` — Custom collections containing references to multiple videos.
- `Tweets` — Short-form community posts.
- `Shorts` — Vertical short-form content.
- `WatchHistory` — Immutable logs of every video watched by a user.
- `WatchProgress` — Tracks exact timestamp where a user paused a video.
- `WatchLater` — Simple queue system for delayed viewing.
- `Notifications` — System alerts for likes, subscriptions, and mentions.
- `Category` / `Interest` — Taxonomies for video categorization and user preferences.
- `Settings` — User-specific UI and application preferences.

---

## 🤝 Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 License

Distributed under the MIT License. Copyright © 2026 [Samarth Thakkar](https://github.com/samarththakkar).

---
<div align="center">
  <sub>Built with ❤️ by Samarth Thakkar</sub>
</div>
