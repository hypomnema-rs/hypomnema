# Hypomnema

> A Stoic CMS for the undistracted developer

Hypomnema is a fast, single-binary content management system written in Rust. It serves Markdown files from a Git repository with zero configuration, no database, and no admin interface.

## Philosophy

**Do one thing well:** Serve markdown as HTML.

If you're tired of Ghost's complexity, WordPress's bloat, or React-based CMSs that require a PhD to configure, Hypomnema is for you.

No admin panels. No databases. No JavaScript frameworks. Just your editor, your markdown files, and your words.

## Features

- 🦀 **Single binary** - No dependencies, no runtime, just one executable
- 📝 **Markdown-first** - Write in markdown, serve as HTML
- 🔄 **Hot reload** - Changes appear instantly via file watching
- 🏷️ **Frontmatter** - YAML metadata for posts (title, date, tags, etc.)
- 🎨 **Templates** - Clean, minimal default theme (customizable)
- 📡 **RSS feed** - Built-in feed generation
- 🚀 **Fast** - Rust performance with in-memory caching
- 🔒 **Git-friendly** - Version control your content naturally

## Installation
```bash
# From source (requires Rust)
cargo install hypomnema

# Or download binary from releases
# Coming soon...
```

## Quick Start
```bash
# Create a directory for your content
mkdir my-blog && cd my-blog

# Initialize with Git (optional)
git init
mkdir content/posts

# Create your first post
cat > content/posts/hello.md <<EOF
---
title: "Hello World"
date: 2025-01-15
tags: [rust, blogging]
---

# My First Post

This is my blog, powered by **Hypomnema**.
EOF

# Start the server
hypomnema serve

# Visit http://localhost:3000
```

## Configuration

Create a `config.toml` in your project root:
```toml
title = "My Blog"
base_url = "https://example.com"
port = 3000
content_dir = "./content"
```

That's it. No complex configuration files, no environment variables, no magic.

## Content Structure
```
my-blog/
├── content/
│   ├── posts/
│   │   ├── first-post.md
│   │   └── second-post.md
│   └── pages/
│       └── about.md
├── templates/          # (optional) Override defaults
│   ├── base.html
│   ├── post.html
│   └── list.html
├── static/             # (optional) CSS, images
│   └── style.css
├── config.toml
└── .git/
```

## Frontmatter
```yaml
---
title: "Post Title"
date: 2025-01-15
slug: custom-slug      # optional, defaults to filename
draft: false           # optional, defaults to false
tags: [rust, cms]      # optional
---

Your markdown content here...
```

## Deployment

### With Git
```bash
# On your server
git clone git@github.com:you/blog-content.git
cd blog-content
hypomnema serve --port 8080

# Update content
git pull
# Hypomnema auto-reloads via file watcher
```

### With systemd
```ini
[Unit]
Description=Hypomnema Blog
After=network.target

[Service]
Type=simple
User=www-data
WorkingDirectory=/var/www/blog
ExecStart=/usr/local/bin/hypomnema serve
Restart=always

[Install]
WantedBy=multi-user.target
```

## Why "Hypomnema"?

Hypomnema (ὑπομνήματα) refers to the Stoic practice of keeping personal notes and records — a collection of knowledge meant for reflection and growth.

Just as the Stoics believed in clarity and purpose, Hypomnema cuts through the noise of modern CMSs to deliver exactly what you need: a way to publish your thoughts without distraction.

## Anti-Features

Things Hypomnema will **never** have:

- ❌ Admin UI / Dashboard
- ❌ Database
- ❌ User authentication
- ❌ Comments system
- ❌ Plugin architecture
- ❌ WYSIWYG editor
- ❌ Automatic Git operations
- ❌ JavaScript framework dependency

If you need these, use Ghost, WordPress, or another CMS. Hypomnema is intentionally minimal.

## Roadmap

### v0.1 (MVP) - Current
- [ ] Basic markdown rendering
- [ ] Frontmatter parsing
- [ ] File watcher
- [ ] Template system
- [ ] RSS feed
- [ ] Tag pages

### v0.2
- [ ] Syntax highlighting
- [ ] Search
- [ ] Table of contents
- [ ] Related posts

### Not Planned
See "Anti-Features" above.

## Contributing

Contributions are welcome, but please keep the philosophy in mind: **radical simplicity**.

Before adding a feature, ask: "Does this make Hypomnema more complex?" If yes, reconsider.

Open an issue to discuss features before submitting PRs.

## Inspiration

- [Zola](https://www.getzola.org/) - Static site generator in Rust
- [Bear Blog](https://bearblog.dev/) - Minimalist blogging
- Stoic philosophy - Do what matters, ignore the rest

**Built with Rust 🦀 • Inspired by Stoicism 🏛️**

## License

Hypomnema is dual-licensed under either:

* MIT License ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)
* Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in Hypomnema by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
