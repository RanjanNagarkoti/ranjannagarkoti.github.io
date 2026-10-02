# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal portfolio website for Ranjan Nagarkoti, built as a static site using HTML5, CSS3, and minimal JavaScript. The site is hosted on GitHub Pages with a custom domain (www.ranjannagarkoti.com.np).

## Development Workflow

### Local Development

Since this is a static site with no build process, you can view changes locally by serving the directory with a simple HTTP server:

```bash
# Using Python 3
python3 -m http.server 8000

# Or using npm (if available)
npx serve .

# Or using Ruby
ruby -run -e httpd . -p 8000
```

Then open `http://localhost:8000` in your browser to view the site.

### Editing Files

All content is in the root directory:
- `index.html` - Home page
- `tools.html` - Custom development utilities showcase
- `futsal-calculator.html` - A specific tool for futsal calculations
- `privacy.html` - Privacy policy (required for AdSense approval)
- `README.md` - Project documentation
- `CNAME` - Domain configuration for GitHub Pages

Edit these files directly to make changes. The site uses:
- **HTML5** with semantic elements
- **Inline CSS** in `<style>` tags (using CSS variables for theming)
- **Inline JavaScript** in `<script>` tags for interactivity

### CSS Variables

The site defines CSS variables in the `:root` selector for easy theming:
```css
:root {
  --ink: #0f1720;
  --panel: #161f2b;
  /* ... */
}
```
These variables are used throughout the stylesheets for colors, spacing, and other values.

### Responsive Design

The site uses responsive design principles with:
- `meta viewport` tag for mobile scaling
- Relative units and media queries (where applicable)
- Flexible layouts that adapt to different screen sizes

## Code Structure

### HTML Files

Each HTML file follows a similar structure:
1. Doctype and html tag with language attribute
2. Head section containing:
   - Meta charset, viewport, and description
   - Font preconnects and Google Fonts links
   - Inline CSS styles
3. Body section with:
   - Header/navigation
   - Main content sections
   - Footer

### JavaScript

JavaScript is included inline where needed for:
- Interactive form handling (e.g., in futsal-calculator.html)
- Dynamic UI updates
- Event listeners

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch. The `CNAME` file configures the custom domain.

## Adding Analytics and Ads

### Google Analytics

To add Google Analytics tracking:
1. Obtain your Google Analytics 4 measurement ID (starts with `G-`)
2. Add the following script to the `<head>` section of each page you want to track (or just specific pages):
   ```html
   <!-- Google Analytics -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'G-XXXXXXXXXX');
   </script>
   ```

### Google AdSense (for futsal-calculator.html only)

**Important: AdSense approval requirements**
Before adding AdSense code, ensure your site meets these basic requirements for approval:
- Sufficient original, high-quality content (the futsal calculator tool qualifies as a useful utility)
- Clear navigation (the site has consistent header/back links)
- About page (information in README.md and site content)
- Contact information (provided in the site's Contact section)
- Privacy policy (we've created `privacy.html` - see below)
- Site must be at least a few days old with some content

**Privacy Policy**
We have created a `privacy.html` page that explains our use of Google Analytics and AdSense. To complete your AdSense preparation:
1. Review the privacy policy at `/privacy.html` to ensure it accurately reflects your site's use
2. Add a link to the privacy policy in your site footer (see "Common Tasks" below)
3. Link to it from your footer or other appropriate location

**Steps to add AdSense:**
1. Once approved, you'll receive an AdSense publisher ID (like `pub-XXXXXXXXXXXXXXXX`)
2. For auto-ads, add this script to the `<head>` of futsal-calculator.html:
   ```html
   <!-- Google AdSense -->
   <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=pub-XXXXXXXXXXXXXXXX"
     crossorigin="anonymous"></script>
   ```
3. For manual ad placements, add `<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="pub-XXXXXXXXXXXXXXXX"
     data-ad-slot="XXXXXXXXXX"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>`
   plus the script:
   ```html
   <script>
      (adsbygoogle = window.adsbygoogle || []).push({});
   </script>
   ```
4. Place ad units where appropriate (consider user experience - avoid covering calculator inputs)

## Common Tasks

### Updating Content

To update text content, simply edit the relevant HTML files. For example:
- To change the homepage content, edit `index.html`
- To add a new tool, edit `tools.html` or create a new HTML file and link to it

### Styling Changes

To modify colors or spacing:
1. Update the CSS variables in the `:root` selector
2. The changes will propagate throughout the site due to the variable usage

### Adding New Pages

1. Create a new HTML file in the root directory
2. Follow the existing structure (doctype, head with meta/tags/styles, body content)
3. Add navigation links in the header/header section of other pages if needed

### Adding Footer Links

To add a privacy policy link (or other footer links):
1. Edit any HTML file where you want the link to appear (typically in the header or at the bottom of main content)
2. Add a link like: `<a href="/privacy.html">Privacy Policy</a>`
3. Style it appropriately to match your site design (consider using the `--paper-dim` or `--amber` variables for color)

## Notes

- There is no build step, linting, or testing framework configured for this project.
- Changes are visible immediately when viewing the served files.
- Ensure that any external resources (fonts, etc.) are accessible and use HTTPS.
- For AdSense, remember that ads will only be shown on futsal-calculator.html as specified.
- The privacy.html page has been created to help with AdSense approval - please review and link to it from your site.