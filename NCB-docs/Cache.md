<h3 align="center">Service Workers</h3>

---

Use This Code With Caution:
|Feature|Browser Cache|Service Worker Cache|
| :--- | :----------- | --- |
|Use|Store responses to network requests|Store static assets for offline access|
|Access|Indirectly accesseded through fetch()|Directly accessible by serviceWorker|
|Purpose|Speed up the retrieving frequently used online resources|Serving cached content that can be served when offline|
|Persistance|May be cleared by the browser|Persists across sessions|
|Threading|Operates only on the main browser thread|Operates in the background in a seperate thread|

---             
##### Service workers access two main types of caches:
1. Service Worker Cache:
A special cache provided by the browser specifically for serviceWorkers. It's designed to store static assets like HTML, CSS, JavaScript, and images. This allows the serviceWorker to intercept network requests and serve these assets from the cache, even when the user is offline.

2. Browser Cache:
Serviceworkers have no direct access to the browser's native cache(HTTP cache), they can indirectly influence it through the fetch() API. When a serviceWorker intercepts a fetch() request, it can decide to serve the response from the serviceWorker cache, which will then be automatically added to the browser cache.

3. Intercept a request sent by the fetch() API to the server:
When a fetch() request is intercepted by a serviceWorker, it does not automatically add the file to the serviceWorker cache. You need to explicitly code the logic to save the file to the cache.
---
#####  How a serviceWorker intercepts a fetch() API request, which can then return a response to the browser, or decide not to return a respones if it's not needed to be acted on by the browser:
1. The servicWorker intercepts the fetch() request using the fetch event listener.
2. Inside the event listener, the serviceWorker decides whether or not to cache the request when the response is received. You can analyze the request URL, response headers, or any other relevant information to make this decision.
3. If you want to save the response and save it to the persistant cache, you can use the cache.put(request, response) method to store it in the serviceWorker cache.
4. You can return the cached response directly to the browser, which can then be saved to browser cache, such as cookies, localStorage() or indexedDB or return the fetched response and simultaneously save it to the serviceWorker cache.
---
#### Intercept serviceWorker fetch() API example:
Use This Code With Caution!
1. Register the serviceWorker:
```javascript
// Register the service worker:
async function registerServiceWorker() {
  try {
    const registration = await navigator.serviceWorker.register('/sw.js');
    console.log('Service worker registered:', registration);
  } catch (error) {
    console.error('Service worker registration failed:', error);
  }
}
registerServiceWorker();
```
2. Add an event listener to intercept the fetch() API event request, and communicate between the browser and the serviceWorker:

```javascript
// Add an event to intercept the fetch() API event
self.addEventListener('fetch', async event => {
  const requestUrl = event.request.url;
  const targetUrl = '/data.json';
  if (requestUrl === targetUrl) {
    try {
      const response = await fetch(event.request);
      const data = await response.json();
      console.log(data);
      const processedData = /** This is where your custom logic is processed */;
      event.respondWith(new Response(JSON.stringify(processedData)));
    } catch (error) {
      console.error('Error fetching or processing data:', error);
    }
  }
});
```
3. Finally, you can use the fetch() API to fetch a file from the server, which will  be intercepted by the fetch() eventListener and operated on by the serviceWorker in a seperate thread in the background. You can then decide to fetch a file from the server, or return a previously fetched file from the serviceWorker cache:

```javascript
// Use the fetch() API to fetch a file:
async function fetchDataAndProcess() {
  const fileUrl = '/data.json';
  try {
    const response = await fetch(fileUrl);
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error fetching or processing data:', error);
  }
}
fetchDataAndProcess();
```
---