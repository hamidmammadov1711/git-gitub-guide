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
| `git branch yeni-funksiyana` | Yeni branch yarat | — |
| `git checkout yeni-funksiyana` | Switch et (köhnə) | — |
| `git switch yeni-funksiyana` | Yeni komanda (2026 tövsiyə) | ən yaxşı |
| `git checkout -b yeni-funksiyana` | Yarat + switch | ən çox |
| `git merge xususiyyət-qolu` | Merge et | — |
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

#### 14.1 Branch Strategiyası

- **Hər funksiya = ayrı branch** (məs., `feature/user-auth`, `bugfix/login-timeout`)
- **Branch adlandırma konvensiyası:**
    - `feature/` – yeni funksiyalar
    - `bugfix/` və ya `fix/` – bug düzəlişləri
    - `hotfix/` – fövqəladə istehsal düzəlişləri (`main`-dən branch et)
    - `docs/` – dokumentasiya yeniləmələri
    - `refactor/` – kod təmizliyi, heç bir davranış dəyişikliyi

```bash
# Yaxşı branch adları
git switch -c feature/dark-mode
git switch -c bugfix/cart-calculation-error
git switch -c hotfix/security-vulnerability

# Qaçın
git switch -c my-stuff              # çox qeyri-müəyyən
git switch -c feature123            # kontekst yoxdur
git switch -c WIP                   # heç vaxt bunu işlətməyin
```

- **`main` branch-ı qoruyun:**
    - Merge etməzdən əvvəl pull request review-u tələb et
    - Ən azı 1-2 approve tələb et
    - `main`-ə birbaşa push-u blok et
    - Statusu yoxlamalar keçməsini tələb et (CI/CD)

#### 14.2 Commit Intizamı

- **Commit mesaj formatı** (Conventional Commits):
    ```
    type(scope): description
    
    *niyə* izah edən isteğe bağlı mətn
    ```

```bash
# Yaxşı commitlər
git commit -m "feat(auth): add two-factor authentication"
git commit -m "fix(api): resolve timeout on user endpoint"
git commit -m "docs: update installation instructions"
git commit -m "refactor(db): optimize query performance"

# Pis commitlər
git commit -m "fixes stuff"         # qeyri-müəyyən
git commit -m "asdfgh"              # mənasız
git commit -m "work in progress"    # tamamlanmamış
```

- **Commit ölçüsü qiymətləndirmə:**
    - Kiçik, atomik commitlər (bir məntiqi dəyişiklik hər commit-ə)
    - Hər commit-ə maksimum ~5-10 fayl
    - 50+ fayllı "böyük pərtilatma" commitlərindən çəkinyin

- **Commit tezliyi:**
    - Kiçik bir tapşırığı tamamladıqdan sonra commit et
    - Hər feature branch-ı üçün 3-5 commit hədəfi
    - Funksiya "tamamlanana" qədər commit-i gözləməyin

```bash
# Işi məntiqi commitlərə bölün
git add src/auth.js
git commit -m "feat(auth): create login form"

git add src/api.js
git commit -m "feat(auth): add API authentication endpoint"

git add tests/auth.test.js
git commit -m "test(auth): add unit tests for login"
```

#### 14.3 Kod Review Prosesi

- **Pull Request gözləntıləri:**
    - Açıq PR başlığı və təsviri yazın
    - Əlaqəli problemləri bağlayın: "Closes #123"
    - PR-ləri kiçik saxlayın (~300-500 sətir maksimum)
    - Merge etməzdən əvvəl ən azı 1 approve gözləyin

```markdown
# PR Təsviri Nümunəsi

## Bu PR nə edir?
E-poçt vasitəsilə istifadəçi parol sıfırlaması funksiyasını tətbiq edir.

## Niyə?
#456-ı bağlayır - İstifadəçilər itirmiş parolları bərpa etməyin yoluna ehtiyac duyurlar.

## Necə test etmə?
1. /forgot-password-a gedin
2. E-poçt ünvanını daxil edin
3. E-poçtda sıfırlama keçidini yoxlayın
4. Keçidi izləyin və yeni parol təyin edin

## Screenshotlar
[Tətbiq olunursa, screenshotlar əlavə edin]
```

