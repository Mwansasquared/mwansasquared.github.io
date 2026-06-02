# Mwansa Mwansa — Portfolio

Personal portfolio site for Mwansa Mwansa, Full-Stack Engineer specialising in Go backends, distributed systems, and React frontends. Built with SvelteKit, Tailwind CSS v4, and deployed via GitHub Pages.

**Live site:** `https://<your-github-username>.github.io/<repo-name>`

## Stack

- **Framework:** SvelteKit (static adapter)
- **Styling:** Tailwind CSS v4 + custom CSS animations
- **Fonts:** Inter · JetBrains Mono (Google Fonts)
- **Deployment:** GitHub Actions → GitHub Pages

## Features

- Multi-layer parallax background orbs
- Scroll-driven hero fade and drift
- Intersection Observer section reveal animations
- Sticky nav with blur backdrop
- Back-to-top button
- Fully static output — no server required

## Local development

```sh
npm install
npm run dev
```

Open [http://localhost:5173](http://localhost:5173).

## Build

```sh
npm run build
```

Preview the production build locally:

```sh
npm run preview
```

Output is written to `build/`.

## Deploy to GitHub Pages

Deployment is automated via `.github/workflows/deploy.yml`. On every push to `main`, the site is built and deployed.

**One-time setup:**
1. Push the repo to GitHub
2. Go to **Settings → Pages → Source** and select **GitHub Actions**
3. Push to `main` — the workflow handles the rest

For a **project page** (`username.github.io/repo-name`), set the `BASE_PATH` environment variable in the workflow to `/<repo-name>`. The workflow already handles this automatically by reading the repository name.

## Customisation

All content lives in [`src/routes/+page.svelte`](src/routes/+page.svelte):

- `projects` array — update titles, descriptions, stack, and year
- `stack` array — update the core tech grid
- Contact email and social links in the contact section
- LinkedIn and GitHub URLs at the bottom of the contact section

## Project structure

```
src/
├── app.css          # Global styles, Tailwind import, animations
├── app.html         # HTML shell, Google Fonts, meta tags
├── lib/
│   └── assets/      # Static assets (favicon, etc.)
└── routes/
    ├── +layout.svelte
    └── +page.svelte  # All portfolio content

static/
└── .nojekyll        # Prevents GitHub Pages Jekyll processing

.github/
└── workflows/
    └── deploy.yml   # GitHub Actions deployment pipeline
```
