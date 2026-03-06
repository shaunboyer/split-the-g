# Deploy "Split the G" to Render

## Prerequisites
- [Git](https://git-scm.com/) installed
- A [GitHub](https://github.com) account
- A [Render](https://render.com) account (free)
- _(Optional)_ [GitHub CLI (`gh`)](https://cli.github.com/) for one-liner repo creation

---

## Step 1 — Set up the project folder

Open your terminal and run:

```bash
# Move the game folder somewhere permanent (e.g. your home directory)
cd ~
mkdir split-the-g
# Copy index.html into ~/split-the-g/ from wherever you saved it
```

---

## Step 2 — Initialise Git and make your first commit

```bash
cd ~/split-the-g

git init
git add index.html
git commit -m "Initial commit: Split the G game"
```

---

## Step 3 — Push to GitHub

### Option A — GitHub CLI (easiest)
```bash
# Log in once if you haven't already
gh auth login

# Create a public repo and push in one command
gh repo create split-the-g --public --source=. --remote=origin --push
```

### Option B — Manually via GitHub.com
1. Go to https://github.com/new
2. Name it `split-the-g`, set to Public, click **Create repository**
3. Back in your terminal:
```bash
git remote add origin https://github.com/YOUR_USERNAME/split-the-g.git
git branch -M main
git push -u origin main
```

---

## Step 4 — Deploy on Render

1. Go to **https://render.com** and sign in
2. Click **New +** → **Static Site**
3. Connect your GitHub account and select the `split-the-g` repo
4. Fill in the settings:
   | Field | Value |
   |---|---|
   | Name | `split-the-g` (or anything you like) |
   | Branch | `main` |
   | Build Command | *(leave empty)* |
   | Publish Directory | `.` |
5. Click **Create Static Site**

Render will deploy in ~30 seconds. Your site will be live at:
```
https://split-the-g.onrender.com
```
(or similar — Render shows the URL on the dashboard)

---

## Updating the site later

Any time you change `index.html`, just push and Render auto-deploys:

```bash
git add index.html
git commit -m "Update game"
git push
```
