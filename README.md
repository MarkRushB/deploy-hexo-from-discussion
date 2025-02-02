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

###  
### 1️⃣ GitHub Discussions Configuration Guide

This GitHub Actions workflow is triggered automatically when a **new GitHub Discussion is created**. It converts the discussion content into a Hexo blog post and commits it to your repository.

#### 🔧 Enabling GitHub Discussions

To use this workflow, ensure that **GitHub Discussions** is enabled for your repository:

1. **Go to your repository settings**  
   - Navigate to your repository on GitHub.
   - Click on **Settings** > **General**.

2. **Enable Discussions**  
   - Scroll down to the **Features** section.
   - Check the box for **Discussions** to enable it.

3. **Create a Discussion**  
   - Go to the **Discussions** tab in your repository.
   - Click **New Discussion**, select a category, enter a title and content, and click **Post**.

---


#### 📝 How the Workflow Processes Discussions

When a new discussion is created, the workflow extracts and formats the following information:

- **Title** (`.title`) → Used as the blog post title.
- **Created Date** (`.created_at`) → Formatted as `YYYY-MM-DD HH:MM:SS`.
- **Body** (`.body`) → The main content of the discussion.
- **Labels** (`.labels[].name`) → Used for custom layouts and icons.

The discussion is then converted into a **Markdown file** in the `source/_posts/` directory of the Hexo repository.

⚠️ **Disclaimer**： This GitHub Actions workflow is **designed for my specific Hexo template**. Some label-based conversions are customized for my Hexo **Front-matter format**, and they may not be compatible with other Hexo themes or templates.

### What You Need to Modify:
- **Label-to-Front-matter conversion**: The `layout` and `icon` fields are assigned based on discussion labels (`memo`, `bullshit`, etc.). If your Hexo template does not use these fields, you should **update the logic** in `.github/workflows/sync-discussions.yml`.
- **Markdown File Structure**: The generated posts follow my template's format. If your template uses different Front-matter keys or additional metadata fields, adjust the workflow accordingly.

https://github.com/MarkRushB/deploy-hexo-from-discussion/blob/d9bc8aa458564570e50cfd4b6b0a167f85ac1953/sync-discussion.yml#L29-L69



##### 📌 Example Output:

If a discussion titled **"My Thoughts on Open Source"** is created with the **`memo`** label, the resulting Markdown file (`source/_posts/My Thoughts on Open Source.md`) will look like:

```markdown
---
title: "My Thoughts on Open Source"
date: 2024-11-15 14:30:00
layout: tweet
icon: sad
---
This is the body content of the discussion...
```

### 2️⃣ Add Secrets

Go to **Settings > Secrets and variables > Actions > New repository secret** and add the following secrets:

| Secret Name | Description |
|------------|-------------|
| `GH_PAT` | A GitHub Personal Access Token with `repo` and `discussion` permissions |
| `GH_REPO` | Your repository in the format `owner/repo-name` |

---

### 3️⃣ Place Workflow Files in the Correct Directory  

Ensure that both workflow files are placed inside the **`.github/workflows/`** directory in your repository.
