# TheFelipeMonreal 
/* â”€â”€ Variables â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
:root {
  --bg:          #0a0a0a;
  --bg-2:        #111111;
  --bg-card:     #161616;
  --border:      #202020;
  --green:       #3d6b4a;
  --green-light: #5e9e70;
  --white:       #f2f2f2;
  --grey:        #888888;
  --muted:       #3a3a3a;
  --nav-h:       60px;
  --ease:        0.3s ease;
  --font-serif:  'Cormorant Garamond', Georgia, serif;
  --font-sans:   'Inter', system-ui, sans-serif;
}

/* â”€â”€ Reset â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--white);
  font-family: var(--font-sans);
  font-weight: 300;
  min-height: 100vh;
  overflow-x: hidden;
}
a { text-decoration: none; color: inherit; }
button { font-family: var(--font-sans); cursor: pointer; }
img { display: block; max-width: 100%; }

/* â”€â”€ Navigation â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
#nav {
  position: fixed;
  inset: 0 0 auto 0;
  height: var(--nav-h);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 48px;
  z-index: 200;
  background: rgba(10, 10, 10, 0.96);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
}

.nav-logo {
  font-family: var(--font-serif);
  font-size: 1.35rem;
  font-weight: 300;
  letter-spacing: 0.06em;
  color: var(--white);
  cursor: pointer;
  user-select: none;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 40px;
}

.nav-links a {
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--grey);
  cursor: pointer;
  transition: color var(--ease);
  user-select: none;
}

.nav-links a:hover,
.nav-links a.active {
  color: var(--green-light);
}

.nav-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  padding: 6px 2px;
  z-index: 201;
}

.nav-toggle span {
  display: block;
  width: 22px;
  height: 1px;
  background: var(--grey);
  transition: var(--ease);
}

/* â”€â”€ Pages â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
#app {
  padding-top: var(--nav-h);
  min-height: calc(100vh - 48px);
}

.page {
  display: none;
  opacity: 0;
  transform: translateY(12px);
  transition: opacity 0.4s ease, transform 0.4s ease;
  min-height: calc(100vh - var(--nav-h) - 48px);
}

.page.active  { display: block; }
.page.visible { opacity: 1; transform: translateY(0); }

/* â”€â”€ Work â€” Category Grid â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
.category-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2px;
  background: var(--border);
  padding: 2px;
}

.cat-card {
  position: relative;
  aspect-ratio: 4 / 3;
  overflow: hidden;
  cursor: pointer;
  background: var(--bg-card);
}

.cat-card img,
.cat-cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.65s ease, opacity 0.4s ease;
  opacity: 0.82;
}

.cat-card:hover img,
.cat-card:hover .cat-cover {
  transform: scale(1.05);
  opacity: 1;
}

.cat-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.78) 0%, rgba(0,0,0,0.1) 55%, transparent 100%);
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 36px;
  transition: background var(--ease);
}

.cat-card:hover .cat-overlay {
  background: linear-gradient(to top, rgba(0,0,0,0.88) 0%, rgba(0,0,0,0.25) 60%, transparent 100%);
}

.cat-title {
  font-family: var(--font-serif);
  font-size: 2rem;
  font-weight: 300;
  color: #fff;
  letter-spacing: 0.04em;
  transform: translateY(5px);
  transition: transform 0.3s ease;
}

.cat-card:hover .cat-title { transform: translateY(0); }

.cat-meta {
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--green-light);
  margin-top: 6px;
  opacity: 0;
  transition: opacity 0.3s ease 0.05s;
}

.cat-card:hover .cat-meta { opacity: 1; }

/* â”€â”€ Gallery Page â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
.gallery-header {
  display: flex;
  align-items: baseline;
  gap: 28px;
  padding: 44px 48px 28px;
  border-bottom: 1px solid var(--border);
}

.back-btn {
  background: none;
  border: none;
  color: var(--grey);
  font-size: 0.7rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  transition: color var(--ease);
  padding: 4px 0;
  flex-shrink: 0;
}

.back-btn:hover { color: var(--green-light); }

#galleryTitle {
  font-family: var(--font-serif);
  font-size: 2.2rem;
  font-weight: 300;
  color: var(--white);
}

.photo-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  background: var(--border);
  padding: 2px;
  margin-top: 2px;
}

.photo-item {
  position: relative;
  aspect-ratio: 3 / 2;
  overflow: hidden;
  cursor: pointer;
  background: var(--bg-card);
}

.photo-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.88;
  transition: transform 0.5s ease, opacity 0.3s ease;
}

.photo-item:hover img {
  transform: scale(1.06);
  opacity: 1;
}

.gallery-empty {
  grid-column: 1 / -1;
  padding: 100px 40px;
  text-align: center;
  color: var(--muted);
  font-size: 0.72rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

/* â”€â”€ Lightbox â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
.lightbox {
  display: none;
  position: fixed;
  inset: 0;
  z-index: 500;
  background: rgba(5, 5, 5, 0.97);
  align-items: center;
  justify-content: center;
}

.lightbox.open { display: flex; }

.lb-content {
  max-width: 90vw;
  max-height: 87vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.lb-content img {
  max-width: 90vw;
  max-height: 87vh;
  object-fit: contain;
}

.lb-close {
  position: fixed;
  top: 20px;
  right: 28px;
  background: none;
  border: none;
  color: var(--grey);
  font-size: 1.5rem;
  line-height: 1;
  padding: 8px;
  transition: color var(--ease);
  z-index: 501;
}

.lb-close:hover { color: var(--white); }

.lb-arrow {
  position: fixed;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  color: var(--grey);
  font-size: 3.5rem;
  line-height: 1;
  padding: 12px 20px;
  transition: color var(--ease);
  z-index: 501;
  user-select: none;
}

.lb-arrow:hover { color: var(--green-light); }
.lb-prev { left: 8px; }
.lb-next { right: 8px; }

.lb-caption {
  position: fixed;
  bottom: 22px;
  left: 50%;
  transform: translateX(-50%);
  color: var(--grey);
  font-size: 0.7rem;
  letter-spacing: 0.12em;
  white-space: nowrap;
}

/* â”€â”€ About â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
.about-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: calc(100vh - var(--nav-h));
}

.about-image-slot {
  background: var(--bg-card);
  min-height: 400px;
  /* Replace with your photo: background-image: url('../images/about.jpg'); background-size: cover; background-position: center; */
}

