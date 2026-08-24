# GitHub Pages TiddlyWiki Plugin Library

A lightweight, host-agnostic TiddlyWiki plugin library designed to run on static hosting platforms like **GitHub Pages**, Vercel, Netlify, or Tiddlyhost.

This library uses a secure `window.postMessage` bridge and native TiddlyWiki startup modules to serve plugins without requiring any server-side backend routing.

---

## Features

* **Fully Static & Host-Agnostic:** Can be hosted on any static file server or hosting provider.
* **Startup Module Architecture (`module-type: startup`):** Cleanly boots alongside TiddlyWiki, eliminating race conditions and manual script injection hacks.
* **In-Memory Retrieval:** Extracts requested plugins instantly from the local memory store using `$tw.wiki.getTiddler()`.
* **Robust Asset Compilation:** Dynamically evaluates filters, readmes, and icons (with automatic SVG namespace correction and safe data URI encoding) natively in JavaScript.
* **Data Integrity:** Automatically serializes dates, arrays, and fields into strict TiddlyWiki-compliant strings using `getFieldStrings()`.

---

## How It Works

1. **The Bridge:** When a parent wiki opens the plugin library, it loads this wiki inside a hidden `iframe` and communicates via `window.postMessage`.
2. **The Index (`tiddlers.json`):** The startup script intercepts the request, evaluates the filter defined in `$:/plugins/theophile.dev/githubpluginlibrary/assetList`, and responds with a clean JSON array of available plugins.
3. **The Payload:** When a plugin is selected for installation, the library fetches its fields directly from memory and returns them securely to the parent wiki.

---

## Installation & Setup

1. Import the plugin into your library TiddlyWiki file.
2. Configure your filter inside the `$:/plugins/theophile.dev/githubpluginlibrary/assetList` tiddler.
3. Export/Save your wiki as a static HTML file.
4. Deploy the HTML file to **GitHub Pages** (or your preferred static host).
