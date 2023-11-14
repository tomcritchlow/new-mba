---
title: The NEW MBA Library
layout: library-new
---

  <!--Table-->
  <div class="w-100 center flex flex-wrap">

  {% for item in site.library %}
  {% for insight in item.insights %}
  
  <div class="w-third-l w-100 pa3 item" data-item-title="{{item.title}}" data-item-source="{{item.link}}" data-item-insight="{{insight}}">
    <div class="pa4 bg-newmba-offwhite f5 br2">
    <div class="flex justify-between pb3 f6">
      <div class="newmba-green ttu">{{item.type}}</div>
      <div class="">{% for tag in item.tags %}<a href="/tag" class="link newmba-purple b">#{{tag}}</a>{% endfor %}</div>
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

<!--Search box-->
<script>

//Highlighter function
const searchHighlighter = (elem, keyword) => {
  let el = elem;
      el.innerHTML = el.innerText
        .replace( new RegExp( keyword + '(?!([^<]+)?<)', 'gi'),
        '<mark>$&</mark>'
    );
  return el
}

  // Event listener for the search box
document.getElementById('searchBox').addEventListener('input', function(e) {
  const searchTerm = e.target.value.toLowerCase(); // Convert search term to lower case
  const closebox = document.getElementById("closebox");

  //scroll so input box at top of page (TODO make sticky?)
  const inputRect = document.getElementById("results").getBoundingClientRect();
  window.scrollTo({
      top: inputRect.top + window.pageYOffset,
      behavior: 'smooth'
    });

  // show/hide the "clear search" link
  if(searchTerm.length > 0){
    closebox.classList.remove("dn");
  } else{
    closebox.classList.add("dn");
  }
  const items = document.querySelectorAll('.item'); // Get all items
  
  // remove all highlighting
  $('mark').contents().unwrap();
  
  // Loop through all items and hide those that don't match the search term
  items.forEach(function(item) {
    const itemTitle = item.getAttribute('data-item-title').toLowerCase(); // Convert title to lower case
    const itemSource = item.getAttribute('data-item-source').toLowerCase(); // Convert source to lower case
    const itemInsight = item.getAttribute('data-item-insight').toLowerCase(); // Convert source to lower case

    if (itemTitle.includes(searchTerm) || itemSource.includes(searchTerm) || itemInsight.includes(searchTerm)) {
      item.classList.remove('dn'); // Show item
      item.classList.add('db'); // Show item
      searchHighlighter(item.querySelector(".itemtext"), searchTerm);
      searchHighlighter(item.querySelector(".itemtitle"), searchTerm);
    } else {
      item.classList.add('dn'); // Hide item
      item.classList.remove('db'); // Hide item
      
    }
  });
});

// Event listener for the clear search link
document.getElementById('closebox').addEventListener('click', function(e) {
  e.preventDefault(); // Prevent default link action

  // Clear the search box
  const searchBox = document.getElementById('searchBox');
  searchBox.value = '';
  e.target.classList.add("dn");


  // Show all items
  const items = document.querySelectorAll('.item');
  // remove all highlighting
  $('mark').contents().unwrap();
  items.forEach(function(item) {
    item.classList.remove('dn');
    item.classList.add('db');
  });
});
</script>





