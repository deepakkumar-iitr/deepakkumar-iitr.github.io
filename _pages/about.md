---
layout: about
title: About
permalink: /
subtitle: Postdoctoral Researcher, AI Division, <a href='https://www.kddi-research.jp/english'>KDDI Research, Inc.</a>

profile:
  align: right
  image: deepak_profile.png
  image_circular: true
  more_info: >
    <p>KDDI Research, Inc.</p>
    <p>Fujimino, Saitama, Japan</p>

selected_papers: true
social: true

announcements:
  enabled: false
  scrollable: true
  limit: 5

latest_posts:
  enabled: false
---

I am a Postdoctoral Researcher in the AI Division at [KDDI Research, Inc.](https://www.kddi-research.jp/english), Japan, where I work on **Vision-Language-Action (VLA) models** for robot manipulation.

I received my Ph.D. in Computer Science from [IIT Roorkee](https://www.iitr.ac.in/), advised by [Prof. Balasubramanian Raman](https://faculty.iitr.ac.in/cs/bala/), with a thesis on multimodal affect and behavior analysis. Before that, I was a research intern at Samsung Research Institute Bangalore, working on Vision-Language Models, and an Assistant Professor at GBPUAT Pantnagar.

My research interests include robot learning with VLA models, multimodal affective computing (audio, video, text, and physiological signals), and Vision-Language Models.


<div class="dk-news">
  <h2>News</h2>
  {% assign all_news = site.news | sort: "date" | reverse %}
  <table class="dk-news-table">
    {% for item in all_news limit: 5 %}
    <tr>
      <th scope="row">{{ item.date | date: "%b %-d, %Y" }}</th>
      <td>{{ item.content | markdownify | remove: "<p>" | remove: "</p>" }}</td>
    </tr>
    {% endfor %}
  </table>
  {% if all_news.size > 5 %}
  <button type="button" class="dk-news-btn" onclick="document.getElementById('dkNewsAll').showModal()">View all news ({{ all_news.size }})</button>
  {% endif %}

  <dialog id="dkNewsAll" class="dk-news-dialog" aria-labelledby="dkNewsTitle">
    <div class="dk-news-head">
      <h3 id="dkNewsTitle">All news</h3>
      <button type="button" class="dk-news-close" aria-label="Close" onclick="this.closest('dialog').close()">&times;</button>
    </div>
    <table class="dk-news-table">
      {% for item in all_news %}
      <tr>
        <th scope="row">{{ item.date | date: "%b %-d, %Y" }}</th>
        <td>{{ item.content | markdownify | remove: "<p>" | remove: "</p>" }}</td>
      </tr>
      {% endfor %}
    </table>
  </dialog>
</div>

<style>
  .dk-news { clear: both; margin-top: 2.5rem; padding-top: 1.5rem; border-top: 1px solid rgba(0,0,0,.15); }
  .dk-news h2 { margin-bottom: 1rem; }
  h2:has(> a[href$="/publications/"]) { clear: both; margin-top: 2.5rem; padding-top: 1.5rem; border-top: 1px solid rgba(0,0,0,.15); }
  .dk-news-table { width: 100%; border-collapse: collapse; }
  .dk-news-table th { white-space: nowrap; vertical-align: top; padding: .35rem 1rem .35rem 0; font-weight: 600; width: 1%; }
  .dk-news-table td { padding: .35rem 0; vertical-align: top; }
  .dk-news-btn { margin-top: .75rem; padding: .4rem 1rem; border-radius: 2rem; cursor: pointer;
    border: 1px solid var(--global-theme-color, #b509ac); background: transparent; color: var(--global-theme-color, #b509ac); }
  .dk-news-btn:hover { background: var(--global-theme-color, #b509ac); color: #fff; }
  .dk-news-dialog { width: min(760px, 92vw); max-height: 80vh; border: none; border-radius: 10px; padding: 1.25rem 1.5rem;
    background: var(--global-bg-color, #fff); color: var(--global-text-color, #000); box-shadow: 0 10px 40px rgba(0,0,0,.25); }
  .dk-news-dialog::backdrop { background: rgba(0,0,0,.5); }
  .dk-news-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: .5rem; }
  .dk-news-head h3 { margin: 0; }
  .dk-news-close { background: none; border: none; font-size: 1.8rem; line-height: 1; cursor: pointer; color: inherit; }
  h2 a[href$="/publications/"] { text-transform: capitalize; }
</style>

<script>
  document.addEventListener('click', function (e) {
    var d = document.getElementById('dkNewsAll');
    if (d && e.target === d) d.close();   // click outside to close
  });
</script>
