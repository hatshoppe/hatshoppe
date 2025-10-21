# Implementation Plan

- [x] 1. Set up Jekyll project structure and configuration
  - Create Gemfile with Jekyll and required plugins (jekyll-seo-tag, jekyll-sitemap)
  - Create _config.yml with site configuration, collections setup, and defaults
  - Create .gitignore file to exclude Jekyll build artifacts
  - _Requirements: 4.1, 4.2, 4.3, 4.4_

- [x] 2. Create base layout and reusable components
  - [x] 2.1 Implement default layout (_layouts/default.html)
    - Create HTML5 structure with semantic elements
    - Include header and footer components
    - Add viewport meta tag for responsive design
    - Integrate jekyll-seo-tag plugin
    - _Requirements: 3.1, 3.3, 5.1, 5.2_
  
  - [x] 2.2 Create header component (_includes/header.html)
    - Implement site title/logo with link to homepage
    - Create navigation menu that dynamically generates links from attractions collection
    - Add active page indicator using Liquid conditionals
    - _Requirements: 3.1, 3.2, 3.4, 1.2_
  
  - [x] 2.3 Create footer component (_includes/footer.html)
    - Add basic footer content with copyright and site info
    - _Requirements: 3.1, 3.3_

- [x] 3. Implement responsive CSS styling
  - [x] 3.1 Create base styles (_sass/_base.scss)
    - Define CSS reset/normalize
    - Set up typography with fluid sizing using rem units
    - Define color variables for consistent branding
    - Create responsive image styles (max-width: 100%)
    - _Requirements: 3.3, 5.1, 5.2, 5.4_
  
  - [x] 3.2 Create layout styles (_sass/_layout.scss)
    - Implement mobile-first flexbox/grid layouts
    - Add responsive navigation styles with mobile hamburger menu
    - Define breakpoints for tablet (768px) and desktop (1024px)
    - Style header and footer components
    - _Requirements: 5.1, 5.2, 5.3_
  
  - [x] 3.3 Create attraction-specific styles (_sass/_attractions.scss)
    - Style attraction cards for homepage grid
    - Style attraction detail page sections
    - Create responsive hours table styling
    - _Requirements: 2.3, 5.1, 5.2_
  
  - [x] 3.4 Create main stylesheet (assets/css/main.scss)
    - Import all Sass partials in correct order
    - Add front matter for Jekyll processing
    - _Requirements: 3.3, 5.1, 5.2_

- [x] 4. Create homepage layout and content
  - [x] 4.1 Implement home layout (_layouts/home.html)
    - Extend default layout
    - Create hero section with town overview
    - Implement attraction cards grid using Liquid loop
    - Sort attractions by order field
    - _Requirements: 1.4, 1.2, 3.1_
  
  - [x] 4.2 Create attraction card component (_includes/attraction-card.html)
    - Display attraction image, title, and tagline
    - Add link to full attraction page
    - _Requirements: 1.2, 2.1_
  
  - [x] 4.3 Create homepage content (index.md)
    - Add front matter with home layout
    - Write welcome content for the town
    - _Requirements: 1.4_

- [x] 5. Create attraction layout and sample content
  - [x] 5.1 Implement attraction layout (_layouts/attraction.html)
    - Extend default layout
    - Display hero image from front matter
    - Render title, tagline, and description
    - Create hours of operation table from hours object
    - Display location information
    - Display contact information
    - Render additional Markdown content
    - _Requirements: 2.1, 2.2, 2.3, 2.4_
  
  - [x] 5.2 Create three sample attraction files
    - Create _attractions/attraction-1.md with complete front matter
    - Create _attractions/attraction-2.md with complete front matter
    - Create _attractions/attraction-3.md with complete front matter
    - Add sample Markdown content to each
    - _Requirements: 1.1, 1.2, 2.1, 2.2, 6.1, 6.2_
  
  - [x] 5.3 Add placeholder images
    - Create assets/images/ directory
    - Add three placeholder images for attractions
    - _Requirements: 2.4, 5.4_

- [x] 6. Set up GitHub Actions workflow
  - Create .github/workflows/jekyll.yml file
  - Configure workflow to trigger on push to main branch
  - Set up Ruby environment and dependency installation
  - Configure Jekyll build step
  - Configure GitHub Pages deployment step
  - _Requirements: 7.1, 7.2, 7.3, 7.4, 8.1, 8.2, 8.3_

- [x] 7. Create documentation
  - [x] 7.1 Write comprehensive README.md
    - Add project overview and description
    - Document prerequisites (Ruby, Bundler, Homebrew)
    - Write step-by-step local setup instructions for macOS
    - Create content management guide with front matter field descriptions
    - Document deployment process
    - Add troubleshooting section for common issues
    - _Requirements: 6.1, 6.2, 6.3, 6.4, 9.1, 9.2, 9.5_
  
  - [ ]* 7.2 Add inline code comments
    - Comment complex Liquid logic in layouts
    - Document layout inheritance
    - Explain responsive breakpoints in CSS
    - _Requirements: 6.4_

- [x] 8. Configure GitHub Pages
  - Update _config.yml with correct baseurl and url for GitHub Pages
  - Create or verify repository settings for GitHub Pages
  - Document custom domain setup process in README (if needed)
  - _Requirements: 8.1, 8.3, 8.4_

- [ ]* 9. Perform manual testing and validation
  - Test all three attraction pages render correctly
  - Verify navigation links and active indicators work
  - Test responsive design at mobile (375px), tablet (768px), and desktop (1440px) viewports
  - Test in Safari, Chrome, and Firefox on macOS
  - Validate HTML and CSS
  - Check accessibility with browser dev tools
  - _Requirements: 5.1, 5.2, 5.3, 3.1, 3.2, 3.4_
