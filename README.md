#XitingGrammar Chat Room
A secure, real-time encrypted chat room application with private and group messaging, file sharing, and end-to-end encryption support.

Features
🔐 Account System – Register and log in with password hashing (bcrypt)

👥 Friends & Private Chats – Add friends and start encrypted private conversations

🗣️ Group Rooms – Create password-protected rooms or join public groups

📎 File Sharing – Upload images, documents, and files; preview images inline

⏱️ Ephemeral Mode – Messages automatically disappear after a set TTL (30s–1h)

🌙 Light/Dark Theme – Toggle between light and dark interface

💾 Local History – Messages are stored in localStorage for persistence (optional ephemeral toggle)

🔒 End-to-End Encryption – Client-side AES encryption of message content (requires shared secret)

🔌 WebSocket Real-Time – Instant message delivery and online status updates

Tech Stack
Backend: Python 3.8+, FastAPI, WebSockets, Uvicorn

Frontend: HTML5, CSS3, Vanilla JavaScript

Storage: JSON files (users, messages, rooms, friendships)

Security: bcrypt for password hashing, AES for message encryption (client-side)

HTTPS: Optional SSL/TLS with provided certificates

Quick Start
Prerequisites
Python 3.8 or higher

pip (Python package manager)

Installation
Clone the repository:

bash
git clone https://github.com/yourusername/xitinggrammar.git
cd xitinggrammar
Install dependencies:

bash
pip install -r requirements.txt
Run the application:

bash
python backend/main.py
The server will start at http://localhost:8000. If cert.pem and key.pem are present, it will use HTTPS.

Open your browser and navigate to http://localhost:8000 (or https://localhost:8000).

Configuration
Data Directory: All JSON data is stored in data/ – you can back up or clear it as needed.

Uploads: Uploaded files are saved in uploads/ directory.

SSL: To enable HTTPS, place cert.pem and key.pem in the project root. The server automatically switches to WSS.

Usage
Login / Register – Enter a username and password. If it's a new user, an account is created automatically.

Join Public Room – The "public" room is available to everyone.

Create/Join Rooms – Use the sidebar buttons to create a password-protected group room or join via room ID.

Add Friends – Add other users to your friend list; private chats become available.

Send Messages – Type in the input field, optionally attach a file, and press send.

Toggle Ephemeral Mode – Switch to “阅后即焚” mode so messages self-destruct after the chosen TTL.

Clear History – Use the sidebar buttons to clear current room history or all rooms’ histories (local storage only).

Project Structure
text
project/
├── backend/
│   ├── main.py              # FastAPI app & WebSocket endpoints
│   ├── models.py            # Data classes
│   ├── storage.py           # JSON file I/O and password utilities
│   ├── websocket_manager.py # WebSocket connection handling
│   └── file_handler.py      # File upload/download logic
├── frontend/
│   └── index.html           # Single-page frontend
├── data/                    # JSON storage files (users, messages, rooms, etc.)
├── uploads/                 # Uploaded files (UUID-named)
├── cert.pem                 # SSL certificate (optional)
├── key.pem                  # Private key (optional)
├── requirements.txt         # Python dependencies
└── README.md
License
This project is licensed under the MIT License – see the LICENSE file for details.
