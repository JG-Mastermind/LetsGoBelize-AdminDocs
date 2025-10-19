# GitHub Pages Deployment Guide

Complete step-by-step instructions to deploy the LetsGoBelize Admin Documentation to GitHub Pages.

---

## 🎯 Overview

This standalone documentation repository will be deployed to:
```
https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/
```

**Benefits**:
- ✅ Free hosting (public repository)
- ✅ Automated deployments (GitHub Actions)
- ✅ Professional documentation site
- ✅ Main codebase stays private
- ✅ Zero exposure of proprietary AI concierge code

---

## 📋 Step-by-Step Setup

### **Step 1: Create New GitHub Repository**

1. **Go to GitHub**: https://github.com/new

2. **Repository Details**:
   - **Repository name**: `LetsGoBelize-AdminDocs`
   - **Description**: "Admin onboarding documentation for LetsGoBelize tourism platform"
   - **Visibility**: ✅ **Public** (required for free GitHub Pages)
   - **Initialize**: ❌ **Do NOT initialize** with README (we have our own)
   - Click **"Create repository"**

3. **Copy the repository URL**:
   ```
   https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs.git
   ```

---

### **Step 2: Push Local Files to GitHub**

Open terminal and run these commands:

```bash
# Navigate to the standalone docs directory
cd /Users/smg.inc/CODES/GitHub/LetsGoBelize/LetsGoBelize-AdminDocs

# Initialize Git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: LetsGoBelize Admin Onboarding Documentation

- Complete MkDocs setup with Material theme
- 15 core documentation modules
- Appendices and reference materials
- Automated GitHub Actions deployment
- Ready for GitHub Pages hosting"

# Add remote repository (use YOUR repository URL)
git remote add origin https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs.git

# Push to GitHub
git branch -M main
git push -u origin main
```

---

### **Step 3: Enable GitHub Pages**

1. **Go to repository on GitHub**:
   ```
   https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs
   ```

2. **Navigate to Settings**:
   - Click **Settings** tab (top-right)

3. **Find Pages section**:
   - Left sidebar → **Pages** (under "Code and automation")

4. **Configure Source**:
   - **Source**: "Deploy from a branch"
   - **Branch**: `gh-pages` (will be created automatically by workflow)
   - **Folder**: `/ (root)`
   - Click **Save**

   > **Note**: The `gh-pages` branch will be created when the GitHub Actions workflow runs for the first time.

---

### **Step 4: Grant Workflow Permissions**

1. **Navigate to Actions settings**:
   - Repository → Settings → Actions → General (left sidebar)

2. **Scroll to "Workflow permissions"**:
   - Select: ✅ **"Read and write permissions"**
   - Check: ✅ **"Allow GitHub Actions to create and approve pull requests"**
   - Click **Save**

---

### **Step 5: Trigger First Deployment**

The GitHub Actions workflow should start automatically after you pushed to `main`.

1. **Go to Actions tab**:
   ```
   https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs/actions
   ```

2. **Watch the "Deploy Documentation" workflow**:
   - Should show as running (yellow dot) or completed (green checkmark)
   - Click on workflow to see detailed logs
   - Deployment takes 2-3 minutes

3. **If workflow hasn't started**, manually trigger it:
   - Click "Deploy Documentation" in workflow list
   - Click "Run workflow" button (top-right)
   - Select `main` branch
   - Click green "Run workflow" button

---

### **Step 6: Verify Deployment**

After workflow completes (green checkmark):

1. **Visit your documentation site**:
   ```
   https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/
   ```

2. **Test functionality**:
   - ✅ Homepage loads correctly
   - ✅ Navigation sidebar works
   - ✅ Search function works
   - ✅ All 15 modules accessible
   - ✅ Appendices load
   - ✅ Dark/light mode toggle works
   - ✅ Mobile responsive design

3. **Share the URL** with your admin team! 🎉

---

## 🔄 Ongoing Updates

### **Automatic Deployment**

Documentation is now fully automated:

1. **Edit files** in `docs/` directory
2. **Commit changes**: `git commit -m "Update documentation"`
3. **Push to GitHub**: `git push origin main`
4. **GitHub Actions** automatically builds and deploys
5. **Live site updates** in 2-3 minutes

