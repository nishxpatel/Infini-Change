# Infini-Change Maintainer's Guide

**A comprehensive guide for editing and expanding the Infini-Change website**

This guide is written for contributors who may not have extensive web development experience. If you're familiar with Python but new to web development, this guide will help you understand how everything works.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Understanding Jekyll](#understanding-jekyll)
3. [File Structure Explained](#file-structure-explained)
4. [Editing Existing Content](#editing-existing-content)
5. [Adding New Content](#adding-new-content)
6. [Styling Basics](#styling-basics)
7. [Local Preview](#local-preview)
8. [Deployment](#deployment)
9. [Troubleshooting](#troubleshooting)
10. [Future Expansion Ideas](#future-expansion-ideas)
11. [Getting Help](#getting-help)

---

## Project Overview

Infini-Change is a **static website** - meaning it's just HTML, CSS, and images with no database or server-side code. We use **Jekyll** to make creating and editing content easier.

### How It Works (Simple Version)

1. You write content in **Markdown** files (`.md`) - a simple text format
2. Jekyll converts these to HTML pages
3. The HTML pages are styled with CSS
4. GitHub Pages hosts the final website for free

### Key Technologies

| Technology | What It Does | You Need to Know |
|------------|--------------|------------------|
| **Markdown** | Simple text formatting | Basic syntax (headers, links, lists) |
| **Jekyll** | Converts Markdown to HTML | Just the basics covered here |
| **HTML** | Structure of web pages | Optional - Markdown handles most cases |
| **CSS** | Visual styling | Optional - existing styles cover most needs |

---

## Understanding Jekyll

Jekyll is a "static site generator." Think of it like a template system:

### The Magic of Templates

Instead of copying the same header and footer into every page, Jekyll lets you define them once and reuse them everywhere.

```
Your Markdown File (index.md)
        ↓
   + Layout Template (default.html)
   + Header Include (header.html)
   + Footer Include (footer.html)
        ↓
   Final HTML Page
```

### Jekyll's Special Syntax

Jekyll uses **Liquid** template tags. You'll see these in the HTML files:

```html
{{ variable }}     <!-- Outputs a variable's value -->
{% include x %}    <!-- Includes another file -->
{% if condition %} <!-- Conditional logic -->
```

**You don't need to understand these deeply** - just know they exist and avoid accidentally deleting them.

---

## File Structure Explained

```
Infini-Change/
│
├── _config.yml              # SITE SETTINGS
│   └── Site title, description, URL settings
│
├── _includes/               # REUSABLE COMPONENTS
│   ├── header.html          # The site header (logo, navigation)
│   └── footer.html          # The site footer (links, copyright)
│
├── _layouts/                # PAGE TEMPLATES
│   └── default.html         # The main template all pages use
│
├── assets/                  # STATIC FILES
│   ├── css/
│   │   └── style.css        # ALL THE STYLING
│   └── images/
│       ├── infinity-16.png  # Small favicon
│       └── infinity-512.png # Logo image
│
├── index.md                 # HOMEPAGE CONTENT
├── about.md                 # ABOUT PAGE CONTENT
├── education.md             # EDUCATION PAGE CONTENT
├── action.md                # ACTION PAGE CONTENT
│
├── Gemfile                  # Ruby dependencies (don't edit)
├── Gemfile.lock             # Dependency versions (don't edit)
├── README.md                # Project overview
└── MAINTAINERS_GUIDE.md     # This file!
```

### What Each File Type Does

| File Extension | Purpose | How to Edit |
|----------------|---------|-------------|
| `.md` | Content pages | Edit the text directly |
| `.html` | Templates/components | Edit carefully, preserve `{{ }}` tags |
| `.css` | Styling | Modify colors, sizes, spacing |
| `.yml` | Configuration | Key: value format |
| `.png/.jpg` | Images | Replace with same filename |

---

## Editing Existing Content

### Editing Page Text

All main content is in Markdown files. Here's how to edit each page:

#### Homepage (`index.md`)

```markdown
---
layout: default
title: Home
---

<!-- Everything below the --- section is your content -->

<div class="hero">
  <h1 class="hero-title">Welcome to Infini-Change</h1>
  <p class="hero-subtitle">
    Your subtitle text here...
  </p>
</div>
```

**To change the main headline:** Find `<h1 class="hero-title">` and edit the text inside.

**To change the subtitle:** Find `<p class="hero-subtitle">` and edit the text inside.

#### About Page (`about.md`)

Find the section you want to edit. The structure is:

```html
<div class="content-section">
  <h2>Section Title</h2>
  <p>Paragraph text goes here...</p>
</div>
```

#### Education Page (`education.md`)

This page has many sections. Use the section IDs to find what you need:

| Section | Look for this ID |
|---------|------------------|
| Starting Point | `id="starting-point"` |
| Books | `id="books"` |
| Videos | `id="videos"` |
| Podcasts | `id="podcasts"` |
| Notes | `id="notes"` |
| Opinions | `id="opinions"` |
| Anti-Capitalism | `id="anti-capitalism"` |
| Socialism | `id="socialism"` |
| (etc.) | ... |

#### Action Page (`action.md`)

Similar structure to Education. Look for section IDs:

| Section | Look for this ID |
|---------|------------------|
| Electoralism | `id="electoralism"` |
| Unionization | `id="unionization"` |
| Recruiting | `id="recruiting"` |
| (etc.) | ... |

### Editing Links

Links follow this pattern:

```html
<a href="URL_HERE">Link Text</a>
```

**External link example:**
```html
<a href="https://www.example.com" target="_blank" rel="noopener">Visit Example</a>
```

**Internal link example:**
```html
<a href="{{ '/education' | relative_url }}">Go to Education</a>
```

The `{{ '/education' | relative_url }}` part is Jekyll magic - it creates the correct URL automatically.

### Editing Navigation

The navigation is in `_includes/header.html`. Each nav link looks like:

```html
<a href="{{ '/about' | relative_url }}" class="nav-link">
  <span class="nav-icon">&#128100;</span>
  About
</a>
```

To add a new nav link, copy this pattern and change:
- The URL (`'/about'` → `'/your-new-page'`)
- The icon (the `&#...;` code)
- The text (`About` → `Your Page Name`)

---

## Adding New Content

### Adding a New Resource (Book, Video, etc.)

Find the appropriate section in `education.md` and copy an existing resource card:

```html
<div class="resource-card">
  <div class="resource-type">Book</div>
  <h4>"Book Title Here"</h4>
  <p class="resource-author">by Author Name</p>
  <p>Description of the book goes here. Keep it to 2-3 sentences.</p>
</div>
```

**Steps:**
1. Find the `<div class="resource-grid">` for your category
2. Copy an existing `<div class="resource-card">...</div>` block
3. Paste it after the last resource card
4. Edit the type, title, author, and description

### Adding a New Action Item

In `action.md`, copy an existing action card:

```html
<div class="action-card">
  <div class="action-icon">&#128269;</div>
  <h4>Action Title</h4>
  <p>Brief description of this action.</p>
  <div class="action-steps">
    <h5>Concrete Steps:</h5>
    <ul>
      <li>Step one</li>
      <li>Step two</li>
    </ul>
  </div>
  <div class="resource-box">
    <strong>Key Resources:</strong>
    <ul>
      <li><a href="URL">Resource Name</a></li>
    </ul>
  </div>
</div>
```

### Creating a New Page

1. **Create the file:** Create a new `.md` file in the root directory (e.g., `newpage.md`)

2. **Add the front matter:** Every page needs this at the top:
   ```markdown
   ---
   layout: default
   title: Your Page Title
   ---
   ```

3. **Add your content:** Below the `---`, add your HTML/Markdown content

4. **Add navigation link:** Edit `_includes/header.html` to add a link

**Example new page (`resources.md`):**

```markdown
---
layout: default
title: Resources
---

<div class="hero">
  <h1 class="hero-title">Additional Resources</h1>
  <p class="hero-subtitle">More materials for your journey.</p>
</div>

<div class="content-section">
  <h2>Websites</h2>
  <ul>
    <li><a href="https://example.com">Example Site</a> - Description</li>
  </ul>
</div>
```

### Adding Images

1. Add your image to `assets/images/`
2. Reference it in your content:
   ```html
   <img src="{{ '/assets/images/your-image.png' | relative_url }}" alt="Description">
   ```

---

## Styling Basics

All styles are in `assets/css/style.css`. Here are the most common things you might want to change:

### Changing Colors

At the top of the CSS file, you'll find color variables:

```css
:root {
  --primary-color: #2563eb;      /* Main blue color */
  --primary-dark: #1d4ed8;       /* Darker blue for hover states */
  --secondary-color: #10b981;    /* Green accent */
  --accent-color: #8b5cf6;       /* Purple accent */
  --dark-bg: #0f172a;            /* Dark background (header/footer) */
  --light-bg: #f8fafc;           /* Light gray background */
  --text-primary: #1e293b;       /* Main text color */
  --text-secondary: #64748b;     /* Secondary/muted text */
}
```

**To change the primary color scheme:** Edit these values. Use a tool like [coolors.co](https://coolors.co) to find complementary colors.

### Common CSS Classes

| Class | What It Styles | Used For |
|-------|----------------|----------|
| `.hero` | Large intro section | Page headers |
| `.content-section` | White card with shadow | Main content blocks |
| `.btn` | Button styling | Clickable buttons |
| `.btn-primary` | Blue filled button | Primary actions |
| `.btn-secondary` | Blue outlined button | Secondary actions |
| `.feature-card` | Card in a grid | Homepage features |
| `.resource-card` | Resource item card | Books, videos, etc. |
| `.action-card` | Action item card | Action page items |

### Adding Custom Styles

Add new styles at the bottom of `style.css`:

```css
/* My Custom Styles */
.my-custom-class {
  color: red;
  font-size: 20px;
}
```

Then use it in your HTML:
```html
<p class="my-custom-class">This text is red and 20px.</p>
```

---

## Local Preview

### Starting the Server

```bash
# Navigate to project folder
cd /path/to/Infini-Change

# Set up environment (required each terminal session)
export GEM_HOME="$PWD/vendor/bundle/ruby/2.6.0"
export GEM_PATH="$GEM_HOME"
export PATH="$GEM_HOME/bin:$PATH"

# Start Jekyll
bundle exec jekyll serve
```

### Viewing Changes

1. Open [http://127.0.0.1:4000](http://127.0.0.1:4000) in your browser
2. Make changes to your files
3. Save the files
4. **Refresh your browser** - Jekyll automatically rebuilds

### Stopping the Server

Press `Ctrl + C` in the terminal.

---

## Deployment

### Automatic Deployment via GitHub Pages

Every time you push to the `main` branch, GitHub automatically rebuilds and deploys your site.

### Step-by-Step Deployment

1. **Make sure everything works locally first!**

2. **Check what changed:**
   ```bash
   git status
   ```

3. **Stage your changes:**
   ```bash
   git add .
   ```
   Or stage specific files:
   ```bash
   git add index.md education.md
   ```

4. **Commit with a descriptive message:**
   ```bash
   git commit -m "Add new book to education resources"
   ```

5. **Push to GitHub:**
   ```bash
   git push origin main
   ```

6. **Wait 1-2 minutes** for GitHub to rebuild

7. **Check your live site** to confirm changes

---

## Troubleshooting

### "Page Not Found" (404 Error)

**Possible causes:**
- File doesn't exist or is named incorrectly
- Missing front matter (the `---` section at the top)
- Navigation link points to wrong URL

**Fix:** Check that your file:
1. Is in the root directory (not in a subfolder)
2. Has the `.md` extension
3. Has correct front matter
4. Is linked correctly in navigation

### Styles Not Applying

**Possible causes:**
- Typo in class name
- CSS file has syntax error
- Browser cache

**Fix:**
1. Check class names match exactly (case-sensitive!)
2. Look for missing semicolons or brackets in CSS
3. Hard refresh: `Ctrl + Shift + R` (Windows) or `Cmd + Shift + R` (Mac)

### Jekyll Won't Start

**Possible causes:**
- Dependencies not installed
- Ruby environment not set up

**Fix:**
```bash
# Re-run the setup
export GEM_HOME="$PWD/vendor/bundle/ruby/2.6.0"
export GEM_PATH="$GEM_HOME"
export PATH="$GEM_HOME/bin:$PATH"
bundle install
bundle exec jekyll serve
```

### Changes Not Showing on Live Site

**Possible causes:**
- Didn't push to GitHub
- GitHub Pages still building
- Browser cache

**Fix:**
1. Confirm you ran `git push`
2. Check GitHub repo → Actions tab for build status
3. Wait 2-3 minutes
4. Hard refresh the page

---

## Future Expansion Ideas

### Easy Additions
- More book/video resources
- Additional opinion pieces
- New action items with resources
- Updated "Thought of the Day"

### Medium Complexity
- New topic pages (e.g., Climate Education)
- Blog/news section using Jekyll posts
- Search functionality
- Newsletter signup (requires external service)

### Advanced
- Multi-language support
- Interactive calculators or tools
- Database-driven content (would need different hosting)

---

## Getting Help

### AI Assistance

This site was built with AI assistance. You can continue using Claude or similar AI tools to:
- Debug issues
- Add new features
- Understand code you're not sure about
- Generate new content sections

**Tip:** When asking for help, share:
- What you're trying to do
- What you've tried
- Any error messages you see
- The relevant code/file

### Learning Resources

- **Markdown:** [Markdown Guide](https://www.markdownguide.org/)
- **Jekyll:** [Jekyll Documentation](https://jekyllrb.com/docs/)
- **CSS:** [MDN CSS Basics](https://developer.mozilla.org/en-US/docs/Learn/CSS)
- **Git:** [Git Handbook](https://guides.github.com/introduction/git-handbook/)

### Common Questions

**Q: Do I need to know HTML/CSS?**
A: For basic content editing, no. For styling changes, basic CSS knowledge helps.

**Q: Can I break the site?**
A: It's hard to permanently break it. Git keeps history of all changes, so you can always revert.

**Q: How do I undo a mistake?**
A: If you haven't pushed yet: `git checkout -- filename` reverts a file. If you have pushed, you can revert commits.

---

## Quick Reference Card

### File Locations
| Task | File to Edit |
|------|--------------|
| Homepage content | `index.md` |
| About page | `about.md` |
| Education content | `education.md` |
| Action content | `action.md` |
| Navigation menu | `_includes/header.html` |
| Footer | `_includes/footer.html` |
| Styling | `assets/css/style.css` |
| Site title/description | `_config.yml` |

### Common Commands
```bash
# Start local server
bundle exec jekyll serve

# Check git status
git status

# Stage all changes
git add .

# Commit changes
git commit -m "Your message"

# Push to GitHub
git push origin main
```

### HTML Patterns to Copy

**Add a section:**
```html
<div class="content-section">
  <h2>Section Title</h2>
  <p>Content here...</p>
</div>
```

**Add a resource card:**
```html
<div class="resource-card">
  <div class="resource-type">Type</div>
  <h4>"Title"</h4>
  <p class="resource-author">by Author</p>
  <p>Description...</p>
</div>
```

**Add a button:**
```html
<a href="URL" class="btn btn-primary">Button Text</a>
```

---

*This guide was created to empower independent maintenance of the Infini-Change website. You've got this!* ✊
