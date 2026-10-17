# NOVA AI 1.1 — Vercel deployment guide

This project includes the latest NOVA AI 1.1 chat UI and serverless chat endpoint. Common questions and small arithmetic are answered immediately; other questions trigger a DuckDuckGo web lookup and return one combined reply with at most one source link.

## Deploy to Vercel (no API key required)

1. Download and extract `nova-ai-1.1-vercel.zip`.
2. Open https://vercel.com and sign in.
3. Click **Add New → Project**.
4. Easiest method: push the extracted folder to a new GitHub repository, then import that repository in Vercel. Alternatively, install Vercel CLI and deploy from this folder.
5. Keep the project settings on the default framework / no build command. The static files are in `public/`; the serverless endpoint is `api/chat.js`.
6. Click **Deploy**. Open the generated `.vercel.app` URL and test `hello`, `what can you do?`, `explain photosynthesis`, `12 + 8`, and a current-news question.

### Optional Vercel CLI route

Install Node.js 18 or newer, then in this folder run:

```bash
npm install -g vercel
vercel login
vercel
```

Follow the prompts. When the preview deployment works, publish it with:

```bash
vercel --prod
```

## How it works

- `public/index.html`: page and chat markup.
- `public/style.css`: animated responsive design.
- `public/app.js`: chat widget; renders one assistant answer and an optional compact source link.
- `api/chat.js`: instant-answer rules plus server-side DuckDuckGo search fallback.
- `vercel.json`: serverless function configuration.

## Important limitation

This version does not use a full large-language-model API. Its built-in responses cover common questions, and web mode combines search-result snippets. It may not deeply reason about unusual or complex questions. Web lookup also depends on DuckDuckGo being reachable from the deployed serverless function.
