---
layout: post
---

## Incldes
{% include note.html content="This is my note." %}

{% include tip.html content="This is my tip." %}

{% include important.html content="This is my important info." %}

{% include warning.html content="This is my warning." %}

## CSS
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
