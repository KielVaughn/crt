# 📺 CRT Hugo Theme

A retro-futuristic, terminal-inspired Hugo theme designed with a classic CRT aesthetic. Perfect for portfolios, technical writeups, and personal logs that require a high-contrast, vintage digital feel.

## 🚀 Quick Start
### 1. Basic Configuration

Open your hugo.toml (or config.toml) and update the following core settings:

hugo.toml:

```
baseURL = "https://your-domain-or-subdomain.com"
title = "Your Site Title"

[params]
  author = "Your Name"
  description = "A brief bio or site description"
  profile_img = "/images/your-photo.png" # Place file in /static/images/
  github = "your-username"
  linkedin = "your-profile"
  email = "you@example.com"
```

### 2. Branding the Footer

To personalize the terminal footer appearing on every page:

    Navigate to layouts/_default/baseof.html.

    Locate Line 61.

    Replace YOUR NAME HERE with your actual name or handle for the copyright/footer section.

### 3. Deployment (GitHub Pages)

If you are deploying via GitHub Pages with a custom domain:

    Open the CNAME file in the root directory.

    Replace the placeholder text with your actual domain name.

## 📂 Content Organization

To maintain the CRT structure, ensure your files are placed in the correct directories:
### 🎓 Certifications

Directory: /content/certifications/

Each certification should be its own .md file. Refer to the samples provided in the directory for formatting.

    Active: Standard front-matter metadata.

    Archived: Add archived = true to the front-matter to move the badge to the legacy section.

### ✍️ Blog Posts

Directory: /content/blogs/

General articles, experience reviews, and opinion pieces belong here.

### 🚩 CTF Writeups

Directory: /content/ctf-writeups/

Technical walkthroughs and machine captures. To ensure the CRT dashboard categorizes these correctly, use the following front-matter:
YAML

```
title: "Machine Name"
layout: "writeup"
difficulty: "Easy"     # Options: Easy, Medium, Hard, Insane
platform: "TryHackMe"  # Or HackTheBox, OffSec, etc.
os: "Linux"            # Or Windows
```

### 📂 Projects

Directory: /content/projects/

Each project should be its own .md file. Refer to the samples provided in the directory for formatting.

### ⌨️ Skill Scroller Configuration

The typewriter effect on the home page is controlled via JavaScript. To change the rotating text:

    File Path: /static/js/main.js

    Target: const skills (Line 12)

Setup Example:
JavaScript

// Locate this array on Line 12 and modify the strings:
const skills = ["PENETRATION TESTING", "RED TEAMING", "WEB APP SEC", "REVERSE ENGINEERING"]

### 🖼️ Media

Place all images (profile photos, certification badges, and screenshots) in the /static/images/ directory.

Reference them in your markdown files using the path:

![Description](/images/filename.png)

### 🛠️ Customization & Aesthetics

This theme is built to emulate a vintage terminal. To maintain the "System Operator" look:

    Images: Use .png or .svg for certification badges to maintain transparency against the dark background.

    Shortcodes: Use standard Markdown for code blocks to ensure the terminal-style syntax highlighting triggers correctly.

    About Me: Update your professional details in content/whoami.md.
