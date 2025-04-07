---
layout: page
title: Search
permalink: /search/
---

<div class="search-container">
    <input type="text" id="search-input" placeholder="Search blog posts...">
    <ul id="search-results"></ul>
</div>

<script src="https://unpkg.com/lunr/lunr.js"></script>
<script>
window.store = {
    {% for post in site.posts %}
        "{{ post.url | slugify }}": {
            "title": "{{ post.title | xml_escape }}",
            "content": {{ post.content | strip_html | strip_newlines | jsonify }},
            "url": "{{ site.baseurl }}{{ post.url | xml_escape }}",
            "date": "{{ post.date | date: '%B %-d, %Y' }}"
        }
        {% unless forloop.last %},{% endunless %}
    {% endfor %}
};

(function() {
    function displaySearchResults(results, store) {
        const searchResults = document.getElementById('search-results');
        if (results.length) {
            let appendString = '';

            for (let i = 0; i < results.length; i++) {
                let item = store[results[i].ref];
                appendString += '<li>';
                appendString += '<h3><a href="' + item.url + '">' + item.title + '</a></h3>';
                appendString += '<p><small>' + item.date + '</small></p>';
                appendString += '<p>' + item.content.substring(0, 150) + '...</p>';
                appendString += '</li>';
            }

            searchResults.innerHTML = appendString;
        } else {
            searchResults.innerHTML = '<li>No results found</li>';
        }
    }

    function getQueryVariable(variable) {
        var query = window.location.search.substring(1);
        var vars = query.split('&');

        for (var i = 0; i < vars.length; i++) {
            var pair = vars[i].split('=');

            if (pair[0] === variable) {
                return decodeURIComponent(pair[1].replace(/\+/g, '%20'));
            }
        }
    }

    var searchTerm = getQueryVariable('query');

    if (searchTerm) {
        document.getElementById('search-input').setAttribute("value", searchTerm);

        var idx = lunr(function () {
            this.field('id');
            this.field('title', { boost: 10 });
            this.field('content');

            for (var key in window.store) {
                this.add({
                    'id': key,
                    'title': window.store[key].title,
                    'content': window.store[key].content
                });
            }
        });

        var results = idx.search(searchTerm);
        displaySearchResults(results, window.store);
    }

    document.getElementById('search-input').addEventListener('keyup', function(e) {
        var idx = lunr(function () {
            this.field('id');
            this.field('title', { boost: 10 });
            this.field('content');

            for (var key in window.store) {
                this.add({
                    'id': key,
                    'title': window.store[key].title,
                    'content': window.store[key].content
                });
            }
        });

        var results = idx.search(this.value);
        displaySearchResults(results, window.store);
    });
})();
</script>

<style>
.search-container {
    margin: 20px 0;
}

#search-input {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
    border: 2px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
}

#search-results {
    list-style: none;
    padding: 0;
}

#search-results li {
    margin-bottom: 20px;
    padding-bottom: 20px;
    border-bottom: 1px solid #eee;
}

#search-results li:last-child {
    border-bottom: none;
}

#search-results h3 {
    margin: 0;
}

#search-results h3 a {
    color: #2a7ae2;
    text-decoration: none;
}

#search-results h3 a:hover {
    text-decoration: underline;
}

#search-results p {
    margin: 5px 0;
    color: #666;
}

#search-results small {
    color: #828282;
}
</style>
