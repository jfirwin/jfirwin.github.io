---
permalink: /contact
title: "Contact"
excerpt: "This is the exerpt on the contact page"
layouts_gallery:
  - url: /assets/images/mm-layout-splash.png
    image_path: /assets/images/mm-layout-splash.png
    alt: "splash layout example"
  - url: /assets/images/mm-layout-single-meta.png
    image_path: /assets/images/mm-layout-single-meta.png
    alt: "single layout with comments and related posts"
  - url: /assets/images/mm-layout-archive.png
    image_path: /assets/images/mm-layout-archive.png
    alt: "archive layout example"
last_modified_at: 2018-06-04T12:04:24-04:00
author_profile: true
layout: single
---
---
<form action="https://formspree.io/foster@jfirwin.com"
      method="POST" id="contact_form">
    <input type="hidden" name="_subject" value="Contact Form Submission" />
    <input type="text" name="_gotcha" style="display:none" />
    <input type="hidden" name="_next" value="https://jfirwin.com/thank-you" />
    Name
    <input type="text" name="name" required autocomplete="off" placeholder="First Last">
    Email
    <input type="email" name="_replyto" required autocomplete="off" placeholder="you@email.com">
    Message
    <textarea form="contact_form" name="message" required autocomplete="off" placeholder="Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."></textarea>
    <input type="submit" value="Send" class="btn btn--primary">
</form>
---
Don't want to hassle with online forms and captchas?

Drop a line at [foster@jfirwin.com](mailto:"foster@jfirwin.com").
