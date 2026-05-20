# Preview Website Locally

Start the local development server to preview the current state of the website.

## Instructions

1. Kill any existing server on port 8001.
2. Start `python3 -m http.server 8001` in the background from the project root.
3. Tell the user the site is available at http://localhost:8001.
   (Port 8000 belongs to Jose's Swing Trader platform — don't use it.)
4. If the user reports issues, check for common problems:
   - Missing images (check `images/` directory for referenced files)
   - Broken links (check `href` attributes)
   - Layout issues (check inline styles and CSS classes)
