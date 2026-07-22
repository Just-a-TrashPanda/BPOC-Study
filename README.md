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
├── study.html              (the study reference app — chapter tabs,
│                             topic sub-tabs within each chapter, and
│                             a search bar across all built-out chapters)
└── supplemental/
    └── penal-code.html      (live — full Penal Code offense reference)
```

Chapters live inside `study.html` as data (see the `chapters` array in
the `<script>` at the bottom) rather than as separate files — this
keeps the tabs, sub-tabs, and search working across all chapters from
one page. You can deep-link to a specific chapter with
`study.html?ch=9`.

## Adding a new chapter

Send Claude the chapter PDF and it'll add a new entry to the `chapters`
array in `study.html` (chapter title, unit goal, topic sub-tabs, and
cards), matching the format already used for Chapters 9 and 10, then
flip its status from "pending" to "live" on both `study.html` and the
hub's chapter grid in `index.html`.
