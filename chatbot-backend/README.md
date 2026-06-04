# Swastik Portfolio Chatbot

A lightweight Node.js proxy that sits between your portfolio and the Anthropic API,
keeping your API key secret while powering the recruiter chatbot widget.

---

## Deploy in 5 minutes (Vercel — free tier)

### 1. Get an Anthropic API key
- Go to https://console.anthropic.com
- Create an account → API Keys → Create Key
- Copy the key (starts with `sk-ant-...`)

### 2. Push this folder to GitHub
```bash
cd chatbot-backend
git init
git add .
git commit -m "init chatbot backend"
# Create a new repo on GitHub, then:
git remote add origin https://github.com/YOUR_USERNAME/swastik-chatbot-backend.git
git push -u origin main
```

### 3. Deploy to Vercel
- Go to https://vercel.com → New Project → Import your GitHub repo
- Vercel auto-detects Node.js
- Go to **Settings → Environment Variables** and add:
  - `ANTHROPIC_API_KEY` = your key from step 1
  - `ALLOWED_ORIGIN` = your portfolio domain e.g. `https://swastikchowdhury.com`
- Click Deploy
- Copy your deployment URL e.g. `https://swastik-chatbot-backend.vercel.app`

### 4. Update your portfolio HTML
In `index.html`, find this line near the bottom:
```js
var BACKEND_URL = "https://YOUR_BACKEND_URL_HERE";
```
Replace it with your Vercel URL:
```js
var BACKEND_URL = "https://swastik-chatbot-backend.vercel.app";
```

### 5. Done!
The chat bubble will appear in the bottom-right corner of your portfolio.
Recruiters can ask things like:
- "What's Swastik's tech stack?"
- "Has he worked with Kafka?"
- "Is he open to relocation?"
- "Tell me about the recommendation systems project"

---

## Alternative: Railway (also free)
- Go to https://railway.app → New Project → Deploy from GitHub repo
- Add env vars: `ANTHROPIC_API_KEY`, `ALLOWED_ORIGIN`, `PORT=3000`
- Railway gives you a URL like `https://swastik-chatbot.up.railway.app`

---

## Local testing
```bash
cp .env.example .env
# Edit .env and paste your ANTHROPIC_API_KEY
npm install
npm start
# Backend runs on http://localhost:3000
```
Then in index.html temporarily set:
```js
var BACKEND_URL = "http://localhost:3000";
```

---

## Cost estimate
- Claude Haiku is ~$0.25 per million input tokens
- A typical chat conversation = ~2,000 tokens
- 1,000 recruiter conversations ≈ $0.50
- Essentially free for a portfolio
