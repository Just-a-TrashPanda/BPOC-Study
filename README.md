[README.md](https://github.com/user-attachments/files/30288508/README.md)
# BPOC Study Hub — Hosting Guide

## Free hosting with GitHub Pages

1. Create a free GitHub account at github.com if you don't have one.
2. Create a new **public** repository (e.g., `bpoc-study`).
3. Upload all files/folders from this package into the repo, keeping the
   folder structure intact (`index.html` at the root, `chapters/` and
   `supplemental/` as subfolders).
4. In the repo, go to **Settings → Pages**.
5. Under "Build and deployment," set Source to **Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
6. GitHub gives you a live URL within a minute or two, in the form:
   `https://yourusername.github.io/bpoc-study/`
7. Share that one link with your classmates. Every time you push updated
   files to the repo, the live site updates automatically — no re-sending
   files.

## Adding a classmate as a contributor (optional)

If you want others to be able to push updates directly:
Settings → Collaborators and teams → Add people.

## File structure

```
bpoc-study/
├── index.html              (home hub — chapter grid + progress tracker)
├── study.html               (the study reference app — chapter tabs,
│                             topic sub-tabs, and search)
├── flashcards.html          (Quizlet-style flip cards, built from the
│                             same chapter data)
├── quiz.html                 (multiple-choice quiz — practice mode with
│                             instant feedback, or a timed test mode —
│                             also built from the same chapter data)
├── assets/
│   └── chapters-data.js     (single source of truth for all chapter
│                             content — study.html, flashcards.html,
│                             and quiz.html all load this file)
└── supplemental/
    └── penal-code.html      (live — full Penal Code offense reference,
                              with its own search bar)
```

Chapter content lives in **one place** — `assets/chapters-data.js` — so
updating a chapter updates it everywhere it's used (the reference page,
flashcards, and quiz) automatically. You can deep-link to a specific
chapter in the reference with `study.html?ch=9`.

## Adding a new chapter

Send Claude the chapter PDF and it'll add a new entry to the `chapters`
array in `assets/chapters-data.js` (chapter title, unit goal, topic
sub-tabs, and cards), matching the format already used for the built
chapters, then flip its status from "pending" to "live" on
`study.html` and the hub's chapter grid in `index.html`.

## Expanding flashcards or the quiz to more chapters

In `flashcards.html`, find:
```javascript
const FLASHCARD_ENABLED_CHAPTERS = [1, 2];
```
In `quiz.html`, find:
```javascript
const QUIZ_ENABLED_CHAPTERS = [1, 2];
```
Add any chapter number that's already "live" in `assets/chapters-data.js`
to either list and that chapter becomes available immediately — no
other changes needed, since both are generated automatically from the
same chapter data.
