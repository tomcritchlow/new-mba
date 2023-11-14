---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">
<div class="mw8 w-100 center">
{% for item in site.library %}
<div class="pv2 mv2 w-100 br1 bg-newmba-offwhite flex">
<div class="w-50 b">{{item.title}}</div>
<div class="w-20 b"><div class="flex"><img class="mr2 v-mid br-100 ba b--newmba-green" src="https://www.google.com/s2/favicons?domain={{page.link}}"> <span class="black-70 i">{{ page.link | split: "//" | last | split: "/" | first }}</span> <a class="link newmba-green" href="{{page.link}}">view source ↗</a></div></div>
<div class="w-10"></div>
<div class="w-20">Tags</div>
</div>
{% endfor %}
</div>
</div>