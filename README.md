# Infini-Change

**Education & Action for Positive Human Change**

A static website built with Jekyll and hosted on GitHub Pages, dedicated to providing educational resources and actionable steps toward creating a world where all humans are ensured the necessities of life.

---

## Quick Start

### Prerequisites
- **Ruby** (version 2.6 or higher)
- **Bundler** (Ruby gem manager)
- **Git** (for version control)

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/Infini-Change.git
   cd Infini-Change
   ```

2. **Install dependencies:**
   ```bash
   # Set up local gem installation (avoids permission issues)
   export GEM_HOME="$PWD/vendor/bundle/ruby/2.6.0"
   export GEM_PATH="$GEM_HOME"
   export PATH="$GEM_HOME/bin:$PATH"

   # Install bundler and dependencies
   gem install bundler -v 2.4.22 --no-document
   bundle install
   ```

3. **Start the development server:**
   ```bash
   bundle exec jekyll serve
   ```

4. **View your site:**
   Open [http://127.0.0.1:4000](http://127.0.0.1:4000) in your browser.

### Deploying to GitHub Pages

1. Make your changes locally and test with `jekyll serve`
2. Commit your changes:
   ```bash
   git add .
   git commit -m "Description of changes"
   ```
3. Push to GitHub:
   ```bash
   git push origin main
   ```
4. GitHub Pages will automatically rebuild your site (usually within 1-2 minutes)

---

## Project Structure

```
Infini-Change/
├── _config.yml          # Site configuration (title, description)
├── _includes/           # Reusable HTML components
│   ├── header.html      # Site header and navigation
│   └── footer.html      # Site footer
├── _layouts/            # Page templates
│   └── default.html     # Main page template
├── assets/
│   ├── css/
│   │   └── style.css    # All site styles
│   └── images/          # Logo and other images
├── index.md             # Homepage content
├── about.md             # About page content
├── education.md         # Education page content
├── action.md            # Action page content
├── Gemfile              # Ruby dependencies
└── README.md            # This file
```

---

## Documentation

For detailed documentation on maintaining and expanding this site, see:

- **[MAINTAINERS_GUIDE.md](MAINTAINERS_GUIDE.md)** - Comprehensive guide for editing and expanding the site

---

## Technology Stack

- **Jekyll** - Static site generator (converts Markdown to HTML)
- **GitHub Pages** - Free hosting for static sites
- **Markdown** - Simple formatting language for content
- **CSS** - Styling (no frameworks, pure CSS)

---

## Contributing

This site was initially built with AI assistance and is designed to be maintainable by contributors with limited web development experience. See the [MAINTAINERS_GUIDE.md](MAINTAINERS_GUIDE.md) for detailed instructions.

---

## License

This project is open source and available for educational purposes.

---

## Contact

Created by Nish - dedicated to driving positive change through education and action.
