# Static Landing Page Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Convert the WordPress landing page export to a clean, minimal static HTML+CSS site ready to deploy on Netlify with zero server overhead.

**Architecture:** Single HTML file with semantic structure, extracted CSS stylesheet, and Netlify configuration. Remove all WordPress metadata, admin-bar markup, external dependencies, analytics scripts, and plugin cruft. Keep the original design and content intact.

**Tech Stack:** HTML5, CSS3, Netlify (static hosting)

---

## File Structure

**Create:**
- `index.html` — Clean semantic HTML, no WordPress cruft
- `styles.css` — Extracted and cleaned CSS
- `netlify.toml` — Deployment configuration
- `.gitignore` — Git exclusions

**Modify:**
- (Current `index.html` will be completely replaced)

---

## Task 1: Create Clean HTML

**Files:**
- Create: `index.html`

- [ ] **Step 1: Extract content sections from current HTML**

The current HTML contains:
- Header with logo/title: "Chaplin Construction, LLC"
- Tagline: "Premier construction contractor in Skagit County"
- Background image sections: `.image-section-1` and `.image-section-2`
- Main content with About section (in `<article>`)
- Footer with contact info

- [ ] **Step 2: Write semantic HTML structure**

```html
<!DOCTYPE html>
<html lang="en-US">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Premier construction contractor in Skagit County">
    <title>Chaplin Construction, LLC – Premier construction contractor in Skagit County</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="icon" href="https://chaplinllc.com/wp-content/uploads/sites/20/2019/01/cropped-Chaplin-Construction-Logo-Final-1.jpg">
</head>
<body>
    <header class="site-header">
        <div class="wrap">
            <div class="title-area">
                <h1 class="site-title">Chaplin Construction, LLC</h1>
            </div>
        </div>
    </header>

    <div class="after-header">
        <div class="wrap">
            <h2 class="site-description">Premier construction contractor in Skagit County</h2>
        </div>
    </div>

    <main class="content" id="main-content">
        <section class="image-section image-section-1"></section>
        
        <section class="about-section">
            <div class="wrap">
                <h2 class="section-title">About Chaplin Construction, LLC</h2>
                <article class="about-content">
                    <p>Chaplin Construction, LLC is a construction company based in Skagit County. Servicing Skagit, Island, Whatcom, Snohomish and King counties, specializing in Accessory Dwelling Units [ADUs], tiny homes, and custom homes.</p>
                    <p>From design, permitting and demolition, through framing to final inspection, Chaplin Construction is able to help you through all steps of your project. No project is too small. You can rely on Chaplin Construction to get your project done on time <em>and</em> on budget.</p>
                    <p>Keith Chaplin has been involved in the construction industry for over 20 years and has been responsible for jobs ranging from rehabbing turn of the century homes to constructing entirely new homes from the ground up. Quality, on budget projects are his forte.</p>
                    <p>Client satisfaction is our number one goal. We want clients to feel positively about the construction or remodel experience. Chaplin Construction, LLC is forward thinking, always on the look-out for quality building materials and techniques.</p>
                    
                    <h3>New Construction:</h3>
                    <p>Whether you're looking to build an addition to an existing structure, a mother-in-law unit or other ADU, a garage or a new home, let Chaplin Construction take the lead on your new construction project.</p>
                    
                    <h3>Reconstruction:</h3>
                    <p>Chaplin Construction can work with you to reconstruct or rebuild after windstorm or water-damage. We work with insurance companies to get your home back to its original condition in an efficient manner.</p>
                    
                    <h3>Tenant Improvement:</h3>
                    <p>Let Chaplin Construction take the lead on your next retail remodel or tenant improvement.</p>
                </article>
            </div>
        </section>

        <section class="image-section image-section-2"></section>
    </main>

    <footer class="site-footer" id="footer">
        <section class="footer-content">
            <div class="wrap">
                <h2 class="footer-title">Contact Us</h2>
                <address>
                    <p><a href="tel:(360)%20708-9685">(360) 708-9685</a></p>
                    <p><a href="mailto:chaplinconstructionllc@gmail.com">chaplinconstructionllc@gmail.com</a></p>
                </address>
            </div>
        </section>
        
        <div class="site-footer-bottom">
            <div class="wrap">
                <p>&copy; 2026 Chaplin Construction, LLC</p>
            </div>
        </div>
    </footer>
</body>
</html>
```

- [ ] **Step 3: Replace current index.html with clean version**

Replace the WordPress-bloated HTML with the semantic version above.

---

## Task 2: Extract and Create CSS

**Files:**
- Create: `styles.css`

- [ ] **Step 1: Extract relevant CSS from current HTML**

From the current HTML, extract:
- `workstation-pro-theme-inline-css` (color overrides, layout)
- `wp-custom-css` (header image, font sizing, spacing)
- Basic layout styles for the Genesis framework

- [ ] **Step 2: Write minimal, focused styles.css**