- **Review çek siyahısı:**
    - ✅ Kod oxunuqdur və layihə stilinə uyğundur
    - ✅ Heç bir debug loqu və ya şərh edilmiş kod qalmayıb
    - ✅ Testlər yazılıb və keçib
    - ✅ Açıq API-ə dəyişiklik yoxdur
    - ✅ Performans təsiri qəbul edilən

#### 14.4 Təhlükəsizlik & Sirrlər

- **Heç vaxt sırları commit etməyin:**
    ```bash
    # .gitignore-ya əlavə edin
    .env
    .env.local
    *.pem
    *.key
    secrets/
    ```

- **Təsadüfən sirr commit etsəniz:**
    ```bash
    # Dərhal sırrı yeniləyin (yeni parol, yeni API açarı)
    # Sonra Git tarixçəsini təmizləyin:
    git log --oneline | grep "secret"
    git rebase -i <secret-əvvəlki-commit>
    # "secret commit"-i 'drop' işarə et
    # Güclü push et (ehtiyatla):
    git push origin feature-branch --force-with-lease
    ```

- **Sərt kodlaşdırılmış dəyərlər əvəzinə mühit dəyişənlərindən istifadə edin:**
    ```javascript
    // Pis
    const API_KEY = "sk-1234567890abcdef";
    
    // Yaxşı
    const API_KEY = process.env.API_KEY;
    ```

- **Komandasız sırlar adasında menecerindən istifadə edin:**
    - GitHub Secrets (CI/CD üçün)
    - HashiCorp Vault
    - Azure Key Vault
    - AWS Secrets Manager

#### 14.5 Əməkdaşlıq Nümunələri

- **Push etməzdən əvvəl pull et:**
    ```bash
    git pull origin main
    git push origin feature-branch
    ```

- **Hər gün main ilə sinxronizasiya edin** (uzun müddətli branch-da işləyirsinizsə):
    ```bash
    git fetch origin
    git rebase origin/main
    # və ya
    git merge origin/main
    ```

- **Silo-dan çəkinyin** – Slack yerinə PR təsvirləri vasitəsilə kommunikasiya qurun
- **Merged PR-ləri review edin** – Komanda yoldaşlarının kodundan öyrənin
- **Tez kömək istəyin** – İş əsasında draft PRs istifadə edin

```bash
# Draft PR yaradın (GitHub CLI)
gh pr create --draft
```

#### 14.6 Tarixçə Təmizliyi

- **Merge etməzdən əvvəl rebase et** (tarixçəni təmiz saxlayın):
    ```bash
    git fetch origin
    git rebase origin/main
    # konflikt varsa, həll edin
    git push origin feature-branch --force-with-lease
    ```

- **Funksiya çox şey varsa commitləri sıxlayın** (isteğe bağlı):
    ```bash
    git rebase -i origin/main
    # commitləri 'squash' və ya 's' işarə edin
    # ilk commit-i açıq saxlayın
    ```

- **Merged branch-ları silin:**
    ```bash
    # Lokal
    git branch -d feature-branch
    
    # GitHub-da
    git push origin --delete feature-branch
    ```

- **Heç vaxt `--force` işlətməyin (`--force-with-lease` istifadə edin):**
    ```bash
    # İyi – uzaq dəyişiklikləri hörmətlə qəbul et
    git push --force-with-lease
    
    # Təhlükəli – hər şeyi üstündən yaz
    git push --force
    ```

#### 14.7 Performans Optimizasiyası

- **Repo ölçüsünü izləyin:**
    ```bash
    git count-objects -v
    du -sh .git
    ```

- **Böyük binary fayllardan çəkinyin:**
    - Binary-lər üçün Git LFS (Large File Storage) istifadə edin
    - node_modules/, venv/, .gradle/ commit etməyin
    - Agresif şəkildə `.gitignore` istifadə edin

- **Böyük repo üçün dayaz clone** (klonlama yavaşdırsa):
    ```bash
    git clone --depth 1 https://github.com/username/huge-repo.git
    ```

