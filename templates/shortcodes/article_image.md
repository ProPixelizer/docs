<div class="article-image">
{% if video %}
<video autoplay muted loop playsinline preload="metadata" width="600" height="600">
<source src="{{ video }}.webm" type="video/webm" />
<source src="{{ video }}.mp4" type="video/mp4" />
Your browser does not support embedded video.
</video>
{% elif gif %}
<img src="{{ image }}" width=600 height=600 />
{% else %}
{% set image = resize_image(path=page.colocated_path ~ image, height=600, width=600, op="fit") %}
<img src="{{ image.url }}" />
{% endif %}

<div>{% if title %}<b>{{ title }}: </b>{% else %}<b>Above: </b>{% endif %}{{ body }}</div>
</div>
