# 🔁 Automatic File Creation with GitHub Actions (Beginner Guide)

This guide walks you through setting up a GitHub Actions workflow that **automatically checks for a file** (e.g., `status.txt`) and creates it only if it does **not** exist. This is called an **idempotent setup** — meaning it doesn’t repeat actions if they were already done.

---

## ✅ What You'll Learn

- How to create a GitHub Actions workflow
- How to use `GITHUB_TOKEN` securely (no PAT needed)
- How to create a `status.txt` file only once
- How to make your workflow idempotent (safe to rerun)
- How to trigger workflows manually or on push

---

## 🔧 Prerequisites

- A GitHub repository (you can use a public or private one)
- Basic knowledge of Git (commit & push)

---

## 🚀 Step 1: Enable Workflow Write Access

1. Go to your repository → **Settings**
2. Click **Actions** → **General**
3. Scroll to **Workflow permissions**
4. Select ✅:  
   ```
   ✅ Read and write permissions
   ```
5. Click **Save**

📷 This allows the built-in GitHub Actions bot to commit and push changes.

---

## 📁 Step 2: Create the Workflow File

Create a new file in your repo:

```
.github/workflows/check-and-create-file.yml
```

Paste the following content:

```yaml
name: Demonstrate Idempotence (File Creation)

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  ensure-file-exists:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository code with write token
        uses: actions/checkout@v4
        with:
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Check if 'status.txt' already exists
        id: check_file
        run: |
          if [ -f status.txt ]; then
            echo "status.txt already exists. Skipping creation."
            echo "exists=true" >> "$GITHUB_OUTPUT"
          else
            echo "status.txt does NOT exist. Proceeding to create."
            echo "exists=false" >> "$GITHUB_OUTPUT"
          fi

      - name: Create and commit status.txt
        if: steps.check_file.outputs.exists == 'false'
        run: |
          echo "This file indicates the initial setup is complete." > status.txt
          git config user.name "github-actions[bot]"
          git config user.email "github-actions[bot]@users.noreply.github.com"
          git add status.txt
          git commit -m "feat: Add status.txt as part of idempotent setup"
          git push
```

✅ **What it does**:
- Checks if `status.txt` exists
- If not, creates it, commits it, and pushes it to `main` branch
- If already exists, it does nothing

---

## 🔄 Step 3: Run the Workflow

You have two ways to run it:

### 🔘 Option 1: Push to `main`
Make any change in the repository and push it:

```bash
git add .
git commit -m "Trigger workflow"
git push origin main
```

### 🧑‍💻 Option 2: Run Manually

1. Go to your **repo on GitHub**
2. Click the **Actions** tab
3. Find your workflow called **"Demonstrate Idempotence..."**
4. Click **Run workflow** → Select `main` → ✅ **Run**

The workflow will run, and `status.txt` will appear in your repo!

---

## 🌐 Confirm That It Worked

Go to your **Code** tab and check if:
```
status.txt
```
was added with this content:

```
This file indicates the initial setup is complete.
```

If you re-run the workflow, it will **not** create it again — because it's already there 👏

---

## 🧠 Bonus: What Is Idempotence?

> **Idempotent workflows** only perform an action once, no matter how many times they run.

That’s ideal for:
- Setup files (like `.env`, `status.txt`, etc.)
- One-time initializations
- Clean + safe automation

---

## 🧼 Optional Cleanup

When you no longer need the auto-create logic, you can:
- Delete or comment out the workflow file
- Keep it if you plan future auto-setup steps!

---

## 📚 Need More Ideas?

This pattern is perfect for:
- Auto generating `.env.example` or config templates
- Creating documentation files
- Initializing folders or boilerplates
- Applying this concept to multiple files

---

## 💬 Credits & Support

Created for educational purposes and beginner automation ✨  
If you liked this, feel free to ⭐️ the repo and share it!

Need help? Open an issue in the repo.

Good luck and happy GitHub-ing! 💻🚀
