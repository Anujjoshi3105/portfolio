# Anuj Joshi — Portfolio

> “[One] who works with the door open gets all kinds of interruptions, but [they] also occasionally gets clues as to what the world is and what might be important.” — Richard Hamming

This is my personal portfolio and digital garden, built with [Quartz v5](https://quartz.jzhao.xyz/). It hosts my projects, experience, education, certifications, testimonials, and competitive-programming blog as a free website.

- 🌐 Live site: https://anujjoshi3105.github.io/portfolio/
- 📝 Quartz documentation: https://quartz.jzhao.xyz/

## What's Inside

- **Projects** — full-stack apps, ed-tech SaaS, vision APIs, and more
- **Experience** — roles, internships, and leadership
- **Education** — academics from B.Tech to CBSE
- **Certifications** — verified credentials
- **Testimonials** — what people say about working with me
- **Blog** — competitive programming write-ups and contest solutions
- **Contact** — get in touch

All content lives in the [`content/`](content/) folder as Markdown notes. Edit or add a note there, then rebuild and push — deployment is fully automated.

## Getting Started (Local Development)

```sh
npm install
npx quartz build --serve
```

Then open http://localhost:8080. See the [Quartz docs](https://quartz.jzhao.xyz/) for details on customizing components, themes, and layout.

## Deploying to GitHub Pages

This repo deploys automatically to GitHub Pages via [GitHub Actions](.github/workflows/deploy-github-pages.yaml) whenever changes are pushed to the `main` branch. No manual build or upload is needed.

### One-time setup (already done for this repo)

1. Create a GitHub repo named `portfolio` (already created: [Anujjoshi3105/portfolio](https://github.com/Anujjoshi3105/portfolio)).
2. Set the remote (already configured):
   ```sh
   git remote add origin https://github.com/Anujjoshi3105/portfolio.git
   ```
   or, if it already exists:
   ```sh
   git remote set-url origin https://github.com/Anujjoshi3105/portfolio.git
   ```
3. In GitHub → repo → **Settings → Pages**, set **Source** to "GitHub Actions".

### Uploading / publishing changes

1. Stage and commit your changes:
   ```sh
   git add .
   git commit -m "Update portfolio content"
   ```
2. Push to the `main` branch (the branch the deploy workflow listens on):
   ```sh
   git push origin main
   ```
   If you're on another branch and want to publish it, first push it and then merge/rename:
   ```sh
   git branch -M main
   git push origin main
   ```
3. Watch the build: GitHub → **Actions** → "Deploy to GitHub Pages" should run and turn green.
4. When it finishes, your site is live at `https://<username>.github.io/portfolio/`.

Every subsequent edit is just three commands:

```sh
git add .
git commit -m "Update content"
git push origin main
```

## Local Build Preview

To preview exactly what will be deployed:

```sh
npm install
npx quartz build
```

The generated static site is written to the `public/` folder.

## License

This repository is for personal use. The [Quartz](https://github.com/jackyzha0/quartz) tooling that powers it is MIT-licensed — see [LICENSE.txt](LICENSE.txt).
