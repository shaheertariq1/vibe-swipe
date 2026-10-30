# 🎵 VibeSwipe — Live Streaming & Creator Social Commerce Platform

[![Flutter](https://img.shields.io/badge/Flutter-3.0+-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
[![Agora](https://img.shields.io/badge/Agora_RTC-Live_Video-099DFD?style=for-the-badge&logo=agora&logoColor=white)](https://www.agora.io/)
[![Riverpod](https://img.shields.io/badge/State-Hooks_Riverpod-blueviolet?style=for-the-badge)](https://riverpod.dev)
[![Python](https://img.shields.io/badge/Backend-Flask_REST-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://flask.palletsprojects.com/)
[![Stripe](https://img.shields.io/badge/Payments-Stripe-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://stripe.com)
[![Apple IAP](https://img.shields.io/badge/Apple-In--App_Purchases-black?style=for-the-badge&logo=apple&logoColor=white)](https://developer.apple.com/in-app-purchase/)

VibeSwipe is an interactive social entertainment and creator commerce application engineered for musicians, performing artists, and fans. Featuring real-time live broadcasting, interactive video feeds, direct fan tipping, and dual-tier monetization.

---

## 🏗️ Architecture & Project Structure

```
vibe-swipe/
├── vibe_swipe/             # Cross-platform Flutter mobile client
│   ├── lib/
│   │   ├── src/
│   │   │   ├── components/ # Reusable UI components & widgets
│   │   │   ├── core/       # Networking, routing (GoRouter), DI (GetIt)
│   │   │   └── modules/
│   │   │       ├── artist/         # Artist dashboard, stream broadcast, analytics
│   │   │       ├── listner/        # Fan discovery feed, live streams, player
│   │   │       ├── authentication/ # OAuth (Google & Apple Sign-In), Auth guard
│   │   │       └── legal/          # Privacy policy, terms, compliance screens
│   └── pubspec.yaml
│
├── backend/                # Python Flask REST API & Streaming Services
│   ├── routes/             # Modular Blueprints (Agora, Stripe, Posts, Chat, etc.)
│   ├── app.py              # Application factory & CORS configuration
│   ├── config.py           # Environment settings & secrets
│   └── requirements.txt    # Gunicorn, Flask, Firebase-Admin, Agora SDK
│
└── DEPLOYMENT.md           # Production VPS deployment & systemd automation guide
```

---

## ✨ Key Features

### 📡 Real-Time Broadcasting (Agora RTC Engine)
- **Low-Latency Live Streams**: High-definition interactive video/audio broadcasting powered by the Agora RTC SDK.
- **Dynamic Token Minting**: Python backend dynamically generates secure, time-expiring Agora tokens via `agora-token-builder` on session creation.
- **Audience Interactivity**: Real-time comments, live reactions, and tipping during active broadcasts.

### 🎭 Dual Persona Architecture (Artist vs. Listener)
- **Artist Workspace**: Live performance scheduler, stream host controls, tip jar management, follower analytics, and promotional campaign configuration.
- **Listener Experience**: Swipeable vertical video reels (`video_player`, `chewie`), personalized artist discovery, and interactive community discussions.

### 💳 Dual Monetization & Store Compliance
- **Apple App Store Review Compliant**: Strictly structured compliance flow adhering to Apple Guideline 3.1.1, routing digital subscriptions and virtual goods through Apple In-App Purchases (StoreKit).
- **Stripe Payments**: Robust Stripe payment intent integration for physical goods, ticketing, and direct payment processing.

### ⚡ Enterprise State Management & Architecture
- **Hooks Riverpod & Flutter Hooks**: Reactive state isolation preventing unnecessary widget rebuilds across high-frequency stream events.
- **GoRouter Deep Linking**: Declarative navigation with nested routing and URL linking (`app_links`).
- **GetIt**: Centralized service locator and dependency injection.

---

## 🛠️ Tech Stack

| Domain | Technologies |
|---|---|
| **Mobile Client** | Flutter 3, Dart, Hooks Riverpod, Flutter Hooks, GoRouter, ScreenUtil, GetIt |
| **Streaming & Media** | Agora RTC Engine (`agora_rtc_engine`), Chewie, Video Player, Cached Network Image |
| **Payments** | Flutter Stripe (`flutter_stripe`), In-App Purchases (`in_app_purchase` / StoreKit) |
| **Backend Services** | Python 3.11+, Flask, Gunicorn (multi-worker), Flask-CORS, Firebase Admin SDK |
| **Cloud & Database** | Firebase Authentication, Cloud Firestore, Firebase Storage, Cloud Messaging (FCM) |
| **DevOps & Hosting** | Linux VPS (Ubuntu/Hostinger), `systemd` service daemon, UFW firewall, Gunicorn WSGI |

---

## 🚀 Getting Started

### 1. Prerequisites
- **Flutter SDK**: `>= 3.0.0 < 4.0.0`
- **Python**: `>= 3.11`
- **Agora Developer Account**: App ID and App Certificate
- **Firebase Project**: Service account credentials and `google-services.json` / `GoogleService-Info.plist`

---

### 2. Backend Setup (Flask API)
```bash
cd backend

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run locally
python app.py
```
Backend runs by default on `http://localhost:8000`.

---

### 3. Production Backend Deployment (Linux VPS)
Refer to [DEPLOYMENT.md](DEPLOYMENT.md) for full instructions:
- Runs multi-worker Gunicorn managed by `systemd`.
- Automatically restarts on system reboot or unexpected worker crashes.
- UFW firewall protection on port 8000.

---

### 4. Flutter Mobile App
```bash
cd vibe_swipe

# Fetch packages
flutter pub get

# Run on an iOS Simulator or Android Emulator
flutter run
```

---

## 📄 License
This repository is privately maintained for the VibeSwipe platform.
