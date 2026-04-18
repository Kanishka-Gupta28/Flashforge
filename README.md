# ⚡ FlashForge — AI Flashcard Engine

> **Cuemath AI Builder Challenge — Problem 1: The Flashcard Engine**

---

## What I Built

FlashForge turns any PDF into a smart, practice-ready flashcard deck using AI. Drop in a chapter, get back a full deck — definitions, examples, edge cases, and concepts — ready to study with spaced repetition.

**Live features:**
- PDF upload with in-browser text extraction (PDF.js — file never leaves your device)
- AI-generated flashcards in 4 types: definition, concept, worked example, edge case
- SM-2 spaced repetition — cards you struggle with reappear sooner
- Progress tracking — mastery %, accuracy, 70-day heatmap, streaks
- Deck management — browse, study, delete, pick up where you left off
- Polished UI — 3D flip animations, keyboard shortcuts, dark theme

---

## Key Decisions & Tradeoffs

**Single-file architecture** — No build step, no npm. Just `index.html`. Trivially deployable, immediately readable. Right choice for this scope.

**PDF.js client-side parsing** — Text extracted in the browser. No file uploads, no storage costs, complete privacy. Tradeoff: scanned/image PDFs won't work.

**SM-2 algorithm** — The same algorithm Anki uses. Battle-tested and proven. Cards start at 1-day intervals, grow exponentially on "Good/Easy", reset on "Again".

**localStorage** — No backend, no cost. Tradeoff: no cross-device sync. V2 would add Supabase.

**AI prompt engineering** — Prompt explicitly requests balanced card types, constrains length, and instructs "write like a great teacher." Far better output than naive prompts.

---

## What I'd Improve With More Time

1. Cross-device sync with Supabase backend
2. Scanned PDF support via Tesseract.js OCR
3. Semantic chunking by document headings
4. Card editor — edit/delete individual cards
5. Multiple study modes (quiz, type-the-answer)
6. Export to CSV / Anki format
7. Shareable deck links

---

## Running Locally

```bash
# Just open the file — no npm, no server needed
open index.html

# Or serve with any static server
npx serve .
```

---

## Tech Stack

| Layer | Choice |
|-------|--------|
| Frontend | Vanilla HTML/CSS/JS |
| PDF Parsing | PDF.js (CDN, client-side) |
| AI | Claude Sonnet API |
| Spaced Repetition | SM-2 Algorithm |
| Storage | localStorage |
| Hosting | Vercel (free) |
