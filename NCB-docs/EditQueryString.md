Use This Code With Caution:
Update a URL without causing the browser to reload the page. Use the history.pushState() method to prevent the window.location event from firing when parameters are added to the query string.
https://example.com/path/to/page.html?new_parameter=new_value#fragment-identifier

Example HTML:
```html
<button onclick="updateUrl()">Update URL</button>

<script>
function updateUrl() {
  // Get the current URL
  const url = window.location.href;

  // Add the query string to the URL
  const newUrl = url + '?new_parameter=new_value';

  // Update the URL without reloading the page
  history.pushState(null, null, newUrl);
}
</script>
```