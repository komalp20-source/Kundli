# Kundli Agent — 7-Layer Vedic Astrology

AI-powered Vedic astrology agent using the 7-layer Jyotish interpretive model. Reads D9, D10, and D12 divisional charts from images (North Indian and South Indian formats). Powered by Claude.

## Features

- 7-layer Vedic astrology model (Foundational Trinity → Full Synthesis)
- 8 life topic modules: Marriage, Career, Money, Health, Future, Doshas, Children, Dharma
- D9 / D10 / D12 image reading — trained on both North Indian and South Indian chart formats
- 3-page flow: chart data → divisional chart uploads → agent dashboard
- Response format: What's happening → What to do → Why (astrological reasoning)

## Deployment (Netlify)

### Step 1 — Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/kundli-agent.git
git push -u origin main
```

### Step 2 — Deploy on Netlify

1. Go to [netlify.com](https://netlify.com) and sign up / log in
2. Click **Add new site → Import an existing project**
3. Connect your GitHub account and select the `kundli-agent` repo
4. Build settings are auto-detected from `netlify.toml` — no changes needed
5. Click **Deploy site**

### Step 3 — Add your Anthropic API key

1. In Netlify, go to **Site configuration → Environment variables**
2. Click **Add a variable**
3. Key: `ANTHROPIC_API_KEY`
4. Value: your Anthropic API key (get one at [console.anthropic.com](https://console.anthropic.com))
5. Click **Save**
6. Go to **Deploys → Trigger deploy → Deploy site** to redeploy with the key

### Step 4 — Share

Your site will be live at `https://YOUR-SITE-NAME.netlify.app`

You can set a custom domain in **Domain management** if needed.

## Local Development

```bash
npm install -g netlify-cli
netlify dev
```

Then open `http://localhost:8888`

Set your API key locally:
```bash
echo "ANTHROPIC_API_KEY=your_key_here" > .env
```

## Project Structure

```
kundli-agent/
  index.html              # Full agent — single page app
  netlify.toml            # Netlify config + routing
  netlify/
    functions/
      claude.js           # API proxy — keeps API key secure
  README.md
```

## Chart Reading — Trained Rules

### North Indian (diamond format)
- Rashi numbers in cells (1-12) are sign numbers, not house numbers
- Find "Asc" marker → that Rashi = House 1
- If no Asc → top-center cell = House 1
- Count forward sequentially, wrap 12→1

### South Indian (4x4 grid format)
- Rashi numbers same as above
- Find cut corner (diagonal line) → that Rashi = House 1
- If no cut corner → top-left cell = House 1
- Count clockwise sequentially, wrap 12→1

### Rashi → Sign mapping
1=Aries 2=Taurus 3=Gemini 4=Cancer 5=Leo 6=Virgo
7=Libra 8=Scorpio 9=Sagittarius 10=Capricorn 11=Aquarius 12=Pisces

## The 7-Layer Model

| Layer | Focus |
|---|---|
| 1 | Foundational Trinity: Lagna, lagna lord, Moon sign |
| 2 | Planetary Strength: dignity, avastha, combustion, retrograde |
| 3 | Nakshatra Analysis: birth nakshatra, lord, sub-lord, pada |
| 4 | Divisional Charts: D9 Navamsa, D10 Dasamsa, D12 Dvadasamsa |
| 5 | Yoga Identification: all major yogas and activation conditions |
| 6 | Dasha Timing: yoga-to-dasha mapping, current period |
| 7 | Full Synthesis: integrated life-narrative and life-shape |
