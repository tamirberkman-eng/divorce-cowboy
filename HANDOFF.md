# HANDOFF — Divorce Cowboy

**Date:** April 27, 2026  
**File:** `divorce-cowboy-v2.html` (847KB, self-contained)  
**Live:** divorcecowboy.com via Netlify Drop

---

## What works

### Landing screen
- Full-bleed cowboy hero image (embedded base64)
- Headline: "Separation is tough, but it can be managed."
- 5 option buttons with arrow indicators, left accent bar on hover
- Each option routes to the correct intervention screen
- Single-select only (clicking one deselects others)

### EMOTIONAL screen
- Guided 5-minute check-in
- Click Start → instructions appear → "I'm ready" button → confirmation
- Leads to email capture

### CONFLICT screen — The Drama Triangle
- Cowboy-illustrated drama triangle image (embedded)
- Villain / Victim / Rescuer role buttons
- Dynamic follow-up question based on role selected
- Confirmation → email capture

### COMMUNICATION screen — Steady Response
Full 9-step guided flow:
1. Intro screen with Tactical Empathy illustration
2. See It (Active Listening)
3. Hold Frame (Mirroring)
4. Respond Clean (Labelling)
5. Input screen — paste her message
6. AI generates 3 calm response options (Claude API)
7. Response cards with Copy / Edit / Use This buttons
8. Edit screen with copy function
9. Done screen with Run Again option

### THOUGHTS screen — The 180 Method
- Write the thought
- Write the 180 version
- Choice buttons appear only after both fields filled
- Clearing a field hides the choice buttons again
- Confirmation → email capture

### ACTION screen — Escape and Cope Buckets
- Escape/Cope bucket illustration (embedded)
- 5 action input rows, each tagged Escape or Cope
- Requires at least one field filled before Done
- Confirmation → email capture

### Email capture
- Appears after every intervention
- Email field only
- Submits to Formspree (NOT YET CONNECTED — see below)
- Skip option available
- Done state shows after submit or skip

### Navigation
- "Start over" link on every screen
- Returns to landing, clears all state

---

## What is unfinished

### 1. Formspree not connected
Search for `PASTE_YOUR_FORMSPREE_ID_HERE` in the HTML and replace with your Formspree form ID.  
Go to [formspree.io](https://formspree.io) → create form → copy the ID.  
Example: `xpzgkwqr`

### 2. EMOTIONAL screen — no real audio
The 5-minute check-in shows breathing instructions as a placeholder. No audio file is connected to this screen in v2. The original `divorce-cowboy.html` has `intro.mp3` working.  
To add: embed the MP3 as base64 or host it externally and reference the URL.

### 3. Mobile not fully tested
The layout is designed mobile-first but has not been tested on an actual device. The landing hero (full-bleed image + two-column on desktop) may need padding adjustments on small screens.

### 4. File size is large
`divorce-cowboy-v2.html` is 847KB because all images are base64-embedded.  
If performance becomes an issue, extract images to separate files and reference by filename (requires hosting all files together, not just the HTML).

### 5. No thank-you redirect after email
After email submission the user sees "Done. Check your inbox." on the same screen. No redirect to a new page or external URL.

### 6. API key is exposed in the HTML
The Anthropic API key is embedded in the client-side HTML. This is functional but not secure for production. For a hardened version, move API calls to a Netlify Function or backend proxy.

### 7. Steady Response edit screen — no "done" flow
After editing and copying, the user can go back to options but there is no explicit "I sent it" confirmation loop (the sr7 "Good." screen is only reached via "Use this", not via the edit path).

---

## File structure

```
divorce-cowboy-v2.html   — Main app, self-contained, deploy this alone
divorce-cowboy.html      — Original quiz + exercise app (archived)
cowboy-hero.jpg          — Hero image (used in original, embedded in v2)
logo-white.png           — White skull wordmark logo
intro.mp3                — Voice intro audio (used in original only)
README.md                — Setup and deploy instructions
HANDOFF.md               — This file
```

---

## Known issues

| Issue | Severity | Fix |
|-------|----------|-----|
| Formspree not connected | High | Add form ID to HTML |
| No real audio on EMOTIONAL screen | Medium | Embed MP3 or link external audio file |
| API key in client HTML | Medium | Move to Netlify Function for production |
| File size 847KB | Low | Extract images to separate files if needed |
| Mobile untested | Medium | Test on iPhone and Android, adjust padding |
| Edit screen missing "Good." flow | Low | Add srUsed() call after copy in edit screen |

---

## Key variables in the code

| Variable | What it does |
|----------|--------------|
| `SR_KEY` | Anthropic API key for Steady Response |
| `KEY` | Anthropic API key (same key, used in original file) |
| `FID` | Formspree form ID — replace `PASTE_YOUR_FORMSPREE_ID_HERE` |
| `S` | Global state object tracking current route and answers |
| `srCurrentStep` | Tracks current step in Steady Response flow |

---

## Intervention screens and their states

| Screen | Entry option | State key |
|--------|-------------|-----------|
| EMOTIONAL | I'm on an emotional rollercoaster | `EMOTIONAL` |
| CONFLICT | There's a lot of drama, arguing and blame | `CONFLICT` |
| COMMUNICATION | I don't know how to communicate with her | `COMMUNICATION` |
| THOUGHTS | I'm overthinking, worried and can't sleep | `THOUGHTS` |
| ACTION | I'm using alcohol/drugs to numb the pain | `ACTION` |

---

## Design system

| Token | Value |
|-------|-------|
| Background | `#050403` |
| Accent / gold | `#C6A46C` |
| Primary text | `#EAEAEA` |
| Secondary text | `#B5B0A8` |
| Muted text | `#8F8A83` |
| Dim text | `#4A4540` |
| Heading font | Playfair Display (Google Fonts) |
| Body font | Inter (Google Fonts) |
| Primary button | `#C6A46C` background, `#050403` text |
| Card border | `rgba(198,164,108,.15)` |

---

## What to build next (suggested)

1. Connect Formspree — 10 minutes
2. Test on mobile — 30 minutes  
3. Add real audio to EMOTIONAL screen — 1 hour
4. Move API calls to Netlify Function for security — 2 hours
5. Add a "Your next step" follow-up email sequence (Mailchimp / ConvertKit)
6. Analytics — add simple event tracking (Plausible or Fathom, privacy-first)