### **Local Preview Before Pushing**

Always preview changes locally first:

```bash
cd LetsGoBelize-AdminDocs
mkdocs serve
# Visit http://127.0.0.1:8000
```

---

## 🎨 Customization

### **Change Theme Colors**

Edit `mkdocs.yml`:

```yaml
theme:
  palette:
    - scheme: default
      primary: blue        # Change to your brand color
      accent: light-blue   # Change accent color
```

Available colors: `red`, `pink`, `purple`, `indigo`, `blue`, `cyan`, `teal`, `green`, `lime`, `yellow`, `amber`, `orange`

### **Add Logo & Favicon**

1. Create `docs/assets/` directory
2. Add your logo: `docs/assets/logo.png`
3. Add favicon: `docs/assets/favicon.ico`
4. Update `mkdocs.yml`:

```yaml
theme:
  logo: assets/logo.png
  favicon: assets/favicon.ico
```

### **Custom Domain (Optional)**

To use `docs.letsgobelize.app`:

1. **Create `docs/CNAME` file**:
   ```
   docs.letsgobelize.app
   ```

2. **Configure DNS** (in your domain registrar):
   - Type: `CNAME`
   - Name: `docs`
   - Value: `jg-mastermind.github.io`

3. **Update `mkdocs.yml`**:
   ```yaml
   site_url: https://docs.letsgobelize.app/
   ```

4. **GitHub Settings**:
   - Settings → Pages
   - Custom domain: `docs.letsgobelize.app`
   - Check "Enforce HTTPS"

---

## 🐛 Troubleshooting

### **Workflow Fails**

**Check logs**:
1. Actions tab → Failed workflow
2. Click on failed job
3. Review error messages

**Common fixes**:
- Grant workflow permissions (Settings → Actions)
- Ensure `mkdocs.yml` is valid YAML
- Check file paths are correct

### **404 Error on Live Site**

**Verify settings**:
1. GitHub Pages enabled? (Settings → Pages)
2. Correct branch? (`gh-pages`, not `main`)
3. Correct folder? (`/ (root)`)
4. Wait 2-3 minutes after deployment

### **Changes Not Appearing**

**Solutions**:
1. Clear browser cache (Cmd+Shift+R / Ctrl+Shift+R)
2. Check workflow completed successfully
3. Verify files were pushed to GitHub
4. Check workflow logs for build errors

### **Search Not Working**

**Fix**:
1. Ensure `search` plugin in `mkdocs.yml`
2. Rebuild site: workflow will regenerate search index
3. Clear browser cache

---

## 📊 Monitoring

### **Deployment Status Badge**

Add to your main project README:

```markdown
[![Deploy Docs](https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs/actions/workflows/deploy.yml/badge.svg)](https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs/actions/workflows/deploy.yml)
```

### **Analytics (Optional)**

Add Google Analytics to track documentation usage:

1. Get Google Analytics ID (e.g., `G-XXXXXXXXXX`)
2. Add to `mkdocs.yml`:

```yaml
extra:
  analytics:
    provider: google
    property: G-XXXXXXXXXX
```

---

## ✅ Deployment Checklist

- [ ] Created new public repository on GitHub
- [ ] Pushed local files to repository
- [ ] Enabled GitHub Pages (Settings → Pages → `gh-pages` branch)
- [ ] Granted workflow permissions (Settings → Actions → Read/write)
- [ ] Verified workflow ran successfully (Actions tab → green checkmark)
- [ ] Visited documentation URL and confirmed it loads
- [ ] Tested navigation, search, and mobile responsiveness
- [ ] Shared URL with admin team
- [ ] (Optional) Set up custom domain
- [ ] (Optional) Added analytics tracking

---

## 🔗 Quick Links

- **Live Documentation**: https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/
- **Repository**: https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs
- **Actions**: https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs/actions
- **MkDocs Docs**: https://www.mkdocs.org/
- **Material Theme**: https://squidfunk.github.io/mkdocs-material/

---

## 📞 Support

**Documentation Issues**: Open an issue in this repository
**Platform Questions**: Refer to the troubleshooting playbook in the docs

---

**Ready to deploy!** Follow the 6 steps above and your documentation will be live in minutes. 🚀
