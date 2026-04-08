# Felipe Magon — Photography Portfolio

A minimal, dark-themed photography portfolio built with plain HTML/CSS/JS. No build tools required — works directly with GitHub Pages.

## How to add your photos

1. **Drop your images** into the matching folder:
   - `images/portraits/`
   - `images/landscapes/`
   - `images/years/`
   - `images/travel/`

2. **Register them** in `js/main.js` — find the gallery you want and add entries to its `photos` array:

```js
portraits: {
  photos: [
    { src: 'images/portraits/photo1.jpg', alt: 'Optional caption' },
    { src: 'images/portraits/photo2.jpg', alt: '' },
  ]
}
```

3. **Set a cover image** for each category card (the image shown on the Work page):

```js
portraits: {
  cover: 'images/covers/portraits.jpg',
  // ...
}
```
   Drop your cover files into `images/covers/`.

4. **Add your About photo** — open `css/style.css`, find `.about-image-slot`, and uncomment the two background lines:
```css
background-image: url('../images/about.jpg');
background-size: cover;
background-position: center;
```

5. **Add your About bio** — open `index.html` and type your text inside the `<p class="about-body">` tag.

6. **Wire up the contact form** — the form is ready but needs a backend. The easiest option is [Formspree](https://formspree.io):
   - Create a free account, get your form endpoint
   - In `index.html`, change `<form class="contact-form" id="contactForm" novalidate>` to add `action="https://formspree.io/f/YOUR_ID" method="POST"`
   - In `js/main.js` you can remove the `form.addEventListener('submit', ...)` block

## Deploy to GitHub Pages

1. Create a new repo on GitHub (e.g. `felipemagon.github.io` for a root site, or any name for a project site)
2. Push this folder:
```bash
git init
git add .
git commit -m "Initial portfolio"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```
3. In GitHub → Settings → Pages → set Source to `main` branch, `/ (root)` folder → Save
4. Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## File structure

```
photography-portfolio/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── main.js
└── images/
    ├── covers/       ← category cover images (Work page cards)
    ├── portraits/
    ├── landscapes/
    ├── years/
    └── travel/
```
