# Divorce Cowboy

**Live site:** [divorcecowboy.com](https://divorcecowboy.com)  
**Netlify project:** bespoke-dragon-7b3b54  
**Deploy method:** Netlify Drop — drag folder to [netlify.com/drop](https://netlify.com/drop)

---

## Two versions

| File | Description | Status |
|------|-------------|--------|
| `divorce-cowboy-v2.html` | Main diagnostic tool — 5-state flow, AI responses | Active |
| `divorce-cowboy.html` | Original — 7-question quiz + guided exercise flow | Archived |

---

## divorce-cowboy-v2.html

Single self-contained HTML file. All images (cowboy hero, triangle diagram, bucket illustration, tactical empathy illustration) are base64-embedded. No external dependencies except Google Fonts and the Anthropic API.

### How to deploy

1. Download `divorce-cowboy-v2.html`
2. Go to [netlify.com/drop](https://netlify.com/drop)
3. Drag the file into the drop zone
4. Site updates immediately at divorcecowboy.com

### API key

The Anthropic API key is embedded in the file. If it needs to be rotated, search for `sk-ant-api03` and replace the value.

### Formspree (email capture)

Search for `PASTE_YOUR_FORMSPREE_ID_HERE` and replace with your Formspree form ID from [formspree.io](https://formspree.io).

---

## divorce-cowboy.html (original)

The original app requires three companion files in the same folder:
- `cowboy-hero.jpg`
- `logo-white.png`  
- `intro.mp3`

Deploy all four files together via Netlify Drop.

---

## Tech stack

- Vanilla HTML / CSS / JS — no frameworks
- Anthropic Claude API (`claude-sonnet-4-20250514`)
- Netlify Drop for deployment
- Formspree for email capture (not yet connected)
