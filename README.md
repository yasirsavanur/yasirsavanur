# First GitHub Commit on macOS (Using SSH)

This guide walks you through your first GitHub commit on macOS using SSH.  
It is written for beginners and focuses on clarity rather than memorisation.

---

## Part 1: One-time setup (SSH)

### 1. Check that Git is installed
Run:
```bash
git --version
```
This confirms that Git is available on your Mac.

---

### 2. Check if you already have an SSH key
Run:
```bash
ls ~/.ssh
```
If you see `id_ed25519` and `id_ed25519.pub`, you already have a key pair and can skip to step 4.

---

### 3. Create a new SSH key
Run:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Press Enter to accept the default file location.  
You can skip the passphrase or set one if you prefer.

This creates:
- `id_ed25519` (private key, keep secret)
- `id_ed25519.pub` (public key, safe to share)

---

### 4. Start the SSH agent and add your key
Run:
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
This allows your system to use the SSH key automatically.

---

### 5. Copy your public key
Run:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```
This copies your public key to the clipboard.

---

### 6. Add the SSH key to GitHub
GitHub → Settings → SSH and GPG keys → New SSH key  
Paste the key and save.

---

### 7. Test the SSH connection
Run:
```bash
ssh -T git@github.com
```
Type `yes` if asked to trust GitHub.  
You should see a successful authentication message.

---

## Part 2: First commit

### 8. Go into your project folder
Run:
```bash
cd /path/to/your/project
```

---

### 9. Initialise Git
Run:
```bash
git init
```

---

### 10. Check repository status
Run:
```bash
git status
```

---

### 11. Create a `.gitignore` file (recommended)
Add common junk files:
```text
.DS_Store
.ipynb_checkpoints/
.env
```

---

### 12. Add files to staging
Run:
```bash
git add .
```

---

### 13. Make your first commit
Run:
```bash
git commit -m "Initial commit"
```

---

### 14. Rename branch to `main`
Run:
```bash
git branch -M main
```

---

## Part 3: Connect to GitHub

### 15. Create a new empty repository on GitHub
Do not add a README or other files yet.

---

### 16. Add GitHub as a remote using SSH
Run:
```bash
git remote add origin git@github.com:username/repo.git
```

---

### 17. Push your code
Run:
```bash
git push -u origin main
```

---

## After this

Your normal workflow:
```bash
git add .
git commit -m "Describe changes"
git push
```

After the initial setup, pushing code becomes simple and quiet.
