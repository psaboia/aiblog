# AI & Software Development Blog

This is a personal blog built with Jekyll and hosted on GitHub Pages, focusing on AI and software development topics.

## Features

### 🔍 Search
- Full-text search functionality powered by [Lunr.js](https://lunrjs.com/)
- Search through all blog posts' titles and content
- Real-time search results as you type
- Search box in the header for quick access
- Dedicated search page with detailed results at `/search/`

### 💬 Comments
- Commenting system powered by [Disqus](https://disqus.com/)
- Support for nested comment threads
- Social media login integration
- Comment moderation capabilities
- Spam protection

### ❤️ Post Reactions
- Like/unlike functionality for each post
- Heart button with counter
- Persistent likes using browser's localStorage
- Visual feedback for liked posts

## Local Development

To run this blog locally:

1. Install Ruby and Bundler
2. Clone this repository
3. Run `bundle install` to install dependencies
4. Run `bundle exec jekyll serve` to start the local server
5. Visit `http://localhost:4000/aiblog` in your browser

### About `bundle exec jekyll serve`

This command starts a local development server with several useful features:

- **Live Preview**: Starts a local web server at `http://localhost:4000/aiblog`
- **Auto-regeneration**: Automatically rebuilds the site when you make changes to any files
- **Local Testing**: Test your site's appearance and functionality before deploying
- **Dependency Management**: Ensures Jekyll runs with the correct gem versions from your Gemfile

When you run this command, you'll see output like:
```
Configuration file: /Users/pmoreira/aiblog/_config.yml
            Source: /Users/pmoreira/aiblog
       Destination: /Users/pmoreira/aiblog/_site
 Incremental build: disabled
      Generating... 
       Jekyll Feed: Generating feed for posts
                    done in 0.108 seconds.
 Auto-regeneration: enabled
    Server address: http://127.0.0.1:4000/aiblog/
```

To stop the server, press `Ctrl+C` in your terminal.

## Contributing

This is a personal blog, but if you find any issues or have suggestions, feel free to open an issue or submit a pull request.

## License

Content is copyrighted. Code is MIT licensed.
