{% set image = resize_image(path=page.colocated_path ~ image, height=300, width=300) %}
<img src="{{ image.url }}" />