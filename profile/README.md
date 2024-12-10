# GCode-codepad

**GCode-codepad** is a collaborative online code editor with real-time video calling capabilities. Built on a distributed microservices architecture, it ensures scalability, low latency, and high availability. Users can create or join coding rooms, collaborate on code in real-time, and communicate seamlessly via video calls.

---

## UML Diagram
![UML Diagram](https://firebasestorage.googleapis.com/v0/b/gcode-45b7f.appspot.com/o/whiteboard_exported_image%20(1).png?alt=media&token=7a661201-0b67-4ae2-9bfa-02050d7c26c9)

---

## Table of Contents

- [Features](#features)
- [Architecture Overview](#architecture-overview)
- [Technologies Used](#technologies-used)
- [System Components](#system-components)
  - [Frontend](#frontend)
  - [Backend Services](#backend-services)
    - [User Service (Spring Boot)](#user-service-spring-boot)
    - [Code Service (Spring Boot)](#code-service-spring-boot)
    - [Video Signaling Service (Node.js)](#video-signaling-service-nodejs)
  - [Real-Time Database (Firebase)](#real-time-database-firebase)
  - [Nginx Reverse Proxy](#nginx-reverse-proxy)
- [Non-Functional Requirements](#non-functional-requirements)
- [Monitoring and Logging](#monitoring-and-logging)
- [License](#license)
- [Contact Information](#contact-information)

---

## Features

- **User Authentication:** Secure signup and login with Firebase Authentication.
- **Room Management:** Create and join collaborative coding rooms using unique room codes.
- **Real-Time Code Synchronization:** Collaborate on code edits powered by Firebase Realtime Database.
- **Video Calling:** Integrated video calling using WebRTC and a Node.js signaling server.
- **Scalability:** Designed to support up to 10,000 concurrent users with minimal latency.
- **Secure Communication:** All communications are encrypted using HTTPS.

---

## Architecture Overview

GCode-codepad follows a distributed microservices architecture. Services are orchestrated via Docker Compose and deployed on an Alibaba Cloud ECS instance, ensuring separation of concerns, scalability, and resilience.

---

## Technologies Used

### Frontend
- **Framework:** React
- **Realtime Updates:** Firebase SDK

### Backend
- **Languages & Frameworks:**
  - Java (Spring Boot)
  - Node.js

### Infrastructure
- Docker
- Docker Compose
- Nginx
- Let's Encrypt (Certbot)

### Database & Authentication
- Firebase Realtime Database
- Firebase Authentication

---

## System Components

### Frontend

- **Responsibilities:**
  - User interface for authentication, room management, collaborative code editing, and video calls.
  - Real-time updates via Firebase SDK.
  - REST API communication with backend services.
  - WebRTC integration for video calls.

---

### Backend Services

#### User Service (Spring Boot)
- **Responsibilities:**
  - Manage user profiles and authentication using Firebase Authentication.
  - Handle user-related API requests (e.g., profile updates).
  - Validate Firebase JWT tokens for secure API access.

#### Code Service (Spring Boot)
- **Responsibilities:**
  - Execute and return code results.
  - Set up isolated Docker environments to run submitted code securely.

#### Video Signaling Service (Node.js)
- **Responsibilities:**
  - Handle WebRTC signaling for peer-to-peer video connections.
  - Manage WebSocket connections for low-latency signaling.
  - Route video call requests efficiently using Global Redis.

---

### Real-Time Database (Firebase)
- **Responsibilities:**
  - Synchronize code changes in real-time between collaborators.
  - Provide scalable, low-latency storage for code edits.
  - Seamlessly integrate with the frontend via Firebase SDK.

---

### Nginx Reverse Proxy
- **Responsibilities:**
  - Route HTTP/HTTPS requests to the correct services.
  - Terminate SSL/TLS for secure communication.
  - Enable WebSocket upgrades for signaling server requests.

---

## Non-Functional Requirements

- **Low Latency:**
  - Real-time communication using Redis and WebRTC.
  - Nginx optimizes request handling.

- **Scalability:**
  - Independent scaling of microservices via Docker Compose.
  - Firebase handles high concurrency for code synchronization.
  - Future-proof architecture for Kubernetes migration.

- **Security:**
  - Encrypted communication over HTTPS.
  - Secure user authentication with Firebase.
  - SSL termination handled by Nginx.

- **Reliability:**
  - Docker containers configured with `restart: always` for high uptime.
  - Isolated microservices to prevent cascading failures.

---

## Monitoring and Logging

- **Logging:**
  - Access Docker logs using `docker logs [container_name]`.
  - Optional integration with ELK Stack for centralized log management.

- **Monitoring:**
  - Use tools like Prometheus and Grafana to track system performance.
  - Monitor key metrics such as CPU usage, memory consumption, and network latency.

---

## License

This project is licensed under the [MIT License](LICENSE.md). You are free to use, modify, and distribute the code.

---

## Contact Information

For questions or suggestions, reach out to [yuqi.guo17@gmail.com](mailto:yuqi.guo17@gmail.com) or open an issue on the GitHub repository.
