## RIC Gaming Club Website

Static site for the RIC Gaming Club, deployed via GitHub Pages.

### Local Development

1. Copy `Project/Ask a question/config.example.js` to `Project/Ask a question/config.js`.
2. Put your Google Generative Language API key in the new file:
     ```js
     export const CONFIG = { API_KEY: "YOUR_KEY" };
     ```
3. Open `index.html` (or `Project/Home/home.html`) in a browser.

### Deployment (GitHub Pages)

The workflow `.github/workflows/deploy-pages.yml` creates `config.js` at build time using the repository secret `GEMINI_API_KEY`.

Steps to configure:

1. Go to Repository Settings → Secrets and variables → Actions → New repository secret.
2. Name: `GEMINI_API_KEY`  Value: your API key.
3. Push to `main`; the action will publish the site with the injected key.

### Security Note

Because this is a client-side static site, the API key delivered to the browser is visible to users. For stronger security, put a lightweight proxy (Cloudflare Worker / Netlify Function / small Node server) between the site and the API to hide the key and optionally enforce simple rate limits.

### Ask a Question Tool

`ask questions.html` attempts multiple Gemini model names across API versions for resilience and logs errors to the page console area. No model listing call is performed (avoids extra failure points).

### Folder Structure (excerpt)

```
Project/
    Home/
        home.html
    Ask a question/
        ask questions.html
        config.example.js
    FAQ List/
        FAQ List.html
```

### Quick Link

Open `Project/Home/home.html` or visit the deployed GitHub Pages URL after the workflow finishes.

### Future Improvements

- Optional proxy to secure key
- Simple latency display per answer
- Rate limiting rapid submits

---
Made with care by the RIC Gaming Club.
