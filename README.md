# BoiseChibuzo.github.io

Personal academic website for **Chibuzo Ukegbu, Ph.D.**, Assistant Professor in the
Dian & Diercks School of Advanced Computing, Milwaukee School of Engineering.

Plain HTML + CSS. No build step, no JavaScript framework. Designed to deploy directly
to GitHub Pages from the **BoiseChibuzo** GitHub account.

> Future-username note: GitHub user-site URLs follow the username. If you ever rename
> your account from `BoiseChibuzo`, also rename this repository to `<new-username>.github.io`.
> GitHub auto-redirects the old URL for a while, but the canonical address moves.

---

## File layout

```
.
├── index.html            # Home (About, Research, Teaching, News, Contact)
├── cv.html               # Curriculum Vitae
├── blog/
│   ├── index.html        # Blog list
│   └── welcome.html      # First post (template for future posts)
├── assets/
│   ├── css/style.css     # All styling lives here
│   └── img/              # Drop profile.jpg here; placeholder shows otherwise
├── .nojekyll             # Tells GitHub Pages to skip Jekyll processing
└── README.md             # This file
```

## Deploy to GitHub Pages — easiest path (browser only, no terminal)

1. Sign in to GitHub as **BoiseChibuzo**.
2. Click the **+** icon (top right) → **New repository**.
3. Repository name: **`BoiseChibuzo.github.io`** (must match the username exactly).
4. Set it to **Public**. Do **not** tick "Add a README" — this folder already has one.
5. Click **Create repository**.
6. On the empty repo page, click the link **"uploading an existing file"**.
7. Drag the entire contents of this folder (`index.html`, `cv.html`, `blog/`, `assets/`,
   `.nojekyll`, `README.md`) into the browser. Scroll down, click **Commit changes**.
8. Go to **Settings → Pages**. Source = "Deploy from a branch", Branch = `main`,
   Folder = `/ (root)`. Save.
9. After ~1 minute, the site is live at **https://boisechibuzo.github.io/**.

> If `.nojekyll` doesn't appear in the upload list, your OS is hiding dotfiles.
> On macOS press `Cmd+Shift+.` in Finder; on Windows enable "Hidden items" in File
> Explorer's View tab. Without `.nojekyll`, the site still works, but GitHub will
> run Jekyll over it unnecessarily.

## Deploy via command line (alternative)

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/BoiseChibuzo/BoiseChibuzo.github.io.git
git push -u origin main
```

You'll be prompted for credentials. GitHub no longer accepts your account password
on the command line — generate a **personal access token** at
https://github.com/settings/tokens (classic, scope: `repo`) and paste it as the
password.

Then complete step 8 above to enable Pages.

## Adding your photo

Save a square photo as `assets/img/profile.jpg`. The site shows a styled "CU"
placeholder until then.

## Adding a new blog post

1. Copy `blog/welcome.html` to `blog/your-post-slug.html`.
2. Edit the `<title>`, `<h1>`, the `<time>` element, and the body.
3. Add a link to the new post at the top of `blog/index.html`:

   ```html
   <li>
     <span class="date">2026-06-01</span>
     <a href="your-post-slug.html">Title of your post</a>
   </li>
   ```

4. Commit and push. The site updates within a minute.

## Updating news on the home page

Edit the `<ul class="news-list">` block in `index.html`. The format:

```html
<li><span class="date">May 2026</span> &mdash; Your news item.</li>
```

## Updating the CV

Edit `cv.html` directly, or drop a PDF version at `assets/cv.pdf` and uncomment the
download link near the top of `cv.html`.

## Customizing the look

All colors, fonts, and the content max-width are CSS variables at the top of
`assets/css/style.css`. The most common edit is the accent color:

```css
--accent: #b21e2c;          /* MSOE-leaning red */
```

Dark mode is automatic and follows the visitor's system setting — no toggle needed.

## Local preview

To view the site locally (so links and stylesheet paths resolve correctly):

```bash
# Python 3
python -m http.server 8000
# then open http://localhost:8000
```

## Custom domain (optional)

If you later want a custom domain (e.g., `chibuzoukegbu.com`):

1. Add a file named `CNAME` at the repo root containing only your domain.
2. In your domain registrar, point the DNS to GitHub Pages
   (see https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Renaming your GitHub username later

If you change your username from `BoiseChibuzo`:

1. Rename this repository to `<new-username>.github.io` under **Settings → General**.
2. Update the `Source on GitHub` link in `index.html` (footer) to the new repo URL.
3. The new live URL is `https://<new-username>.github.io/`. The old URL will redirect
   for a while but won't last forever.

## TODOs already marked in the files

- `index.html` — replace the `[TODO]` news items.
- `cv.html` — fill in start year, selected publications, and service.
- `assets/img/profile.jpg` — add your photo.
