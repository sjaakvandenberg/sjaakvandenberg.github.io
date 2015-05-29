title: Content
date: 2014-01-01 00:00:00
---
Curabitur sed diam eget dolor fermentum semper at eu lorem. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.

<!-- more -->

## Icons

Hey guys, here's some pretty buttons:

<a class="btn small-button icon-twitter" href="#"> twitter</a> <a class="btn small-button icon-feed" href="#"> feed</a> <a class="btn small-button icon-pinterest" href="#"> pinterest</a> <a class="btn small-button icon-linkedin" href="#"> linkedin</a> <a class="btn small-button icon-link" href="#"> link</a> <a class="btn small-button icon-key" href="#"> key</a> <a class="btn small-button icon-location" href="#"> location</a> <a class="btn small-button icon-github" href="#"> github</a> <a class="btn small-button icon-gplus" href="#"> gplus</a> <a class="btn small-button icon-heart" href="#"> heart</a> <a class="btn small-button icon-facebook" href="#"> facebook</a> <a class="btn small-button icon-dribbble" href="#"> dribbble</a> <a class="btn small-button icon-dropbox" href="#"> dropbox</a> <a class="btn small-button icon-attach" href="#"> attach</a> <a class="btn small-button icon-chat" href="#"> chat</a> <a class="btn small-button icon-email" href="#"> email</a> <a class="btn small-button icon-bitcoin" href="#"> bitcoin</a> <a class="btn small-button icon-hexo" href="#"> hexo</a>

CAPS:

<a class="btn small-button icon-twitter" href="#"> TWITTER</a> <a class="btn small-button icon-feed" href="#"> FEED</a> <a class="btn small-button icon-pinterest" href="#"> PINTEREST</a> <a class="btn small-button icon-linkedin" href="#"> LINKEDIN</a> <a class="btn small-button icon-link" href="#"> LINK</a> <a class="btn small-button icon-key" href="#"> KEY</a> <a class="btn small-button icon-location" href="#"> LOCATION</a> <a class="btn small-button icon-github" href="#"> GITHUB</a> <a class="btn small-button icon-gplus" href="#"> GPLUS</a> <a class="btn small-button icon-heart" href="#"> HEART</a> <a class="btn small-button icon-facebook" href="#"> FACEBOOK</a> <a class="btn small-button icon-dribbble" href="#"> DRIBBBLE</a> <a class="btn small-button icon-dropbox" href="#"> DROPBOX</a> <a class="btn small-button icon-attach" href="#"> ATTACH</a> <a class="btn small-button icon-chat" href="#"> CHAT</a> <a class="btn small-button icon-email" href="#"> EMAIL</a> <a class="btn small-button icon-bitcoin" href="#"> BITCOIN</a> <a class="btn small-button icon-hexo" href="#"> HEXO</a>

Lorem ipsum <a class="btn small-button icon-twitter" href="#"> twitter</a> dolor sit amet, consectetur adipisicing elit. Perferendis <a class="btn small-button icon-dropbox" href="#"> dropbox</a> esse, <a class="btn small-button icon-key" href="#"> key</a> nihil odit, sed quis reprehenderit qui eius id aspernatur quia.

---
<a href="#" class="btn small-button icon-twitter"> TWITTER</a>

## Block Quote

{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.

Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}

{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

---

## Pull Quote

{% pullquote %}
content
{% endpullquote %}

---

## Code Blocks

{% codeblock %}
alert(‘Hello World!’);
{% endcodeblock %}

{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}

{% codeblock .compact http://underscorejs.org/#compact Underscore.js %}
.compact([0, 1, false, 2, ‘’, 3]);
=> [1, 2, 3]
{% endcodeblock %}

## Backtick Code Block

``` css Some CSS @ http://svdb.co svdb.co
/* comment */
a {
    color: #f00;
    text-decoration: none;
    height: 100%;
}
```

---

## JSFiddle

    {% jsfiddle S66zA %}

## Gist

    {% gist b70bb7b48d3e229feebf test.css %}

## Iframe

    {% iframe # 100% 900px %}

## Image

{% img http://placehold.it/1500x600 Title %}

## YouTube

    {% youtube qpgTC9MDx1o %}

## Vimeo

    {% vimeo 63502573 %}

## Raw
