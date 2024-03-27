<a id="top"></a>
<h3 align="center">Cookies, Local Storage, and serviceWorker Cache</h3>

This page is still under construction!

---

#### Understanding Cookies
Browsers use cookies for local storage, they're small text files that store data on a user’s device. They contain information such as preferences, browsing history, login credentials, and other data. Cookies communicate between a website and the browser. When you visit a website, the server sends a cookie to the browser, and it stores the cookie on your device. Each time you revisit the website, your browser sends the stored cookie back to the server. The website uses it to recognize you, remember your preferences, and offer a customized experience. Cookies can degrade the performance of a website, so modern APIs such as `localStorage` and `sessionStorage` are recommended.

#### Cookie Examples
##### 1. Creating a Cookie
When a user visits a website, the server can set a cookie by including a 'Set-Cookie' directive in the HTTP response header. The user’s browser receives this response and stores the cookie locally. From this point forward, whenever the user makes subsequent requests to the same website, the cookie will be automatically included in the request headers. The following code snippet demonstrates how a cookie named 'username' is set with the value 'JohnDoe.'
`Set-Cookie: username=JohnDoe`

##### 2. Accessing Cookie Values
The `document.cookie` property is used to return a string containing all the cookies associated with the current website. Here’s a Javascript example of how to access the value of a cookie named 'username.'
```javascript
  // Get all the cookies as a string
  const cookies = document.cookie;
  // Output: "username=JohnDoe"
  console.log(cookies);
```

##### 3. Extracting Cookie Parameters
Cookie parameters from the `document.cookie` property string can be extracted and parsed as the following example illustrates.
```javascript
  function getCookie(name) {
    const cookies = document.cookie.split(";"); // Split the string into individual cookies
    for (let i = 0; i < cookies.length; i++) {
      const cookie = cookies[i].trim(); // Remove leading/trailing whitespaces
      if (cookie.startsWith(name + "=")) {
        return cookie.substring(name.length + 1); // Extract and return the cookie value
      }
    }
    return null; // Cookie not found
  }

const username = getCookie("username");
console.log(username); // Output: "JohnDoe"
```

##### 4. Modifying and Deleting Cookies
Cookies can be modified or deleted by setting a new cookie with updated values or by instructing the browser to remove the cookie. When deleting cookies, you must set the path parameter to the same path that was used to create the cookie.
```javascript
// Modify the value of the "username" cookie
  document.cookie = "username=JaneDoe";
  // Cookies can be set to expire at a designated time
  // They can be deleted by setting the expires parameter to a past date
  document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC";
```

[Back to Top](#top)

---

#### Understanding Local Storage:

Local storage allows websites to store larger amounts of data on a user’s device than cookies allow. Unlike cookies, which are sent to the server with every request, local storage data remains on the client side and is not automatically sent to the server. This provides faster access to stored information, reducing the need for frequent server requests and thereby improving website performance.

Local storage offers the following benefits over cookies.
1. Enhanced User Experience:
More data storage for customized preferences, saved settings, and cached data.
2. Offline Functionality:
Local storage enables websites to work offline by storing essential data on the client side. This is particularly useful for applications that need to maintain functionality even when the user is not connected to the internet.
3. Streamlined Performance:
By reducing the need for frequent server requests, local storage significantly improves a websites performance by caching static resources and storing frequently accessed data locally.
4. Persistent Data:
Unlike session-based cookies, local storage data remains persistent after the browser is closed and reopened. This means users can revisit a website and find their preferences and saved data intact.

#### Local Storage Examples
##### 1. Creating Local Storage

[Back to Top](#top)

---

<br>

<h6 align="center" title="God's Word Is Not For Sale">Bible Code Project - Copyright © Free - Inspired by God</h3>
<h6 align="center">Good luck with your efforts!</h6>