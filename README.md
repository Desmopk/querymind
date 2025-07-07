🎯 QueryMind — AI-Powered RAG Chat App

QueryMind is a cross-platform AI chatbot built with **Flutter** and powered by a **FastAPI backend** that uses Google's **Gemini API**. It leverages **Retrieval-Augmented Generation (RAG)** to search, retrieve, and respond with accurate, context-rich answers from the web or document corpus.

🧰 Tech Stack

🔙 Backend  
- FastAPI (Python)
- Gemini API (LLM)
- WebSocket API for streaming responses
- Cosine Similarity & Vector Search (custom logic)
- Async I/O with `httpx`, `websockets`, etc.

📱 Frontend  
- Flutter (Cross-platform: Android, iOS, Web, Desktop)
- Riverpod (State Management)
- Flutter Markdown for rich text rendering
- WebSocket client for live streaming responses
- Skeletonizer for UI loading states

🔥 Key Features

🧠 Retrieval-Augmented Generation (RAG)  
🔍 Real-time search over online sources  
🧮 Cosine similarity-based document retrieval  
💬 Gemini LLM API integration with prompt engineering  
📡 WebSocket-based live streaming responses  
📝 Markdown support for AI replies  
📱 Optimized and responsive UI (desktop & mobile)  
🎭 Loading skeletons for smoother UX

🚀 Getting Started

📦 Prerequisites
- Python 3.9+
- Flutter SDK
- Dart SDK ≥ 3.7.0
- Gemini API Key (from Google AI Studio)

🐍 Backend Setup

```bash
# Clone the repo
git clone https://github.com/Desmopk/querymind.git
cd querymind/backend

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up your Gemini API Key in `.env`
cp .env.example .env

# Run the FastAPI server
uvicorn main:app --reload
```
📱 Frontend Setup

```bash
cd ../flutter_client

# Install Flutter packages
flutter pub get

# Run on emulator or real device
flutter run
```
🧠 RAG Architecture Overview

User Prompt →
- FastAPI receives input
- Search external content sources
- Compute cosine similarity to rank sources
- Send top documents and prompt to Gemini LLM
- Stream response via WebSocket
- Flutter displays live chat with Markdown rendering

🛡️ Token & API Security

- Gemini API key stored in .env (never hardcoded)
- API routes are scoped and minimal
- No user auth required for demo, but JWT can be added

📦 Deployment

- Backend: Deployable via Docker, Uvicorn/Gunicorn
- Frontend: Flutter web or native builds
- Future enhancements: Vector DB integration, Authentication, Chat history
  
📂 Repository Structure
```bash
querymind/
├── backend/                     # FastAPI backend
│   ├── main.py                  # FastAPI app entrypoint
│   ├── requirements.txt        # Python dependencies
│   ├── .env.example             # Template for env variables (e.g. Gemini API key)
│   ├── services/                # Modules for Gemini integration, retrieval logic
│   │   ├── rag.py               # Core RAG logic (search + similarity + LLM)
│   │   ├── gemini_api.py        # Wrapper around Gemini API calls
│   │   └── docs_search.py       # Web/document search and retrieval
│   └── websocket.py            # WebSocket endpoint implementation for streaming
└── flutter_client/              # Flutter frontend app
    ├── lib/
    │   ├── main.dart           # Entrypoint for Flutter app
    │   ├── pages/              # UI screens (e.g. Home, Chat)
    │   │   ├── home_page.dart
    │   │   └── chat_page.dart
    │   ├── models/             # Data models (e.g. message, stream models)
    │   ├── services/           # API clients (REST and WebSocket)
    │   │   ├── api_service.dart
    │   │   └── ws_service.dart
    │   ├── widgets/            # Shared UI components (Markdown viewer, skeleton loader)
    │   └── utils/              # Helpers (Markdown formatter, constants)
    ├── assets/                 # Images, fonts
    └── pubspec.yaml            # Dart & Flutter dependencies

```

