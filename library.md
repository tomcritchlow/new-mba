---
title: The NEW MBA Library
layout: library-new
---



<!--Sources-->
<div class="w-100 center">
<div class="mw8 w-100 center">
{% assign sorted_items = site.library | sort:"date_saved"  | reverse %}
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

<!--Tags-->
<div class="w-100 center dn">
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