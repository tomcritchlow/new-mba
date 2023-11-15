---
layout: library-new
---

<!--Table-->
<div class="w-100 center flex flex-wrap">
<div class="mw8 w-100 center">

{% assign tags = site.library | where: 'layout', 'libraryitem' | map: 'tags' | join: ',' | split: ',' | uniq %}
<div class="w-100 center flex flex-wrap">
{% for tag in tags %}
<div class="w-third-l w-100 pa3 item">
    <div class="pa4 bg-newmba-offwhite f5 br2">
        <div class="newmba-purple">#{{tag}}</div>
    </div>
</div>
{% endfor %}
</div>