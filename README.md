# Git Fetch and Git Pull

## Introduction

Jab hum GitHub (remote repository) ke saath kaam karte hain, tab hume remote repository ke latest changes apne local repository me lana padta hai.

Iske liye Git do important commands provide karta hai:

```bash
git fetch
git pull
```

Dono commands remote repository se data laati hain, lekin inka behavior alag hota hai.

---

# What is Git Fetch?

`git fetch` remote repository se latest commits aur updates download karta hai, lekin unhe current branch me merge nahi karta.

Matlab:

* Latest changes download ho jayenge.
* Aapke local files change nahi honge.
* Aap pehle changes review kar sakte hain.

---

# Syntax

```bash
git fetch
```

Ya specific remote ke liye:

```bash
git fetch origin
```

---

# Example

Maan lo GitHub par kisi ne naya commit push kiya:

```text
GitHub (origin/main)

A → B → C → D
```

Lekin aapka local repository:

```text
Local (main)

A → B → C
```

Ab:

```bash
git fetch origin
```

karne par Git D commit download kar lega.

```text
origin/main

A → B → C → D
```

Lekin local main branch abhi bhi:

```text
main

A → B → C
```

par hi rahegi.

---

# Check Fetched Changes

```bash
git log main..origin/main --oneline
```

Ya:

```bash
git diff main origin/main
```

Isse aap dekh sakte hain ki remote me kya changes aaye hain.

---

# What is Git Pull?

`git pull` remote repository se latest changes download bhi karta hai aur automatically merge bhi kar deta hai.

Ye actually do commands ka combination hai:

```bash
git fetch
git merge
```

---

# Syntax

```bash
git pull
```

Ya:

```bash
git pull origin main
```

---

# Example

Current situation:

```text
GitHub

A → B → C → D
```

Local:

```text
A → B → C
```

Command:

```bash
git pull origin main
```

Result:

```text
A → B → C → D
```

Ab local repository update ho jayegi.

---

# How Git Pull Works Internally

```bash
git pull
```

Internally:

```bash
git fetch
git merge
```

ke equal hota hai.

---

# Git Fetch vs Git Pull

| Feature                           | Git Fetch | Git Pull |
| --------------------------------- | --------- | -------- |
| Remote changes download karta hai | ✅ Yes     | ✅ Yes    |
| Local branch update karta hai     | ❌ No      | ✅ Yes    |
| Automatic merge karta hai         | ❌ No      | ✅ Yes    |
| Safe for checking changes         | ✅ Yes     | ❌ No     |
| Quick update ke liye              | ❌ No      | ✅ Yes    |

---

# Visual Difference

### Before

```text
GitHub

A → B → C → D

Local

A → B → C
```

---

### After Git Fetch

```text
origin/main

A → B → C → D

main

A → B → C
```

Changes sirf download hue hain.

---

### After Git Pull

```text
main

A → B → C → D
```

Changes merge bhi ho gaye.

---

# When to Use Git Fetch?

Use `git fetch` when:

* Team project par kaam kar rahe ho.
* Pehle changes review karna chahte ho.
* Direct merge nahi karna chahte.
* Safe workflow follow karna chahte ho.

Example:

```bash
git fetch
git log HEAD..origin/main --oneline
```

---

# When to Use Git Pull?

Use `git pull` when:

* Direct latest changes chahiye.
* Remote changes merge karne ke liye ready ho.
* Quick update karna ho.

Example:

```bash
git pull origin main
```

---

# Fetch + Manual Merge

Step 1:

```bash
git fetch origin
```

Step 2:

```bash
git merge origin/main
```

Ye exactly `git pull` ke equivalent hai.

---

# Common Commands

### Fetch Latest Changes

```bash
git fetch
```

### Fetch From Origin

```bash
git fetch origin
```

### Pull Latest Changes

```bash
git pull
```

### Pull Specific Branch

```bash
git pull origin main
```

### See Difference After Fetch

```bash
git diff main origin/main
```

### See New Commits

```bash
git log main..origin/main --oneline
```

---

# Best Practice

Team projects me pehle:

```bash
git fetch
```

phir changes review karo.

Agar sab sahi lage:

```bash
git merge origin/main
```

Ya directly:

```bash
git pull
```

use kar sakte ho.

---

# Summary

`git fetch` remote repository se latest updates download karta hai lekin local branch ko modify nahi karta.

`git pull` latest updates download karta hai aur unhe current branch me merge bhi kar deta hai.

### Important Commands

```bash
# Download changes only
git fetch

# Download and merge changes
git pull

# Fetch from origin
git fetch origin

# Pull from main branch
git pull origin main

# Compare local and remote
git diff main origin/main

# Show new commits
git log main..origin/main --oneline
```

### Remember

```text
git fetch = Download only

git pull = Download + Merge
```
