---
layout: post
---

## Includes

### Callouts
{% include note.html content="This is my note." %}

{% include tip.html content="This is my tip." %}

{% include important.html content="This is my important info." %}

{% include warning.html content="This is my warning." %}

### Colors
{% include callout.html content="This is my primary type callout. It has a border on the left whose color you define by passing a type parameter." type="primary" %}

{% include callout.html content="This is my success type callout. It has a border on the left whose color you define by passing a type parameter." type="success" %}

{% include callout.html content="This is my warning type callout. It has a border on the left whose color you define by passing a type parameter." type="warning" %}

{% include callout.html content="This is my danger type callout. It has a border on the left whose color you define by passing a type parameter." type="danger" %}

## CSS
### Callouts
This is another note. And the **cool** thing is that *Markdown* still [works](#)!
{: .notice}

This is another callout. And the **cool** thing is that *Markdown* still [works](#)!
{: .info}

This is another callout. And the **cool** thing is that *Markdown* still [works](#)!
{: .caution}

This is another warning. And the **cool** thing is that *Markdown* still [works](#)!
{: .warning}

## Differences
{%raw%}{% include note.html content="This is my note." %}{% endraw%}
{% include note.html content="This is my note." %}

This is my note. <br/> {: .notice}

This is my note. 
{: .notice}
