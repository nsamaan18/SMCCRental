---
layout: default
title: About
permalink: /about/
nav: about

site_name: "St. Mary Community Centre"
mission: "To provide a welcoming, accessible space for worship, community gatherings, cultural events, and social support in Ottawa."

highlights:
  - title: Community Programs
    text: "Youth activities, family gatherings, cultural celebrations, and educational workshops."
  - title: Accessible Spaces
    text: "Flexible rooms for meetings, celebrations, classes, and community initiatives."
  - title: Volunteer-Driven
    text: "Operated by dedicated volunteers committed to serving the local community."
    
address_line: "Ottawa, ON"
street_line: "123 Example St."
phone: "613-000-0000"
email: "info@smcc.ca"
---

<style>
  .smcc-about{
    max-width: 1100px;
    margin: 0 auto;
    padding: 24px 0 40px;
    font-family: "Nunito", system-ui, sans-serif;
  }

  .about-hero{
    border: 1px solid #eee;
    border-radius: 14px;
    padding: 18px 18px;
    background: #fff;
    margin-bottom: 18px;
  }

  .about-hero h1{
    margin: 0 0 8px;
    font-weight: 800;
    color: #0D5295;
  }

  .about-hero p{
    margin: 0;
    font-size: 17px;
  }

  .about-grid{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 18px;
  }

  @media (max-width: 900px){
    .about-grid{ grid-template-columns: 1fr; }
  }

  .panel{
    border: 1px solid #eee;
    border-radius: 14px;
    background: #fff;
    padding: 16px 16px;
  }

  .panel h2{
    margin: 0 0 12px;
    font-size: 18px;
    font-weight: 800;
  }

  .highlight-list{
    display: grid;
    gap: 10px;
  }

  .highlight{
    border: 1px solid #eee;
    border-radius: 12px;
    padding: 12px 12px;
  }

  .highlight strong{
    display:block;
    margin-bottom: 4px;
  }

  .contact-list{
    line-height: 1.7;
  }

  .contact-list a{
    color: #000;
    text-decoration: none;
    border-bottom: 1px solid transparent;
  }

  .contact-list a:hover{
    border-bottom-color: #000;
  }
</style>

<section class="smcc-about">

  <!-- HERO / MISSION -->
  <div class="about-hero">
    <h1>{{ page.site_name }}</h1>
    <p>{{ page.mission }}</p>
  </div>

  <div class="about-grid">

    <!-- WHAT WE DO -->
    <div class="panel">
      <h2>What We Do</h2>

      <div class="highlight-list">
        {% for item in page.highlights %}
          <div class="highlight">
            <strong>{{ item.title }}</strong>
            <span>{{ item.text }}</span>
          </div>
        {% endfor %}
      </div>
    </div>

    <!-- CONTACT / LOCATION -->
    <div class="panel">
      <h2>Location & Contact</h2>

      <div class="contact-list">
        <div><strong>Address</strong></div>
        <div>{{ page.street_line }}</div>
        <div>{{ page.address_line }}</div>

        {% if page.phone %}
          <div style="margin-top:10px;">
            <strong>Phone</strong><br>
            <a href="tel:{{ page.phone | replace: ' ', '' | replace: '-', '' }}">{{ page.phone }}</a>
          </div>
        {% endif %}

        {% if page.email %}
          <div style="margin-top:10px;">
            <strong>Email</strong><br>
            <a href="mailto:{{ page.email }}">{{ page.email }}</a>
          </div>
        {% endif %}

        <div style="margin-top:14px;">
          <a href="{{ '/rentals/' | relative_url }}"
             style="display:inline-block;padding:10px 14px;border-radius:12px;border:1px solid #6495ED;color:#6495ED;text-decoration:none;font-weight:800;">
            View Room Rentals
          </a>
        </div>
      </div>
    </div>

  </div>

</section>
