# babixGO Website v2

Migrated to Eleventy (11ty) static site generator.

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- npm

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

This starts a local development server with live reload at `http://localhost:8081`.

### Build

```bash
npm run build
```

This generates static files in the `dist/` directory.

## 🎯 SEO Features (Phase 2)

All pages include:
- **Meta tags**: Title, description, robots
- **Canonical URLs**: Proper canonical links for each page
- **Open Graph**: Full OG tags with fallbacks
- **Twitter Cards**: Summary large image cards
- **Sitemap**: Auto-generated `/sitemap.xml`
- **Structured Data**: JSON-LD for Organization, WebSite, and HowTo (where applicable)

## 📁 Project Structure

```
org-web1/
├── src/                          # Source files
│   ├── _includes/               # Templates and partials
│   │   ├── layouts/             # Page layouts
│   │   │   └── base.njk         # Base layout template
│   │   └── partials/            # Reusable components
│   │       ├── header.njk       # Site header
│   │       ├── footer.njk       # Site footer
│   │       └── cookie-banner.njk # Cookie consent banner
│   ├── assets/                  # Static assets
│   │   ├── css/                 # Stylesheets
│   │   ├── icons/               # SVG icons
│   │   └── logo/                # Logo files
│   ├── public/                  # Public downloads
│   ├── index.njk                # Homepage (downloads)
│   ├── impressum/               # Legal pages
│   ├── datenschutz/             # Privacy policy
│   ├── downloads/               # Downloads page
│   ├── anleitungen/             # Guides/tutorials
│   ├── 404.njk                  # 404 error page
│   └── robots.txt               # SEO robots file
├── dist/                        # Built files (not in git)
├── eleventy.config.js           # Eleventy configuration
├── package.json                 # Dependencies
└── README.md                    # This file
```

## 🌐 Deployment to Strato (Apache Shared Hosting)

### Important Notes
- **Eleventy runs locally or in CI only** - the server cannot run Node.js
- **Deploy only the `dist/` folder contents** to your webroot

### Deployment Steps

1. **Build the site locally:**
   ```bash
   npm run build
   ```

2. **Upload `dist/` contents to Strato:**
   - Connect via FTP/SFTP to your Strato hosting
   - Navigate to your webroot directory (usually `/` or `/public_html/`)
   - Upload **all contents** from the `dist/` folder (including `.htaccess`)
   - **Important**: `.htaccess` must be uploaded to enable redirects and caching

3. **Verify deployment:**
   - Visit your domain
   - Check that all pages load correctly
   - Test old URLs redirect (e.g., `/impressum_page.html` → `/impressum/`)
   - Test CSS and images
   - Verify 404 page works
   - Check that `.htaccess` is active (proper caching headers, redirects)

### File Transfer Options
- FTP client (FileZilla, Cyberduck, etc.)
- SFTP
- Strato's web-based file manager

## 🛠 Technology Stack

- **Static Site Generator:** Eleventy 2.0.1
- **Template Engine:** Nunjucks
- **CSS:** Plain CSS (no preprocessor)
- **JavaScript:** Vanilla JS (cookie banner, year auto-update)

## 📝 Pages

- `/` - Homepage/Downloads page
- `/downloads/` - Downloads (duplicate of homepage)
- `/impressum/` - Imprint/Legal notice
- `/datenschutz/` - Privacy policy
- `/anleitungen/freundschaftsbalken-fuellen/` - Tutorial page
- `/404.html` - Custom 404 error page

## 🔧 Maintenance

### Adding a New Page

1. Create a new `.njk` file in `src/` (or appropriate subdirectory)
2. Add frontmatter with title, description, etc.
3. Use the base layout: `layout: layouts/base.njk`
4. Add your content
5. Build and deploy

### Updating Content

1. Edit the `.njk` file in `src/`
2. Run `npm run build`
3. Upload the updated `dist/` contents to Strato

### Modifying Header/Footer

Edit the partials in `src/_includes/partials/`:
- `header.njk` - Navigation and logo
- `footer.njk` - Footer links and copyright
- `cookie-banner.njk` - Cookie consent

## 📦 Build Output

The `dist/` folder contains:
- Static HTML files
- CSS and assets
- `.htaccess` (Apache configuration with redirects and caching)
- `robots.txt`
- `sitemap.xml`
- Public downloads folder
- 404.html

**Note:** The `dist/` folder is excluded from git via `.gitignore`.

## 🔒 Apache/Strato Features (Phase 3)

The generated `.htaccess` file provides:

### URL Redirects
- **301 redirects** for old v1 URLs:
  - `/impressum_page.html` → `/impressum/`
  - `/datenschutz_page.html` → `/datenschutz/`
- Clean URL handling (removes `index.html` from URLs)

### Caching Strategy
- **HTML files**: No cache (always fresh)
- **CSS/JS**: 1 month cache
- **Images/Fonts**: 3 months cache (moderate, no aggressive caching)
- All wrapped in `<IfModule>` for safety

### Compression
- **mod_deflate** enabled (if available) for:
  - HTML, CSS, JavaScript
  - JSON, XML
  - SVG images

### Security Headers
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: SAMEORIGIN`
- `Referrer-Policy: strict-origin-when-cross-origin`
- All headers wrapped in `<IfModule>` blocks

### Error Handling
- Custom 404 error page (`/404.html`)

**Note:** All Apache directives are wrapped in `<IfModule>` blocks to prevent errors if modules are unavailable on Strato.

## 🚫 What NOT to Commit

- `node_modules/` - Dependencies (install with `npm install`)
- `dist/` - Build output (generated with `npm run build`)
- `.DS_Store` - macOS system files

## 📞 Support

For questions or issues:
- WhatsApp: +49 152 23842897
- Email: info@babixgo.de
- Facebook: [babixGO](https://www.facebook.com/share/1DC2snqois/)

---

**Version:** 2.0.0  
**Last Updated:** January 2026
