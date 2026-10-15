# flashcards-app

A Claude Code plugin with one skill. It builds a **single-file HTML flashcards app** (Flip, Next, Shuffle buttons, keyboard shortcuts, a themed look and an optional free-license photo background), then opens it in the preview and tests every button.

## Install

Add the marketplace from GitHub:

```
/plugin marketplace add ShaharGadot/flashcards-app
```

Or from a local copy of this folder:

```
/plugin marketplace add ./flashcards-app
```

Then install the plugin:

```
/plugin install flashcards-app@shahargadot-skills
```

## Use

Ask Claude something like:

> Make me a Spanish–English flashcards app with 40 words, 10 cards per round, and a beach theme.

Claude asks about anything you left open (subject, word count, theme, name, background, file path), shows a short plan, builds the file and reports which buttons passed.
