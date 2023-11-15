---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">
<div class="mw8 w-100 center">

{% assign tags = site.library | where: 'layout', 'libraryitem' | map: 'tags' | join: ',' | split: ',' | uniq %}
{% for tag in tags %}
<div class="w-third-l w-100 pa3 item">
<div class="newmba-purple">#{{tag}}</div>
</div>
{% endfor %}