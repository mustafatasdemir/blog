---
layout: page
title: Arşiv
---
<ul class="posts">
  {% for post in site.posts %}

    {% capture time_post %}{{ post.date | date: "%Y" }}{% endcapture %}
    {% capture time_now %}{{ site.time | date: "%Y" | minus:1 }}{% endcapture %}
    {% if time_post <= time_now %}

      {% unless post.next %}
        <h3>{{ post.date | date: '%Y' }}</h3>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          <h3>{{ post.date | date: '%Y' }}</h3>
        {% endif %}
      {% endunless %}

      <li itemscope>
        <a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
        <p class="post-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {% include date-time.html %} - <i class="fa fa-pencil-square-o" aria-hidden="true"></i> {% include word-count.html %}</span></p>
      </li>

    {% endif %}

  {% endfor %}
</ul>
