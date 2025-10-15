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
- 🤖 **AI-Powered Chat** - Powered by knj 2.5 Flash, knj OpenAI, or custom models
- 💾 **Persistent Storage** - Automatic conversation history and preferences saving
- 🔒 **Secure Architecture** - Sandboxed Electron with CSP and proper isolation
- 🐳 **Docker Support** - Easy deployment with Docker Compose
- ⌨️ **Keyboard Shortcuts** - Efficient workflow with hotkeys
- 📱 **Responsive Design** - Beautiful UI that adapts to any screen size
- 🎯 **Drag & Drop** - File support for enhanced interactions

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

- 🐛 **Issues**: [GitHub Issues](https://github.com/CRTYPUBG/knj-coder--de/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/CRTYPUBG/knj-ai-assistant/discussions)
- 📧 **Email**: support@knj-ai.com

---

<div align="center">

Made with ❤️ by the KNJ Team

**[⬆ Back to Top](#-knj---ai-powered-desktop-assistant)**

</div>



