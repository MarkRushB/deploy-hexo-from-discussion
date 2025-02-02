# Sync Discussions to Hexo & Deploy Hexo Blog 🚀

This GitHub Action automates syncing GitHub Discussions to a Hexo blog and deploying the blog to GitHub Pages. When a new discussion is created, it is converted into a Hexo post and committed to your repository. The workflow then triggers a build and deployment process to keep your blog updated.

## ✨ Features

- ✅ **Sync GitHub Discussions to Hexo**
- ✅ **Convert Discussions into Blog Posts Automatically**
- ✅ **Support for Different Layouts & Icons Based on Labels**
- ✅ **Automated Hexo Build & Deployment to GitHub Pages**
- ✅ **Manual Workflow Dispatch Support**

---

## 📌 Setup & Usage

### 1️⃣ Enable GitHub Discussions  
Ensure that GitHub Discussions is enabled for your repository.

### 2️⃣ Add Secrets  
Go to **Settings > Secrets and variables > Actions > New repository secret** and add the following secrets:

| Secret Name | Description |
|------------|-------------|
| `GH_PAT` | A GitHub Personal Access Token with `repo` and `discussion` permissions |
| `GH_REPO` | Your repository in the format `owner/repo-name` |

---