- **Binary fayllar üçün `.gitattributes` istifadə edin:**
    ```gitattributes
    *.png binary
    *.jpg binary
    *.zip binary
    ```

#### 14.8 Bərpa & Debugging

- **İtirmiş commitləri bərpa etmək üçün `git reflog` istifadə edin:**
    ```bash
    git reflog
    git reset --hard HEAD@{n}  # n - reflog indeksi
    ```

- **`git bisect` ilə bir şeyi pozan commit-i tapın:**
    ```bash
    git bisect start
    git bisect bad HEAD          # cari versiya pozulub
    git bisect good v1.0.0       # bu versiya yaxşı idi
    # Git ortada commit-ə keçir
    # Yoxla... pozan: git bisect bad
    # İşləyən: git bisect good
    # ... tapmayana qədər təkrarlayın
    git bisect reset
    ```

- **Hansı xəttin dəyiştirildiğini `git blame` ilə görün:**
    ```bash
    git blame src/app.js
    ```

- **Mesaj ilə commit tapın:**
    ```bash
    git log --grep="login bug"
    git log --all --oneline | grep -i "auth"
    ```

---

### 15. Tez-tez Problemlər və Həlləri

#### 🔴 KRİTİK (Məlumat İtirmə Riski)

Bu problemlər permanent olaraq commitləri itirə biləcək. Cəld hərəkət edin!

**Problem: Güclü push etdim və komanda yoldaşımın commitlərini sildim**

```bash
# Komanda yoldaşınız reflog istifadə edərək bərpa edə biləcək:
git reflog
# İtirmiş commit hash-i tapın
git reset --hard <lost-commit-hash>
git push origin feature-branch --force-with-lease
```

**Təhvil:**
- `--force` əvəzinə `--force-with-lease` istifadə edin
- `main` branch-ı qoruyun (güclü push-u blok et)
- GitHub ayarlarında qorumlu branch-lar istifadə edin

---

**Problem: Təsadüfən unpushed commitləri olan lokal branch-ı sildim**

```bash
# Panikləməyin! Reflog istifadə edərək bərpa edin
git reflog
# Branch ucunu tapın
git checkout -b feature-branch <commit-hash>
```

**Təhvil:**
- Tez-tez push edin, işi yalnız lokal saxlamayın
- Branch-ları silmək əvəzinə `git stash` istifadə edin

---

**Problem: Verilənlər bazası parolunu / API açarını ictimai repo-ya commit etdim**

```bash
# DƏRHAL sırrı yeniləyin (yeni parol, yeni açar)

# Sonra Git tarixçəsindən təmizləyin:
git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch secrets.txt' \
  --prune-empty --tag-name-filter cat -- --all

# Güclü push et
git push origin main --force-with-lease

# Komandanı xəbərdar edin
```

**Təhvil:**
- İlk commit-dən əvvəl `.env`-ni `.gitignore`-ya əlavə edin
- GitHub sirr skanlamasından istifadə edin (avtomatik xəbərdarlıq)
- Istehsalda sırlar menecerindən istifadə edin

---

#### 🔶 YÜKSƏK (Əməkdaşlıq Blokeri)

Bunlar komandanızın işləməsini blok edir. Fövqəladə lakin bərpa edilə bilir.

**Problem: `fatal: not a git repository`**

```bash
# Siz Git repo-sunda deyilsiniz:
cd /path/to/correct/folder

# Və ya yenisini initialize edin:
git init

# Düzgün yerdə olduğunuzu yoxlayın:
pwd
ls -la | grep .git
```

**Təhvil:**
- Həmişə `git clone` və ya `git init` ilə başlayın
- Əmrləri işə salmadan əvvəl cari qovluğunuzu yoxlayın

---

**Problem: Push edərkən `Permission denied`**

