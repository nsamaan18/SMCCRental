---
layout: default
title: Media
permalink: /media/
nav: media
# Hero banner image (optional)
hero_image: /images/media/hero-banner.jpg
hero_alt: SMCC Media Gallery
---
<style>
  /* Reuse homepage vars for consistency */
  :root {
    --ink: #111;
    --muted: #666;
    --border: #e9e9e9;
    --card: #fff;
    --blue: #0D5295;
    --lightblue: #6495ED;
    --radius: 14px;
  }
  .smcc-media {
    max-width: 1100px;
    margin: 0 auto;
    padding: 20px 0 40px;
    font-family: "Nunito", system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
    color: var(--ink);
  }
  /* Hero */
  .hero {
    border-radius: var(--radius);
    overflow: hidden;
    border: 1px solid var(--border);
    background: #f7f7f7;
    position: relative;
    z-index: 1;
    text-align: center;
  }
  .hero img {
    width: 100%;
    height: auto;
    max-height: 300px;
    object-fit: cover;
  }
  .hero-title {
    position: absolute;
    bottom: 20px;
    left: 20px;
    color: #fff;
    font-size: 28px;
    font-weight: 800;
    text-shadow: 0 2px 8px rgba(0,0,0,.5);
  }
  /* Sections */
  .section {
    margin-top: 30px;
  }
  .section h2 {
    font-size: 22px;
    font-weight: 800;
    margin-bottom: 16px;
  }
  /* Photo Gallery */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 12px;
  }
  .gallery-item {
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
    background: var(--card);
  }
  .gallery-item img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }
  .gallery-caption {
    padding: 10px;
    text-align: center;
    font-size: 14px;
    color: var(--muted);
  }
  /* Videos */
  .videos {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 18px;
  }
  .video-item {
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 12px;
    background: var(--card);
  }
  .video-item iframe {
    width: 100%;
    height: 200px;
    border: 0;
  }
  .video-title {
    margin-top: 8px;
    font-weight: 700;
  }
  /* Press */
  .press-list {
    display: grid;
    gap: 12px;
  }
  .press-item {
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 12px;
    background: var(--card);
  }
  .press-item a {
    font-weight: 800;
    color: var(--blue);
    text-decoration: none;
  }
  .press-item a:hover {
    text-decoration: underline;
  }
  .press-date {
    font-size: 13px;
    color: var(--muted);
  }
  /* CTA */
  .cta-row {
    margin-top: 24px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
  }
  .cta {
    padding: 10px 14px;
    border-radius: 12px;
    border: 1px solid var(--lightblue);
    color: var(--lightblue);
    text-decoration: none;
    font-weight: 800;
    background: #fff;
  }
  .cta:hover {
    background: var(--lightblue);
    color: #fff;
  }
  @media (max-width: 768px) {
    .gallery, .videos { grid-template-columns: 1fr; }
  }
</style>

<section class="smcc-media">
  <!-- Hero -->
  <div class="hero">
    {% if page.hero_image %}
      <img src="{{ page.hero_image | relative_url }}" alt="{{ page.hero_alt | default: 'SMCC Media' }}">
    {% endif %}
    <h1 class="hero-title">Media Gallery</h1>
  </div>

  <!-- Photos -->
  <div class="section">
    <h2>Photos</h2>
    {% assign photos = site.data.smcc_media.photos %}
    {% if photos and photos.size > 0 %}
      <div class="gallery">
        {% for photo in photos %}
          <div class="gallery-item">
            <img src="{{ photo.src | relative_url }}" alt="{{ photo.alt }}">
            {% if photo.caption %}
              <div class="gallery-caption">{{ photo.caption }}</div>
            {% endif %}
          </div>
        {% endfor %}
      </div>
    {% else %}
      <p style="color: var(--muted);">Add photos to _data/smcc_media.yml or upload directly.</p>
    {% endif %}
  </div>

  <!-- Videos -->
  <div class="section">
    <h2>Videos</h2>
    {% assign videos = site.data.smcc_media.videos %}
    {% if videos and videos.size > 0 %}
      <div class="videos">
        {% for video in videos %}
          <div class="video-item">
            <iframe src="{{ video.embed }}" title="{{ video.title }}" allowfullscreen></iframe>
            <div class="video-title">{{ video.title }}</div>
          </div>
        {% endfor %}
      </div>
    {% else %}
      <p style="color: var(--muted);">Embed YouTube/Vimeo videos in _data/smcc_media.yml.</p>
    {% endif %}
  </div>

  <!-- Press Mentions -->
  <div class="section">
    <h2>Press Mentions</h2>
    {% assign press = site.data.smcc_media.press | sort: "date" | reverse %}
    {% if press and press.size > 0 %}
      <div class="press-list">
        {% for item in press %}
          <div class="press-item">
            <a href="{{ item.link }}" target="_blank" rel="noopener noreferrer">{{ item.headline }}</a>
            <div class="press-date">{{ item.date | date: "%b %-d, %Y" }}</div>
            {% if item.excerpt %}
              <p>{{ item.excerpt }}</p>
            {% endif %}
          </div>
        {% endfor %}
      </div>
    {% else %}
      <p style="color: var(--muted);">Add press links to _data/smcc_media.yml.</p>
    {% endif %}
  </div>

  <!-- CTA -->
  <div class="cta-row">
    <a class="cta" href="{{ '/donate/' | relative_url }}">Donate</a>
    <a class="cta" href="{{ '/contact/' | relative_url }}">Contact Us</a>
  </div>
</section>
