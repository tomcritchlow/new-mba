---
layout: library-new
---

<!--Table-->


<div class="w-100 center flex flex-wrap">
{% for tag in tags %}
<div class="w-third-l w-100 pa3 item">
    <div class="pa4 bg-newmba-offwhite f5 br2">
        <div class=""><a class="link newmba-purple b" href="/library/?search={{tag}}">#{{tag}}</a></div>
    </div>
</div>
{% endfor %}
</div>