```bash
# Səbəb 1: Yadda saxlanmış etimad olmadan HTTPS istifadə
# Həll: Əvəzən SSH istifadə edin
git remote set-url origin git@github.com:username/repo.git
# VEYA GitHub-da Personal Access Token (PAT) yaradın

# Səbəb 2: SSH açarı yüklənməyib
ssh -T git@github.com  # əlaqə testi
ssh-add ~/.ssh/id_ed25519

# Səbəb 3: Səhv repo icazələri
# Repo sahibindən sizi əməkdaş olaraq əlavə etməsini istəyin
```

**Təhvil:**
- SSH açarlarını bir dəfə quraşdırın (Bölmə 13)
- Setup-u doğrulamaq üçün `ssh -T git@github.com` istifadə edin

---

**Problem: `Updates were rejected` – push edə bilmirəm**

```bash
# Sizin uzaq branch-ınız lokal branch-ınızdan qabaqda
git pull --rebase origin main
# Konflikt varsa, həll edin
git push origin feature-branch
```

**Təhvil:**
- Push etməzdən əvvəl həmişə `git pull` edin
- Standart olaraq `git pull --rebase` istifadə edin:
  ```bash
  git config --global pull.rebase true
  ```

---

**Problem: package.json / requirements.txt-də merge conflikti**

```bash
# Bu fayllar avtomatik qenerated məzmuna və xüsusi merge qaydalara malikdir
# Seçim 1: Sizninkini saxlayın (asılılıqları yenilədiysəniz)
git checkout --ours package.json

# Seçim 2: Onunkini saxlayın (daha son olanlarsa)
git checkout --theirs package.json

# Seçim 3: Əl ilə həll edin və işə salın:
npm install  # və ya pip install -r requirements.txt
git add package.json package-lock.json  # və ya requirements.txt
git commit -m "chore: resolve dependency conflict"
```

**Təhvil:**
- Fərqli branchlarda eyni zamanda asılılıqları yeniləməyin
- Asılılıq yeniləmələri üçün ayrı PRs istifadə edin

---

**Problem: Detached HEAD – commit edə bilmiqəm**

```bash
# Bir commit və ya tag əvəzinə branch çıxış etdiniz
git log --oneline | head -1  # harada olduğunuzu görün

# Həll: Cari mövqedən branch yaradın
git switch -c feature-branch
# İndi normal olaraq commit edə bilərsiniz

# VEYA main-ə qayıdın:
git switch main
```

**Təhvil:**
- `git checkout commit-hash` əvəzinə `git switch branch-name` istifadə edin
- Tag-ları çıxış etməkdə ehtiyatlı olun (onlar branch-lar deyil)

---

#### 🟡 ORTA (İş Axışı Sürtünməsi)

Bunlar sizi yavaşlatır, lakin kritik deyil.

**Problem: Bundan sonra istəmədiyim faylı commit etdim – necə uncommit edim?**

```bash
# Commit hələ push edilməyib:
# Seçim 1: Bütün commit-i geri al (dəyişiklikləri saxla)
git reset --soft HEAD~1
# Dəyişikliklər arxada qalır

# Seçim 2: Commit və staging-i geri al (fayl dəyişiklikləri saxla)
git reset --mixed HEAD~1

# Seçim 3: Commit-i tamamilə sil (dəyişiklikləri itirlər)
git reset --hard HEAD~1

# Commit artıq push olunub – əvəzən revert istifadə edin:
git revert <commit-hash>
```

---

**Problem: Böyük binary fayl repo-mu şişirtdi**

```bash
# Məsulun tapın:
git rev-list --all --objects | sort -k2 | tail -10

# Tarixçədən çıxarın:
git filter-branch --tree-filter 'rm -f large-file.zip' --all

# VEYA: Gələcək binary fayllar üçün Git LFS istifadə edin
git lfs install
git lfs track "*.psd"
git add .gitattributes
```

---

**Problem: `git clone` çox yavaşdır (böyük repo)**

```bash
# Yalnız son tarixçəni klonlayın:
git clone --depth 1 https://github.com/username/huge-repo.git

# Daha sonra, tam tarixçə əldə edin:
cd huge-repo
git fetch --unshallow
```

---

**Problem: Master branch-ı main-ə adlandırmaq istəyirəm**

