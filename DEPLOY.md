# Deploying Humanizer to Render.com

## What you need
- A GitHub account (free)
- A Render.com account (free)
- Your Anthropic API key (from console.anthropic.com)

---

## Step 1 — Push to GitHub

1. Go to github.com → New repository
2. Name it `humanizer`, set to **Private**, click Create
3. On your machine, open Terminal and run:

```bash
cd humanizer
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/YOUR_USERNAME/humanizer.git
git push -u origin main
```

---

## Step 2 — Deploy on Render

1. Go to **render.com** → Sign up (free)
2. Click **New +** → **Web Service**
3. Connect your GitHub account → select the `humanizer` repo
4. Fill in:
   - **Name:** humanizer (or anything)
   - **Runtime:** Node
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Instance Type:** Free
5. Click **Advanced** → **Add Environment Variable**:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your API key (starts with `sk-ant-...`)
6. Click **Create Web Service**

Render builds and deploys in ~2 minutes.

---

## Step 3 — Share with your team

Render gives you a permanent URL like:
```
https://humanizer-xxxx.onrender.com
```

Send that URL to your team. Done. No login required.

---

## Notes

- Free tier on Render spins down after 15 mins of inactivity — first load after idle takes ~30 seconds to wake up. Upgrade to $7/month instance to avoid this.
- Your API key stays server-side — never exposed to the browser.
- Usage costs come from your Anthropic account (roughly $0.003 per humanize request on Sonnet).
