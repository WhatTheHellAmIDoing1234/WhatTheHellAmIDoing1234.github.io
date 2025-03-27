---
layout: page
title: "All Blog Posts"
description: "Browse all our articles on Psychology & AI Insights."
permalink: /blog/
---
<section id="blog-navigation">
<div class="blog-input">
  <h2>All Articles</h2>
  <input type="text" id="searchInput" onkeyup="filterArticles()" placeholder="Search Articles" />
</div>
  <div class="articles">
    {% for post in site.posts %}
      <article class="article">
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt | strip_html | truncatewords: 60 }}</p>
      </article>
    {% endfor %}
  </div>
</section>

<script>
  // JavaScript to filter articles
  function filterArticles() {
    const input = document.getElementById('searchInput').value.toLowerCase();
    const articles = document.getElementsByClassName('article');
    for (let i = 0; i < articles.length; i++) {
      const title = articles[i].querySelector('h3').innerText.toLowerCase();
      const summary = articles[i].querySelector('p').innerText.toLowerCase();
      articles[i].style.display = (title.includes(input) || summary.includes(input)) ? '' : 'none';
    }
  }
</script>
