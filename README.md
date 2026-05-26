# 📅 MiMoPlanner

### Weekly Schedule Planner — Powered by Xiaomi MiMo V2.5

A fully client-side weekly schedule planner with drag & drop events, color-coded categories, recurring events, and browser notifications. Plan your week in a 7×24 grid, organize by category (Work, Study, Exercise, Social, Health, Hobby), and export/import your schedule as JSON. Zero dependencies, single HTML file.

[![Live Demo](https://img.shields.io/badge/Live-Demo-000?style=for-the-badge&logo=github)](https://gyoomei.github.io/mimoplanner/)
[![Try Now](https://img.shields.io/badge/Try-Now-6366f1?style=for-the-badge&logo=googlechrome)](https://gyoomei.github.io/mimoplanner/)
[![AI](https://img.shields.io/badge/AI-Xiaomi%20MiMo%20V2.5-f97316?style=for-the-badge)](https://mimo.xiaomi.com/)
[![Zero API](https://img.shields.io/badge/Zero-API-22c55e?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📖 The Problem

Online calendar apps (Google Calendar, Outlook) require accounts, sync setup, and are heavyweight for simple scheduling. There's no instant, privacy-first weekly planner that works offline with zero setup — just open and start planning.

## ✨ How it works

```
You click:     Any cell on the 7×24 grid → event modal opens
You fill:      Title, time, category, notes, recurring toggle
You drag:      Move events between cells
You export:    JSON backup, import on any device
```

**That's the entire UX** — click, plan, done. No accounts, no sync, no internet required.

## 🎯 Core Features

| Capability | Detail |
|---|---|
| Grid | 7 days × 24 hours with half-hour precision |
| Categories | 8 color-coded: Work, Study, Exercise, Social, Health, Hobby, Errands, Other |
| Drag & Drop | Move events between days/times by dragging |
| Recurring | Weekly repeat toggle for repeating schedules |
| Reminders | Browser notification 5 minutes before event |
| Notes | Optional text notes per event |
| Export/Import | JSON backup for data portability |
| Navigation | Week-by-week navigation with "Today" button |
| Auto-scroll | Scrolls to current hour on "Today" click |
| Dark/Light | Toggle with persistence |
| Mobile | Responsive grid for small screens |

## 🏗️ Architecture

```
┌─────────────────────────────────────────┐
│  7×24 CSS Grid ── Event Blocks          │
│       │                                  │
│  Click cell → Modal (title/time/cat)    │
│  Drag block → Drop on new cell          │
│  localStorage → Persist all events      │
│       │                                  │
│  Recurring: match by day-of-week        │
│  Reminder: Notification API + 5min      │
│  Export: JSON download                  │
│  Import: JSON file upload               │
└─────────────────────────────────────────┘
```

## 💡 Architecture Decisions

**Why CSS Grid?** A 7×24 schedule is naturally a grid. CSS Grid with `grid-template-columns: 50px repeat(7, 1fr)` gives perfect column alignment. Event blocks are positioned absolutely within hour cells for precise time placement.

**Why localStorage?** Schedule data is personal and small (~100KB max). localStorage persists across sessions without any server, account, or sync setup. Export/JSON handles backup and cross-device transfer.

**Why browser notifications?** The Notification API fires reminders even when the tab is backgrounded. One-time permission request, then automatic 5-minute-before alerts. Works on desktop and mobile browsers.

## 🧪 Try these examples

| Action | Result |
|---|---|
| Click Monday 9:00 | Opens modal, create "Kuliah" event |
| Set category to Study (blue) | Blue event block on grid |
| Toggle "Repeat weekly" | Event appears every Monday 9:00 |
| Drag event to Tuesday | Event moves to Tuesday same time |
| Export JSON | Downloads backup file |

## 🛠️ Stack

- **Frontend:** Vanilla JavaScript, single HTML file (~26KB)
- **Layout:** CSS Grid (7×24 schedule)
- **Storage:** localStorage for events, theme
- **Notifications:** Browser Notification API
- **Fonts:** [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) + [Outfit](https://fonts.google.com/specimen/Outfit) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- **Hosting:** GitHub Pages (zero infra cost)

## 🚀 Quick Start

```bash
git clone https://github.com/gyoomei/mimoplanner.git
open mimoplanner/index.html
# or
python3 -m http.server 8080 -d mimoplanner
```

## 📄 License

MIT — free for personal and commercial use.

**Built with 🧠 [Xiaomi MiMo V2.5](https://mimo.xiaomi.com/) · Submitted to [MiMo 100T program](https://mimo.xiaomi.com/)**
