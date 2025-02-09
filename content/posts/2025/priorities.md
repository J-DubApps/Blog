+++
date = '2025-02-09T12:30:51-06:00'
draft = false
title = 'Remember, When *Everything* Is a Priority...'
description = "...nothing is a priority"
type = 'post'
tags = ["thought", "personal-development", "project-mgmt", "opinion", "tech", "task-mgmt", "skill-development"]
+++
<style>
    /* Basic styling for the thumbnail */
    #thumbnail {
      cursor: pointer;
      border: 1px solid #ccc;
      margin: 20px;
    }

    /* The overlay (initially hidden) */
    #overlay {
      display: none;              /* Hidden by default */
      position: fixed;           /* Stays in place */
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-color: rgba(0,0,0,0.8); /* Dim overlay */
      justify-content: center;   /* Center the image horizontally */
      align-items: center;       /* Center the image vertically */
      z-index: 9999;
    }

    /* The full-size image in the overlay */
    #overlay img {
      max-width: 90%;
      max-height: 90%;
      cursor: pointer;
      box-shadow: 0 0 10px #000;
      border: 2px solid #fff;
    }
  </style>

<div align="center">
  <img 
    id="thumbnail"
    src="https://julianwest.me/Blog/posts/images/priorities.jpg" 
    alt="Thumbnail" 
    width="400"
    height="auto" 
  />
</div>

>
<div id="overlay">
    <img 
      id="fullSize" 
      src="https://julianwest.me/Blog/posts/images/priorities.jpg"" 
      alt="Full Size" 
      title="Click to close"
    />
  </div>

  <script>
    const thumbnail = document.getElementById('thumbnail');
    const overlay   = document.getElementById('overlay');
    const fullSize  = document.getElementById('fullSize');

    // When thumbnail is clicked, show overlay
    thumbnail.addEventListener('click', () => {
      overlay.style.display = 'flex';
    });

    // When full-size image (or overlay) is clicked, hide overlay
    overlay.addEventListener('click', () => {
      overlay.style.display = 'none';
    });
  </script>

<blockquote style="text-align:center; margin-left: 50px;">
 "<b>When <i>everything</i> is A priority, <i>nothing</i> is a priority</b>..." -Karen Martin
</blockquote>


**And** ***remember***: [We Can Do *Anything*, But Not *Everything*](https://julianwest.me/Blog/anything-vs-everything/)