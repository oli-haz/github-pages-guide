---
layout: default
title: GitHub Pages — Complete Guide
---

# GitHub Pages — Complete Guide

> From zero to a live website — using GitHub's free static site hosting. No server required.

⏱ ~15 min read · 🆓 Completely free · 🌐 Custom domain support

---

## What is GitHub Pages?

GitHub Pages is a **free static site hosting service** built directly into GitHub. You push HTML, CSS, and JavaScript files to a repository and GitHub serves them as a live website — no backend, no database, no hosting fees.

| Feature | Description |
|---------|-------------|
| 🚀 Instant Deployment | Push code → site updates automatically. No manual deploy steps needed. |
| 🔒 Free HTTPS | Every site gets a free SSL certificate via Let's Encrypt automatically. |
| 🌍 Custom Domains | Use your own domain (e.g. `mysite.com`) instead of the default URL. |
| ⚙️ Jekyll Support | Built-in support for Jekyll, a static site generator with themes and templates. |

> **Limitation:** GitHub Pages only serves *static* files. You cannot run server-side code (e.g. Node.js, PHP, Python) directly on GitHub Pages.

---

## Prerequisites

Before getting started, make sure you have the following:

- **A GitHub account** — Sign up free at [github.com](https://github.com)
- **Git installed** — Download from [git-scm.com](https://git-scm.com). Verify with:
  ```bash
  git --version
  ```
- **A text editor** — VS Code, Sublime Text, or any editor you prefer.

> 💡 **First time with Git?** Configure your identity before making commits:
> ```bash
> git config --global user.name "Your Name"
> git config --global user.email "you@example.com"
> ```

---

## Step-by-Step Guide

### Step 1 · Create a Repository

Your GitHub Pages site lives inside a GitHub repository. There are two types:

| Type | Repo Name | URL | Limit |
|------|-----------|-----|-------|
| **User / Org site** | `<username>.github.io` | `https://<username>.github.io` | 1 per account |
| **Project site** | any name | `https://<username>.github.io/<repo>` | Unlimited |

**Create the repository on GitHub:**

1. Go to [github.com/new](https://github.com/new)
2. Set the repository name (e.g. `my-portfolio` or `username.github.io`)
3. Choose **Public** (required for free GitHub Pages)
4. Check **Add a README file**
5. Click **Create repository**

---

### Step 2 · Build Your Site

Clone your new repository locally and add your site files.

```bash
git clone https://github.com/<username>/<repo-name>.git
cd <repo-name>
```

Create a minimal `index.html` as the entry point of your site:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Site</title>
</head>
<body>
  <h1>Hello, GitHub Pages!</h1>
</body>
</html>
```

> 💡 **Using a framework?** For React, Vue, or other SPAs, you need to **build first** (e.g. `npm run build`) and deploy the output folder (e.g. `dist/` or `build/`) — or use GitHub Actions for automated builds.

---

### Step 3 · Push to GitHub

Stage, commit, and push your files to the repository:

```bash
git add .
git commit -m "Initial site"
git push origin main
```

Verify your files appear in the repository on [github.com](https://github.com) before proceeding.

> ⚠️ **Branch name matters.** GitHub Pages defaults to the `main` branch. If your default branch is named `master`, replace `main` with `master` in all commands.

---

### Step 4 · Enable GitHub Pages

Turn on GitHub Pages from your repository settings:

1. Open your repository on GitHub
2. Click the **Settings** tab
3. Scroll down to the **Pages** section in the left sidebar
4. Under *Source*, select **Deploy from a branch**
5. Choose branch `main` and folder `/ (root)`
6. Click **Save**

> For **User/Org sites** (`<username>.github.io`), GitHub Pages is automatically enabled and always deploys from the `main` branch.

---

### Step 5 · View Your Live Site

After saving, GitHub will build and deploy your site. This usually takes **30 seconds to 2 minutes**.

Your site URL will be shown in **Settings → Pages**:

```
https://<username>.github.io/<repo-name>/
```

You can also check the deployment status under the **Actions** tab of your repository. Look for the *pages build and deployment* workflow.

---

### Step 6 · Deploy Updates

Every time you push changes to the configured branch, GitHub automatically rebuilds and redeploys your site.

```bash
# 1. Edit your files...

# 2. Stage changes
git add .

# 3. Commit with a message
git commit -m "Update homepage content"

# 4. Push — deployment starts automatically
git push origin main
```

**Flow:** Edit files → `git push` → GitHub builds → Site updates

---

## Custom Domain (Optional)

Point your own domain (e.g. `www.mysite.com`) to your GitHub Pages site.

### 1. Add a CNAME file to your repository

Create a file named `CNAME` containing just your domain:

```
www.mysite.com
```

### 2. Configure DNS with your domain registrar

| Record type | Host | Value |
|-------------|------|-------|
| CNAME | `www` | `<username>.github.io` |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

### 3. Set custom domain in GitHub

Go to **Settings → Pages → Custom domain**, enter your domain, and click **Save**. Check **Enforce HTTPS** after DNS propagates (~24 hours).

---

## Tips & Troubleshooting

**✅ Site not updating?**  
Check the **Actions** tab for build errors. Hard-refresh your browser with `Ctrl+Shift+R` (or `Cmd+Shift+R`) to bypass cache.

**⚠️ 404 on project site?**  
Make sure `index.html` (or `index.md`) is in the root of the branch/folder selected as the source. Asset paths must be relative or use the correct base path.

**🔵 Using React / Vue / Vite?**  
Set `base` in your config to `/<repo-name>/`. Deploy the `dist` folder using **GitHub Actions** or the `gh-pages` npm package.

**🟣 Automate with GitHub Actions**  
Use the official **actions/deploy-pages** action to build and deploy on every push, perfect for static site generators and frameworks.

**✅ Jekyll themes**  
Add a `_config.yml` with `theme: minima` (or any supported theme) to apply a pre-built Jekyll theme without any extra setup.

**⚠️ Private repos**  
GitHub Pages from private repos requires a **GitHub Pro, Team, or Enterprise** plan. Free accounts can only publish from *public* repositories.

---

## Further Resources

- 📄 [GitHub Pages Official Docs](https://docs.github.com/en/pages)
- 💎 [Jekyll — Static Site Generator](https://jekyllrb.com)
- ⚙️ [Deploy Pages GitHub Action](https://github.com/marketplace/actions/deploy-pages)
- 📦 [gh-pages npm package](https://www.npmjs.com/package/gh-pages)
