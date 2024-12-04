{% set image = resize_image(path=page.colocated_path ~ image, width=600, height=600, op="fit") %}
<div class="article-image">
    <img src="{{ image.url }}" />
    <div><b>Above: </b>{{ body }}</div>
</div>