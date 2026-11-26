# Emir Senol — Personal Website

A simple, fast personal website made with plain HTML, CSS and JavaScript.
There is **nothing to install** — no Node, no npm, no build step.

```
.
├── index.html      ← all the text on the site lives here
├── styles.css      ← colors, fonts, layout
├── script.js       ← small extras (mobile menu, scroll animations)
├── README.md       ← this file
└── images/
    ├── profile.svg              ← placeholder for your photo
    ├── project-placeholder.svg  ← placeholder for project screenshots
    ├── og-image.png             ← preview image shown when your link is shared
    ├── og-image.svg             ← editable source for og-image.png
    └── favicon.svg              ← the little icon in the browser tab
```

---

## 1. Open the site on your computer

1. Open the project folder in Finder (Mac) or File Explorer (Windows).
2. **Double-click `index.html`.**
3. It opens in your web browser. That's it — the site works offline.

After you edit a file, save it and **refresh the browser** (⌘R on Mac, Ctrl+R on Windows) to see the change.

---

## 2. Put the project on GitHub

You only need to do this once. You'll need [Git](https://git-scm.com/downloads) installed
(on a Mac, typing `git --version` in Terminal will offer to install it).

### a) Create an empty repository on GitHub

1. Go to <https://github.com/new>.
2. **Repository name:** something like `personal-website`.
3. Choose **Public** (or Private — Netlify works with both).
4. **Do not** tick "Add a README", ".gitignore" or "license" (this project already has a README).
5. Click **Create repository**. Keep the page open — it shows your repository's URL,
   e.g. `https://github.com/YOUR-USERNAME/personal-website.git`.

### b) Upload your files from the Terminal

Open Terminal (Mac) or Git Bash (Windows), go into the project folder, and run these
commands one at a time. Replace the URL with the one from your repository page.

```bash
cd path/to/your/project-folder
```

```bash
git init
```

```bash
git add .
```

```bash
git commit -m "First version of my website"
```

```bash
git branch -M main
```

```bash
git remote add origin https://github.com/YOUR-USERNAME/personal-website.git
```

```bash
git push -u origin main
```

If Git asks you to sign in, follow the prompt (GitHub uses a browser login or a
personal access token, not your account password).

Refresh the GitHub page — your files are now there.

### Sending later changes to GitHub

Whenever you've edited something and want to publish it:

```bash
git add .
```

```bash
git commit -m "Describe what you changed"
```

```bash
git push
```

> **Prefer not to use the Terminal?** [GitHub Desktop](https://desktop.github.com/) does
> the same thing with buttons: *File → Add Local Repository*, then *Publish repository*.

---

## 3. Put the site online with Netlify

Netlify hosts the site for free and **re-publishes it automatically every time you push to GitHub.**

1. Go to <https://app.netlify.com> and sign up / log in (choosing **Sign up with GitHub** is easiest).
2. Click **Add new project** → **Import an existing project**.
3. Choose **GitHub**, and allow Netlify to access your account if it asks.
4. Pick your `personal-website` repository.
5. On the settings screen:
   - **Branch to deploy:** `main`
   - **Base directory:** leave **empty**
   - **Build command:** leave **empty**
   - **Publish directory:** leave **empty** (or type `.`) — this means "the project root"
6. Click **Deploy**.

After a few seconds you'll get an address like `https://something-random.netlify.app`.
You can change it in Netlify under **Manage → Name and address → Rename**.
This site lives at **https://emirsenol.netlify.app**.

From now on: **edit → commit → push**, and Netlify updates the live site by itself within a minute.

### If you change the address: fix the sharing preview

Renaming the project (or adding your own domain) changes the site's address, and the
old address stops working. Open `index.html` and, near the top, replace every
`https://emirsenol.netlify.app` with the new address. This keeps the preview image
working when you share your link on LinkedIn, WhatsApp, X, etc. Then commit and push.

---

## 4. Where to change things

Every spot you should edit is marked with an **`EDIT ME`** comment in `index.html`.
Search the file for `EDIT ME` (⌘F / Ctrl+F in your editor), and look for text in
`[square brackets]` — those are placeholders.

| What | Where |
| --- | --- |
| Page title, description, share preview | Top of `index.html`, inside `<head>` |
| Name & tagline | `index.html` → **HERO** section |
| Bio and skills | `index.html` → **ABOUT** section (one `<li>` per skill) |
| Projects | `index.html` → **PROJECTS** section (copy a whole `<li class="card"> … </li>` block to add one) |
| Experience / education | `index.html` → **EXPERIENCE** section (one `<li>` per item, newest first) |
| Email & social links | `index.html` → **CONTACT** section |
| Colors | `styles.css` → the `:root` block at the top (light mode) and the block right below it (dark mode) |
| Fonts | `styles.css` → `--font` in the `:root` block |

### Swapping in your own images

1. Put your image files in the `images/` folder.
2. In `index.html`, change the `src="images/..."` to your file name.
3. Update the `alt="..."` text to describe the image (this is read aloud by screen readers).

| Image | Suggested size | Replace in `index.html` |
| --- | --- | --- |
| Your photo | square, 400×400 or larger (e.g. `profile.jpg`) | `src="images/profile.svg"` in the HERO section |
| Project screenshots | 16:9, e.g. 1280×720 (`project-1.png`, …) | each `src="images/project-placeholder.svg"` in PROJECTS |
| Sharing preview | exactly 1200×630, PNG or JPG | overwrite `images/og-image.png` (keep the same name) |
| Browser tab icon | square SVG or PNG | overwrite `images/favicon.svg` |

**Tip:** keep file names lowercase with no spaces (`my-photo.jpg`, not `My Photo.JPG`).
Your computer may not care about capitals, but Netlify does — a mismatch means a broken image online.

### Want a custom font?

The site uses your device's built-in system font, so it works offline and loads instantly.
To use a different font: download its `.woff2` files (for example from
[Google Fonts](https://fonts.google.com) via [google-webfonts-helper](https://gwfh.mranftl.com/fonts)),
put them in a new `fonts/` folder, and add to the top of `styles.css`:

```css
@font-face {
  font-family: "Inter";
  src: url("fonts/inter-v13-latin-regular.woff2") format("woff2");
  font-weight: 400;
  font-display: swap;
}
```

Then change `--font` in `:root` to start with `"Inter", ` followed by the existing list.
