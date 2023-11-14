---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">
<div class="mw8 w-100 center">
{% assign sorted_items = site.library | sort:"date_saved" %}
{% for item in sorted_items %}
{% if item.layout == "libraryitem" %}
<div class="pa3 mv3 w-100 br1 bg-newmba-offwhite flex items-center item" data-item-title="{{item.title}}" data-item-source="{{item.link}}">
<div class="w-40 b itemtitle"><a class="link black" href="{{item.url}}">{{item.title}}</a></div>
<div class="w-30 f7"><div class="flex"><img class="mr2 v-mid" src="https://www.google.com/s2/favicons?domain={{item.link}}"> <span class="black-70 i"><a class="link black" href="{{item.url}}">{{ item.link | split: "//" | last | split: "/" | first }}</a></span></div></div>
<div class="w-10"></div>
<div class="w-20 f7">{% for tag in item.tags %}<a href="/tag" class="link newmba-purple b">#{{tag}}</a>{% endfor %}</div>
</div>
{% endif %}
{% endfor %}
</div>
</div>