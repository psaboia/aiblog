# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Local Development
- `bundle install` - Install Ruby dependencies
- `bundle exec jekyll serve` - Start local development server at http://localhost:4000/aiblog
- `bundle exec jekyll build` - Build the site for production

### Testing
- Test locally by visiting http://localhost:4000/aiblog after running `bundle exec jekyll serve`
- Test search functionality at http://localhost:4000/aiblog/search/
- Test comments by checking Disqus integration on individual posts

## Architecture Overview

This is a Jekyll-based blog with GitHub Pages deployment using the Minima theme. Key architectural components:

### Content Structure
- `_posts/` - Blog posts in Markdown format with YAML front matter
- `_layouts/` - HTML templates (default.html, post.html)  
- `_includes/` - Reusable HTML components (header.html, google-analytics.html)
- `assets/images/` - Static image assets for blog posts

### Key Features
- **Search**: Client-side search using Lunr.js with real-time results
- **Comments**: Disqus integration for post comments
- **Likes**: localStorage-based like system for posts
- **Analytics**: Google Analytics integration
- **Mermaid**: Diagram support in posts

### Configuration
- `_config.yml` - Site configuration including baseurl `/aiblog`, Disqus shortname, Google Analytics ID
- `Gemfile` - Ruby dependencies including Jekyll 4.3.3 and plugins
- Uses Jekyll plugins: jekyll-feed, jekyll-seo-tag

### Search Implementation
- Search index built from all posts using Jekyll Liquid templates
- Lunr.js provides client-side full-text search
- Search box in header submits to dedicated `/search/` page
- Real-time search results without page refresh

### Deployment
- Hosted on GitHub Pages at https://psaboia.github.io/aiblog
- Automatic deployment on push to main branch
- Site builds to `_site/` directory (excluded from git)
- **Important**: After every push, verify GitHub Actions status with `gh run list --limit 3` to ensure successful deployment

### Styling
- Based on Minima theme with custom CSS overrides
- Responsive header layout with collapsible navigation
- Custom search box styling integrated into header