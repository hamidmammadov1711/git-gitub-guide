**✅ Tam Professional Git + GitHub Dokumentasiyası (2026 versiyası)**  
Bu sənəd **terminaldan, VS Code-dan, WebStorm-dan, PyCharm-dan və ya hər hansı digər IDE-dən** istifadə edərək **heç bir detalı atmadan** Git və GitHub işlərini öyrənmək üçün hazırlanıb.

### Mündəricat

1. Giriş və Terminlər  
2. Quraşdırma və İlk Konfiqurasiya  
3. Lokal Repozitoriya Yaradılması  
4. Layihəni GitHub-a İlk Dəfə Yükləmə (tam addım-addım)  
5. Mövcud Layihəni GitHub-dan Yükləmə (Clone)  
6. Ən Çox İstifadə Olunan Əmrlər (Cheat Sheet)  
7. Branching və Pull Request (PR)  
8. Dəyişikliklərin Sinxronizasiyası (Push / Pull / Fetch)  
9. Konfliktlərin həlli  
10. .gitignore və fayl idarəsi  
11. VS Code + IDE-lərdə Git (ən rahat yol)  
12. GitHub CLI (`gh`) – 2026-da ən sürətli yol  
13. SSH quraşdırması (tövsiyə olunur)  
14. Best Practices və Təhlükəsizlik  
15. Tez-tez rast gəlinən problemlər və həlləri  

---

### 1. Giriş və Terminlər

- **Git** – lokal versiya nəzarət sistemi (kompüterinizdə işləyir)  
- **GitHub** – uzaq server (remote) – kodunuzu saxlayır, komanda ilə işləməyə imkan verir  
- **Repository (Repo)** – layihə qovluğu  
- **Main / Master** – əsas branch (2026-cı ildə **main** standartdır)  
- **Commit** – dəyişikliklərin “şəkil”i  
- **Push** – lokal dəyişiklikləri GitHub-a göndərmək  
- **Pull** – GitHub-dakı dəyişiklikləri yerli kompüterə gətirmək  

---

### 2. Quraşdırma və İlk Konfiqurasiya (bir dəfə edilir)

**Terminalda (Git Bash, PowerShell, Terminal, VS Code Terminal):**

```bash
# Git quraşdırılıb-yoxlanılır
git --version

# İstifadəçi məlumatları (mütləq!)
git config --global user.name "Sizin Adınız Soyadınız"
git config --global user.email "emailiniz@gmail.com"

# Default branch-ı main et
git config --global init.defaultBranch main

# Editor seçimi (VS Code istifadə edirsinizsə)
git config --global core.editor "code --wait"
```

**VS Code-da**:

- `Ctrl + Shift + P` → “Git: Enable” axtarın → aktiv edin.

---

### 3. Lokal Repozitoriya Yaradılması

```bash
cd /path/to/your/project
git init                  # yeni repo yaradır
git status                # status yoxlamaq
```

---

### 4. Layihəni GitHub-a İlk Dəfə Yükləmə (Ən Ətraflı Addım-addım)

#### Addım 1: GitHub-da repo yarat

1. github.com → New repository  
2. Repository name: `my-awesome-project`  
3. Description (istəyə görə)  
4. **Public / Private** seç  
5. **Add a README file** → **İŞARƏT QOYMAYIN!**  
6. **Create repository**

#### Addım 2: Terminalda

```bash
cd my-awesome-project

git init
git add .                    # bütün faylları əlavə et (və ya git add -A)
git commit -m "Initial commit"

# Remote əlavə et (HTTPS)
git remote add origin https://github.com/istifadeci-adi/my-awesome-project.git

# Əgər branch main deyilsə
git branch -M main

# İlk push
git push -u origin main
```

**SSH ilə daha rahat (tövsiyə olunur):**

```bash
git remote set-url origin git@github.com:istifadeci-adi/my-awesome-project.git
git push -u origin main
```

---

### 5. Mövcud Layihəni GitHub-dan Yükləmə (Clone)

```bash
git clone https://github.com/istifadeci-adi/proyekt-adi.git
# və ya SSH
git clone git@github.com:istifadeci-adi/proyekt-adi.git
```

---

### 6. Ən Çox İstifadə Olunan Əmrlər (Cheat Sheet)

