---
title: "Assignment 2"
draft: false
author: "Tianning Liu"
---

# Hugo Static Blog Deployment & Version Control Report

## Project Name: Alastor's Blog  
## Remote Git Repository: [http://10.61.2.24:2025/ZY2457B16/site_alastor](http://10.61.2.24:2025/ZY2457B16/site_alastor)

---

## ✅ v1: Initialize Hugo Project & Git Repository

- Used `hugo new site myblog` to create Hugo project structure.
- Initialized Git version control using `git init`.
- Connected to the remote repository and pushed the initial commit:

```bash
git remote add origin http://10.61.2.24:2025/ZY2457B16/site_alastor
git add .
git commit -m "v1: Initialize Hugo project"
git push -u origin master
```

---

## ✅ v2: Add and Configure the PaperMod Theme

- Added PaperMod theme as a Git submodule:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

- Updated `config.toml` with site basics and theme settings:

```toml
baseURL = "http://10.61.2.24:2025/ZY2457B16/site_alastor/"
title = "Alastor's Blog"
theme = "PaperMod"
languageCode = "en-us"
defaultContentLanguage = "en"

[params]
  ShowReadingTime = true
  ShowCodeCopyButtons = true
```

- Committed as version 2:

```bash
git add .
git commit -m "v2: Add PaperMod theme and basic configuration"
git push
```

---

## ✅ v3: Personalize Site Information (Title, Language, Welcome Message)

- Edited `config.toml` to include author name, description, and welcome message:

```toml
[params]
  author = "Tianning Liu"
  description = "Personal notes and technical sharing."
  homeInfoCenter = true
  defaultTheme = "dark"

[params.homeInfoParams]
  Title = "Welcome to my site!"
  Content = ""

[pagination]
  size = 5
```

- Committed as version 3:

```bash
git add .
git commit -m "v3: Customize site (author, language, welcome message)"
git push
```

---

## ✅ v4: Beautify Homepage (Remove Cards and Default Prompts)

- Hide default article cards on the homepage:

```toml
[params]
  hidePostsSectionInHome = true
```

- Adjust menu and site layout:

```toml
[[menu.main]]
  name = "Home"
  url = "/"
  weight = 1

[[menu.main]]
  name = "Assignments"
  url = "/assignments/"
  weight = 2
```

- Committed as version 4:

```bash
git add .
git commit -m "v4: Beautify homepage (remove prompts and cards)"
git push
```

---

## ✅ v5: Publish First Blog Post

- Put assignment 1 into D:\Site_Alastor\content:

🎉 The blog is now online!
This is the first test post.
```

- Committed as version 5:

```bash
git add .
git commit -m "v5: Publish first blog post"
git push
```

---

## 📌 Notes:

- Previewed using `hugo server -D` throughout development.
- All five versions were pushed to the private remote Git server.
- PaperMod was chosen for its minimalist and responsive design, ideal for personal technical blogs.

---
