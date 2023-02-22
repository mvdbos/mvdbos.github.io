---
layout: base
---
<!--suppress HtmlUnknownTarget -->
<ul>
    {% for post in site.posts %}
        <div>
            <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
            {% include excerpt.html post=post %}
            <span class="reading-time" title="Estimated read time">
                [ {{ post.date | date: '%b %d, %Y' }} ] [ {% include read_time.html content=post.content     %} ]
            </span> 
            <hr />
        </div>
    {% endfor %}
</ul>