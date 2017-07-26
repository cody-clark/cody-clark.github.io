---
layout: post
---

{% include note.html content="This is my note. But the **sad** thing is that *Markdown* doesn't [work](#)!" %}

{% include tip.html content="This is my tip." %}

{% include warning.html content="This is my warning." %}

{% include important.html content="This is my important info." %}

{% include callout.html content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. But the **sad** thing is that *Markdown* doesn't [work](#)!" type="primary" %}

{% include callout.html content="This is my danger type callout. It has a border on the left whose color you define by passing a type parameter." type="danger" %}

{% include callout.html content="This is my default type callout. It has a border on the left whose color you define by passing a type parameter." type="default" %}

{% include callout.html content="This is my primary type callout. It has a border on the left whose color you define by passing a type parameter." type="primary" %}

{% include callout.html content="This is my success type callout. It has a border on the left whose color you define by passing a type parameter." type="success" %}

{% include callout.html content="This is my info type callout. It has a border on the left whose color you define by passing a type parameter." type="info" %}

{% include callout.html content="This is my warning type callout. It has a border on the left whose color you define by passing a type parameter." type="warning" %}

This is another test. And the **cool** thing is that *Markdown* still [works](#)!
{: .notice}

This is another test. And the **cool** thing is that *Markdown* still [works](#)!
{: .info}

This is another test. And the **cool** thing is that *Markdown* still [works](#)!
{: .caution}

This is another test. And the **cool** thing is that *Markdown* still [works](#)!
{: .warning}
