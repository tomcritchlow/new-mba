---
layout: null
---

<!DOCTYPE html>
<html>
<head>
    <title>Bookmarklet Landing Page</title>
    <link rel="stylesheet" href="https://unpkg.com/tachyons/css/tachyons.min.css">
</head>
<body class="pa4 sans-serif">
    <div class="mw6 center">
        <form id="bookmarklet-form" class="pa4 black-80">
            <div class="measure">
                <label for="title" class="f6 b db mb2">Title:</label>
                <input type="text" id="title" name="title" class="input-reset ba b--black-20 pa2 mb2 db w-100">
            </div>
            <div class="measure">
                <label for="url" class="f6 b db mb2">URL:</label>
                <input type="text" id="url" name="url" class="input-reset ba b--black-20 pa2 mb2 db w-100">
            </div>
            <div class="measure">
                <label for="description" class="f6 b db mb2">Description:</label>
                <textarea id="description" name="description" class="db border-box hover-black w-100 measure ba b--black-20 pa2 br2 mb2"></textarea>
            </div>
            <div class="measure">
                <label for="author" class="f6 b db mb2">Author:</label>
                <input type="text" id="author" name="author" class="input-reset ba b--black-20 pa2 mb2 db w-100">
            </div>
            <div class="measure">
                <label for="image" class="f6 b db mb2">Image URL:</label>
                <input type="text" id="image" name="image" class="input-reset ba b--black-20 pa2 mb2 db w-100">
            </div>
            <div class="measure">
                <input type="button" value="Generate .md File" onclick="generateMdFile()" class="input-reset ba b--black bg-transparent grow pointer f6 dib">
            </div>
        </form>
    </div>
    
    <script>
        // Parse the query string and populate the form
        var urlParams = new URLSearchParams(window.location.search);
        document.getElementById('title').value = urlParams.get('title');
        document.getElementById('url').value = urlParams.get('url');
        document.getElementById('description').value = urlParams.get('description');
        document.getElementById('author').value = urlParams.get('author');
        document.getElementById('image').value = urlParams.get('image');
        
        function generateMdFile() {
            var title = document.getElementById('title').value;
            var url = document.getElementById('url').value;
            var description = document.getElementById('description').value;
            var author = document.getElementById('author').value;
            var image = document.getElementById('image').value;

            var markdown = [
                "---",
                "layout: post",
                "title: \"" + title + "\"",
                "url: \"" + url + "\"",
                "type: Article",
                "date_saved: " + new Date().toISOString().split('T')[0],
                "tags: ",
                "author: \"" + author + "\"",
                "image: \"" + image + "\"",
                "---",
                description
            ].join("\n");

            var blob = new Blob([markdown], {type: "text/plain;charset=utf-8"});
            var blobUrl = URL.createObjectURL(blob);
            var a = document.createElement("a");
            a.href = blobUrl;
            a.download = title.replace(/[^a-z0-9]/gi, '_').toLowerCase() + ".md";
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
        }
    </script>
</body>
</html>
