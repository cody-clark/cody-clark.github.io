{% assign tab_set_id = tab_set_name | default: "tabset" | slugify %}

{% for name in tab_names %}
{{ name | strip }}
{% endfor %}
{% for content in tab_contents %}
{{ content | markdownify }}
{% endfor %}
<script>$(function(){$("#{{tab_set_id}}").tabs();});</script>
