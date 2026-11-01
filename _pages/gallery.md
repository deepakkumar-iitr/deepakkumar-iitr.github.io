---
layout: page
title: Gallery
permalink: /gallery/
description: Moments from conferences, academic visits, and travel.
nav: true
nav_order: 7
albums:
  - { folder: FG2026,               cat: conference, title: "FG 2026",          where: "Kyoto, Japan",              when: "May 2026" }
  - { folder: IndoML2024,           cat: conference, title: "IndoML 2024",      where: "BITS Pilani Goa, India",    when: "Dec 2024" }
  - { folder: FG2024,               cat: conference, title: "FG 2024",          where: "Istanbul, Türkiye",         when: "May 2024" }
  - { folder: ICVGIP2023,           cat: conference, title: "ICVGIP 2023",      where: "IIT Ropar, India",          when: "Dec 2023" }
  - { folder: NII_Tokyo,            cat: visit,      title: "Visit to NII",     where: "Tokyo, Japan",              when: "" }
  - { folder: IISC_Bangalore_Visit, cat: visit,      title: "Visit to IISc",    where: "Bangalore, India",          when: "" }
  - { folder: JapanDiaries,         cat: travel,     title: "Japan Diaries",    where: "Japan",                     when: "" }
  - { folder: Kedarnath,            cat: travel,     title: "Kedarnath",        where: "Uttarakhand, India",        when: "" }
---

{% assign all_photos = site.static_files | where_exp: "f", "f.path contains '/assets/img/gallery/'" | where_exp: "f", "f.extname == '.webp'" %}

<div class="gal-filters" role="group" aria-label="Filter albums">
  <button type="button" class="gal-btn is-active" data-filter="all">All</button>
  <button type="button" class="gal-btn" data-filter="conference">Conferences</button>
  <button type="button" class="gal-btn" data-filter="visit">Academic visits</button>
  <button type="button" class="gal-btn" data-filter="travel">Travel</button>
</div>

{% for a in page.albums %}
  {% assign prefix = '/assets/img/gallery/' | append: a.folder | append: '/' %}
  {% assign pics = all_photos | where_exp: "f", "f.path contains prefix" | sort: "name" %}
  {% if pics.size > 0 %}
  <section class="gal-album" data-cat="{{ a.cat }}">
    <div class="gal-album-head">
      <h3>{{ a.title }}</h3>
      <span>{{ a.where }}{% if a.when != "" %} · {{ a.when }}{% endif %} · {{ pics.size }} photo{% if pics.size > 1 %}s{% endif %}</span>
    </div>
    <div class="gal-grid">
      {% for p in pics %}
      <figure class="gal-item" tabindex="0" data-caption="{{ a.title }}, {{ a.where }}{% if a.when != '' %} · {{ a.when }}{% endif %}">
        <img src="{{ p.path | relative_url }}" alt="{{ a.title }} photo {{ forloop.index }}" loading="lazy">
      </figure>
      {% endfor %}
    </div>
  </section>
  {% endif %}
{% endfor %}

<dialog class="gal-box" id="galBox">
  <button type="button" class="gal-close" aria-label="Close">&times;</button>
  <button type="button" class="gal-nav gal-prev" aria-label="Previous">&#8249;</button>
  <img id="galBoxImg" alt="">
  <button type="button" class="gal-nav gal-next" aria-label="Next">&#8250;</button>
  <p id="galBoxCap"></p>
</dialog>

<style>
  .gal-filters { display: flex; gap: .5rem; margin-bottom: 1.75rem; flex-wrap: wrap; }
  .gal-btn { border: 1px solid var(--global-theme-color); background: transparent; color: var(--global-theme-color);
    padding: .35rem 1rem; border-radius: 2rem; font-size: .9rem; cursor: pointer; }
  .gal-btn.is-active, .gal-btn:hover { background: var(--global-theme-color); color: #fff; }
  .gal-album { margin-bottom: 2.25rem; padding-bottom: 1.5rem; border-bottom: 1px solid rgba(0,0,0,.1); }
  .gal-album[hidden] { display: none; }
  .gal-album-head { display: flex; align-items: baseline; justify-content: space-between; flex-wrap: wrap; gap: .5rem; margin-bottom: .9rem; }
  .gal-album-head h3 { margin: 0; font-size: 1.25rem; }
  .gal-album-head span { color: #6c757d; font-size: .9rem; }
  .gal-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: .75rem; }
  .gal-item { margin: 0; cursor: zoom-in; overflow: hidden; border-radius: 8px; }
  .gal-item img { width: 100%; aspect-ratio: 4 / 3; object-fit: cover; display: block; transition: transform .25s; }
  .gal-item:hover img { transform: scale(1.04); }
  .gal-box { border: none; padding: 0; background: transparent; max-width: 94vw; overflow: visible; }
  .gal-box::backdrop { background: rgba(0,0,0,.88); }
  .gal-box img { max-width: 86vw; max-height: 80vh; display: block; margin: 0 auto; border-radius: 4px; }
  .gal-box p { color: #fff; text-align: center; margin-top: .6rem; }
  .gal-close { position: fixed; top: 1rem; right: 1.25rem; background: none; border: none; color: #fff; font-size: 2.2rem; cursor: pointer; }
  .gal-nav { position: fixed; top: 50%; transform: translateY(-50%); background: rgba(255,255,255,.12); border: none; color: #fff;
    font-size: 2.4rem; width: 3rem; height: 3rem; border-radius: 50%; cursor: pointer; line-height: 1; }
  .gal-prev { left: 1rem; } .gal-next { right: 1rem; }
</style>

<script>
(function () {
  const box = document.getElementById('galBox'); if (!box) return;
  const img = document.getElementById('galBoxImg'), cap = document.getElementById('galBoxCap');
  let list = [], idx = 0;
  const visible = () => [...document.querySelectorAll('.gal-album:not([hidden]) .gal-item')];
  const show = i => { idx = (i + list.length) % list.length; const it = list[idx], im = it.querySelector('img');
    img.src = im.src; img.alt = im.alt; cap.textContent = it.dataset.caption + '  (' + (idx + 1) + '/' + list.length + ')'; };
  document.querySelectorAll('.gal-btn').forEach(btn => btn.addEventListener('click', () => {
    document.querySelectorAll('.gal-btn').forEach(b => b.classList.remove('is-active'));
    btn.classList.add('is-active');
    const f = btn.dataset.filter;
    document.querySelectorAll('.gal-album').forEach(a => { a.hidden = !(f === 'all' || a.dataset.cat === f); });
  }));
  document.querySelectorAll('.gal-item').forEach(it => {
    const open = () => { list = visible(); show(list.indexOf(it)); box.showModal(); };
    it.addEventListener('click', open);
    it.addEventListener('keydown', e => { if (e.key === 'Enter') open(); });
  });
  box.querySelector('.gal-close').addEventListener('click', () => box.close());
  box.querySelector('.gal-prev').addEventListener('click', e => { e.stopPropagation(); show(idx - 1); });
  box.querySelector('.gal-next').addEventListener('click', e => { e.stopPropagation(); show(idx + 1); });
  box.addEventListener('click', e => { if (e.target === box) box.close(); });
  document.addEventListener('keydown', e => { if (!box.open) return;
    if (e.key === 'ArrowRight') show(idx + 1); if (e.key === 'ArrowLeft') show(idx - 1); });
})();
</script>
