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

selected_papers: false
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


<div class="dk-section">
  <h2>Education</h2>
  <div class="dk-edu-grid">
    <div class="dk-edu-card">
      <h3>Ph.D. in Computer Science</h3>
      <p class="dk-inst">Indian Institute of Technology Roorkee, Uttarakhand, India</p>
      <p class="dk-date">&bull; Dec 2021 – Jul 2025</p>
      <p class="dk-note">Thesis: <em>From Signals to Visuals: Multimodal Affect and Behavior Analysis</em></p><p class="dk-note">Supervisor: Prof. Balasubramanian Raman</p>
    </div>
    <div class="dk-edu-card">
      <h3>M.Tech.</h3>
      <p class="dk-inst">Motilal Nehru National Institute of Technology Allahabad, Prayagraj, India</p>
      <p class="dk-date">&bull; Aug 2014 – Jun 2016</p>
      <p class="dk-note">Supervisor: Prof. Rajesh Tripathi</p>
    </div>
    <div class="dk-edu-card">
      <h3>B.Tech.</h3>
      <p class="dk-inst">Uttar Pradesh Technical University, Lucknow, India</p>
      
      
    </div>
  </div>
</div>

<div class="dk-section">
  <h2>Work Experience</h2>
  <div class="dk-exp-list">
    <div class="dk-exp-item">
      <h3>KDDI Research, Inc., Fujimino, Saitama, Japan</h3>
      <div class="dk-exp-row"><span class="dk-role">Postdoctoral Researcher</span><span class="dk-date">Apr 2026 – Present</span></div>
      <p class="dk-note">Working on Vision-Language-Action (VLA) models for robot manipulation.</p>
    </div>
    <div class="dk-exp-item">
      <h3>Samsung Research Institute Bangalore (SRI-B), India</h3>
      <div class="dk-exp-row"><span class="dk-role">Research Intern</span><span class="dk-date">Feb 2025 – Aug 2025</span></div>
      <p class="dk-note">Worked on Vision-Language Models (VLMs).</p>
    </div>
    <div class="dk-exp-item">
      <h3>Deloitte US-India Offices</h3>
      <div class="dk-exp-row"><span class="dk-role">Work-Studentship</span><span class="dk-date">Aug 2023 – Jan 2024</span></div>
      
    </div>
    <div class="dk-exp-item">
      <h3>College of Technology, GBPUAT, Pantnagar, Uttarakhand, India</h3>
      <div class="dk-exp-row"><span class="dk-role">Assistant Professor under TEQIP-III (NPIU-MHRD)</span><span class="dk-date">Oct 2018 – Dec 2021</span></div>
      
    </div>
  </div>
</div>

<h2><a href="{{ '/publications/' | relative_url }}" style="color: inherit">selected publications</a></h2>
<div class="publications">
{% bibliography --group_by none --query @*[selected=true]* %}
</div>

<div class="dk-research">
  <div class="dk-research-head">
    <h2>Research Areas</h2>
    <a class="dk-news-btn" href="{{ '/research/' | relative_url }}">Research details &rarr;</a>
  </div>
  <div class="dk-cards">
    <a class="dk-card" href="{{ '/research/' | relative_url }}">
      <div class="dk-card-img"><img src="{{ '/assets/img/research/research-vla.svg' | relative_url }}" alt="Vision-Language-Action Models" loading="lazy"></div>
      <h3>Vision-Language-Action Models</h3>
      <p>Adapting and evaluating robot foundation models for reliable real-world manipulation.</p>
    </a>
    <a class="dk-card" href="{{ '/research/' | relative_url }}">
      <div class="dk-card-img"><img src="{{ '/assets/img/research/research-affective.svg' | relative_url }}" alt="Multimodal Affective Computing" loading="lazy"></div>
      <h3>Multimodal Affective Computing</h3>
      <p>Emotion, engagement, and personality from video, audio, text, and EEG/ECG signals.</p>
    </a>
    <a class="dk-card" href="{{ '/research/' | relative_url }}">
      <div class="dk-card-img"><img src="{{ '/assets/img/research/research-vlm.svg' | relative_url }}" alt="Vision-Language Models" loading="lazy"></div>
      <h3>Vision-Language Models</h3>
      <p>Multimodal understanding that connects what a model sees with what it reads.</p>
    </a>
  </div>
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
  @media (min-width: 768px) { .profile { margin-top: -5.5rem; width: 25%; max-width: 240px; } }
  .profile .more-info { font-family: inherit; text-align: center; font-size: .95rem; }
  .profile .more-info p { margin: 0; }
  .dk-research { clear: both; margin-top: 2.5rem; padding-top: 1.5rem; border-top: 1px solid rgba(0,0,0,.15); }
  .dk-research-head { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: .75rem; margin-bottom: 1.25rem; }
  .dk-research-head h2 { margin: 0; }
  .dk-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); gap: 1.25rem; }
  .dk-card { display: block; background: #fff; border: 1px solid rgba(0,0,0,.08); border-radius: 14px; overflow: hidden;
             box-shadow: 0 2px 10px rgba(0,0,0,.06); color: inherit; text-decoration: none; transition: transform .15s, box-shadow .15s; }
  .dk-card:hover { transform: translateY(-3px); box-shadow: 0 8px 22px rgba(0,0,0,.10); text-decoration: none; color: inherit; }
  .dk-card-img { aspect-ratio: 2 / 1; background: #faf5fc; }
  .dk-card-img img { width: 100%; height: 100%; object-fit: contain; display: block; }
  .dk-card h3 { font-size: 1.1rem; font-weight: 700; text-align: center; margin: 1rem 1rem .4rem; }
  .dk-card p { font-size: .92rem; text-align: center; color: #555; margin: 0 1rem 1.1rem; }
  .dk-section { clear: both; margin-top: 2.5rem; padding-top: 1.5rem; border-top: 1px solid rgba(0,0,0,.15); }
  .dk-section > h2 { margin-bottom: 1.25rem; }
  .dk-edu-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); gap: 1.25rem; }
  .dk-edu-card { background: #fff; border: 1px solid rgba(0,0,0,.08); border-left: 4px solid var(--global-theme-color, #b509ac);
                 border-radius: 12px; padding: 1rem 1.1rem; box-shadow: 0 2px 10px rgba(0,0,0,.05); }
  .dk-edu-card h3, .dk-exp-item h3 { font-size: 1.08rem; font-weight: 700; margin: 0 0 .3rem; }
  .dk-inst { margin: 0 0 .3rem; color: #444; }
  .dk-date { color: var(--global-theme-color, #b509ac); font-size: .92rem; font-weight: 600; margin: 0 0 .35rem; white-space: nowrap; }
  .dk-note { font-size: .92rem; color: #555; margin: 0 0 .2rem; }
  .dk-exp-list { display: flex; flex-direction: column; gap: 1rem; }
  .dk-exp-item { padding: .25rem 0 .9rem 1.1rem; border-left: 3px solid rgba(0,0,0,.12); position: relative; }
  .dk-exp-item::before { content: ""; position: absolute; left: -7px; top: .45rem; width: 11px; height: 11px; border-radius: 50%;
                         background: var(--global-theme-color, #b509ac); }
  .dk-exp-row { display: flex; justify-content: space-between; flex-wrap: wrap; gap: .5rem; margin-bottom: .25rem; }
  .dk-role { font-style: italic; }
  h2:has(> a[href$="/publications/"]) { clear: both; }
</style>

<script>
  document.addEventListener('click', function (e) {
    var d = document.getElementById('dkNewsAll');
    if (d && e.target === d) d.close();   // click outside to close
  });
</script>
