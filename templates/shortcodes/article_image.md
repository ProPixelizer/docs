<div class="article-image">
{% if gif %}
<img src="{{ image }}" width=600 height=600 />
{% else %}
{% set image = resize_image(path=page.colocated_path ~ image, height=600, width=600, op="fit") %}
<img src="{{ image.url }}" />
{% endif %}
<div><b>Above: </b>{{ body }}</div>
</div>