---
title: "Welcome"
layout: splash
permalink: /
date: 2016-03-23T11:48:41-04:00
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/bryce-canyon-hoodoos.jpg
  cta_label: "View My Portfolio"
  cta_url: "/portfolio"
  caption: "Photo credit: [**Marilyn Irwin**](https://instagram.com/marilyn.m.irwin)"
excerpt: "Hi! I'm Foster Irwin. I like bikes, code, camping, and the Oxford Comma. Parks, Recreation, and Tourism was my major at the University of Utah. I learned how to teach others in that program, and I learned that I never want to stop teaching myself. <br/> <br/>So now I program."
about_row:
  - image_path: /assets/images/bio-pic.jpg
    alt: "Foster Irwin"
    title: "Parks, Rec, & Tourism =/= Programming?"
    excerpt: "I know, I know. When you think of Parks & Rec you think of Leslie Knope, Andy Dwire, or Ron Swanson. The truth is, programming is something I have always loved since I was a kid. I first learned how to work with HTML when I was trying to get my MySpace theme just perfect. (yuck) I always knew that programming would be something I would pursue."
    url: "/about"
    btn_label: "Read About Me"
    btn_class: "btn--primary"
contact_row:
  - image_path: #
    alt: #
    title: "Let's Connect"
    excerpt: ""
    url: "/contact"
    btn_label: "Contact Foster"
    btn_class: "btn--primary"
---

{% include feature_row id="about_row" type="right" %}

{% include feature_row id="contact_row" type="center" %}

<div class="feature__wrapper">
    <div class="feature__item--center">
      <div class="archive__item">
        <div class="archive__item-body">
            <h2 class="archive__item-title">Recent Blog Posts</h2>
        </div>
      </div>
    </div>
    <div class="grid__wrapper">
      {% for post in site.posts limit:4 %}
        {% include archive-single.html type="grid" %}
      {% endfor %}
      <a href="/blog" class="btn btn--primary">View Other Blog Posts</a>
    </div>
</div>
