# AI-Powered-Enterprise-Meeting-Collaboration_Platform_Zidio_Development
An AI-powered enterprise meeting and collaboration platform built to streamline virtual communication with features like video conferencing, real-time chat, screen sharing, speech-to-text transcription, AI-generated meeting summaries, team workspaces, and secure user management for enhanced productivity.

## ✨ Features & Capabilities

### 🎙️ High-Fidelity WebRTC Mesh Audio & Video

- **Decentralized Multi-User Mesh Architecture:** Powering instant peer-to-peer audio and video transmission with ultra-low latency via `simple-peer`.
- **Privacy-by-Default Controls:** Microphone and camera tracks automatically join muted/camera-off by default, protecting user privacy in every session.
- **Smart Screen Sharing:** Instant, high-resolution screen-sharing with dynamic, smooth track replacement (`replaceTrack`) that works perfectly in both camera-enabled and camera-disabled environments.
- **Device-Safe Fallbacks:** Multi-tier `getUserMedia` fallbacks and mobile-ready display media controls to support tablets, smartphones, and low-end devices flawlessly.
- **Real-time Media Badges:** Beautiful floating state overlays (`🔇 MUTED`, `Camera Disabled`) on active grid cards to ensure instant room awareness.

### 🤖 Intelligent AI Assistance

- **Live Transcription:** Real-time meeting audio speech capture and text translation.
- **AI Summary Engine:** High-performance NLP generation producing instant executive summaries, decision trackers, and tags.
- **Auto-Task Extraction:** Automated tracking of action items and assignments directly from meeting transcripts.

### 🤝 Multi-User Collaboration Board

- **Dynamic Chat:** Glassmorphic instant-message sidebar featuring typing indicators and dynamic chat overlays.
- **Collaborative Real-time Notes:** Shared rich-text note pad synchronized across all room attendees using fast Socket relays.
- **Actionable Task Board:** Add, assign, and track completion progress of actionable tasks during the call.
- **Secure File-Sharing:** Seamless document, asset, and image sharing directly within the dashboard.

### 📊 Historical Analytics & Recovery

