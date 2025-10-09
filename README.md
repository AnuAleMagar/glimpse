# Glimpse

**Capture a single second, relive a lifetime of memories.**

## Overview

Memories matter. They are how we hold onto the people we love, the places we have been, and the versions of ourselves we do not want to forget. Yet the best moments are often small—easy to lose in the noise of a busy day.

Glimpse is built on a simple belief: **a one-second clip can be enough for a flash of memory**. You do not need a long film to feel something again. A breath of video—a face, a laugh, light through a window—can bring an entire day rushing back. Over time, those tiny glimpses stack into something bigger: a honest timeline of your life, month by month.

This project turns that idea into software: record or upload short clips, browse them on a calendar-style timeline, stitch them into **monthly montages**, add mood with **background music**, and optionally ask **AI** to describe the story your montage tells.

## Features

- **Daily glimpses** — Record from the browser or upload a short video; clips are stored and thumbnailed via Cloudinary.
- **Timeline** — See your memories grouped by month and year.
- **Monthly montages** — Combine clips for a chosen month with FFmpeg; optional soundtrack and music library / search flows in the UI.
- **AI summaries** — Optional Gemini-powered summaries of montage videos.
- **Accounts** — Sign up, email verification (Nodemailer), and JWT-based login.

## Tech stack

| Layer    | Technologies                                      |
| -------- | ------------------------------------------------- |
| Frontend | React 19, Vite, Tailwind CSS, React Router, Axios |
| Backend  | Node.js, Express 5, MongoDB (Mongoose)            |
| Media    | Cloudinary, FFmpeg (`fluent-ffmpeg`)              |
| Auth     | JWT, bcrypt                                       |
| AI       | Google Generative AI (Gemini)                     |

## Repository layout

```
glimpse/
├── frontend/     # React + Vite app
└── backend/      # Express API
```

## Prerequisites

- **Node.js** (recent LTS recommended)
- **MongoDB** (local or Atlas URI)
- **FFmpeg** on your PATH (required for montage generation). On Linux/macOS, install via your package manager; on Windows, install FFmpeg and ensure the path in `backend/controllers/montage.js` matches your install if the default does not.
- **Cloudinary** account (video upload and delivery)
- Optional: **Gmail** (or compatible SMTP) for verification emails; **Gemini API key** for summarization

## Environment variables

Create `backend/.env` (never commit real secrets):

```env
PORT=3001
MONGODB_URI=mongodb://localhost:27017/glimpse
SECRET=your_jwt_secret

CLOUD_NAME=
API_KEY=
API_SECRET=

EMAIL_USER=
EMAIL_PASS=

GEMINI_API_KEY=
```

The frontend currently calls `http://localhost:3001` for the API; keep the backend port in sync or update the URLs under `frontend/src/` if you deploy elsewhere.

## Getting started

**Backend**

```bash
cd backend
npm install
# add .env as above
npm run dev
```

**Frontend** (separate terminal)

```bash
cd frontend
npm install
npm run dev
```

Open the URL Vite prints (usually `http://localhost:5173`). Register, verify email if SMTP is configured, then log in to capture, upload, and build montages.

## License

ISC (see `backend/package.json`). Add or align a top-level license file if you standardize on something else.
