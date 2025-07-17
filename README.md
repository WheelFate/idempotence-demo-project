# 🚀 Idempotence Demo Project

[![Auto File Creation](https://github.com/WheelFate/idempotence-demo-project/actions/workflows/check-and-create-file.yml/badge.svg)](https://github.com/WheelFate/idempotence-demo-project/actions/workflows/check-and-create-file.yml)

[![Setup Project Files](https://github.com/WheelFate/idempotence-demo-project/actions/workflows/setup-files.yml/badge.svg)](https://github.com/WheelFate/idempotence-demo-project/actions/workflows/setup-files.yml)

A GitHub Actions-powered automation project that safely creates required files (like `status.txt`, `.env.example`, and `config.json`) **only if they don't exist**.

Perfect for learning:
- Idempotent workflows
- Multi-file automation
- First-time project setup
- Beginner-friendly CI/CD

---

## 📘 About

**Idempotence Demo Project** is a step-by-step GitHub Actions project that automates **creating missing files**, only when they’re needed — ensuring clean git history and avoiding redundant commits.

This project walks you through:
- ✅ Creating files using GitHub Actions
- ✅ Using `GITHUB_TOKEN` to commit and push
- ✅ Workflow permission setup tips
- ✅ Expanded automation and modular logic
- ✅ Low-code beginner onboarding

---

## 📁 Project Structure

```
.
├── .github/
│   └── workflows/
│       ├── check-and-create-file.yml    # Creates `status.txt` once (basic)
│       └── setup-files.yml              # Creates multiple files if missing (advanced)
├── status.txt                           # Auto-generated setup marker
├── .env.example                         # Environment template (if missing)
├── config.json                          # Basic config file (if missing)
├── guide.md                             # For beginners to replicate the setup
├── README.md                            # Project overview and usage
└── LICENSE                              # MIT License
```

---

## 🧠 How It Works

### ✅ Basic Workflow (`check-and-create-file.yml`)

- Triggers on push or manual run
- If `status.txt` doesn't exist, it creates and pushes it
- Otherwise, does nothing

### ⚡ Advanced Workflow (`setup-files.yml`)

- Checks for 3 critical files:
  - `status.txt`
  - `.env.example`
  - `config.json`
- Only creates missing files (preserves existing ones)
- Commits once with all new files
- Keeps your repo clean and idempotent!

```
📦 Push or Manual Trigger
   ⬇️
🔍 Check what files are missing
   ⬇️
📄 Only create missing files
   ⬇️
📤 One commit + push
```

---

## 🛠️ Setup

**No install required!** Just:

1. Fork or clone this repo
2. Go to `Settings > Actions > General`
3. Enable:
   ```
   ✅ Read and write permissions
   ```
4. Push to `main` or run workflows manually

🏁 First run will auto-generate any missing setup files.

---

## 🔄 How to Run

### Option 1: Push to `main`

```bash
git add .
git commit -m "Trigger workflows"
git push origin main
```

### Option 2: Manually from GitHub

1. Go to your repo → **Actions**
2. Select either workflow:
   - "Demonstrate Idempotence (File Creation)" ✅
   - "Setup Project Files (Idempotent Multi-File)" ⚡
3. Click **Run workflow** → Select `main` → Press ✅ "Run"

---

## 🌟 What Gets Created?

| File            | Condition                        | Purpose                                |
|-----------------|----------------------------------|----------------------------------------|
| `status.txt`     | Created if not found             | Marks first-time setup completed       |
| `.env.example`   | Created if not found             | Template for app environment configs   |
| `config.json`    | Created if not found             | Base config for initializing software  |

All content is customizable in the workflow.

---

## 📸 Preview (Optional)

| ✅ Workflow Success | 📝 Files Created |
|--------------------|-----------------|
| ![Action](assets/workflow-success.png) | ![Files](assets/files-created.png) |

> Upload screenshots to an `/assets` folder and update the links above

---

## 🎯 Learning Goals

- Show how to create idempotent infrastructure setup
- Teach beginners how to commit safely from Actions
- Automate templated setups across teams
- Avoid duplicate commits with clean logic

---

## 🤝 Contributing

Contributions are welcome! ⚙️  
You're invited to:

- Improve the guide or structure
- Add more file creation logic
- Add validation/lint steps
- Localize the guide into other languages

Open [issues](https://github.com/WheelFate/idempotence-demo-project/issues) or [pull requests](https://github.com/WheelFate/idempotence-demo-project/pulls) anytime!

---

## 🧪 Coming Soon (Roadmap)

- ✨ `workflow_dispatch` inputs to define dynamic file content  
- ✨ Zip + upload generated files as artifacts  
- ✨ Deploy guide site via GitHub Pages  
- ✨ Add matrix builds to test across repos

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

Enjoy it, fork it, share it!

---

## 🙌 Special Thanks

Thanks to the awesome GitHub Actions community and everyone learning CI/CD through real demos like this one.  
Drop a ⭐ if you found this helpful!
