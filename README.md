# Knock-Knock: Real-Time Communication App

Knock-Knock is a **real-time communication platform** built as a **monorepo**, featuring:

- **Android Application** (Kotlin) for real-time audio (Push-to-Talk) and future video/chat features.
- **Backend Services** (Node.js + Spring Boot) for signaling, authentication, and scalability.

---

## ✅ Core Features

- **Push-to-Talk (PTT):** Both users can talk simultaneously (no lock).
- **Push-Lock Mode:** Works like hands-free calls.
- **Background Mode:** Runs in the background with persistent connection.
- **Instant Audio Relay:** Audio plays automatically on the receiver’s device without answering.

---

## ✅ Future Roadmap

- [ ] Video Calling (1-to-1)
- [ ] Screen Sharing
- [ ] Chat (1-to-1)
- [ ] Group Voice Calls
- [ ] Group Video Calls
- [ ] Group Chat

---

## ✅ Tech Stack

### **Android App**

- **Language:** Kotlin
- **UI:** Jetpack Compose
- **Architecture:** MVVM
- **Real-Time Communication:** WebRTC (audio/video)
- **Networking:** Socket.IO client, Retrofit (future REST calls)
- **Background Services:** Foreground Service with WakeLock

### **Backend**

- **Signaling Service:** Node.js + Socket.IO for WebRTC signaling
- **API Service:** Spring Boot for REST APIs & authentication
- **Database:** PostgreSQL (user data, chat history)
- **Cache & Pub/Sub:** Redis (presence, scaling signaling)
- **TURN/STUN:** Coturn (NAT traversal)
- **Media Service (future):** Mediasoup for group calls
- **Authentication:** OAuth 2.0 (Google) + JWT

---

## ✅ Monorepo Structure

```
knock-knock/
├── apps/
│   ├── android-app/            # Kotlin Android app
│   │   ├── app/
│   │   │   ├── src/main/java/com/knockknock/
│   │   │   │   ├── ui/         # Jetpack Compose screens
│   │   │   │   ├── service/    # Foreground service for PTT
│   │   │   │   ├── webrtc/     # WebRTC handling
│   │   │   │   ├── socket/     # Socket.IO signaling client
│   │   │   │   └── MainActivity.kt
│   │   │   ├── AndroidManifest.xml
│   │   │   └── build.gradle.kts
│   │   └── build.gradle.kts
│   ├── backend/
│   │   ├── signaling-service/  # Node.js signaling server
│   │   ├── api-service/        # Spring Boot APIs
│   │   ├── media-service/      # Future: Mediasoup
│   │   ├── chat-service/       # Future: Chat service
│   │   ├── common/
│   │   ├── docker-compose.yml
│   │   └── README.md
├── libs/
│   ├── shared-models/          # Shared DTOs between backend and Android
│   └── utils/                  # Common utilities
├── infra/
│   ├── kubernetes/             # Deployment configs
│   ├── docker/                 # Dockerfiles
│   └── ...
└── README.md
```

---

## ✅ Setup Instructions

### **1. Clone the Repository**

```bash
git clone https://github.com/somnesh/knock-knock.git
cd knock-knock
```

### **2. Backend Setup**

#### Prerequisites:

- Node.js (v18+)
- Java 21 (Spring Boot)
- PostgreSQL & Redis
- Docker & Docker Compose

Run backend services:

```bash
cd apps/backend
docker-compose up --build
```

### **3. Android App Setup**

- Open `apps/android-app` in **Android Studio**.
- Build and run on an emulator or real device.

---

## ✅ How Push-to-Talk Works (Phase 1)

- **Signaling:** Socket.IO maintains a persistent connection with the backend.
- **Connection:** When a user presses the talk button, the backend initiates a WebRTC connection to the friend.
- **Audio Streaming:** Audio data is transmitted via WebRTC channels instantly.
- **Push-Lock:** Keeps the session open for continuous communication.

---

## ✅ Future Enhancements

- AI-driven transcription and meeting summaries
- Advanced media encryption
- Full Kubernetes deployment for global scale

---

## ✅ License

MIT License
