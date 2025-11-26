# Shimmer Effect Highlight - Documentation Website

Professional documentation website for the Shimmer Effect Highlight Unity Asset, built with MkDocs Material theme.

## 🌟 Features

- **Beautiful Material Design** interface
- **Responsive** layout for all devices
- **Dark/Light mode** support
- **Search functionality** for easy navigation
- **Organized sections**: Getting Started, User Guide, Examples, Reference
- **Code syntax highlighting**
- **Automatic deployment** to GitHub Pages

## 📦 What's Included

- Complete installation and setup guides
- Comprehensive property reference documentation
- Real-world use cases and examples
- Best practices and optimization tips
- Detailed FAQ section
- Support information

## 🚀 Deployment Instructions

### Prerequisites

- GitHub account
- Git installed on your computer
- Python 3.x installed (for local testing)

### Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the **"+"** icon in the top-right corner
3. Select **"New repository"**
4. Name your repository (e.g., `shimmer-effect-docs`)
5. Make it **Public** (required for free GitHub Pages)
6. **Do NOT** initialize with README, .gitignore, or license
7. Click **"Create repository"**

### Step 2: Update Configuration

Before pushing to GitHub, update the `mkdocs.yml` file:

```yaml
repo_url: https://github.com/YOUR_USERNAME/YOUR_REPO_NAME
```

Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual GitHub username and repository name.

### Step 3: Push Your Code to GitHub

Open PowerShell or Terminal in your project folder and run:

```powershell
# Initialize git repository
git init

# Add all files
git add .

# Commit files
git commit -m "Initial commit: Documentation website"

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your values.

### Step 4: Enable GitHub Pages

1. Go to your GitHub repository
2. Click **"Settings"** tab
3. In the left sidebar, click **"Pages"**
4. Under **"Build and deployment"**:
   - **Source**: Select **"GitHub Actions"**
5. Click **"Save"**

### Step 5: Trigger Deployment

The GitHub Action will automatically run when you push to the main branch. You can also:

1. Go to the **"Actions"** tab in your repository
2. Click on **"Deploy Documentation to GitHub Pages"**
3. Click **"Run workflow"** dropdown
4. Click **"Run workflow"** button

### Step 6: Access Your Website

After the action completes (1-2 minutes):

1. Go back to **Settings > Pages**
2. You'll see: **"Your site is live at https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/"**
3. Click the link to view your documentation site!

## 🖥️ Local Development

### Install Dependencies

```powershell
# Install Python packages
pip install mkdocs
pip install mkdocs-material
pip install pymdown-extensions
```

### Preview Locally

```powershell
# Start development server
mkdocs serve
```

Then open your browser to: `http://127.0.0.1:8000`

The site will auto-reload when you save changes to any files.

### Build Locally

```powershell
# Build static site
mkdocs build
```

This creates a `site/` folder with the static website files.

## 📁 Project Structure

```
ShimmerDocSite/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions workflow
├── docs/                       # Documentation content
│   ├── index.md               # Homepage
│   ├── getting-started/
│   │   ├── installation.md
│   │   └── quick-start.md
│   ├── user-guide/
│   │   ├── material-properties.md
│   │   ├── shimmer-controls.md
│   │   └── wave-tiling.md
│   ├── examples/
│   │   ├── use-cases.md
│   │   └── best-practices.md
│   ├── reference/
│   │   ├── asset-contents.md
│   │   └── faq.md
│   └── support.md
├── mkdocs.yml                 # MkDocs configuration
├── README.md                  # This file
└── DOCUMENTATION.md           # Original documentation
```

## ✏️ Customization

### Change Colors

Edit `mkdocs.yml`:

```yaml
theme:
  palette:
    primary: indigo    # Change to: red, pink, purple, blue, etc.
    accent: amber      # Change to: any Material color
```

### Add New Pages

1. Create a new `.md` file in the appropriate `docs/` subfolder
2. Add it to the `nav` section in `mkdocs.yml`:

```yaml
nav:
  - Your Section:
    - Page Title: path/to/your-file.md
```

### Update Repository Links

In `mkdocs.yml`, update:

```yaml
repo_url: https://github.com/yourusername/your-repo
repo_name: GitHub
```

And in the `extra` section:

```yaml
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/yourusername
```

## 🔄 Updating Documentation

After making changes:

```powershell
# Add changed files
git add .

# Commit with a message
git commit -m "Update documentation"

# Push to GitHub
git push
```

The site will automatically rebuild and deploy!

## 📱 Custom Domain (Optional)

To use a custom domain:

1. Buy a domain from a registrar
2. In your GitHub repo, go to **Settings > Pages**
3. Enter your custom domain in the **"Custom domain"** field
4. Add a `CNAME` file to your `docs/` folder containing your domain
5. Configure DNS records at your registrar:
   - Add CNAME record pointing to `YOUR_USERNAME.github.io`

## 🛠️ Troubleshooting

### Build Fails

- Check the Actions tab for error messages
- Ensure all markdown files are valid
- Verify `mkdocs.yml` syntax is correct

### Page Not Found (404)

- Wait 5-10 minutes after first deployment
- Clear browser cache
- Check that GitHub Pages is enabled
- Verify the repository is public

### Changes Not Showing

- Check if the GitHub Action completed successfully
- Clear browser cache (Ctrl+F5)
- Wait a few minutes for CDN propagation

### Local Preview Issues

```powershell
# Reinstall dependencies
pip install --upgrade mkdocs mkdocs-material pymdown-extensions

# Clear cache and rebuild
mkdocs build --clean
mkdocs serve
```

## 📚 Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)

## 📄 License

This documentation website is created for the Shimmer Effect Highlight Unity Asset by Sector4.

## 🤝 Support

For questions about the documentation website setup:
- Check this README
- Review MkDocs documentation
- Check GitHub Actions logs for deployment issues

For questions about the Unity asset itself:
- Refer to the documentation site
- Contact publisher through Unity Asset Store

---

**Built with ❤️ using MkDocs Material**
