---
layout: page
title: Gallery
permalink: /gallery/
description: Moments from conferences and travel.
nav: false
photos:
  - { file: photo-1.webp, cat: conference, caption: "Caption for photo 1" }
  - { file: photo-2.webp, cat: conference, caption: "Caption for photo 2" }
  - { file: photo-3.webp, cat: conference, caption: "Caption for photo 3" }
  - { file: photo-4.webp, cat: travel,     caption: "Caption for photo 4" }
---

<div class="gal-filters" role="group" aria-label="Filter photos">
  <button type="button" class="gal-btn is-active" data-filter="all">All</button>
  <button type="button" class="gal-btn" data-filter="conference">Conferences</button>
  <button type="button" class="gal-btn" data-filter="travel">Travel</button>
</div>

<div class="gal-grid">
{% for p in page.photos %}
  <figure class="gal-item" data-cat="{{ p.cat }}" tabindex="0">
    <img src="{{ '/assets/img/gallery/' | append: p.file | relative_url }}" alt="{{ p.caption }}" loading="lazy">
    <figcaption>{{ p.caption }}</figcaption>
  </figure>
{% endfor %}
</div>

<dialog class="gal-box" id="galBox">
  <button type="button" class="gal-close" aria-label="Close">&times;</button>
  <img id="galBoxImg" alt="">
  <p id="galBoxCap"></p>
</dialog>

<style>
  .gal-filters { display: flex; gap: .5rem; margin-bottom: 1.5rem; flex-wrap: wrap; }
  .gal-btn { border: 1px solid var(--global-theme-color, #4F46E5); background: transparent; color: var(--global-theme-color, #4F46E5);
    padding: .35rem 1rem; border-radius: 2rem; font-size: .9rem; cursor: pointer; }
  .gal-btn.is-active, .gal-btn:hover { background: var(--global-theme-color, #4F46E5); color: #fff; }
  .gal-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 1rem; }
  .gal-item { margin: 0; cursor: zoom-in; }
  .gal-item[hidden] { display: none; }
  .gal-item img { width: 100%; aspect-ratio: 4 / 3; object-fit: cover; border-radius: 8px; display: block; }
  .gal-item figcaption { font-size: .85rem; color: #6c757d; margin-top: .4rem; }
  .gal-box { border: none; padding: 0; background: transparent; max-width: 92vw; }
  .gal-box::backdrop { background: rgba(0,0,0,.85); }
  .gal-box img { max-width: 92vw; max-height: 82vh; display: block; border-radius: 4px; }
  .gal-box p { color: #fff; text-align: center; margin-top: .6rem; }
  .gal-close { position: absolute; top: .25rem; right: .5rem; background: none; border: none; color: #fff; font-size: 2rem; cursor: pointer; }
</style>

<script>
(function () {
  const items = document.querySelectorAll('.gal-item');
  const box = document.getElementById('galBox'); if (!box) return;
  const img = document.getElementById('galBoxImg'), cap = document.getElementById('galBoxCap');
  document.querySelectorAll('.gal-btn').forEach(btn => btn.addEventListener('click', () => {
    document.querySelectorAll('.gal-btn').forEach(b => b.classList.remove('is-active'));
    btn.classList.add('is-active');
    const f = btn.dataset.filter;
    items.forEach(it => { it.hidden = !(f === 'all' || it.dataset.cat === f); });
  }));
  items.forEach(it => {
    const open = () => { const i = it.querySelector('img'); img.src = i.src; img.alt = i.alt;
      cap.textContent = it.querySelector('figcaption').textContent; box.showModal(); };
    it.addEventListener('click', open);
    it.addEventListener('keydown', e => { if (e.key === 'Enter') open(); });
  });
  box.querySelector('.gal-close').addEventListener('click', () => box.close());
  box.addEventListener('click', e => { if (e.target === box) box.close(); });
})();
</script>