.about-text {
  padding: 88px 64px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-left: 1px solid var(--border);
}

.about-text h1 {
  font-family: var(--font-serif);
  font-size: 3.2rem;
  font-weight: 300;
  color: var(--white);
  margin-bottom: 36px;
}

.about-body {
  color: var(--grey);
  line-height: 1.85;
  font-size: 0.88rem;
  max-width: 480px;
}

/* â”€â”€ Contact â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
.contact-container {
  max-width: 580px;
  margin: 0 auto;
  padding: 88px 40px 64px;
}

.contact-container h1 {
  font-family: var(--font-serif);
  font-size: 3.2rem;
  font-weight: 300;
  color: var(--white);
  margin-bottom: 52px;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 24px;
  margin-bottom: 48px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-group label {
  font-size: 0.68rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--grey);
}

.required { color: var(--green-light); }

.form-group input,
.form-group textarea {
  background: var(--bg-card);
  border: 1px solid var(--border);
  color: var(--white);
  padding: 13px 16px;
  font-family: var(--font-sans);
  font-size: 0.85rem;
  font-weight: 300;
  outline: none;
  transition: border-color var(--ease);
  resize: vertical;
  -webkit-appearance: none;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--green);
}

.btn-submit {
  background: var(--green);
  color: #fff;
  border: none;
  padding: 13px 44px;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  transition: background var(--ease);
  align-self: flex-start;
  margin-top: 4px;
}

.btn-submit:hover { background: var(--green-light); }

.form-note {
  font-size: 0.75rem;
  color: var(--green-light);
  min-height: 1.2em;
}

.back-to-top {
  display: inline-block;
  font-size: 0.7rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--grey);
  border-top: 1px solid var(--border);
  padding-top: 20px;
  margin-top: 16px;
  transition: color var(--ease);
}

.back-to-top:hover { color: var(--green-light); }

/* â”€â”€ Footer â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
#footer {
  padding: 16px 48px;
  border-top: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: center;
}

#footer p {
  font-size: 0.62rem;
  color: var(--muted);
  letter-spacing: 0.22em;
  text-transform: uppercase;
}

/* â”€â”€ Responsive â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€ */
@media (max-width: 900px) {
  .about-container { grid-template-columns: 1fr; }
  .about-text { border-left: none; border-top: 1px solid var(--border); padding: 48px 32px; }
}

@media (max-width: 768px) {
  #nav { padding: 0 20px; }

  .nav-links {
    display: none;
    position: absolute;
    top: var(--nav-h);
    left: 0;
    right: 0;
    background: rgba(10,10,10,0.98);
    flex-direction: column;
    gap: 0;
    border-bottom: 1px solid var(--border);
    padding: 0;
  }

  .nav-links.open { display: flex; }

  .nav-links li { border-bottom: 1px solid var(--border); }

  .nav-links a {
    display: block;
    padding: 18px 20px;
    font-size: 0.75rem;
  }

  .nav-toggle { display: flex; }

  .category-grid { grid-template-columns: 1fr; }

  .cat-overlay { padding: 24px; }
  .cat-title { font-size: 1.6rem; }

  .gallery-header { padding: 28px 20px 20px; gap: 16px; }
  #galleryTitle { font-size: 1.6rem; }

  .photo-grid { grid-template-columns: repeat(2, 1fr); }

  .contact-container { padding: 48px 20px 40px; }

  #footer { padding: 14px 20px; }
}

@media (max-width: 480px) {
  .photo-grid { grid-template-columns: 1fr; }
  .lb-arrow { font-size: 2.5rem; padding: 8px 12px; }
Portafolio
