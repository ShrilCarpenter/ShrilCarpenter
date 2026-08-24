# GitHub Profile Setup Guide

This guide walks you through activating your automated GitHub Profile README for **@ShrilCarpenter**.

---

## Step 1: Create the Magic Repository

1. Go to **[github.com/new](https://github.com/new)**
2. Set **Repository name**: `ShrilCarpenter` (identical to your username)
   - *GitHub will show: "✨ You found a secret! ShrilCarpenter/ShrilCarpenter is a special repository... ✨"*
3. Select **Public** *(Required: private repos will cause all profile images to show broken for visitors)*
4. **Do NOT** initialize with README / .gitignore / license (you are pushing the existing local files)
5. Click **Create repository**

---

## Step 2: Enable Workflow Write Permissions

1. Open your new `ShrilCarpenter` repo on GitHub
2. Go to **Settings** → **Actions** → **General**
3. Scroll down to **Workflow permissions**
4. Select **Read and write permissions**
5. Click **Save**

---

## Step 3: Add `METRICS_TOKEN` Secret

The `lowlighter/metrics` workflow requires a Personal Access Token (Classic) to fetch your full contribution calendar and achievement badges:

1. Go to **[github.com/settings/tokens](https://github.com/settings/tokens)** → **Generate new token (classic)**
2. Set **Note**: `METRICS_TOKEN`
3. Set **Expiration**: e.g., 90 days or No expiration
4. Check scopes:
   - `read:user`
   - `repo` *(optional, if you want private contributions included in counts)*
5. Click **Generate token** and **copy the token string**
6. Back in your `ShrilCarpenter` repository:
   - Go to **Settings** → **Secrets and variables** → **Actions**
   - Click **New repository secret**
   - Name: `METRICS_TOKEN`
   - Value: paste the token
   - Click **Add secret**

---

## Step 4: Push to GitHub

In your PowerShell / terminal inside this repository:

```powershell
git remote add origin https://github.com/ShrilCarpenter/ShrilCarpenter.git
git branch -M main
git push -u origin main
```

---

## Step 5: Trigger First Workflow Runs

1. Go to the **Actions** tab on your GitHub repository.
2. If GitHub shows a banner *"Workflows aren't running on this repository"*, click **Enable workflows**.
3. For each of the three workflows:
   - **Charts and cards** (`radar.yml`): Click → **Run workflow**
   - **Snake** (`snake.yml`): Click → **Run workflow**
   - **Metrics** (`metrics.yml`): Click → **Run workflow**
4. Wait 1–2 minutes for the initial runs to complete green.
5. Visit your profile at **[github.com/ShrilCarpenter](https://github.com/ShrilCarpenter)**!

---

## Automated Refresh Schedule

Your profile will now maintain and regenerate itself automatically:
- **Metrics** (Isometric calendar, languages, badges): Every 6 hours
- **Snake** (Contribution graph eating animation): Every 12 hours
- **Charts & Cards** (Radars, stat card, project cards): Daily at 03:30 UTC
