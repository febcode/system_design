
# Difference Between Local Storage, Session Storage And Cookies

The HTTP protocol is one of the most important protocols for smooth communication between the server and the client. The main disadvantage of the HTTP protocol is that it is a stateless protocol, which means it does not track any kind of response or request by the server or the client. So, to resolve this problem, we have Local Storage, Session Storage, and Cookies to manage and track data between server requests. In this article, we are going to see the difference between local storage, session storage, and cookies and why a web developer needs to know these terms.

# 1. What is Local Storage?
Local Storage allows websites to store key-value pairs persistently in a user’s browser, even after the browser is closed and reopened. Similar to sessionStorage, except that SessionStorage data is cleared when the tab or browser window is closed, but it persists through page reloads. In private browsing (incognito) mode, localStorage behavior varies across browsers. In most cases, data is automatically deleted once the session ends.

DOMStrings are storage formats that use UTF-16 to encode data, which uses two bytes per character. Strings are automatically generated from integer keys, just as they are for objects. The data stored in LocalStorage is specific to a protocol in the document. If the site is loaded over HTTP (e.g., http://example.com), localStorage returns a different object than if it is loaded over HTTPS (e.g., https://abc.com).

Points to Know about Local Storage
Storage Capacity: Up to 5MB or 10MB, depending on the browser.
Persistence: Data persists even when the browser or tab is closed.
Scope: Data is stored per domain and is specific to the protocol (HTTP vs. HTTPS).
Browser Support: Local Storage is supported by all major browsers.
Methods of Local Storage
There are four methods of local storage

1. setItem() Method
This method takes two parameters: one is key, and the other one is value. It is used to store the value in a particular location with the name of the key.

localStorage.setItem(key, value)
2. getItem() Method
This method takes one parameter that is key which is used to get the value stored with a particular key name.

localStorage.getItem(key)
3. removeItem() Method
This is method is used to remove the value stored in the memory in reference to key.

localStorage.removeItem(key)
4. clear() Method
This method is used to clear all the values stored in localstorage.

localStorage.clear()


# 2. What is Session Storage?
Session Storage objects can be accessed using the sessionStorage read-only property. The difference between sessionStorage and localStorage is that localStorage data does not expire, whereas sessionStorage data is cleared when the page session ends.

Session Storage is a temporary storage feature in web browsers that saves data only while a tab is open. It allows web pages to store information that remains available even if the page is refreshed. However, once the tab or browser is closed, all stored data is automatically deleted. Unlike localStorage, which keeps data permanently until manually cleared, sessionStorage is designed for short-term use. It is useful for storing temporary data like user preferences, form inputs, or session-based authentication details that should not persist beyond the current browsing session.

A page's protocol determines what data is stored in sessionStorage. Particularly, data stored by scripts accessed through HTTP (for example, http://abc.com) is stored in a separate object from the same site accessed through HTTPS (for instance, https://abc.com). A DOMString number is two bytes per character in UTF-16 DOMString format. Strings are automatically generated from integer keys just as they are for objects.

Point to Know about Session Storage:
Storage Capacity: Typically 5MB.
Persistence: Data lasts only as long as the session (tab or window) is open.
Scope: Session-specific storage per tab/window. If you open a new tab or window, a new sessionStorage is created.
Browser Support: Supported by all major browsers
Methods of Session Storage
There are mainly four methods

1. setItem() Method
This method takes two parameters one is key and another one is value. It is used to store the value in a particular location with the name of the key.

sessionStorage.setItem(key, value)
2. getItem() Method
This method takes one parameter that is key which is used to get the value stored with a particular key name.

var user = sessionStorage.getItem("key");
3. removeItem() Method
This is method is used to remove the value stored in the memory in reference to key.

sessionStorage.removeItem(key)
4. clear() Method
This method is used to clear all the values stored in the session storage

sessionStorage.clear()


3. Cookies
Cookies are small pieces of data stored in a user’s browser, primarily used for session management, authentication, and tracking user activity. In order to recognize you and show you results according to your preferences, this website saves some information in your local system when you visit a particular website. The history of the internet has long been marked by the use of cookies. A website visitor asks the server for a web page when they visit it. Every request for a server is unique.

Likewise, if you visit a hundred times, each request will be considered unique by the server. Since a server receives many requests every second, storing every user's information on a server doesn't seem logical and obvious.

The same information may not be needed again if you don't return. Therefore, a cookie is sent and stored on your local machine to uniquely identify you. You will receive a response from the same server the next time you hit it since it recognizes you. Almost every server uses this cookie (some exceptions exist today because of advertisements). Therefore, although you might have many cookies in your system, such cookies will be recognized by a server and analyzed.

Points to Know about Cookies
Storage Capacity: Typically limited to 4KB.
Persistence: Expiration is defined when setting the cookie and can vary (session-based or persistent).
Scope: Cookies are domain-specific but can be shared between server and client.
Data Transfer: Cookies are sent with every HTTP request, which can affect performance.

## Difference Between Local Storage, Session Storage, And Cookies
Local Storage	 Session Storage	Cookies
 
- The storage capacity of local storage is 5MB/10MB	The storage capacity of session storage is 5MB	The storage capacity of Cookies is 4KB

- local storage As it is not session-based, it must be deleted via javascript or manually.	
Ss It's session-based and works per window or tab. This means that data is stored only for the duration of a session, i.e., until the browser (or tab) is closed.
	Cookies expire based on the settings defined during their creation. They can be session-based (deleted when the browser is closed) or persistent (stored for a set duration).

- The client  can read and write local storage.
	The client can read and write session storage	.
Both clients and servers can read and write the cookies.

- There is no transfer of data to the server.
	There is no transfer of data to the server.
	Data transfer to the server is exist.

- Supported by all browsers, including older ones.	
Supported by all browsers, including older ones.
	It is supported by all the browser including older browser
