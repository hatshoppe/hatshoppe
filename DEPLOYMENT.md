# GitHub Pages Deployment Guide

## Initial Setup

### 1. Create GitHub Repository

1. Go to GitHub and create a new repository
2. Name it something like `town-attractions` (or your preferred name)
3. Make it public (required for free GitHub Pages)
4. Don't initialize with README (we already have one)

### 2. Push Your Code

```bash
git init
git add .
git commit -m "Initial commit: Town attractions website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
git push -u origin main
```

### 3. Configure GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under "Build and deployment":
   - Source: Select **GitHub Actions**
4. The site will automatically deploy when you push to `main`

### 4. Update Configuration

Edit `_config.yml` and update these values:

```yaml
baseurl: "/YOUR-REPO-NAME"  # e.g., "/town-attractions"
url: "https://YOUR-USERNAME.github.io"  # e.g., "https://johndoe.github.io"
```

**Important**: If your repository name is `YOUR-USERNAME.github.io`, leave `baseurl` empty:

```yaml
baseurl: ""
url: "https://YOUR-USERNAME.github.io"
```

### 5. Commit and Push Changes

```bash
git add _config.yml
git commit -m "Update config for GitHub Pages"
git push
```

### 6. Wait for Deployment

1. Go to the **Actions** tab in your repository
2. Watch the deployment workflow run
3. Once complete (green checkmark), your site is live!

### 7. Access Your Site

Your site will be available at:
- With repository name: `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`
- User/org site: `https://YOUR-USERNAME.github.io/`

## Custom Domain Setup (Optional)

### 1. Add CNAME File

Create a file named `CNAME` in the root directory:

```
yourdomain.com
```

### 2. Configure DNS

Add these DNS records with your domain provider:

For apex domain (yourdomain.com):
```
A     185.199.108.153
A     185.199.109.153
A     185.199.110.153
A     185.199.111.153
```

For www subdomain:
```
CNAME www.yourdomain.com YOUR-USERNAME.github.io
```

### 3. Update _config.yml

```yaml
baseurl: ""
url: "https://yourdomain.com"
```

### 4. Configure in GitHub

1. Go to Settings → Pages
2. Under "Custom domain", enter your domain
3. Check "Enforce HTTPS" (after DNS propagates)

## Troubleshooting

### Site Not Loading

- Check Actions tab for build errors
- Verify `baseurl` and `url` in `_config.yml`
- Ensure GitHub Pages is enabled in Settings

### 404 Errors

- Make sure `baseurl` matches your repository name
- Check that all links use `{{ '/' | relative_url }}` or `{{ page.url | relative_url }}`

### CSS Not Loading

- Verify the stylesheet link in `_layouts/default.html` uses `relative_url` filter
- Check browser console for 404 errors
- Ensure `baseurl` is set correctly

### Build Failures

- Check the Actions tab for detailed error logs
- Common issues:
  - Invalid YAML syntax in front matter
  - Missing required front matter fields
  - Broken image links

## Making Updates

After initial deployment, simply push changes to the `main` branch:

```bash
git add .
git commit -m "Update content"
git push
```

GitHub Actions will automatically rebuild and deploy your site.

## Monitoring

- **Actions Tab**: View build and deployment status
- **Environments**: See deployment history under Settings → Environments
- **Pages Settings**: View current deployment URL and status
