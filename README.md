# XitingGrammar – Encrypted Real‑Time Chat Room
```
https://img.shields.io/badge/License-MIT-yellow.svg
https://img.shields.io/badge/Python-3.8+-blue.svg
https://img.shields.io/badge/FastAPI-0.95+-green.svg
https://img.shields.io/badge/Encryption-AES--256-blue
https://img.shields.io/badge/E2EE-Supported-brightgreen
```
A secure, real‑time chat room application with end‑to‑end encryption (E2EE) , private and group messaging, file sharing, and ephemeral message modes. All messages are encrypted on the client side using AES‑256 – no plaintext is ever stored on the server.

🔒 End‑to‑end encryption ensures that only you and your intended recipient can read the messages.

✨ Features
🔐 Account System – Register and log in with bcrypt‑hashed passwords.

👥 Friends & Private Chats – Add friends and start encrypted 1:1 conversations.

🗣️ Group Rooms – Create password‑protected group rooms or join public rooms.

📎 File Sharing – Upload images, documents, and files; images preview inline.

⏱️ Ephemeral Mode – Messages self‑destruct after a chosen TTL (30s–1h).

🌙 Light/Dark Theme – One‑click toggle between light and dark interface.

💾 Local History – Messages are stored in your browser’s localStorage (optional ephemeral toggle).

🔒 End‑to‑End Encryption (E2EE) – All message content is encrypted with AES‑256 on the client side.

🔌 Real‑Time Communication – WebSocket ensures instant delivery and online status updates.

🛠️ Tech Stack
Layer	Technology
Backend	Python 3.8+, FastAPI, Uvicorn
Real‑time	WebSockets
Frontend	HTML5, CSS3, Vanilla JavaScript
Storage	JSON files (users, messages, rooms)
Security	bcrypt (passwords), AES‑256 (messages, client‑side)
Transport	HTTPS / WSS (optional SSL)
🚀 Quick Start
Prerequisites
Python 3.8 or higher

pip (Python package manager)

Installation
Clone the repository

bash
git clone https://github.com/yourusername/xitinggrammar.git
cd xitinggrammar
Install dependencies

bash
pip install -r requirements.txt
Run the application

bash
python backend/main.py
The server will start at http://localhost:8000. If cert.pem and key.pem are present in the project root, it will use HTTPS (WSS for WebSockets).

Open your browser and navigate to http://localhost:8000 (or https://localhost:8000 if SSL is enabled).

📁 Project Structure
text
```
xitinggrammar/
├── backend/
│   ├── main.py              # FastAPI app & WebSocket endpoints
│   ├── models.py            # Data classes (User, Message, Room, etc.)
│   ├── storage.py           # JSON file I/O, password utilities
│   ├── websocket_manager.py # WebSocket connection handling
│   └── file_handler.py      # File upload/download logic
├── frontend/
│   └── index.html           # Single‑page frontend application
├── data/                    # JSON storage (users, messages, rooms, friendships)
├── uploads/                 # Uploaded files (named with UUID)
├── cert.pem                 # Optional SSL certificate
├── key.pem                  # Optional private key
├── requirements.txt         # Python dependencies
└── README.md                # This file
```
🔒 How Encryption Works
Passwords: Stored using bcrypt with a salt – never in plaintext.

Messages: When a user sends a message, the client encrypts the content with AES‑256 using a shared secret (e.g., a password known to both participants). The server only stores and forwards the encrypted ciphertext.

Transport: Communication between client and server can be secured via HTTPS/WSS to prevent man‑in‑the‑middle attacks.

Note: The current implementation requires both parties to know the same encryption key (e.g., room password or private chat password). For simplicity, the key is entered when creating or joining a room.

📖 Usage Guide
Login / Register – Enter any username and password. New users are automatically registered.

Join Public Room – The “public” room is available to everyone.

Create a Group Room – Click “Create Group” in the sidebar, enter a name and optional password.

Join a Room – Use “Join Room” and provide the room ID and password (if any).

Add Friends – Use “Add Friend” to connect with other users.

Start a Private Chat – Click the chat bubble next to a friend’s name.

Send Messages – Type your message, attach a file (optional), choose a TTL (if ephemeral mode is on), and press Send.

Ephemeral Mode – Toggle the mode switch; messages will be deleted after the selected TTL.

Clear History – Use the sidebar buttons to erase local message history for the current room or all rooms.

🔧 Configuration
Data Storage: All JSON files are stored in data/. You can back them up or delete them to reset the application.

Upload Directory: Files are saved in uploads/.

SSL: To enable HTTPS, place your cert.pem and key.pem in the project root. The server will automatically switch to HTTPS/WSS.

Ephemeral Mode: When enabled, messages are not saved to localStorage and self‑destruct after the specified TTL.

🤝 Contributing
Contributions are welcome! Feel free to open issues or submit pull requests. Please follow the existing code style and include clear descriptions of changes.

📄 License
This project is licensed under the MIT License – see the LICENSE file for details.
