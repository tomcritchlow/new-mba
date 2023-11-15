---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">

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
