# Single File Library

A lightweight, single file TiddlyWiki plugin library designed to run on static hosting platforms like GitHub Pages, Vercel, Netlify, or Tiddlyhost.

## How It Works

1. When a client wiki opens the plugin library, it loads the library inside a hidden `iframe` and communicates via `window.postMessage`.
2. A startup module inside the library intercepts the request, evaluates the `assetList` filter, and responds with a clean JSON array of available plugins.
3. When a plugin is selected for installation, the library fetches its fields directly from the library tiddler store and returns them to the parent wiki.

---

## Installation & Setup

1. Import the plugin into your TiddlyWiki file. 
2. Configure your filter inside the `$:/plugins/theophile.dev/githubpluginlibrary/assetList` tiddler.
3. Deploy the HTML file to your favorite hosting provider (Github Page, Cloudflare Page, Tiddlyhost, etc).

> ⚠️ Your hosting solution must allow iframe embedding.
