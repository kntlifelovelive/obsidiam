

---

# Concept (Simple)

==> SSH key တစ်ခုစီ = Account တစ်ခု  
==> `~/.ssh/config` နဲ့ **Host alias** သတ်မှတ်မယ်  
==>  Git remote မှာ alias သုံးမယ်

---

#  Key တစ်ခုစီ Generate လုပ်မယ်

##  GitHub Personal

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_github_personal -C "personal@email.com"
```

##  GitHub Work

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_github_work -C "work@email.com"
```

##  GitLab

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_gitlab -C "gitlab@email.com"
```

---

# SSH Agent ထဲ Add လုပ်မယ်

```bash
eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519_github_personal
ssh-add ~/.ssh/id_ed25519_github_work
ssh-add ~/.ssh/id_ed25519_gitlab
```

---

#  Public Key တွေကို Website တွေထဲထည့်

- GitHub → Settings → SSH Keys
    
- GitLab → Preferences → SSH Keys
    

`cat ~/.ssh/filename.pub` နဲ့ copy လုပ်ပီး paste လုပ်ပါ။

---

#  Advanced SSH Config

ဖိုင် create လုပ်မယ် 

```bash
nano ~/.ssh/config
```

ဒီလိုရေးပါ 

```ssh
# GitHub Personal
Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github_personal

# GitHub Work
Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github_work

# GitLab
Host gitlab
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_ed25519_gitlab
```

Save ==

---

#  Remote URL မှာ Alias 

## GitHub Personal Repo

```bash
git remote set-url origin git@github-personal:username/repo.git
```

## GitHub Work Repo

```bash
git remote set-url origin git@github-work:workname/repo.git
```

## GitLab Repo

```bash
git remote set-url origin git@gitlab:username/repo.git
```

---

#  Test 

```bash
ssh -T git@github-personal
ssh -T git@github-work
ssh -T git@gitlab
```

Successful message ထွက်ရင် OK 

---
---

#  Target Structure

```
~/projects/
    github-personal/
    github-work/
    gitlab/
```

 Folder အလိုက် account auto switch ဖြစ်မယ်။

---
---
---

# Global Default (Personal GitHub)

`~/.gitconfig` ထဲမှာ 

```ini
[user]
    name = Kyaw Personal
    email = personal@email.com

# GitHub Work
[includeIf "gitdir:~/projects/github-work/"]
    path = ~/.gitconfig-github-work

# GitLab
[includeIf "gitdir:~/projects/gitlab/"]
    path = ~/.gitconfig-gitlab
```

=> Default = GitHub personal  
=> Folder match ဖြစ်ရင် override လုပ်မယ်။

---

#  GitHub Work Config File

ဖိုင် create လုပ်ပါ 

```bash
nano ~/.gitconfig-github-work
```

ထဲမှာ 

```ini
[user]
    name = Kyaw Work
    email = work@email.com
```

---

# GitLab Config File

```bash
nano ~/.gitconfig-gitlab
```

ထဲမှာ 

```ini
[user]
    name = Kyaw GitLab
    email = gitlab@email.com
```

---

# SSH Config (Important)

`~/.ssh/config` ထဲမှာ 

```ssh
# GitHub Personal
Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github_personal

# GitHub Work
Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github_work

# GitLab
Host gitlab
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_ed25519_gitlab
```

---

#  Remote URL Example

## GitHub Personal Repo

```bash
git remote set-url origin git@github-personal:username/repo.git
```

## GitHub Work Repo

```bash
git remote set-url origin git@github-work:workname/repo.git
```

## GitLab Repo

```bash
git remote set-url origin git@gitlab:username/repo.git
```

---

#  Check Working Config

Repo ထဲဝင်ပြီး 

```bash
git config user.email
```

Folder အလိုက် email ပြောင်းနေတာမြင်ရမယ် 

---

#  Result

|Folder|Account|Email|
|---|---|---|
|github-personal|GitHub #1|personal@email|
|github-work|GitHub #2|work@email|
|gitlab|GitLab|gitlab@email|

---

Enterprise level dev တွေသုံးတဲ့ pattern လည်း ဒီလိုပဲဖြစ်တယ်။

---

