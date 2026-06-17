# Cryo — Gulf Cryo AI Champion

An interactive, voice-enabled web chatbot featuring **Cryo**, Gulf Cryo's AI Champion. Cryo answers questions about Gulf Cryo — its 70+ year history, gas portfolio, industries served, sustainability and carbon-capture work — with a friendly on-brand interface, speech recognition, and spoken replies.

![Cryo](assets/cryo-character.png)

## Features

- **Voice in, voice out** — tap the mic to speak; Cryo listens, then answers out loud (text-to-speech). Voice can be toggled off.
- **Animated avatar** — Cryo reacts to each state: a calm breathing idle, a listening pulse, a thinking bob, and a speaking nod.
- **Grounded knowledge** — answers are built from Gulf Cryo's real company materials.
- **Self-contained** — `index.html` is the entire app. The character image, logo, styling, and logic are all embedded. No build step, no dependencies.

## Quick start

Just open `index.html` in a modern browser (Chrome, Edge, or Safari).

> **Voice note:** microphone access requires the page to be served over **HTTPS** or from **`localhost`**. Opening the file directly with a `file://` path will load the chat and text-to-speech, but browsers block the microphone on `file://`. Use one of the options below.

### Run locally with a quick server

```bash
# Python 3
python3 -m http.server 8000
# then open http://localhost:8000
```

```bash
# Node
npx serve .
```

## Deploy to GitHub Pages (free HTTPS hosting)

1. Create a new GitHub repository and push these files.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
4. Choose branch `main` and folder `/ (root)`, then **Save**.
5. After a minute, your site is live at `https://<your-username>.github.io/<repo-name>/`.

Because GitHub Pages serves over HTTPS, the microphone works there with no extra setup.

```bash
git init
git add .
git commit -m "Initial commit: Cryo AI Champion chatbot"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Using the microphone

1. Tap the round **mic** button (bottom-left of the chat).
2. The browser asks for microphone permission the first time — choose **Allow**.
3. Speak your question. The mic button pulses orange and Cryo shows a "Listening…" state.
4. When you stop, Cryo processes and answers out loud.

If nothing happens, see Troubleshooting below.

## Troubleshooting voice

| Symptom | Cause | Fix |
| --- | --- | --- |
| Mic does nothing, no prompt | Page opened via `file://` | Serve over `localhost` or HTTPS (see above) |
| "Microphone access is blocked" | Permission denied earlier | Click the lock/camera icon in the address bar → allow microphone → reload |
| "Couldn't find a microphone" | No input device | Check your system microphone settings |
| Works in Chrome but not Firefox | Firefox has limited Web Speech support | Use Chrome, Edge, or Safari |
| Cryo doesn't speak | Browser needs a user interaction first, or voice toggled off | Click anywhere once; check the "Voice on" toggle |

## Going live with real AI (optional)

Out of the box, Cryo answers from a built-in knowledge base using keyword matching — works instantly with zero setup and no API key. For full conversational intelligence (any phrasing, follow-up questions, reasoning), connect it to Claude via the Anthropic API.

In `index.html`, find the `getAnswer()` function and the `setTimeout` inside `handleUser()`. Replace the local lookup with a `fetch()` to a small backend you control that calls the Anthropic API, passing the knowledge base as system context.

**Important:** never put an API key in this page or anywhere client-side — it must live on a server you control.

## Customizing the knowledge base

Open `index.html` and find the `KB` array near the top of the `<script>`. Each entry has:

- `tags`: keywords/phrases that should match this answer
- `a`: the answer (supports simple HTML like `<strong>` and `<br>`)

Add, edit, or remove entries to change what Cryo knows. Update the `SUGGESTIONS` array to change the starter chips.

## Files

```
index.html                  The complete app (open or deploy this)
assets/cryo-character.png   Source character image (for re-editing)
assets/gulf-cryo-logo.jpg   Source logo (for re-editing)
README.md
LICENSE
.gitignore
```

The images in `assets/` are the originals kept for convenience; the running app uses its own embedded copies, so you only ever need to deploy `index.html`.

## Browser support

| Browser | Chat | Text-to-speech | Voice input |
| --- | --- | --- | --- |
| Chrome | ✅ | ✅ | ✅ |
| Edge | ✅ | ✅ | ✅ |
| Safari | ✅ | ✅ | ✅ |
| Firefox | ✅ | ✅ | ⚠️ limited |

---

Built for Gulf Cryo. "We go beyond the molecules."
