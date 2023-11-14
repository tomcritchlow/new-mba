---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">
<div class="mw8 w-100 center">
{% for item in site.library %}
<div class="pv2 ph2 mv3 w-100 br1 bg-newmba-offwhite flex items-center item" data-item-title="{{item.title}}" data-item-source="{{item.link}}">
<div class="w-40 b"><a class="link black" href="{{item.url}}">{{item.title}}</a></div>
<div class="w-30 f7"><div class="flex"><img class="mr2 v-mid" src="https://www.google.com/s2/favicons?domain={{item.link}}"> <span class="black-70 i"><a class="link black" href="{{item.url}}">{{ item.link | split: "//" | last | split: "/" | first }}</span></a></div></div>
<div class="w-10"></div>
<div class="w-20">{% for tag in item.tags %}<a href="/tag" class="link newmba-purple b">#{{tag}}</a>{% endfor %}</div>
</div>
{% endfor %}
</div>
</div>