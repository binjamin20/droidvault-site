DroidVault — APK Store
=======================

This folder contains your complete website. Just upload everything inside
this folder to any web host (Netlify, Vercel, GitHub Pages, cPanel, your
own server, etc.) and your site is live.

------------------------------------------------------------
HOW TO ADD / EDIT / REMOVE APPS
------------------------------------------------------------

Open the file:  apps.json

Each app is one block like this:

  {
    "id": "my-app",
    "name": "My App",
    "tagline": "Short one-line description",
    "fullDescription": "Long description. Use \\n\\n for paragraph breaks.",
    "category": "Tools",
    "version": "1.0.0",
    "sizeMb": 25,
    "iconUrl": "images/my-icon.png",
    "screenshots": [
      "images/my-screen-1.png",
      "images/my-screen-2.png"
    ],
    "downloadUrl": "https://drive.google.com/uc?id=YOUR_FILE_ID&export=download",
    "downloadsBase": 0
  }

Rules:
- "id" must be unique and use only lowercase letters, numbers, and dashes.
- "category" must be one of:  Games, Tools, Social, Productivity, Entertainment
- "iconUrl" and "screenshots" can be either:
     a) a path to an image inside this folder, e.g. "images/my-icon.png"
        (drop the image file inside the "images" folder first)
     b) a full URL to an image hosted anywhere, e.g.
        "https://i.imgur.com/abc.png"
- "downloadUrl" is the public link to your .apk file.
  For Google Drive, use the direct-download format:
     https://drive.google.com/uc?id=FILE_ID&export=download
- Don't forget the comma between each app block.
- After saving apps.json, just refresh your browser. No rebuild needed.

------------------------------------------------------------
HOW TO REPLACE THE LOGO / FAVICON
------------------------------------------------------------

- Favicon: replace  favicon.svg
- Open Graph share image: replace  opengraph.jpg  (1200x630 recommended)

------------------------------------------------------------
HOW TO HOST
------------------------------------------------------------

Easiest free options:

1. Netlify Drop  ->  https://app.netlify.com/drop
   Drag this entire folder onto the page. Done.

2. GitHub Pages
   - Create a new repo
   - Upload everything from this folder
   - Enable Pages in repo settings (branch: main, folder: /root)

3. Your own server (Apache / Nginx / cPanel)
   - Upload everything to your public_html (or equivalent) folder.
   - The site is fully static, no server-side code needed.

IMPORTANT: This site uses client-side routing. If your host returns a 404
when refreshing /app/something, add a redirect rule to send all unknown
paths to index.html. Examples:

  Netlify:  add a file named "_redirects" with one line:
            /*    /index.html   200

  Apache:   add a .htaccess file with:
            RewriteEngine On
            RewriteRule ^index\.html$ - [L]
            RewriteCond %{REQUEST_FILENAME} !-f
            RewriteCond %{REQUEST_FILENAME} !-d
            RewriteRule . /index.html [L]

That's it. Enjoy!
