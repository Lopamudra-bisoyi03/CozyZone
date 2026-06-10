# Cozy Zone

A cozy, cat-themed browser game collection with a lightweight AI-powered mystery feature.

## What is included

- A single-page HTML app: [`cozy-zone.html`](./cozy-zone.html)
- A Netlify config file: [`netlify.toml`](./netlify.toml)
- A Netlify Function that proxies AI requests to Groq: [`netlify/functions/ai.js`](./netlify/functions/ai.js)

## AI setup

The app does not call Groq directly from the browser. Instead, it sends requests to `/api/ai`, and Netlify forwards them to Groq on the server side.

Set this environment variable in Netlify:

- `GROQ_API_KEY` = your Groq API key

Optional:

- `GROQ_MODEL` = `llama-3.3-70b-versatile`

## Local testing

If you open the HTML file directly with `file://`, AI features will not work because browsers block that kind of request flow.

Use Netlify deploy or `netlify dev` instead.

## Deploy to Netlify

1. Push this repo to GitHub.
2. Import the repo into Netlify.
3. Add `GROQ_API_KEY` in Netlify environment variables.
4. Deploy the site.

## Notes

- The app is intentionally cat-themed and cozy.
- The old color game has been removed.
- The AI endpoint is server-side, so the Groq key stays private.