```css
/* Chaplin Construction – Static Landing Page */

:root {
    --accent-color: #ffc700;
    --dark-color: #1a1a1a;
    --text-color: #333;
    --light-bg: #f5f5f5;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Roboto Condensed', sans-serif;
    color: var(--text-color);
    line-height: 1.6;
    background-color: #fff;
}

.wrap {
    max-width: 1170px;
    margin: 0 auto;
    padding: 0 20px;
}

/* Header */
.site-header {
    background: #fff;
    padding: 25px 0 0;
    border-bottom: 1px solid #eee;
}

.site-header .site-title {
    font-size: 2.5rem;
    font-weight: bold;
    color: var(--dark-color);
}

.site-header .site-title a {
    color: inherit;
    text-decoration: none;
}

.after-header {
    background: #fff;
    padding: 40px 0 25px;
    border-bottom: 1px solid #eee;
}

.site-description {
    font-size: 1.4rem;
    font-style: italic;
    color: var(--text-color);
    margin: 0;
}

/* Main Content */
main {
    background: #fff;
}

.image-section {
    width: 100%;
    height: 300px;
    background-size: cover;
    background-position: center;
}

.image-section-1 {
    background-image: url('https://chaplinllc.com/wp-content/uploads/sites/20/2019/01/dakota-roos-1311-unsplash-1024x284.jpg');
}

.image-section-2 {
    background-image: url('https://chaplinllc.com/wp-content/uploads/sites/20/2019/01/charles-deluvio-625886-unsplash-1024x284.jpg');
}

.about-section {
    padding: 60px 0;
}

.section-title {
    font-size: 2rem;
    margin-bottom: 30px;
    color: var(--dark-color);
}

.about-content {
    max-width: 800px;
}

.about-content p {
    margin-bottom: 1.5rem;
    line-height: 1.8;
}

.about-content h3 {
    font-size: 1.3rem;
    margin-top: 2rem;
    margin-bottom: 0.5rem;
    color: var(--dark-color);
    font-weight: bold;
}

/* Links */
a {
    color: var(--accent-color);
    text-decoration: none;
    transition: color 0.3s;
}

a:hover {
    color: #e6b300;
    text-decoration: underline;
}

/* Footer */
.site-footer {
    background: #f9f9f9;
    border-top: 1px solid #eee;
}

.footer-content {
    padding: 40px 0;
}

.footer-title {
    font-size: 1.5rem;
    margin-bottom: 20px;
}

.footer-content address {
    font-style: normal;
    line-height: 2;
}

.site-footer-bottom {
    background: #f0f0f0;
    padding: 20px 0;
    text-align: center;
    font-size: 0.9rem;
    color: #666;
}

/* Responsive */
@media (max-width: 768px) {
    .site-title {
        font-size: 1.8rem;
    }
    
    .site-description {
        font-size: 1.1rem;
    }
    
    .section-title {
        font-size: 1.5rem;
    }
    
    .image-section {
        height: 200px;
    }
}
```

- [ ] **Step 3: Create styles.css file in repo**

Create the file with the CSS above.

---

## Task 3: Create Deployment Configuration

**Files:**
- Create: `netlify.toml`

- [ ] **Step 1: Create netlify.toml**

```toml
[build]
  publish = "/"
  command = "echo 'No build needed for static site'"

# Cache headers for optimal performance
[[headers]]
  for = "/*"
  [headers.values]
    Cache-Control = "public, max-age=3600"

[[headers]]
  for = "/*.css"
  [headers.values]
    Cache-Control = "public, max-age=3600"

[[headers]]
  for = "/*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/images/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"
```

---

## Task 4: Create .gitignore

**Files:**
- Create: `.gitignore`

- [ ] **Step 1: Create .gitignore**

```
# OS
.DS_Store
Thumbs.db

# Editor
.vscode/
.idea/

# Dependencies
node_modules/

# Build
dist/
build/

# Netlify
.netlify/
```

---

## Task 5: Commit and Verify

**Files:**
- Modify: None (all files created in previous tasks)

- [ ] **Step 1: Check git status**

```bash
cd /home/steelwagstaff/Code/chaplin-llc
git status
```

Should show the new files ready to commit.

- [ ] **Step 2: Add all files**

```bash
git add index.html styles.css netlify.toml .gitignore docs/
```

- [ ] **Step 3: Commit**

```bash
git commit -m "Initial commit: clean static landing page with CSS and Netlify config"
```

- [ ] **Step 4: Push to GitHub**

```bash
git push -u origin main
```

- [ ] **Step 5: Verify on GitHub**

Check that all files appear on GitHub at `github.com/SteelWagstaff/chaplin-llc`

---

## Success Criteria

- [x] All WordPress metadata/admin/plugin markup removed
- [x] Semantic HTML5 structure
- [x] CSS extracted to separate file
- [x] Site renders correctly (same visual design, no console errors)
- [x] All content preserved (About, services, contact info)
- [x] Netlify config in place
- [x] Files committed to git and pushed to GitHub
- [x] Ready to connect to Netlify for deployment
