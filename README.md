# 🚀 Idempotence Demo Project

![Setup Files](https://github.com/WheelFate/idempotence-demo-project/actions/workflows/setup-files.yml/badge.svg)
![License](https://img.shields.io/github/license/WheelFate/idempotence-demo-project)
![Repo Stars](https://img.shields.io/github/stars/WheelFate/idempotence-demo-project?style=social)

A simple GitHub Actions demo that automatically checks for a file (`status.txt`) and creates it only if it doesn't exist — a real-world example of **idempotent automation** using built-in GitHub tools.

---

## 📘 About

**Idempotence Demo Project** is a beginner-friendly GitHub Actions example that demonstrates how to:

- Automatically create a file like `status.txt` only once
- Safely commit & push using `GITHUB_TOKEN`
- Use idempotent workflows that don't repeat completed tasks
- Trigger workflows manually or via pushes

✨ Whether you're a GitHub Actions beginner or teaching others — this repo is your go-to!

---

## 📁 Project Structure

```
.
├── .github/
│   └── workflows/
│       └── check-and-create-file.yml  # The GitHub Actions workflow
├── status.txt                         # Automatically created file (if not exists)
├── guide.md                           # Step-by-step setup for beginners
├── README.md                          # This file 📚
└── LICENSE                            # MIT License
```

---

## 🧠 How It Works

- ✅ On push to the `main` branch or manual trigger:
- 🔍 Checks if the file `status.txt` exists
- 🛠️ If missing, creates and commits it
- 💾 If exists, skips creation (idempotent logic!)

```text
📥 Push or Manual Trigger
   ⬇️
📂 Check: status.txt exists?
   ✔️ Yes → Skip
   ❌ No → Create → Commit → Push
```

---

## 🛠️ Setup

Anyone can use this!

1. **Fork or clone** this repo
2. Go to `Settings > Actions > General`
3. Under **Workflow Permissions**, select:
   ```
   ✅ Read and write permissions
   ```
4. Push to `main` or run the action manually

> After the first run, `status.txt` will be created if it doesn't exist.

---

## 🔄 How to Run

### Option 1: Trigger Automatically
Pushing to the `main` branch activates the workflow:

```bash
git add .
git commit -m "Test auto-create workflow"
git push origin main
```

### Option 2: Run Manually
On GitHub:
1. Click the **Actions** tab
2. Open **"Demonstrate Idempotence (File Creation)"**
3. Click **Run Workflow** → Choose `main` → ✅ Confirm

---

## 📸 Preview (Optional – Add Screenshots Here)

| ✅ Successful Action | 📄 File Created |
|---------------------|----------------|
| ![Action Success](assets/action-success.png) | ![File](assets/file-created.png) |

> You can remove or update this section — store screenshots in a folder like `/assets`.

---

## 🎯 Project Goals

- Teach GitHub Actions to beginners
- Automate initial project setup tasks (file creation)
- Provide reusable workflow patterns
- Promote clean, idempotent CI/CD practices

---

## 🤝 Contributing

Contributions are welcome! 🙌  
Feel free to:

- Improve this guide
- Translate content
- Add new automation use cases
- Submit issues or ideas

👉 Just [fork the repo and send a pull request](https://github.com/WheelFate/idempotence-demo-project/pulls)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).  
You are free to use, modify, and distribute with attribution.

---

## 🙌 Acknowledgements

Built with ❤️ to help others learn GitHub Actions by example.

Give the repo a ⭐ if you like it and want more examples coming!
