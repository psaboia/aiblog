# Blog Maintenance Guide

This document provides detailed instructions for maintaining this Jekyll blog.

## Adding New Posts

### 1. Create Post File
Create a new file in `_posts/` with the naming convention:
```
YYYY-MM-DD-post-title.md
```

Example: `2024-04-15-my-new-post.md`

### 2. Post Structure
```markdown
---
layout: post
title: "Your Post Title"
date: 2024-04-15 10:00:00 -0000
categories: [category1, category2]
---

Your post content here in Markdown format.
```

### 3. Adding Images
- Place images in `assets/images/`
- Reference in posts: `![Alt text](/aiblog/assets/images/your-image.png)`
- Supported formats: PNG, JPG, SVG

### 4. Special Features
- **Mermaid diagrams**: Wrap in ```mermaid code blocks
- **Comments**: Enabled by default on all posts
- **Likes**: Automatically available on all posts

## Deployment Process

### Automatic Deployment
1. Push changes to `main` branch
2. GitHub Pages automatically rebuilds the site
3. Site updates at https://psaboia.github.io/aiblog
4. Usually takes 1-2 minutes to reflect changes

### Manual Build (Local Testing)
```bash
# Install dependencies (first time only)
bundle install

# Start development server
bundle exec jekyll serve

# Visit http://localhost:4000/aiblog
```

## Configuration Management

### Site Settings (`_config.yml`)
- **baseurl**: `/aiblog` (GitHub Pages subpath)
- **url**: `https://psaboia.github.io`
- **Google Analytics**: `G-DN4VL9R9W0`
- **Disqus**: `aiblog-prisaboia`

### Key Configurations
```yaml
# Enable comments on all posts
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      comments: true
```

## Search Functionality

### How It Works
- Lunr.js indexes all posts at build time
- Search data generated in `search.md` using Jekyll Liquid
- Client-side search with real-time results
- No server required

### Search Index Updates
- Automatically updates when new posts are added
- No manual intervention needed
- Searches title and content with title boost

## File Structure

```
_posts/           # Blog posts (Markdown files)
_layouts/         # HTML templates
  ├── default.html
  └── post.html
_includes/        # Reusable components
  ├── header.html
  └── google-analytics.html
assets/
  └── images/     # Static images
_config.yml       # Site configuration
Gemfile          # Ruby dependencies
```

## Comments System (Disqus)

### Configuration
- Shortname: `aiblog-prisaboia`
- Configured in `_config.yml`
- Enabled by default on all posts

### Moderation
- Access Disqus admin panel
- Moderate comments before they appear
- Spam protection enabled

## Analytics

### Google Analytics
- Measurement ID: `G-DN4VL9R9W0`
- Tracks page views, user behavior
- Access Google Analytics dashboard for reports

## Troubleshooting

### Local Development Issues
```bash
# Clear Jekyll cache
bundle exec jekyll clean

# Reinstall dependencies
bundle install

# Check Ruby version (should be compatible with Gemfile)
ruby -v
```

### Build Failures
- Check GitHub Pages build status in repository settings
- Verify YAML front matter syntax
- Ensure all links and image paths are correct

### Search Not Working
- Check browser console for JavaScript errors
- Verify search.md generates proper JSON
- Test locally first

## Best Practices

### Writing Posts
- Use descriptive filenames and titles
- Add relevant categories
- Optimize images before uploading
- Test locally before publishing

### Maintenance Schedule
- Check for broken links monthly
- Update dependencies quarterly
- Review analytics monthly
- Backup content regularly

### Security
- Never commit API keys or secrets
- Keep dependencies updated
- Use HTTPS for all external resources