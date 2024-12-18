+++
date = '2024-12-17T14:14:51-06:00'
draft = false
title = 'Random Photo'
type = 'page'
+++
<script>
  async function randomPhoto() {
    const response = await fetch('/tags/photos/index.json');
    const posts = await response.json();
    const randomPost = posts[Math.floor(Math.random() * posts.length)];
    window.location.href = randomPost.url; // Redirect to the random post
  }
</script>
