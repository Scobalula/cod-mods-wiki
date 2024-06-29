---
layout: page
title: Software
permalink: /docs/software/
---

Welcome to our software section, here you'll find apps, tools, and plugins made by the community!

<div class="section-index">
    <hr class="panel-line">
    {% for post in site.docs  %}   
        {% if post.section == "software" %}  
            <div class="entry">
            <h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
            <p>{{ post.description }}</p>
            </div>
        {% endif %}
    {% endfor %}
</div>
