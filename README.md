 # 📹 P2P Video Chat Application  

A real-time, **peer-to-peer (P2P) video chat application** built using **WebRTC, Socket.IO, and React**.  
This project enables **seamless** video and audio communication **without a central media server** using direct peer-to-peer connections.  

---

## 🏗️ **Architecture Overview**  

The application follows a **WebRTC-based architecture** with **Socket.IO** for signaling.  
It establishes direct **P2P connections** using **STUN/TURN servers** for NAT traversal.  

### 🔹 **Architecture Diagram**  

```plaintext
+----------------+       +----------------+
|  Peer A (UI)   |       |  Peer B (UI)   |
|  React + WebRTC|       |  React + WebRTC|
+-------+--------+       +-------+--------+
        |                      |
        |    Signaling (Offer/Answer)  
        |  via Socket.IO (WebSockets)   
        |                      |
+----------------+       +----------------+
|  Signaling Server (Node.js + Express)  |
|  Handles WebRTC Offer/Answer exchange  |
+----------------+       +----------------+
        |                      |
        |    ICE Candidate Exchange  
        |    via STUN/TURN Servers  
        |                      |
+-----------------------------------------+
|        WebRTC P2P Connection            |
|    Direct Media & Data Streaming        |
+-----------------------------------------+
```

# 🚀 Features

✅ Peer-to-Peer (P2P) Video Calling – Uses WebRTC for direct media streaming.
✅ Real-Time Signaling via Socket.IO – Exchanges WebRTC SDP (offer/answer) & ICE candidates.
✅ Low Latency Audio & Video – Uses navigator.mediaDevices.getUserMedia().
✅ STUN/TURN Support – Ensures connectivity behind firewalls.
✅ Minimal Backend Load – Backend only assists in signaling.

# 🛠️ Installation & Setup

# 📌 Project Structure




# 🖥️ How It Works?
1️⃣ User A initiates a call → getOffer() generates an SDP offer.
2️⃣ Offer is sent to User B via Socket.IO.
3️⃣ User B receives the offer → getAnswer() generates an SDP answer.
4️⃣ Answer is sent back to User A → WebRTC connection is established.
5️⃣ WebRTC streams video & audio directly between peers.


# 🛠️ Tech Stack

Frontend: React, WebRTC

Backend: Node.js, Express, Socket.IO

Styling: CSS, Tailwind

Testing: Jest, React Testing Library


# project strcut
```

video-chat-app/
│── server/                   # Backend (Node.js + Socket.IO)
│   ├── index.js              # Express & WebSocket server
│   ├── package.json          # Backend dependencies
│── client/                   # Frontend (React + WebRTC)
│   ├── src/
│   │   ├── context/
│   │   │   ├── SocketProvider.js  # Socket.IO context provider
│   │   ├── screens/
│   │   │   ├── Lobby.jsx        # Lobby screen
│   │   │   ├── Room.jsx         # Room screen
│   │   ├── service/
│   │   │   ├── peer.js          # WebRTC PeerService
│   │   ├── App.js               # Main React component
│   │   ├── app.css              # Global styles
│   │   ├── index.js             # Entry point
│   │   ├── index.css            # Global CSS
│   │   ├── app.test.js          # Frontend test file
│   │   ├── reportWebVitals.js   # Performance metrics
│   │   ├── setupTests.js        # Jest setup file
│   ├── package.json          # Frontend dependencies
│── README.md                 # Project Documentation
```
# 📜 Code Overview

SocketProvider.js - Handles real-time WebSocket communication.

peer.js - Manages WebRTC peer connections.

Lobby.jsx - Main lobby where users can create or join a room.

Room.jsx - Handles video chat using WebRTC.

reportWebVitals.js - Measures app performance.

setupTests.js - Configures Jest testing environment.

# 🏗️ Architecture

[Client (React)] <--> [WebRTC (P2P Connection)] <--> [Client (React)]
     │                                │
     └───> [Socket.IO Server (Node.js)] <───┘
