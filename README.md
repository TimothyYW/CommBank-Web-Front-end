# CommBank Web

A React + TypeScript frontend for the Commonwealth Bank Software Engineering virtual experience on Forage. It connects to the CommBank Server API and lets users manage their financial goals — including adding emoji icons to them.

---

## What's in here

```
src/
├── api/
│   ├── lib.ts          # All API calls (get/create/update goals, users, transactions)
│   └── types.ts        # TypeScript interfaces for all data models
├── store/              # Redux state management (goals, modal, theme, user)
├── ui/
│   ├── components/     # Reusable components (EmojiPicker, Card, DatePicker, etc.)
│   ├── features/
│   │   └── goalmanager/  # GoalManager, GoalIcon, AddIconButton
│   ├── pages/
│   │   └── Main/         # Dashboard, GoalCard, GoalsSection, Transactions
│   └── surfaces/         # Modal, Navbar, Drawer
└── App.tsx             # Root component
```

---

## Getting started

### 1. Clone the repo

```bash
git clone https://github.com/TimothyYW/CommBank-Web-Front-end.git
```

### 2. Install dependencies

```bash
npm install
```

### 3. Make sure the backend is running

The app talks to the local CommBank Server at `http://localhost:5203`. Make sure it's up before starting the frontend. Check out the [CommBank Server repo](https://github.com/TimothyYW/CommBank-Server) for setup instructions.

### 4. Start the app

```bash
npm start
```

Opens at `http://localhost:3000`.

---

## What changed from the original

- **Added `icon` field to the `Goal` type** in `src/api/types.ts` — optional string to store an emoji
- **GoalCard now displays the icon** — if a goal has an emoji set, it shows on the card in the dashboard
- **Emoji picker in GoalManager** — click "Add icon" to open the emoji picker, pick one, and it saves instantly
- **GoalIcon component** — clicking the emoji in the Goal Manager reopens the picker so you can change it
- **API pointed to local server** — `API_ROOT` in `lib.ts` set to `http://localhost:5203` so changes actually persist

---

## How the emoji feature works

1. Open any goal card on the dashboard
2. Click the smiley **"Add icon"** button
3. Pick an emoji from the picker
4. Close the modal by clicking the dark overlay
5. The emoji appears on the goal card
6. Refresh the page — it's still there (saved to the database)

---

## Notes

- Requires Node.js to run
- Backend must be running at `http://localhost:5203` for data to load
- `emoji-mart` v3 is used for the emoji picker
