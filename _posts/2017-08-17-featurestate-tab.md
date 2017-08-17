{% capture stable %}
Feature State: Stable

* The version name is vX where X is an integer.
* Stable versions of features will appear in released software for many subsequent versions.

{% endcapture %}

{% assign tab_names = 'Stable' | split: ',' | compact %}
{% assign tab_contents = site.emptyArray | push: stable %}

{% include tabs.md %}
