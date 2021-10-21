---
title: Categories
section: blog
layout: blog
---
<div class="hcat">
  <!-- <h2>Posts by category:</h2> -->
  <ul>
  {% assign sorted_categories = site.categories | sort %}
  {% for category in sorted_categories %}
    <li>
      <h5 id="{{ category | first }}">&raquo; {{ category | first | capitalize }}</h5>
      <ul>
      {% for posts in category %}
        {% for post in posts %}
          {% if post.title %}
            <li><a href="{{ post.url }}">{{ post.title }}</a> <span class="byline"> · {{ post.date | date: "%Y.%m.%d" }}</span></li>
          {% endif %}
        {% endfor %}
      {% endfor %}
      </ul>
    </li>
  {% endfor %}
  </ul>
</div><!-- .hfeed -->
