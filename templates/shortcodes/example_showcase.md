## {{ name }}
{% if gif %}
<img src="{{ image }}" width=300 height=300 />
{% else %}
{% set image = resize_image(path=page.colocated_path ~ image, height=300, width=300) %}
<img src="{{ image.url }}" />
{% endif %}
{{ body }}