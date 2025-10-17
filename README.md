<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Run and deploy your AI Studio app

This contains everything you need to run your app locally and deploy to GitHub Pages.

View your app in AI Studio: https://ai.studio/apps/temp/5

## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
3. Run the app:
   `npm run dev`

## Deploy to GitHub Pages

This repository is configured to deploy to GitHub Pages using GitHub Actions.

### One-time setup

1. Push this repository to GitHub under the account that will host the page.
2. In GitHub, go to: Settings → Pages
   - Build and deployment → Source: select "GitHub Actions".
3. In GitHub, go to: Settings → Secrets and variables → Actions → New repository secret
   - Name: `GEMINI_API_KEY`
   - Value: your Gemini API key

### Branch and base path

- The Vite base path is set to `/bunny-bomber/` in `vite.config.ts`. Make sure the repository name is `bunny-bomber`. If you use a different repo name, update the `base` value accordingly.

### How it works

- On pushes to `main`, the workflow `.github/workflows/deploy.yml`:
  - installs dependencies via `npm ci`
  - builds the app via `npm run build`
  - creates `dist/404.html` for SPA routing via `npm run postbuild`
  - uploads `dist` as the Pages artifact and deploys

### View your site

- User/Org page: `https://<your-username>.github.io/bunny-bomber/`
- Project page path is required due to the configured base path.

### Local production preview

You can preview the production build locally:

```
npm run build && npm run postbuild
npm run preview
```