```bash
# Lokal:
git branch -M master main

# Uzaqda:
git push -u origin main

# GitHub-a ana əsas branch main etməsini söylə:
# GitHub → Settings → Default branch → main seçin
```

---

**Problem: `git status` redaktə etmədiyim faylları göstərir**

```bash
# Səbəb 1: Sıra sonu fərqləri (CRLF vs LF)
git config core.autocrlf true  # Windows
git config core.autocrlf input  # Mac/Linux

# Səbəb 2: Fayl icazələri dəyişdi
git config core.filemode false  # tələb olunmursa

# Səbəb 3: Nə dəyişdiyini yoxlayın
git diff filename.txt
```

---

**Problem: Dəyişiklikləri əl ilə saxlamağı unutdum**

```bash
# Bütün stash-ları tapın:
git stash list

# Ən son-u bərpa edin:
git stash pop

# Və ya xüsusi birini:
git stash apply stash@{2}

# Tətbiq etməzdən əvvəl diff-i görün:
git stash show stash@{0} -p
```

---

**Problem: Nəşr edilmiş commitləri TARIXÇE yeniləməsi BEZ undo eləməliləm**

```bash
# Git revert istifadə edin (dəyişiklikləri ləğv edən yeni commit yaradır)
git revert <commit-hash>
git push origin main

# Bu təhlükəsizdir, çünki tarixçəni dəyişdirmir
```

---

#### 🟢 AŞ AĞIR (Öyrənmə Eğrisi)

Bunlar çaşqın, lakin pozan deyil.

**Problem: Klonladım, lakin `fatal: remote origin already exists` aldım**

```bash
# Klonlanmış qovluğda git init işə saldınız
git remote -v  # remotləri sıradakı edin

# Həll: Kopyağı çıxarın
git remote remove origin
git remote add origin https://github.com/username/repo.git
```

---

**Problem: Tag vs Branch – hansı nədir?**

```bash
# Branch: commit edərkən hərəkət edir (göstərici kimi)
#   Istifadə edin: aktiv inkişaf üçün
git branch feature-feature
git commit -m "add feature"
# Branch ucu yeni commit-ə keçir

# Tag: tarixçədə sabit nöqtə (etiket kimi)
#   Istifadə edin: buraxılışlar üçün
git tag v1.0.0
# Tag v1.0.0 da selamlaşmır

# Sıradakı:
git branch -a   # bütün branchlar
git tag -l      # bütün taglar
```

---

**Problem: `Everything up-to-date` amma GitHub-da yoxdur**

```bash
# Siz uzaq-bilmir lokal branchda-sınız
git branch -a  # -a bütün branch-ları göstərir

# Həll: -u bayrağı ilə push edin, uzaq branch yaradın
git push -u origin feature-branch
```

---

**Problem: Nə dəyişdirdiyimi xatırlamıram – tarixçə lazım**

```bash
# Branch-ınızda bütün commitləri görün:
git log --oneline

# Son 3 commit-də nə dəyişdi:
git log -p -3

# Main-dən o zamandan tarixçə:
git log main..feature-branch --oneline

# Hər xəttin kimin dəyişdirdiyini görün:
git blame filename.txt
```

---

**Problem: Submodullar çaşqındır**

```bash
# Submodullar repo-daxili repo-lardır (qabaqcıl, mümkün olduqca çəkinyin)

# Submodullu layihə sahibi əldə etsəniz:
git clone --recurse-submodules https://github.com/username/repo.git

# Və ya klonladıqdan sonra:
git submodule update --init --recursive
```

---

**Problem: Cherry-pick – başqa branch-dan bir commit lazımdır**

```bash
# Cari branch: main
# Feature-branch-dan commit istiyrsiniz:

git log feature-branch --oneline  # commit hash tapın
git cherry-pick <commit-hash>

# İndi bu commit main-də oynadılır
```

---

---

**Bu dokumentasiya tam olaraq “əlimin altında” olsun deyə** Markdown formatındadır. İstəsəniz onu `.md` faylı kimi yadda saxlaya bilərsiniz və ya VS Code-da açaraq axtarış edə bilərsiniz.

---