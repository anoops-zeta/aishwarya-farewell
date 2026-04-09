# Aishwarya's Farewell Wordle 💛

A personalised farewell website — a series of Wordle puzzles, each revealing a message from the team.

---

## How to run locally

Because the app fetches `data.json`, you need a simple local server (browsers block `fetch()` on `file://`).

```bash
# Option 1 — Node (if installed)
npx serve .

# Option 2 — Python 3
python3 -m http.server 8000

# Option 3 — VS Code
Install "Live Server" extension → right-click index.html → Open with Live Server
```

Then open `http://localhost:8000` (or whatever port the tool shows).

---

## How to edit `data.json`

### Change intro text
```json
"intro": {
  "title": "...",
  "subtitle": "...",
  "buttonText": "..."
}
```

### Add / edit puzzles
Each puzzle needs:
- `"word"` — **exactly 5 uppercase letters** (e.g. `"CRAFT"`)
- `"hint"` — shown above the grid before the puzzle is solved
- `"message"` — revealed after solving

```json
{
  "id": 1,
  "word": "CRAFT",
  "hint": "What Aishwarya brings to every piece of content she writes.",
  "message": {
    "from": "Teammate Name",
    "role": "Job Title",
    "photo": "photos/teammate1.jpg",
    "text": "Your farewell message here..."
  }
}
```

### Add photos
1. Put the photo file in the `photos/` folder (JPG, PNG, or WebP)
2. Reference it in `data.json` as `"photo": "photos/your-filename.jpg"`
3. If a photo is missing or broken, the app automatically shows an emoji avatar fallback

### Edit the finale
```json
"finale": {
  "title": "Until we meet again, Aishwarya! 🎉",
  "message": "Your collective message here...",
  "signoff": "With love, the whole team 💛"
}
```

---

## Word rules
- Must be **exactly 5 letters**
- All caps in the JSON (the app is case-insensitive but uppercase keeps it consistent)
- Pick real English words — the game has no dictionary validation, so anything 5 letters works
- Avoid repeated letters if possible (easier for players), but duplicates are handled correctly

---

## File structure
```
index.html      ← entire app (no build step needed)
data.json       ← all content — edit this to personalise
photos/         ← put teammate photos here
README.md       ← this file
```
