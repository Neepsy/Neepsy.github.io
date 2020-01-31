---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: splash
title: Home

header:
 overlay_image: assets/images/splash.jpg
 overlay_color: '#7d7d7d'
 overlay_filter: ".35"
 caption: "Phtoto Credit: Me!"
excerpt: "Welcome to my website. There isn't much on it so far. Hopefully that changes in the future."


intro:
 - excerpt: 'On this site you can find information regarding the projects I have done, and maybe an occasional blog post or two.'
  
projects_row:
 - image_path: assets/images/script.png
   alt: "picture of some JavaScript"
   title: "Projects"
   excerpt: "Take a gander at some of my projects!"
   url: "/projects"
   btn_label: "Read More"
   btn_class: "btn--primary"

info_row:
 - image_path: assets/images/unsplash_nametag.jpg
   image_caption: "[Image Credit: Unsplash](https://unsplash.com/photos/2enBTsIVhUU)"
   alt: "nametag with hello written on it"
   title: "About Me"
   excerpt: "Learn more about me through what personal info I am willing to share"
   url: "/about"
   btn_label: "Read More"
   btn_class: "btn--primary"

---

{% include feature_row id="intro" type="center" %}

{% include feature_row id="projects_row" type="left" %}

{% include feature_row id="info_row" type="right" %}