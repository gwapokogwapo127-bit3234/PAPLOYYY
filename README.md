# 🤖 PAPLOY.AI

**Your friendly Gen-Z AI assistant** — built with Node.js, Express, and the OpenAI API.

Multiple users can access PAPLOY.AI through a shared link. Each person gets their own chat session — no login required.

---

## 📁 Folder Structure

```
paploy-ai/
├── public/
│   ├── index.html       # Chat UI
│   ├── style.css        # Dark-mode styles
│   └── app.js           # Frontend logic
├── server.js            # Express backend
├── package.json         # Dependencies & scripts
├── .env.example         # Template for env vars
├── .gitignore
└── README.md
```

---

## 🚀 Quick Start

### 1. Install Dependencies

```bash
cd paploy-ai
npm install
```

### 2. Set Up Your API Key

```bash
# Copy the example env file
cp .env.example .env
```

Open `.env` and replace `sk-your-api-key-here` with your actual OpenAI API key:

```env
OPENAI_API_KEY=sk-your-real-key-here
```

### 3. Run Locally

```bash
npm start
```

Open **http://localhost:3000** in your browser. That's it! 🎉

### Development Mode (auto-restart on changes)

```bash
npm run dev
```

---

## ⚙️ Configuration

All settings are in `.env`:

| Variable | Default | Description |
|---|---|---|
| `OPENAI_API_KEY` | *(required)* | Your OpenAI API key |
| `OPENAI_BASE_URL` | `https://api.openai.com/v1` | API endpoint (change to use other providers) |
| `AI_MODEL` | `gpt-3.5-turbo` | The model to use |
| `AI_NAME` | `PAPLOY.AI` | Name shown in UI and system prompt |
| `PORT` | `3000` | Server port |
| `MAX_HISTORY` | `30` | Max messages per session to send to the API |

---

## 🌐 Deploy for Friends

### Option A: Ngrok (quickest way to share)

```bash
# Install ngrok: https://ngrok.com
ngrok http 3000
```

Share the `https://xxxx.ngrok.io` link with friends.

### Option B: Railway / Render (free hosting)

1. Push your code to a GitHub repo
2. Go to [railway.app](https://railway.app) or [render.com](https://render.com)
3. Create a new project → connect your repo
4. Add environment variables (`OPENAI_API_KEY`, etc.)
5. Deploy — you'll get a public URL to share!

### Option C: VPS (DigitalOcean, AWS, etc.)

```bash
# On your server:
git clone <your-repo-url>
cd paploy-ai
npm install
cp .env.example .env
# Edit .env with your API key
npm start
```

Use a process manager like `pm2` to keep it running:

```bash
npm install -g pm2
pm2 start server.js --name paploy-ai
```

---

## 🔒 Security Features

- **Rate limiting** — 20 requests/min per IP
- **Profanity filter** — blocks messages with bad words
- **No hardcoded secrets** — all keys in `.env`
- **Input validation** — max 4000 chars per message

---

## 🎨 Customization

### Change the AI personality

Edit the `SYSTEM_PROMPT` in `server.js` to change how PAPLOY.AI talks and behaves.

### Change the AI name

Update `AI_NAME` in `.env` — it automatically updates the system prompt. For the UI header/welcome message, edit `public/index.html`.

### Change the color scheme

Edit the CSS variables at the top of `public/style.css` (the `--accent` colors).

---

## 📜 License

MIT — do whatever you want with it! 💜