- **Session Archive:** Interactive meeting history table listing participant rosters, duration, and completion details.
- **Locked Recording Playbacks:** Smart UI recording states that conditionally display video players if a meeting session was recorded, or disable them with professional placeholders if not.
- **Secure Key Recovery:** Complete password reset mechanism utilizing secure, customizable database-backed security questions (e.g. *What is your mother's name?*) and trimmed verification layers.

| Component            | Technology                 | Description                                                                                            |
| -------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Frontend Core**    | React 18 + Vite            | Rapid bundling, fast-refresh HMR, component isolation, and optimized builds.                           |
| **Styling & UX**     | Glassmorphism & Custom CSS | Custom CSS variables, linear gradients, dynamic keyframe glow animations, and responsive layout grids. |
| **Backend API**      | Node.js + Express.js       | High-performance, scalable asynchronous event-driven RESTful architecture.                             |
| **Real-time Engine** | Socket.io v4               | Dual-channel WebSockets signaling, roster updates, chat, tasks, and notes sync.                        |
| **WebRTC Mesh**      | Simple-Peer                | Lightweight wrapper for WebRTC peer connection, offer/answer exchange, and ICE handshakes.             |
| **Database**         | MongoDB + Mongoose         | Document-based schema design with pre-save encryption, validator hooks, and relational models.         |
| **Asset Storage**    | Cloudinary API             | Secure cloud storage for meeting recordings, profile pictures, and uploaded files.                     |


# ⚡ Setup & Installation

## Prerequisites

Before running IntelliMeet, ensure the following dependencies are installed:

| Requirement | Version |
|------------|------------|
| **Node.js** | v18.0.0 or higher |
| **MongoDB** | Local MongoDB Community Server or MongoDB Atlas Cluster URI |
| **NPM** | v9.0.0 or higher |

---

## Step 1: Environment Configuration

Inside the `/server` directory, duplicate the `.env.example` file and rename it to `.env`.

Populate the file with the following configuration values:

```env
# Server Details
PORT=5000
NODE_ENV=development

# Database URI
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/intellmeet

# Security Token Secret
JWT_SECRET=super_secure_jwt_secret_token_123!

# Client Application URL (CORS)
CLIENT_URL=http://localhost:5173

# Optional: Cloudinary Storage Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Optional: Hugging Face API Key
HUGGINGFACE_API_KEY=your_hugging_face_token
```

> **Note:** Never commit your `.env` file to version control. Keep all secrets and API keys private.

---

## Step 2: Running the Backend Server

Navigate to the `server` directory, install dependencies, and start the development server:

```bash
cd server
npm install
npm run dev
```

### Expected Result

The backend API and Socket.io server will start on:

```text
http://localhost:5000
```

### Backend Features Enabled

- RESTful API endpoints
- JWT Authentication
- MongoDB Database Connection
- Socket.io Real-time Communication
- Meeting Room Management
- Chat, Notes, and Task Synchronization
- WebRTC Signaling Events

---

## Step 3: Running the Frontend Client

Open a new terminal, navigate to the `client` directory, install dependencies, and launch the Vite development server:

```bash
cd client
npm install
npm run dev
```

### Expected Result

The React frontend application will be available at:

```text
http://localhost:5173
```

### Frontend Features Enabled

- React 18 + Vite
- Hot Module Replacement (HMR)
- Authentication Pages
- Meeting Dashboard
- Real-time Collaboration Workspace
- WebRTC Video Conferencing
- Responsive Glassmorphism UI

---

## 🚀 Full Startup Workflow

```bash
# Terminal 1 - Backend
cd server
npm install
npm run dev

# Terminal 2 - Frontend
cd client
npm install
npm run dev
```

### Application URLs

| Service | URL |
|----------|-----|
| Frontend Client | `http://localhost:5173` |
| Backend API | `http://localhost:5000` |
| Socket.io Server | `ws://localhost:5000` |

---

## ✅ Verification Checklist

After starting both services:

- MongoDB connects successfully
- Backend runs on port `5000`
- Frontend runs on port `5173`
- User registration/login works
- Meeting room creation works
- WebSocket connection is established
- WebRTC peer connections initialize correctly
- Chat, tasks, and notes synchronize in real time

---

## 🎉 Ready to Go

If all checks pass, IntelliMeet is fully configured and ready for development, testing, and deployment.

# 🚢 Production Deployment

IntelliMeet supports multiple deployment strategies depending on your infrastructure requirements. You can either deploy everything as a single Node.js service or use a modern multi-service cloud deployment architecture.

---

# Option A: Serve Frontend Static Bundle from Express Server

This approach is ideal for:

- Render Web Services
- Heroku
- Railway
- VPS Deployments
- Docker Containers

Both the frontend and backend are served from a single Node.js application.

## Step 1: Build the Frontend

Navigate to the client directory and generate a production build:

```bash
cd client
npm run build
```

### Build Output

```plaintext
client/
└── dist/
    ├── assets/
    ├── index.html
    └── ...
```

The generated `dist` directory contains optimized production assets including:

- Minified JavaScript bundles
- Optimized CSS
- Static assets
- Vite production manifest

---

## Step 2: Start the Backend

Navigate to the server directory and launch the production server:

```bash
cd ../server
npm start
```

### Expected Behavior

The Express server will:

1. Serve REST API endpoints.
2. Handle Socket.io real-time communication.
3. Serve the React production bundle.
4. Route SPA requests back to `index.html`.

### Production URL

```text
http://your-domain.com
```

Everything will be accessible through a single web service.

---

# Option B: Infrastructure-as-Code Deployment on Render

IntelliMeet includes a preconfigured `render.yaml` file for automated cloud deployment.

This approach provisions:

- Separate Backend API Service
- Separate Frontend Static Site
- Automatic CI/CD Deployments
- GitHub Integration

---

## Step 1: Push Project to GitHub

Initialize and push your project:

```bash
git init
git add .
git commit -m "Initial IntelliMeet deployment"
git branch -M main
git remote add origin https://github.com/your-username/intellmeet.git
git push -u origin main
```

---

## Step 2: Create a Render Blueprint

1. Log in to Render.
2. Open the Dashboard.
3. Click **Blueprints**.
4. Select **New Blueprint Instance**.
5. Connect your GitHub repository.
6. Choose the IntelliMeet repository.

Render automatically detects:

```yaml
render.yaml
```

and provisions all required services.

---

## Step 3: Automatic Service Creation

Render will automatically configure:

### Backend Web Service

- Node.js Runtime
- Express API
- Socket.io Server
- Auto Deploy on Git Push

### Frontend Static Site

- React + Vite Production Build
- Global CDN Distribution
- Automatic Cache Optimization

### Networking

- Frontend connected to Backend API
- HTTPS Enabled
- Environment Isolation

---

## Step 4: Configure Environment Variables

Inside the Render Dashboard, add the following variables:

```env
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/intellmeet

JWT_SECRET=super_secure_jwt_secret_token_123!

CLIENT_URL=https://your-frontend-domain.onrender.com

NODE_ENV=production
```

### Optional Variables

```env
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

HUGGINGFACE_API_KEY=your_hugging_face_token
```

---

## Deployment Architecture

```plaintext
                    ┌───────────────────────┐
                    │     Render CDN        │
                    │  React Frontend Site  │
                    └───────────┬───────────┘
                                │ HTTPS
                                ▼
                    ┌───────────────────────┐
                    │   Express Backend     │
                    │    Socket.io API      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │      MongoDB Atlas    │
                    │   Persistent Storage  │
                    └───────────────────────┘
```

---

## CI/CD Workflow

Every push to the configured branch automatically triggers:

```plaintext
Developer Push
       │
       ▼
GitHub Repository
       │
       ▼
Render Build Pipeline
       │
       ├── Build Frontend
       ├── Install Backend Dependencies
       ├── Run Deployment Checks
       └── Deploy Services
       │
       ▼
Production Environment
```

---

## ✅ Production Readiness Checklist

Before deploying:

- Environment variables configured
- MongoDB Atlas cluster accessible
- JWT secret generated securely
- CORS client URL updated
- Frontend production build verified
- Socket.io production transport tested
- HTTPS enabled
- Cloudinary credentials configured (if used)
- AI integrations configured (if used)

---

# 🎉 Deployment Complete

Once deployment finishes successfully:

- Frontend is publicly accessible.
- Backend APIs are available via HTTPS.
- Socket.io real-time communication is active.
- MongoDB persistence is connected.
- IntelliMeet is fully production-ready.

## 📜 License
This project is licensed under the MIT License.
