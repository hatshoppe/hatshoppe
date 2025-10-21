# Town Attractions Website

A Jekyll-based static website showcasing three local attractions in our town. This site features individual pages for each attraction with details about hours, location, and contact information.

## Project Overview

This website serves as a unified platform for three town attractions:
- Historic Town Museum
- Riverside Nature Park
- Artisan Marketplace

Each attraction has its own dedicated page with rich content, while maintaining consistent navigation and branding throughout the site.

## Prerequisites

Before you begin, ensure you have the following installed on your macOS system:

- **Homebrew**: Package manager for macOS
- **Ruby**: Version 3.0 or higher
- **Bundler**: Ruby dependency manager

## Local Setup Instructions

### 1. Install Homebrew (if not already installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install Ruby via Homebrew

macOS comes with Ruby, but it's recommended to use a newer version via Homebrew:

```bash
brew install ruby
```

Add Ruby to your PATH by adding this to your `~/.zshrc` file:

```bash
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Verify Ruby installation:

```bash
ruby -v
```

### 3. Install Bundler

```bash
gem install bundler
```

### 4. Clone the Repository

```bash
git clone <your-repository-url>
cd <repository-name>
```

### 5. Install Dependencies

```bash
bundle install
```

### 6. Run the Local Development Server

```bash
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`

### 7. Making Changes

The local server includes live reload functionality. When you make changes to content files, the site will automatically rebuild. Simply refresh your browser to see the changes.

To stop the server, press `Ctrl+C` in the terminal.

## Content Management Guide

### Editing Attraction Content

Attraction content is stored in the `_attractions/` directory. Each attraction is a Markdown file with YAML front matter.

#### Front Matter Fields

- **layout**: Should always be `attraction`
- **title**: Name of the attraction (required)
- **tagline**: Brief tagline or slogan (optional)
- **description**: Full description of the attraction (required)
- **hours**: Operating hours by day of the week (required)
  - Format: `day: "HH:MM AM/PM - HH:MM AM/PM"` or `"Closed"`
- **location**: Address information (required)
  - `address`: Street address
  - `city`: City name
  - `state`: State name
  - `zip`: Zip code
- **contact**: Contact details (required)
  - `phone`: Phone number
  - `email`: Email address
  - `website`: Website URL
- **image**: Path to hero image (required)
  - Format: `/assets/images/filename.jpg`
- **order**: Display order on homepage (required)
  - Use numbers 1, 2, 3, etc.

#### Example Attraction File

```yaml
---
layout: attraction
title: "My Attraction"
tagline: "A great place to visit"
description: "Full description here"
hours:
  monday: "9:00 AM - 5:00 PM"
  tuesday: "9:00 AM - 5:00 PM"
  wednesday: "Closed"
  thursday: "9:00 AM - 5:00 PM"
  friday: "9:00 AM - 5:00 PM"
  saturday: "10:00 AM - 6:00 PM"
  sunday: "10:00 AM - 6:00 PM"
location:
  address: "123 Main St"
  city: "Town Name"
  state: "State"
  zip: "12345"
contact:
  phone: "(555) 123-4567"
  email: "info@example.com"
  website: "https://example.com"
image: "/assets/images/my-attraction.jpg"
order: 1
---

Additional content in Markdown format goes here...
```

### Adding Images

1. Add your images to the `assets/images/` directory
2. Recommended size: 1200x600 pixels
3. Supported formats: JPG, PNG, WebP
4. Reference images in front matter using: `/assets/images/filename.jpg`

### Editing the Homepage

Edit `index.md` to change the homepage hero content. The attraction cards are automatically generated from the attractions collection.

### Changing Site Configuration

Edit `_config.yml` to change:
- Site title and description
- Base URL (for GitHub Pages)
- Other Jekyll settings

**Note**: After changing `_config.yml`, you must restart the Jekyll server for changes to take effect.

## Deployment

### Automatic Deployment via GitHub Actions

This site is configured to automatically deploy to GitHub Pages when you push changes to the `main` branch.

#### Setup Steps:

1. Push your code to a GitHub repository
2. Go to repository Settings → Pages
3. Under "Build and deployment", select "GitHub Actions" as the source
4. Push a commit to the `main` branch
5. GitHub Actions will automatically build and deploy your site

The workflow file is located at `.github/workflows/jekyll.yml`.

### Viewing Your Deployed Site

After deployment, your site will be available at:
```
https://<username>.github.io/<repository-name>/
```

### Custom Domain (Optional)

To use a custom domain:

1. Add a `CNAME` file to the root directory with your domain name
2. Configure DNS settings with your domain provider
3. Update the `url` in `_config.yml` to your custom domain
4. See [GitHub Pages documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site) for detailed instructions

## Troubleshooting

### Port Already in Use

If you see an error that port 4000 is already in use:

```bash
bundle exec jekyll serve --port 4001
```

### Bundle Install Fails

If `bundle install` fails, try:

```bash
bundle update
bundle install
```

### Changes Not Appearing

1. Make sure the Jekyll server is running
2. Hard refresh your browser (Cmd+Shift+R on macOS)
3. Check the terminal for build errors
4. Restart the Jekyll server

### Ruby Version Issues

If you encounter Ruby version issues:

```bash
brew upgrade ruby
gem install bundler
bundle install
```

### GitHub Actions Build Fails

1. Check the Actions tab in your GitHub repository
2. Review the build logs for specific errors
3. Common issues:
   - Missing or invalid YAML front matter
   - Broken image links
   - Invalid `_config.yml` syntax

## Project Structure

```
.
├── _attractions/          # Attraction content files
├── _layouts/              # Page templates
├── _includes/             # Reusable components
├── _sass/                 # Sass stylesheets
├── assets/
│   ├── css/              # Compiled CSS
│   └── images/           # Image files
├── .github/
│   └── workflows/        # GitHub Actions workflows
├── _config.yml           # Jekyll configuration
├── Gemfile               # Ruby dependencies
├── index.md              # Homepage
└── README.md             # This file
```

## Technologies Used

- **Jekyll 4.3**: Static site generator
- **Liquid**: Templating language
- **Sass**: CSS preprocessor
- **GitHub Actions**: CI/CD
- **GitHub Pages**: Hosting

## Support

For Jekyll documentation, visit: https://jekyllrb.com/docs/

For GitHub Pages documentation, visit: https://docs.github.com/en/pages

## License

This project is open source and available for use and modification.
