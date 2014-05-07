---
layout: page
title: Xi Dai's Blog
tagline: Guns for show, knives for pro.
---
{% include JB/setup %}
<ul class="posts">
  {% for post in site.posts %}
    <div>
     <h2><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h2>
     <div><em>{{ post.date | date_to_string }} </em>
          by <strong>{{ site.author.name }}</strong>
          {% unless post.tags == empty %}
            <span class="tag_box inline">
            {% assign tags_list = post.tags %}
            {% include JB/tags_list %}
            </span>
          {% endunless %} 
      </div><br>
     <div>{{ post.description }}</div>
   </div>
   <hr>
  {% endfor %}
</ul>