| Əmr | Mənası | Tez-tez istifadə |
|-----|--------|------------------|
| `git status` | Cari vəziyyət | hər dəfə |
| `git add .` | Bütün dəyişiklikləri stage et | ən çox |
| `git add fayl.txt` | Tək faylı stage et | — |
| `git commit -m "mesaj"` | Commit et | ən çox |
| `git commit -am "mesaj"` | add + commit (izlənilən fayllar) | tez-tez |
| `git push` | GitHub-a göndər | ən çox |
| `git pull` | GitHub-dan çək | ən çox |
| `git fetch` | Dəyişiklikləri gör, amma çəkmə | — |
| `git log --oneline` | Commit tarixçəsi | — |
| `git log --graph --all` | Şəkilli tarixçə | — |
| `git branch` | Branch-ləri göstər | — |
| `git branch yeni-ozellik` | Yeni branch yarat | — |
| `git checkout yeni-ozellik` | Switch et (köhnə) | — |
| `git switch yeni-ozellik` | Yeni komanda (2026 tövsiyə) | ən yaxşı |
| `git checkout -b yeni-ozellik` | Yarat + switch | ən çox |
| `git merge feature-branch` | Merge et | — |
| `git rebase main` | Rebase (təmiz tarixçə) | — |
| `git stash` | Dəyişiklikləri müvəqqəti saxla | — |
| `git stash pop` | Geri qaytar | — |
| `git reset --hard HEAD~1` | Son commit-i sil (ehtiyatla!) | — |
| `git restore fayl.txt` | Faylı əvvəlki vəziyyətə qaytar | — |

---

### 7. Branching və Pull Request (PR)

```bash
git switch -c feature/login-page     # yeni branch
# ... kod yazırsan ...
git add .
git commit -m "feat: add login page"
git push -u origin feature/login-page
```

**GitHub-da:**

1. Repo → Pull requests → New pull request  
2. `feature/login-page` → `main`  
3. Review + Merge

---

### 8. Sinxronizasiya

```bash
git pull origin main                 # ən təhlükəsiz
# və ya
git fetch origin
git merge origin/main
```

---

### 9. Konfliktlərin həlli

VS Code avtomatik açır → hansı dəyişikliyi saxlayacağınızı seçin → `Accept Current Change` / `Accept Incoming Change`.

Terminalda:

```bash
git mergetool   # və ya əl ilə redaktə et
git add .
git commit      # mesaj olmadan (merge commit)
```

---

### 10. .gitignore (vacib!)

Layihə qovluğunda `.gitignore` faylı yaradın:

```gitignore
# Node.js
node_modules/
dist/
.env

# Python
__pycache__/
venv/
*.pyc

# VS Code
.vscode/
*.code-workspace

# OS
.DS_Store
Thumbs.db
```

---

### 11. VS Code-da Git (Ən Rahat Yol)

- Sol panel → **Source Control** (üçüncü ikon)  
- Dəyişikliklər avtomatik görünür  
- Stage → Commit → Sync (Pull + Push bir düymədə)  
- `GitLens` extension (mütləq quraşdırın!) – tarixçə, blame, PR inteqrasiyası

**VS Code Command Palette (Ctrl+Shift+P)** ilə:

- `Git: Commit`  
- `Git: Push`  
- `Git: Pull`  
- `Git: Create Branch`  
- `Git: Checkout to...`

---

### 12. GitHub CLI (`gh`) – 2026-cı ildə ən sürətli

```bash
# Quraşdırma (bir dəfə)
# Windows: winget install --id GitHub.cli
# Mac: brew install gh
# Linux: sudo apt install gh

gh auth login
gh repo create my-project --public --source=. --remote=origin --push
gh pr create --fill
gh pr merge
```

---

### 13. SSH Quraşdırması (Tövsiyə olunan)

```bash
ssh-keygen -t ed25519 -C "emailiniz@gmail.com"
# Enter → Enter → Enter

cat ~/.ssh/id_ed25519.pub     # copy edin

# GitHub → Settings → SSH and GPG keys → New SSH key → yapışdırın
```

---

### 14. Best Practices (Professional Səviyyə)

- Hər kiçik funksiya üçün ayrı branch  
- Commit mesajları: `type: description` (feat:, fix:, docs:, refactor:)  
- `main` branch-ı **heç vaxt** birbaşa redaktə etmə  
- Hər gün `git pull` et  
- `.env` faylını heç vaxt commit etmə  
- `git rebase` istifadə et (təmiz tarixçə üçün)

---

### 15. Tez-tez Problemlər və Həlləri

| Problem | Həll |
|--------|------|
| `fatal: not a git repository` | `git init` et və ya `cd` düzgün qovluğa |
| `Permission denied` | SSH istifadə et və ya PAT yarat |
| `Updates were rejected` | `git pull --rebase` sonra `git push` |
| `main` branch-ı silmək istəyirəm | `git branch -M main` |
| `Everything up-to-date` amma GitHub-da yoxdur | `git push -u origin main --force-with-lease` (ehtiyatla) |

---

**Bu dokumentasiya tam olaraq “əlimin altında” olsun deyə** Markdown formatındadır. İstəsəniz onu `.md` faylı kimi yadda saxlaya bilərsiniz və ya VS Code-da açaraq axtarış edə bilərsiniz.

---