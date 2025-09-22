`loadimages()` Content Loader
=============================

Global function defined inline in `www/index.html`. Fetches the next batch of posts from the backend and appends them to the page. Designed to be used with infinite scroll.

Signature
---------
- Parameters: none
- Returns: void

Globals Used
------------
- `lastID` (number|string): Updated to the id of the last loaded post
- `isLoading` (boolean): Guards concurrent requests

Behavior
--------
- If `isLoading` is `false`:
  - Sets `isLoading = true`
  - Shows jQuery Mobile page loading message
  - POSTs to `http://www.fssguncut.com/app/getnext.php` with `{ after: lastID }`
  - For each `\r\n`-separated row in the response:
    - Splits by `^!` into `[id, title, imageUrl]`
    - Clones hidden `#postitem` template
    - Sets `.post-title` text and `#post-image` `src`
    - Appends to `#post-body`
    - Hides loading message and updates `lastID`
  - Sets `isLoading = false` when done

DOM Expectations
----------------
- A hidden template with id `postitem` exists in the DOM
- A container with id `post-body` exists to receive posts
- jQuery and jQuery Mobile are loaded

Usage Examples
--------------
Manual trigger:
```html
<button onclick="loadimages()">Load More</button>
```

Infinite scroll hook:
```html
<script>
  $(window).scroll(function () {
    if ($(window).scrollTop() + $(window).height() + 1000 > $('.footer').offset().top) {
      loadimages();
    }
  });
</script>
```

Notes
-----
- Network errors are not currently handled; consider adding `.fail()` and a `try/catch` around DOM updates.
- The endpoint returns delimited text; if it changes to JSON, update the parser accordingly.
