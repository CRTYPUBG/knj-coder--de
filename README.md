# 🚀 KNJ - AI-Powered Desktop Assistant

<div align="center">

![KNJ Logo](http://knj.gt.tc/logo_no_bg.png)

**K** **N** **J** - Your Intelligent Desktop Companion

[![Electron](https://img.shields.io/badge/Electron-28.0.0-47848F?logo=electron)](https://www.electronjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=node.js)](https://nodejs.org/)
[![OpenAI](https://img.shields.io/badge/OpenAI-API-412991?logo=openai)](https://openai.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker)](https://www.docker.com/)

</div>

---

## ✨ Features

- 🎨 **Dynamic Theme System** - Three vibrant color themes (K: Blue, N: Green, J: Purple)
- 🤖 **AI-Powered Chat** - Powered by Google Gemini 2.5 Flash, OpenAI GPT-4, or custom models
- 💾 **Persistent Storage** - Automatic conversation history and preferences saving
- 🔒 **Secure Architecture** - Sandboxed Electron with CSP and proper isolation
- 🐳 **Docker Support** - Easy deployment with Docker Compose
- ⌨️ **Keyboard Shortcuts** - Efficient workflow with hotkeys
- 📱 **Responsive Design** - Beautiful UI that adapts to any screen size
- 🎯 **Drag & Drop** - File support for enhanced interactions

---

## 🎨 Theme Colors

KNJ features three distinct color themes representing each letter:

| Theme | Letter | Primary Color | RGB | Preview |
|-------|--------|---------------|-----|---------|
| **K** | Blue | `#00A3FF` | `rgb(0, 163, 255)` | 🔵 |
| **N** | Green | `#00FF99` | `rgb(0, 255, 153)` | 🟢 |
| **J** | Purple | `#9900FF` | `rgb(153, 0, 255)` | 🟣 |

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** - Comes with Node.js
- **Docker** (optional, for containerized deployment) - [Download](https://www.docker.com/get-started)
- **AI API Key** - Choose one:
  - **Google Gemini** (Recommended) - [Get API Key](https://aistudio.google.com/app/apikey)
  - **OpenAI** - [Get API Key](https://platform.openai.com/api-keys)

---

## 🚀 Quick Start

### 1️⃣ Clone & Install

```bash
# Clone the repository
git clone https://github.com/yourusername/knj-ai-assistant.git
cd knj-ai-assistant

# Install all dependencies
npm run install:all
```

### 2️⃣ Configure Environment

```bash
# Copy backend environment file
cp backend/.env.example backend/.env

# Edit backend/.env and add your API key
# For Gemini (Recommended):
# AI_PROVIDER=gemini
# GEMINI_API_KEY=your-gemini-api-key

# For OpenAI:
# AI_PROVIDER=openai
# OPENAI_API_KEY=sk-your-key-here
```

**Windows PowerShell:**
```powershell
Copy-Item backend\.env.example backend\.env
notepad backend\.env
```

**📖 Detailed Gemini Setup:** See [GEMINI_SETUP.md](GEMINI_SETUP.md) for step-by-step instructions.

### 3️⃣ Start the Application

**Option A: Local Development**

```bash
# Terminal 1: Start Backend
npm run backend:dev

# Terminal 2: Start Electron App
npm start
```

**Option B: Docker (Recommended for Production)**

```bash
# Start backend with Docker
npm run docker:up

# Start Electron app
npm start
```

---

## 📁 Project Structure

```
knj-ai-assistant/
├── src/                      # Electron frontend
│   ├── main.js              # Electron main process
│   ├── preload.js           # Secure IPC bridge
│   ├── renderer.js          # UI logic & event handling
│   ├── index.html           # Main UI
│   └── styles.css           # Theme styles (K, N, J colors)
│
├── backend/                  # Express API server
│   ├── server.js            # Main server file
│   ├── routes/              # API routes
│   │   ├── chat.js          # AI chat endpoint
│   │   └── health.js        # Health check
│   ├── Dockerfile           # Backend Docker image
│   ├── package.json         # Backend dependencies
│   └── .env.example         # Environment template
│
├── docker-compose.yml        # Docker orchestration
├── package.json             # Main package file
├── .gitignore               # Git ignore rules
└── README.md                # This file
```

---

## ⚙️ Configuration

### Backend Environment Variables

Edit `backend/.env`:

**Option 1: Google Gemini (Recommended)**
```env
# AI Model Selection
AI_PROVIDER=gemini

# Gemini API Configuration
GEMINI_API_KEY=your-gemini-api-key-here
GEMINI_MODEL=gemini-2.5-flash

# Server
PORT=3000
HOST=0.0.0.0
NODE_ENV=development
CORS_ORIGIN=*
```

**Option 2: OpenAI**
```env
# AI Model Selection
AI_PROVIDER=openai

# OpenAI Configuration
OPENAI_API_KEY=sk-your-openai-api-key
OPENAI_MODEL=gpt-4

# Server
PORT=3000
HOST=0.0.0.0
NODE_ENV=development
CORS_ORIGIN=*
```

### Supported AI Providers

**1. Google Gemini (Default & Recommended)**
- Fast and efficient responses
- Excellent multilingual support
- Generous free tier
- Models: `gemini-2.5-flash`, `gemini-1.5-pro`, `gemini-1.5-flash`

**2. OpenAI**
- High-quality responses
- Industry standard
- Models: `gpt-4`, `gpt-4-turbo-preview`, `gpt-3.5-turbo`

**3. Custom Models**
KNJ supports custom AI models (e.g., locally hosted LLMs):

1. Set `AI_PROVIDER=custom` in `backend/.env`
2. Set `CUSTOM_MODEL_URL` to your model endpoint
3. Ensure your model exposes a compatible API

Example with Ollama:
```env
AI_PROVIDER=custom
CUSTOM_MODEL_URL=http://localhost:11434
```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+K` / `Cmd+K` | Focus input field |
| `Ctrl+L` / `Cmd+L` | Clear chat history |
| `Ctrl+N` / `Cmd+N` | New chat session |
| `Ctrl+R` / `Cmd+R` | Reload application |
| `Ctrl+Shift+I` | Toggle DevTools |
| `Enter` | Send message |
| `Shift+Enter` | New line in input |
| `Esc` | Clear input field |

---

## 🐳 Docker Deployment

### Build and Run

```bash
# Build Docker images
npm run docker:build

# Start services
npm run docker:up

# Stop services
npm run docker:down
```

### Custom Docker Compose

Add custom AI model to `docker-compose.yml`:

```yaml
services:
  custom-model:
    image: your-model-image:latest
    container_name: knj-custom-model
    ports:
      - "8080:8080"
    volumes:
      - ./models:/models
    networks:
      - knj-network
```

---

## 🔧 Development

### Running in Development Mode

```bash
# Backend with hot reload
npm run backend:dev

# Electron with hot reload (requires nodemon)
npm run dev
```

### Building for Production

```bash
# Install electron-builder
npm install --save-dev electron-builder

# Build for your platform
npx electron-builder --win   # Windows
npx electron-builder --mac   # macOS
npx electron-builder --linux # Linux
```

---

## 🎯 API Endpoints

### Backend API

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | API information |
| `GET` | `/health` | Health check |
| `POST` | `/api/chat` | Send message to AI |
| `GET` | `/api/chat/:id` | Get conversation history |
| `DELETE` | `/api/chat/:id` | Clear conversation |

### Example Request

```bash
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{
    "message": "Hello, KNJ!",
    "conversationId": "optional-id"
  }'
```

---

## 🎨 Customization

### Changing Themes

Themes are defined in `src/styles.css`:

```css
.theme-blue {
    --primary-color: #00A3FF;
    --primary-rgb: 0, 163, 255;
    --primary-gradient: linear-gradient(135deg, #00A3FF 0%, #0077CC 100%);
}
```

Add custom themes by:
1. Adding new theme class in `styles.css`
2. Adding theme button in `index.html`
3. Updating theme logic in `renderer.js`

### Custom AI Personality

Edit the system prompt in `backend/routes/chat.js`:

```javascript
{
    role: 'system',
    content: `You are KNJ, an intelligent AI assistant...`
}
```

---

## 🐛 Troubleshooting

### Backend Not Connecting

1. Check if backend is running: `curl http://localhost:3000/health`
2. Verify `.env` file exists in `backend/` directory
3. Check OpenAI API key is valid
4. Look for error messages in backend console

### Electron Not Starting

1. Clear Electron cache: Delete `node_modules` and reinstall
2. Check `src/main.js` for errors
3. Run with DevTools: `npm start` and press `Ctrl+Shift+I`

### Docker Issues

```bash
# View logs
docker-compose logs backend

# Restart services
docker-compose restart

# Clean rebuild
docker-compose down
docker-compose build --no-cache
docker-compose up
```

---

## 📊 Performance

- **Startup Time**: ~2-3 seconds
- **Memory Usage**: ~150-200 MB (Electron)
- **API Response**: ~1-3 seconds (depends on AI model)
- **Storage**: Minimal (~50 MB including node_modules)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/AmazingFeature`
3. Commit changes: `git commit -m 'Add AmazingFeature'`
4. Push to branch: `git push origin feature/AmazingFeature`
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **OpenAI** for providing powerful AI models
- **Electron** for cross-platform desktop framework
- **Express** for robust backend API
- **Community** for inspiration and support

---

## 📞 Support

- 🐛 **Issues**: [GitHub Issues](https://github.com/yourusername/knj-ai-assistant/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/yourusername/knj-ai-assistant/discussions)
- 📧 **Email**: support@knj-ai.com

---

<div align="center">

Made with ❤️ by the KNJ Team

**[⬆ Back to Top](#-knj---ai-powered-desktop-assistant)**

</div>

