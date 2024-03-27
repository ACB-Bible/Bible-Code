<h3 align="center">serviveWorker fetch() event Intercept</h3>

This page is still under construction!

---
<br>

##### Register the serviceWorker and create the cache:
Use This Code With Caution:
```javascript
// Register the ServiceWorker
if ('serviceWorker' in navigator) {
  window.addEventListener('load', async () => {
    try {
      const registration = await navigator.serviceWorker.register('/sw.js');
      console.log('ServiceWorker registration successful with scope: ', registration.scope);
    } catch (error) {
      console.error('ServiceWorker registration failed: ', error);
    }
  });
}

// Create the cache
self.addEventListener('install', async event => {
  const cache = await caches.open('my-cache');
  await cache.addAll([
    '/index.html',
    '/styles.css',
    '/app.js'
  ]);
});
```
<br>

##### Intercept the fetch() event:

```javascript
self.addEventListener('fetch', async event => {
    const cache = await caches.open('my-cache');
    const cachedResponse = await cache.match(event.request);
    // If the file is in the serviceworker cache - return the response
    if (cachedResponse) { return cachedResponse; };

    // If file isn't in the cache fetch it from the server
    try {
        // Clone the request
        const fetchRequest = event.request.clone();
        // fetch() the request
        const response = await fetch(fetchRequest);
        // Check if a valid response was received
        if (!response || response.status !== 200 || response.type !== 'basic') {
        return response;
        }
        // Clone the response
        const responseToCache = response.clone();
        // Add the cloned response to the cache
        await cache.put(event.request, responseToCache);
        // return the response to the original fetch() request
        return response;
    } catch (error) {
        console.error(error);
    }
});
```

