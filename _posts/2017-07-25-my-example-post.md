---
layout: post
---

## The Code
```console
{% raw %} {% include note.html content="This is my note." %}{% endraw %}
```

{% include note.html content="This is my note." %}

```console
{% raw %} {% include callout.html content="This is my primary type callout. It has a border on the left whose color you define by passing a type parameter." type="primary" %} {% endraw %}
```

{% include callout.html content="This is my primary type callout. It has a border on the left whose color you define by passing a type parameter." type="primary" %}

```console
This is my note. 
{: .notice}
```

This is my note. 
{: .notice}

```console
This is my note. Unfortunately, you have to use ```<br/>``` for multiple lines. <br/> <br/> But otherwise, _Markdown_ still **works**!
{: .notice1}
```
This is my note. Unfortunately, you have to use ```<br/>``` for multiple lines. <br/> <br/> But otherwise, _Markdown_ still **works**!
{: .notice1}

## Includes
### Callouts
{% include note.html content="This is my note." %}

{% include tip.html content="This is my tip." %}

{% include important.html content="This is my important info." %}

{% include warning.html content="This is my warning." %}

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

This is another note. And the **cool** thing is that *Markdown* still [works](#)!
{: .notice1}

This is another callout. And the **cool** thing is that *Markdown* still [works](#)!
{: .info1}

This is another callout. And the **cool** thing is that *Markdown* still [works](#)!
{: .caution1}

This is another warning. And the **cool** thing is that *Markdown* still [works](#)!
{: .warning1}









## Callout Formatting
Callouts help create different rhetorical appeal levels. Our documentation supports three different callouts: note, caution, and warning. 

Use the following syntax to apply style:

```console
**Note:** This is my note. 
{: .notice1}
```

The output is:

**Note:** This is my note. 
{: .notice1}

Callouts should generally be single sentences but can span multiple lines if you use ```<br/>``` tags.

```console
**Note:"** This is my note. Use ```<br/>``` to create multiple lines. <br/> <br/> **You** can still use _Markdown_ to ~format text~!
{: .notice1}
```

The output is:

**Note:** This is my note. Use ```<br/>``` to create multiple lines. <br/> <br/> **You** can still use _Markdown_ to ~format text~!
{: .notice1}

Trying to use regular Markdown with multiple lines will **not** work.
{: .warning1}

```console
**Note:** This is my note. 

I didn't read the stlye guide.
{: .notice1}
```

**Note** This is my note. 

I didn't read the stlye guide.
{: .notice1}
