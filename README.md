# Cozy Zone

Cozy Zone is a cat-themed browser game collection with soft visuals, calming mini games, and a lightweight AI-powered mystery feature.

## Highlights

- Cozy, cat-inspired game cards and screens
- A simple `index.html` entry page for Netlify
- A server-side AI proxy powered by Netlify Functions
- Groq-backed AI that keeps your API key private
- No framework required: just static HTML, CSS, and JavaScript

## Project files

- [`cozy-zone.html`](./cozy-zone.html) - main app experience
- [`index.html`](./index.html) - Netlify entry page that redirects to the app
- [`netlify.toml`](./netlify.toml) - Netlify build and redirect config
- [`netlify/functions/ai.js`](./netlify/functions/ai.js) - AI proxy endpoint

## How the AI works

The browser does not call Groq directly.

Instead:

1. The app sends a `POST` request to `/api/ai`
2. Netlify forwards that request to a serverless function
3. The function reads `GROQ_API_KEY` from Netlify environment variables
4. The function calls Groq and returns only the generated text

This avoids browser CORS issues and keeps your API key off the client.

## Required Netlify environment variables

Set this in your Netlify site settings:

- `GROQ_API_KEY` - your Groq API key

Optional:

- `GROQ_MODEL` - defaults to `llama-3.3-70b-versatile`

## Deploy on Netlify

1. Push this repo to GitHub.
2. In Netlify, choose `Add new site` -> `Import an existing project`.
3. Select this repository.
4. Keep the publish directory as `.`.
5. Add `GROQ_API_KEY` in environment variables.
6. Deploy.

Once deployed, the site root will load `index.html`, which redirects to the main app.

## Local development

You can open the app locally for UI testing, but AI features will only work when the site is served through Netlify or `netlify dev`.

If you open `cozy-zone.html` directly with `file://`, browser security will block the AI request flow.

## Notes

- The old color game has been removed.
- The cards are now cat-themed.
- The AI feature is designed for cozy mystery generation and similar gentle interactions.

