Getting Started
===============

Prerequisites
-------------
- Node.js and npm (for Cordova tooling, if building as a device app)
- Cordova CLI (optional): `npm i -g cordova`
- A modern browser to run `www/index.html` during development

Project Structure
-----------------
- `www/` contains the web assets (HTML, CSS, JS, images)
- `www/js/index.js` defines the `app` object and lifecycle
- `www/index.html` defines UI, `loadimages()`, and infinite scroll
- `www/spec.html` runs Jasmine tests

Run in Browser
--------------
Open `www/index.html` in a browser. The infinite scroll will request data from the configured endpoint.

Run as Cordova App (optional)
-----------------------------
1. Initialize a Cordova project or use an existing one
2. Copy the `www/` directory into the Cordova project's `www`
3. `cordova platform add android` (or ios)
4. `cordova run android`

Configuration
-------------
- `www/config.xml` contains metadata and preferences for Cordova builds
- Network endpoint for posts is hardcoded in `index.html` under `loadimages()`
