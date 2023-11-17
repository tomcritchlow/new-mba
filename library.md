---
title: The NEW MBA Library
layout: library-new
---



<!--Sources-->
<div class="w-100 center" id="sources">
<div class="mw8 w-100 center">
{% assign sorted_items = site.library %}
{% assign sorted_items = sorted_items | push: sorted_items.first %}
{% assign formatted_posts = "" | split: "," %}
{% for post in site.posts %}
    {% capture new_post %}{"title":{{post.title}}}{% endcapture %}
    {% assign formatted_posts = formatted_posts | push: new_post %}
{% endfor %}
Formatted posts {{ formatted_posts | jsonify | pretty_print }}
Sorted items: {{ sorted_items | jsonify | pretty_print }}
{% assign sorted_items = sorted_items | sort:"date_saved" | reverse %}
{% for item in sorted_items %}
{% if item.layout == "libraryitem" %}
<div class="pa3 mv3 w-100 br1 bg-newmba-offwhite item" data-item-title="{{item.title}}" data-item-source="{{item.link}}" data-item-tags="{{item.tags | join:',' }}">
<div class="flex flex-wrap w-100 items-center">
<a class="link black w-40-l w-100 b itemtitle" href="{{item.url}}">{{item.title}}</a>
<div class="w-30-l w-100 f7"><div class="flex"><img class="mr2 v-mid" src="https://www.google.com/s2/favicons?domain={{item.link}}"> <span class="black-70 i"><a class="link black" href="{{item.url}}">{{ item.link | split: "//" | last | split: "/" | first }}</a></span></div></div>
<div class="w-10"></div>
<div class="w-20-l w-100 tr f7">{% for tag in item.tags %}<a href="/library/?search={{tag}}" class="link newmba-purple b">#{{tag}}</a>{% endfor %}</div>
</div>
</div>
{% endif %}
{% endfor %}
</div>
</div>

<!--Quotes-->
<div class="w-100 center dn" id="quotes">
<div class="flex flex-wrap">

{% assign sorted_items = site.library | sort:"date_saved"  | reverse %}

{% for item in sorted_items %}
{% for insight in item.insights %}

<div class="w-third-l w-100 pa3 item" data-item-title="{{item.title}}" data-item-source="{{item.link}}" data-item-insight="{{insight}}" data-item-tags="{{item.tags | join:','}}">
  <div class="pa4 bg-newmba-offwhite f5 br2">
  <div class="flex justify-between pb3 f6">
    <div class="newmba-green ttu">{{item.type}}</div>
    <div class="">{% for tag in item.tags %}<a href="/library/?tag={{tag}}" class="link newmba-purple b">#{{tag}}</a>{% endfor %}</div>
  </div>
  <a href="{{item.url}}" class="link"><div class="i lh-copy b itemtext black">“{{insight |truncatewords: 60}}”</div></a>
  <div class="f6 pt3">
    <a href="{{item.url}}" class="link"><div class="pb2 itemtitle black">{{item.title}}</div></a>
    <div class="flex"><img class="mr2 v-mid br-100 ba b--newmba-green" src="https://www.google.com/s2/favicons?domain={{item.link}}"> <span class="black-70 i">{{ item.link | split: "//" | last | split: "/" | first }}</span></div>
  </div>
</div>

</div>

{% endfor %}
{% endfor %}
</div>
</div>


<!--Tags-->
<div class="w-100 center dn" id="tags">
<div class="flex flex-wrap">
{% assign tags = site.library | where: 'layout', 'libraryitem' | map: 'tags' | join: ',' | split: ',' | uniq %}
{% for tag in tags %}
<div class="w-third-l w-100 pa3 item">
    <div class="pa4 bg-newmba-offwhite f5 br2">
        <div class=""><a class="link newmba-purple b ttl" href="/library/?search={{tag}}">#{{tag}}</a></div>
    </div>
</div>
{% endfor %}
</div>
</div>