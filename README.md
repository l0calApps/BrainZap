# 🧠 BrainZap

A self-hosted, fully offline trivia app with **850 questions**, **12 categories**, and **3 game modes**. Built with React + Vite, served by nginx, containerized with Docker. No AI, no internet connection, no external APIs required.

---

## Quick Start

```bash
# Clone or extract the project
cd brainzap

# Option A — Docker (recommended)
docker compose up -d --build
# Visit http://localhost:3444

# Option B — Local dev (requires Node.js 20+)
npm install
npm run dev
# Visit http://localhost:3444
```

---

## Features

| Feature | Details |
|---|---|
| **850 Questions** | 12 categories - 3 modes |
| **Classic Mode** | Answer at your own pace, no time pressure |
| **Blitz Mode ⚡** | 15 seconds per question — think fast! |
| **Endurance Mode ❤️** | 3 lives, wrong answers cost a life, no question limit |
| **Streak Counter 🔥** | Tracks consecutive correct answers, animates at 3x and 5x |
| **Balanced Selection** | Round-robin distribution ensures category variety in mixed games |
| **Option Shuffling** | Answer order randomized every session — no memorizing positions |
| **Shareable Results** | Copy score summary to clipboard |
| **Fully Offline** | No network calls after first load. Works on an air-gapped server. |

---

## Categories

| # | Category | Questions |
|---|---|---|
| 1 | 🌍 Geography | 60 |
| 2 | 🔬 Science | 60 |
| 3 | 📜 History | 60 |
| 4 | ⚽ Sports | 60 |
| 5 | 🎵 Music | 60 |
| 6 | 🎬 Movies & TV | 60 |
| 7 | 💻 Technology | 60 |
| 8 | 🍕 Food & Drink | 60 |
| 9 | 🦁 Animals | 60 |
| 10 | ➗ Math | 60 |
| 11 | 🌟 Pop Culture | 60 |
| 12 | 📚 Literature | 60 |

---

## Project Structure

```
brainzap/
├── src/
│   ├── App.jsx                 ← All UI (Home, Setup, Game, Results screens)
│   ├── main.jsx                ← React entry point
│   └── questions/
│       ├── index.js            ← Category registry + selectQuestions() function
│       ├── geography.json
│       ├── science.json
│       ├── history.json
│       ├── sports.json
│       ├── music.json
│       ├── movies.json
│       ├── technology.json
│       ├── food.json
│       ├── animals.json
│       ├── math.json
│       ├── popculture.json
│       └── literature.json
├── index.html
├── vite.config.js
├── package.json
├── nginx.conf
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── .gitignore
├── validate-questions.js       ← Run before deploying
└── QUESTIONS.md                ← Full guide for adding/editing questions
```

---

## Adding or Editing Questions

See **[QUESTIONS.md](./QUESTIONS.md)** for the complete developer guide, including:
- JSON format specification
- Step-by-step instructions for adding questions
- How to add a new category
- Validation script usage
- Deployment procedure

**Quick validation:**
```bash
node validate-questions.js
```

---

## Deployment

```bash
# Rebuild and redeploy (required after any content change)
docker compose up -d --build

# Check status
docker compose ps
docker compose logs brainzap

# Change the port (edit docker-compose.yml):
ports:
  - "8080:3444"   # host:container
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 18 + Vite 5 |
| Styling | Inline CSS (zero dependencies) |
| Fonts | Google Fonts (Fredoka One + Nunito) — loaded at runtime |
| Build | Vite (TypeScript-free, zero config) |
| Server | nginx 1.27-alpine |
| Container | Docker + Docker Compose |
| Data | Static JSON bundled at build time |

---

## License

MIT — use, modify, and self-host freely.
