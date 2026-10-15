---
name: flashcards-app
description: "Build a single-file HTML flashcards app (flip, next, shuffle) with a themed look and an optional photo background, then test every button in the preview. Use when the user asks to make or change a flashcards app."
---

# Flashcards app

## 1. Ask first
Before planning, find out (ask only what the request leaves open):
- **Subject**: the language pair or topic, and which side is the front.
- **Word list**: how many words in total, and how many cards per round.
- **Look**: the theme or color style.
- **Name**: if none is given, suggest 10 short names that fit the subject and theme, and let the user pick.
- **Background**: plain colors, a drawn background made in code, or a real photo.
- **File**: the path, e.g. `flashcards.html`.

## 2. Plan, then build
Show a short plan in plain language and wait for approval. Then write **one self-contained .html file**: inline CSS and JS only, no CDN links, no web fonts, no outside images.

**Cards**
- Keep a `dictionary` array of `{ front, back }` objects, grouped by theme with comments.
- Each round deals `ROUND_SIZE` random cards (Fisher–Yates shuffle). It prefers words that weren't in the previous round, so every Shuffle shows new words. The first round on page load is random too.

**Buttons** (large, at least 64px tall)
- **Flip**: toggles a CSS 3D rotate between front and back. Clicking the card also flips it.
- **Next**: moves to the next card and wraps from the last card back to 1.
- **Shuffle**: deals a new round, goes back to card 1 and briefly shows a "Shuffled" message.
- Keyboard: Space flips, → goes to the next card.
- When moving to a new card, snap it back to the front side **without the flip animation**. Otherwise the answer of the next card shows for a moment.

**Layout**
- Title, a counter ("CARD 01 / 10"), the card, then the buttons.
- At phone width (375px) the buttons wrap and nothing scrolls sideways.
- Define the colors once as CSS variables, and make sure the text stays readable on top of the background.

## 3. Photo background (only if a real photo is wanted)
1. Search a free-license photo site (Unsplash or Pexels) and preview 3–4 candidates that match the theme.
2. Before downloading, tell the user the photo, the photographer, the license, the source URL, the file name and the size, and **wait for their OK**. If they pick a different one, show that photo's details and ask again.
3. Download a version about 1600px wide (under ~400 KB) into the scratchpad folder, never into the project.
4. Embed it in the .html as a base64 `data:` URI on a fixed `body::before` layer. Put a semi-transparent gradient tint over it in the theme colors so the cards stay readable.
5. Add a small credit line: "Photo: <photographer> / <site>".

## 4. Test every button in the preview
Open the file in the Browser pane, then:
- Take a screenshot to check the name, theme and background.
- **Flip** twice: the card shows the back side, then the front again.
- **Next** through every card: the counter reaches the last card and wraps to 01, and each card lands on the front side.
- **Shuffle** about 3 times: record each round's words and confirm the rounds differ, the counter resets to 01 and the front side shows.
- Click the card itself to check that it flips.
- Check the console for errors and test phone width (375px), then reset the viewport.
- If the pane is small, set a desktop viewport and click buttons by element ref instead of screen position. Read the counter and card text with JS to confirm what changed.

## 5. Report
Explain in plain language what changed. Add a table with one row per button showing what was checked and ✅ or ❌, and mention the file size if a photo was embedded. End by inviting the user to try the buttons themselves and describe anything that looks off.
