---
layout: default
title: Community
permalink: /community/
nav: community
---

<style>
  .community-wrap{
    max-width:1100px;
    margin:0 auto;
    padding:30px 0 50px;
    font-family:"Nunito", system-ui, sans-serif;
  }

  .community-header{
    margin-bottom:30px;
  }

  .community-header h1{
    font-weight:800;
    color:#0D5295;
    margin-bottom:10px;
  }

  .events-grid{
    display:grid;
    grid-template-columns: repeat(3, 1fr);
    gap:20px;
  }

  @media (max-width: 1000px){
    .events-grid{ grid-template-columns: repeat(2,1fr); }
  }

  @media (max-width: 700px){
    .events-grid{ grid-template-columns: 1fr; }
  }

  .event-card{
    background:#fff;
    border:1px solid #eee;
    border-radius:14px;
    overflow:hidden;
    box-shadow:0 2px 6px rgba(0,0,0,0.06);
    transition:transform .2s ease, box-shadow .2s ease;
    display:flex;
    flex-direction:column;
  }

  .event-card:hover{
    transform:translateY(-4px);
    box-shadow:0 4px 12px rgba(0,0,0,0.12);
  }

  .event-image{
    width:100%;
    height:200px;
    object-fit:cover;
  }

  .event-content{
    padding:14px 16px;
    flex:1;
  }

  .event-title{
    font-weight:800;
    font-size:16px;
    margin-bottom:6px;
  }

  .event-meta{
    font-size:13px;
    color:#666;
    margin-bottom:10px;
  }

  .event-description{
    font-size:14px;
    line-height:1.5;
    margin-bottom:10px;
  }

  .event-link{
    display:inline-block;
    margin-top:auto;
    padding:8px 12px;
    border-radius:10px;
    border:1px solid #6495ED;
    color:#6495ED;
    font-weight:700;
    text-decoration:none;
    transition:all .2s ease;
  }

  .event-link:hover{
    background:#6495ED;
    color:#fff;
  }

  .section-title{
    margin-top:50px;
    margin-bottom:20px;
    font-weight:800;
    font-size:20px;
    border-bottom:2px solid #eee;
    padding-bottom:6px;
  }
</style>

<section class="community-wrap">

  <div class="community-header">
    <h1>Community Events</h1>
    <p>Discover programs, celebrations, and gatherings happening at SMCC.</p>
  </div>

  {%- assign today_ts = "now" | date: "%s" | plus: 0 -%}
  {%- assign upcoming = site.data.events
      | where_exp: "e", "e.date and (e.date | date: '%s' | plus: 0) >= today_ts"
      | sort: "date"
  -%}
  {%- assign past = site.data.events
      | where_exp: "e", "e.date and (e.date | date: '%s' | plus: 0) < today_ts"
      | sort: "date"
      | reverse
  -%}

  {% if upcoming.size > 0 %}
    <div class="section-title">Upcoming Events</div>
    <div class="events-grid">
      {% for event in upcoming %}
        <div class="event-card">
          {% if event.image %}
            <img src="{{ event.image | relative_url }}" class="event-image" alt="{{ event.title }}">
          {% endif %}
          <div class="event-content">
            <div class="event-title">{{ event.title }}</div>
            <div class="event-meta">
              {{ event.date | date: "%B %-d, %Y" }}
              {% if event.time %} · {{ event.time }}{% endif %}
              {% if event.location %}<br>{{ event.location }}{% endif %}
            </div>
            <div class="event-description">
              {{ event.description }}
            </div>
            {% if event.link %}
              <a href="{{ event.link }}" class="event-link" target="_blank">Learn More</a>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% endif %}

  {% if past.size > 0 %}
    <div class="section-title">Past Events</div>
    <div class="events-grid">
      {% for event in past %}
        <div class="event-card">
          {% if event.image %}
            <img src="{{ event.image | relative_url }}" class="event-image" alt="{{ event.title }}">
          {% endif %}
          <div class="event-content">
            <div class="event-title">{{ event.title }}</div>
            <div class="event-meta">
              {{ event.date | date: "%B %-d, %Y" }}
            </div>
            <div class="event-description">
              {{ event.description }}
            </div>
          </div>
        </div>
      {% endfor %}
    </div>
  {% endif %}

</section>
