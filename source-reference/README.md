# Source reference (split files)

This folder contains the same app as the root `index.html`, split into separate files so it is easier to read and edit:

- `css/artifact-reset.css`: the small reset stylesheet from the top of the published file.
- `css/styles.css`: the app's full stylesheet, copied verbatim.
- `js/app.js`: the app's full JavaScript, copied verbatim.
- `index.html`: the HTML shell, linking the two stylesheets and the script.

The code is identical to the root `index.html`; only the packaging differs. It was tested to load and navigate without errors. Like the root `index.html`, it loads fonts from Google Fonts and the QR libraries from CDNs.

The root `index.html` remains the authoritative copy. If you edit here, test the result before deploying it.
