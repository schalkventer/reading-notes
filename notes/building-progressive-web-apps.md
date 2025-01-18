Building Progressive Web Apps: Bringing the Power of Native to the Browser (2017)

Tal Ater

---

▪ Progressive web apps are an exciting new form of modern web apps. These apps leverage the latest web capabilities to deliver an experience that combines the unique features of native mobile apps with the advantages of the web.

▪ You will learn how to build web apps that take advantage of features that have so far been the exclusive domain of native apps

▪ will get you thinking about the new capabilities offered by progressive web apps as more than just a new set of tricks to apply to your apps.

▪ As such a game changer, progressive web apps defy the expectations users have from the web.

▪ Some of these challenges include reinforcing the user’s trust that her data won’t be lost when she is offline, informing her that the content she is seeing may be a few hours old if she is offline, and letting her know she can trust the app to send her a notification whenever anything important changes.

▪ When handled properly, these can offer great opportunities to increase users’ trust in your app, improve conversions, and gain a permanent place on their phones.

▪ Once every few years, the web experiences a pivotal moment. A moment where several separate technologies click together and make a splash in the public’s eye. These may be existing technologies that have been around for years or newer ones that have just now gained browser support. But to the outside observer, it seems like there is one shining moment in which the web suddenly takes a leap forward.

▪ We saw this happen with Ajax, which one day exploded seemingly out of nowhere (despite much of the underlying technology, such as XMLHttpRequest being around for years) and changed our notion of the web as a series of linked, mostly static, pages.

▪ Ajax itself was a part of the Web 2.0 revolution, another powerful name that seemingly popped out of nowhere in 2004 and exploded overnight.

▪ A few years later, mobile-first came into the spotlight and signaled a shift in how we look at web development. By giving a name to a set of design philosophies, these two words gained incredible power. With just two words we could shout out that the days of the user sitting in front of her home computer with a 20-inch monitor and a cable connecting it to the wall were over. With two words we understood that it was time to change the way we approach web development.

▪ Such moments often appear not when a technology is born, but when it is named.

▪ Progressive web apps are a new breed of web apps that combine the benefits of a native app with the low friction of the web.

▪ Progressive web apps start off as simple websites, but as the user engages with them, they progressively acquire new powers. They transform from a website into something much more like a traditional, native app.

▪ Instead of trying to send you to the app store, hoping you will install their app, the train company has earned a permanent place on your phone — one step at a time.

▪ This new progressive model replaces the binary installed/not installed nature of native apps.

▪ Progressive web apps build trust with their users and acquire new powers as they are needed.

▪ You may be asking yourself, how is this an improvement over native apps? Why shouldn’t we just stick with what works? Well, unless you are one of the lucky few, you already know that what we have right now isn’t working.

▪ Every year, the chances of users installing your app are growing smaller and smaller. Every year, the cost of acquiring new users balloons. Every year, keeping your users engaged gets harder and harder.

▪ When the first iPhone was launched in 2007, its killer feature was allowing you to browse websites on your phone. When mobile apps were introduced a year later, developers were finally able to break beyond the limited functionality of the web page (while taking on many new limitations, thanks to the introduction of the App Store).

▪ With features like advanced graphics, geolocation, push notifications, offline availability, homescreen icons, and more, the web seemed to pale in comparison in the eyes of many developers. Native apps took over the world (and our phones) by storm.

▪ But this trend is shifting. While we spend more time than ever before on our phones and using mobile apps, we spend that time in an increasingly smaller number of apps.

▪ Users are installing fewer apps and using only a handful of the ones they have installed. If your app is one of the top 10 apps in the app store, you are probably doing fine. But trying to break into the market with a new app is near impossible, not to mention costly.

▪ According to a 2016 comScore report, the average person spends 84% of his time on mobile devices using just the top 5 most popular apps. I’m sorry to say, these are not your apps. On tablets that number is even higher, with 95% of user time spent in the top 5 apps. The same report also presents figures showing that it is much easier to reach a large audience on a mobile site than in a native app. There are close to 600 mobile web properties that reach audiences larger than 5 million visitors — nearly 4.5 times greater than the number of native apps with similar audiences. The top 1,000 mobile web properties have audiences that are almost 3 times the size of the top 1,000, apps and their audiences are growing twice as fast as native app audiences.

▪ Getting users to install and use your app means surviving a vicious funnel. Users need to find out about your site (through traditional online advertising or on your website). They then have to visit your page on the app store. Then they need to click install. They need to agree to give the app different permissions. Then they need to wait for the app to download and install. Finally, they need to actually launch the app at least once and maybe even use it.

▪ This funnel may not seem too bad when you are installing an app you know and love, such as Twitter or Facebook. But a number of studies have shown that an average of 20% of users are lost during every step of this funnel. It is not uncommon for app developers to pay for banner clicks, only to discover that less than 20% of those users actually launched the app.

▪ Sites have become so desperate to get you to install their app that they have resorted to a new method of advertising. You know the one: you arrive at a site looking to read a short article or find out tomorrow’s weather. The info is right there, within your grasp, but then a banner pops up on your screen blocking the very content you want. It asks you if you would like to install an app instead of reading the content that is already right in front of your eyes. Some people call these a full-page interstitial ad. I prefer a shorter name: the door slam (Figure 1-1). For more details on the effects and the ineffectiveness of full-page interstitial ads, see Appendix B.

▪ It is a brutal, costly battle to get a user to install your app on her phone. But the edge that native apps held over the web meant app developers were willing to endure (and inflict) much for each app install.

▪ A native app, as opposed to a traditional website, has a life beyond the short time a user spends with it when he first discovers it, and the time (sometimes seconds later) when he wanders away. Once installed, apps have a permanent place on your homescreen. They can reach out to you with notifications at any time and remind you of their existence. They give their developers many chances to try and get a return on their investment over the long lifetime of their app.

▪ But with the introduction of progressive web apps, the tide is finally turning. The edge granted by these superpowers, which have so far been the exclusive domain of native apps, is now available to web apps.

▪ Couple that with the low friction, one-step funnel of the web (clicking a link versus installing an app), and you can see why users, web developers, and businesses have much to gain from embracing progressive web apps.

▪ Availability regardless of connection

▪ Progressive web apps are not dependent on the user’s connection like traditional websites are. When a user visits a progressive web app, it will register a service worker (see “The Tab, the Web, and the Service Worker”) that can detect and react to changes in the user’s connection. It can provide a fully featured user experience for users who are offline, online, or suffering from an unreliable connection.

▪ Your users could be using your progressive web app while flying over the Atlantic, and even take actions (e.g., posting messages, RSVPing for events, or commenting on posts) knowing that their actions will complete as soon as they go back online — even if they close your app and their browser. S

▪ Progressive web apps introduce a level of reliability, and in turn, gain the user’s trust to a level that was so far only given to native apps. A user knows she can open the WhatsApp app at any time, write a quick message, and close her phone without worrying about the current state of her connection. The web hasn’t enjoyed this level of trust until now, which is one of the reasons users often preferred native apps.

▪ Fast load times

▪ Push notifications

▪ Homescreen shortcut

▪ Native look

▪ As part of Lyft’s ongoing efforts to reach more users, the company found itself having to support a growing number of devices and mobile OS versions. As the app evolved, Lyft had to deprecate support for older iOS and Android versions or face growing maintenance costs. Rather than giving up on these potential clients (which made up 8% of iOS users, and 3% of Android users), Lyft built a progressive web app.

▪ By adopting progressive web apps, the team at Lyft was able to decrease the technical and operational costs associated with supporting multiple apps and devices. More importantly, they were able to reach new users on iOS and Android, as well as audiences they previously ignored: Windows Mobile and Amazon Fire users.

▪ Before service workers, we had code running either on the server or in the browser window. Service workers introduce another layer.

▪ A service worker is a script that can be registered to control one or more pages of your site. Once installed, a service worker sits outside of any single browser window or tab.

▪ From this place, a service worker can listen and act on events from all pages under its control. Events such as requests for files from the web can be intercepted, modified, passed on, and returned to the page (Figure 1-3).

▪ This means that there is a layer between the page and the web that can respond to requests independently of a network connection. A layer that works even when the user is offline. This layer can detect an offline state or slow responses from the server and return cached content instead (Figure 1-4).

▪ Taking this logic a step further, it means that even if the user closed all the tabs running your app in her browser, there is still a layer that can communicate with your server (Figure 1-5). It can receive and display push notifications, or make sure any actions performed by the user get delivered to the server (even if she stepped into the elevator just as she took that action and then closed your app before regaining connectivity).

▪ You can see why service workers are at the heart of every progressive web app. Their persistent nature allows progressive web apps to fulfill our expectations of what an app should do.

▪ But perhaps their greatest power is that service workers are simply JavaScript files. They are written just like any other JavaScript code you have been writing for years.

▪ As developers, the benefits of understanding service workers and the associated technologies covered in this book are huge. They allow us to leverage our existing knowledge of web technologies, such as JavaScript, HTML, and CSS, to write web apps that can truly compete with and even surpass native mobile apps. 

▪ This is the web as it is today. Rich, beautiful, and useful. Actually, this is the web as it is today for you — the developer. As developers, we usually look at our sites from a relatively modern desktop, laptop, or mobile device. We have a reliable connection either to a local server, or a development server in close proximity to us. But our users might be experiencing our web apps very differently than us. What happens when a user visits our web app when he is offline (Figure 2-3)?

▪ Thankfully, most modern browsers include tools for simulating an offline state and even different connection speeds (Figure 2-4). See the section on “Developer Tools” for more details.

▪ if ("serviceWorker" in navigator) { navigator.serviceWorker.register("/serviceworker.js") .then(function(registration) { console.log("Service Worker registered with scope:", registration.scope); }).catch(function(err) { console.log("Service worker registration failed:", err); }); }

▪ The code begins by verifying that the current browser supports service workers. It then registers our service worker by calling navigator.serviceWorker.register, which takes two arguments. The first is the URL of our service worker script. The second is an optional options object (which we have omitted here, but will explore later in this chapter in “Understanding Service Worker Scope”).

▪ By testing for service worker support before using it, we make sure we are not excluding users of older browsers from using our app, while offering an enhanced experience to users of more modern browsers. This practice of progressive enhancement is central to how we will build our app (see “What Is Progressive Enhancement?”).

▪ The register call returns a promise. If the promise is fulfilled, meaning the service worker was registered successfully, the function defined in the then statement is called. If there was any problem, the function defined inside the catch block would be executed.

▪ If you refresh the sample app in your browser, you should see an error message in your browser’s console telling you that “Service worker registration failed.”1 The service worker registration failed and the promise was rejected because we have not created our serviceworker.js file yet.

▪ Even though our service worker is nothing but an empty file, it is still a valid service worker and was registered successfully.

▪ You may be tempted to move the serviceworker.js file into the js subdirectory of the project. Keep it in the root directory for now. You will learn why this is important in the section “Understanding Service Worker Scope”.

▪ Add the following code to serviceworker.js: self.addEventListener("fetch", function(event) { console.log("Fetch request for:", event.request.url); });

▪ This listener will listen to all fetch events that pass through the service worker and run the function we define next, passing it an event object as its sole argument. The function we define to handle these events accesses the request object (available as a property of the fetch event) and logs the URL of that request.

▪ You may have noticed that as you make changes to your service worker file, those changes don’t immediately take effect after refreshing your browser. This is because your old service worker is still the active one, while your new service worker remains in a waiting state until the old one is no longer controlling the page.

▪ browser: self.addEventListener("fetch", function(event) { if (event.request.url.includes("bootstrap.min.css")) { event.respondWith( new Response( ".hotel-slogan {background: green!important;} nav {display:none}", { headers: { "Content-Type": "text/css" }} ) ); } });

▪ In just a few lines of JavaScript, we were able to create a service worker that intercepted a request to a third-party server, made up a new response out of thin air, and presented it to the browser as if it came from that server. We essentially created a proxy server inside the browser.

▪ For an up-to-date status of browser support for service worker, and related technologies, visit Jake Archibald’s web page “Is ServiceWorker Ready?”

▪ Central to the philosophy of our app, and for any modern web app, is the principle of progressive enhancement.

▪ Think of progressive enhancement as a way to build your web app in a layered fashion. Begin with basic content, simple HTML links, images, and so on. Then, for your users with JavaScript support, add a layer that enhances the links to fetch the content asynchronously and replace static images of maps with interactive Google Maps. Add offline support for browsers that support service workers. Send push notifications to users who can receive them.

▪ Don’t confuse the term progressive enhancement with progressive web apps. While progressive web apps should ideally be developed with progressive enhancement in mind, it is not a technical requirement. You can build a progressive web app that works beautifully on one modern browser, while crashing miserably in all others — please don’t.

▪ As you just saw, service workers can intercept requests, modify their content, or even completely replace them with new responses. To protect users and prevent man-in-the-middle attacks, in which a malicious third party can take advantage of these abilities, only pages served over secure connections (HTTPS) can register a service worker.

▪ During development, you can use service workers without a secure connection by using localhost as your hostname (for example, both http://localhost/ and http://localhost:1234/user/index.html can register and use service workers). But once you deploy your web app to your server, it must be served over a secure HTTPS connection for service workers to work.

▪ In the code we wrote earlier, we built a new response object from scratch by specifying its content and headers, and then responding to the request with it.

▪ Replace the code in serviceworker.js with the following: self.addEventListener("fetch", function(event) { if (event.request.url.includes("/img/logo.png")) { event.respondWith( fetch("/img/logo-flipped.png") ); } });

▪ Let’s use everything we just learned about service workers to detect when our user is offline, and present him with a friendly error message, instead of the browser’s default error message.

▪ for: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request) ); });

▪ So what is the point of this? Well, you may recall that in the previous example, I mentioned that fetch returns the response wrapped in a promise. By wrapping our response with a promise, we can catch it if it is rejected and do something about it.

▪ Replace the code in serviceworker.js with the following code: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return new Response( "Welcome to the Gotham Imperial Hotel.\n"+ "There seems to be a problem with your connection.\n"+ "We look forward to telling you about our hotel as soon as you go online." ); }) ); });

▪ Now, instead of the browser’s native error message, you should see a personalized message from the Gotham Imperial Hotel (Figure 2-8).

▪ Replace the code in serviceworker.js with the following code: var responseContent = "" + "" + "" + "body {text-align: center; background-color: #333; color: #eee;}" + "" + "

Gotham Imperial Hotel

" + "

There seems to be a problem with your connection.

" + "

Come visit us at 1 Imperial Plaza, Gotham City for free WiFi.

" + "" + ""; self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return new Response( responseContent, {headers: {"Content-Type": "text/html"}} ); }) ); });

▪ When a fetch event is detected, our function is called, receiving a FetchEvent object as an argument. We then use that event object’s respondWith method to respond to the event ourselves instead of letting its default behavior play out.

▪ The respondWith method takes one argument, containing either a response object or code that resolves to a response object. The rest of our code builds that response.

▪ We begin by calling fetch, and passing it the original request (found inside the FetchEvent object). We pass the original request object, not just its URL, to make sure any headers, cookies, and the request method are left untouched. fetch returns a promise.

▪ If the user is online, the server is online, the file is in the right place, and everything is right in the universe, then the promise is fulfilled, and fetch returns the response. This, in turn, gets passed back to event.respondWith, which sends it back to the page the user is browsing. If, however, something goes wrong while trying to fetch our file (e.g., the user boarded a plane), the promise is rejected, and the callback function we define inside the catch method is called.

▪ This function constructs a response by calling new Response, passing it two arguments. The first is the body of the response (the HTML we defined earlier). The second is an optional options object. We use this options object to add a Content-Type header to the response.

▪ To prevent this issue, each service worker has a limited scope it can control. This scope is defined by the directory where the service worker’s JavaScript file is placed in. By placing our serviceworker.js file in the root directory of our project earlier, we allow it to control all requests that originate anywhere in the site. If we had placed it in the js directory, only requests that originated from that subdirectory would have passed through it.

▪ You can overwrite a service worker’s scope by passing it a scope option when registering it. This can limit the service worker’s scope to a smaller subset of directories, but it cannot extend the scope to a wider scope than would otherwise be available to it (e.g., you can limit a service worker located at /ginnos/sw.js to only affect requests to /ginnos/menu/, but you can’t extend its scope to the root of the domain).

▪ // These two commands will register two service workers // each controlling a different directory: navigator.serviceWorker.register("/sw-ginnos.js", {scope: "/Ginnos"}); navigator.serviceWorker.register("/sw-ralphs.js", {scope: "/Ralphs"});

▪ Users arriving in Gotham City (where cell towers tend to mysteriously go up in flames every other day) can browse a simplified version of our site even while offline.

▪ You can probably guess that in order to achieve this, we will have to catch requests that fail and return the alternate content: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return fetch("/index-offline.html"); }) ); });

▪ Can you see the problem with this code? It’s not a coding error, but an error in our logic. We are trying to fetch the offline file only when we know the user is offline. We need to fetch it while he is online, store it on the device, and serve it when he is offline.

▪ Luckily, when service workers were introduced, we also got the new CacheStorage API — the missing piece of the puzzle.

▪ CacheStorage is a new type of caching layer that is completely under your control.

▪ CacheStorage is also nothing like the old AppCache API, which enabled a more primitive, rigid way to define which files should be available offline using a cache manifest file. This API has since been removed from web standards, and was famously torn to bits in Jake Archibald’s article “Application Cache is a Douchebag”.

▪ By combining service workers with the power of CacheStorage, we can get direct programmatic control over what gets cached, what gets removed from the cache, and which responses are returned from the cache and which are returned from the network.

▪ So far, we only used the service worker to listen to fetch events — events that can only be caught by an active service worker. We need to listen for an earlier event and use it to cache the files that our service worker depends on.

▪ For this, we can use the service worker’s install event — an event that happens once in the life of each service worker, right after it is registered for the first time, and before it activates. By listening for this event, we get an excellent opportunity to cache all of the files we would like to make available offline — before the service worker takes control of the page and starts listening to fetch events.

▪ If anything goes wrong while caching, we can abort the installation, knowing that the browser will try to install the service worker again the next time the user visits the page. This way we are effectively creating install dependencies for our service worker — files that must be downloaded and cached before our service worker is considered installed and active.

▪ Clear serviceworker.js and replace the code in it with the following: self.addEventListener("install", function(event) { event.waitUntil( caches.open("gih-cache").then(function(cache) { return cache.add("/index-offline.html"); }) ); });

▪ To accomplish this, we call waitUntil on our install event. waitUntil extends the lifetime of the event until the promise we pass to it is resolved. This allows us to wait until we successfully store the file in the cache before declaring the install event complete, and gives us the chance to abort the installation if there is a problem at any stage by rejecting the promise.

▪ Within our waitUntil function, we call caches.open, passing it the name of our cache (this hints at another powerful feature of CacheStorage: we can create multiple caches for our site, a feature we will take advantage of in Chapter 4).

▪ caches.open either opens and returns an existing cache or, if it does not find an existing cache with that name, will create it and then return it.

▪ caches.open returns a cache object wrapped in a promise, which is why we continue with a then statement, passing it a function that will accept the cache object as its argument.

▪ The last thing we have to do is call cache.add('/index-offline.html'), which fetches the file and places it in the cache with the key "/index-offline.html".

▪ By telling the install event to waitUntil caching is done, we made sure that if anything breaks along the chain, the service worker will not be installed. 

▪ Now that we have the offline version of our page stored in CacheStorage, we need to retrieve it and return it to the user.

▪ self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return caches.match("/index-offline.html"); }) ); });

▪ This code should be familiar to you from the previous chapter. The only change is that instead of constructing a new response or fetching it from the web, we return it from CacheStorage by calling caches.match.

▪ You might have also noticed that the code returns the request from the cache without even verifying that it exists in the cache first. This is because we have made our service worker’s installation dependent on caching this request successfully.

▪ CacheStorage follows the same-origin security policy. Whether you are using caches.match() or caches.open(), only caches created by the current origin are accessible. In other words, when your app runs caches.match("bank-password"), only caches created by your app will be searched. For more on the same-origin policy, see “The Same-origin Policy”.

▪ The match method returns a response object from the cache for a given request. The match method can be called on either the caches object, which will look for a match in all caches, or on a specific cache object:

▪ // Look for a matching request in all caches caches.match("logo.png"); // Look for a matching request in a specific cache caches.open("my-cache").then(function(cache) { return cache.match("logo.png"); });

▪ match’s first argument is a request object or a URL to look for in the cache. This should match the request you added to the cache. The second argument is an optional options object.

▪ match returns a promise that resolves to the first response object found in the cache, or to undefined if no match was found.

▪ The promise returned by match will not be rejected even if a response was not found. For this reason, unless you are sure a match exists, you will often want to verify that a match was found before returning it: caches.match("/logo.png").then(function (response) { if (response) { return response; } });

▪ Furthermore, our code naïvely caches and returns the same HTML file for any request that fails. It does not matter if the user requested index.html, bootstrap.min.css, or gih-offline.css. If any request fails, the service worker will always return the same HTML file (Figure 3-3).

▪ We could accomplish this using everything we have learned so far and simply chain a number of cache.add calls together: self.addEventListener("install", function(event) { event.waitUntil( caches.open("gih-cache").then(function(cache) { return cache.add("/index-offline.html").then(function() { return cache.add( "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" ); }).then(function() { return cache.add("/css/gih-offline.css"); }).then(function() { return cache.add("/img/jumbo-background-sm.jpg"); }).then(function() { return cache.add("/img/logo-header.png"); }); }) ); });

▪ In serviceworker.js, replace the code of the install event handler with the following code: var CACHE_NAME = "gih-cache"; var CACHED_URLS = [ "/index-offline.html", "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css", "/css/gih-offline.css", "/img/jumbo-background-sm.jpg", "/img/logo-header.png" ]; self.addEventListener("install", function(event) { event.waitUntil( caches.open(CACHE_NAME).then(function(cache) { return cache.addAll(CACHED_URLS); }) ); });

▪ The code in this example begins by setting two new variables. The first contains the name of our cache, and the second is an array containing a list of URLs we would like to cache.

▪ Next, instead of calling cache.add(); we call cache.addAll() and pass it the array of URLs to cache.

▪ We need to match each failing request with the correct cached response and serve it.

▪ Replace the code of the fetch event handler in serviceworker.js with the following code: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return caches.match(event.request).then(function(response) { if (response) { return response; } else if (event.request.headers.get("accept").includes("text/html")) { return caches.match("/index-offline.html"); } }); }) ); }); 

▪ The new fetch event handler code in this example still attempts to fetch requests from the network and return those responses to online users. But if any fetch fails, the new function within the catch block springs into action.

▪ The catch function begins by trying to match the request made with requests stored in any of our caches. Because the promise returned by caches.match is never rejected (even if a match was not found), we check if a response was found in the cache using if (response) before returning it. If, however, it was not found in the cache, we return the contents of index-offline.html instead.

▪ Just to be on the safe side, I threw in an extra check before returning index-offline.html. This check makes sure that the request contains the accept header for text/html.

▪ You may remember that when we created a new HTML response from scratch, we had to define its "Content-Type" as "text/html" for the browser to correctly identify that response as HTML. Why then were we able to return responses in the preceding code example without manually defining their content type as HTML, CSS, or image first? The reason is that cache.add() and cache.addAll() fetch and then cache a complete response object. This doesn’t just include their body, but also any response headers returned by the server (including "Content-Type").

▪ ignoreSearch Looking for an entry in the cache by passing the request object (e.g., caches.match(event.request)) has a potential pitfall that you should keep in mind. Users may not always visit your site using the same URL. For example, let’s say you are running a new promotion on your site. Users clicking through to this page from your home page will visit https://www.site.com/promo.html. But if they clicked a banner linking to the same page from an advertising campaign, they may be visiting https://www.site.com/promo.html?utm_source=halloweencampaign&utm_medium=cpc. It is not uncommon to have hundreds of different URL variations, each differing only by their query string (also known as the search attribute, also known as that unreadable mess after the question mark). If your install event saves /promo.html into the cache while caches.match(event.request) attempts to find /promo.html?utm_source=a, nothing will be found. You could solve this by writing specific rules to strip the query string from the URL before passsing it to match(), or you could test if the URL string includes promo.html and then pass a hardcoded URL to match(). There is a better way.

▪ If you are sure the query parameters have no effect on the content of the page, you can instruct match() to ignore them by asking it to ignoreSearch: caches.match(event.request, {ignoreSearch: true}) This will match entries for the request’s URL while disregarding the query parameters (e.g., /promo.html will match both /promo.html?utm_source=urchin, and /promo.html?utm_medium=social.)

▪ It is important to remember that CacheStorage does not replace the good old HTTP cache.

▪ If your server serves a file with an HTTP header that says that file can be saved in the browser’s cache for a year, your browser will keep serving that file from the browser cache.

▪ If your server serves that file with a header of Cache-Control: max-age=31536000 (which is the server’s way of saying that content can be cached for a year), then it will also be saved in the browser’s cache in addition to the service worker saving it in CacheStorage.

▪ If you then update main.css a week later and decide to update your service worker so that it calls cache.addAll(['/main.css']) again, that file will be returned from the browser’s cache and not from the network.

▪ This isn’t a CacheStorage-specific issue. It’s just how HTTP caching has always worked. Understanding HTTP caching and doing it right is just as important today as it ever was. For an excellent primer on the subject, check out Jake Archibald’s “Caching best practices & max-age gotchas”.

▪ In Chapter 2, I encouraged you to turn on “Update on reload,” which allowed you to see any change made to your service worker immediately after each page refresh.

▪ And yet, just like a cheat-code in an old-school video game, this convenient workaround makes things easy for you but does not represent how things behave in the real world.

▪ Service worker peculiarities can be confusing at first, but once you understand the simple flow of a service worker from one state to the next, it all makes sense.

▪ When a page registers a new service worker, the service worker goes through a number of states

▪ Once a service worker has successfully installed, it enters the installed state. It will then immediately move on to the activating state unless another active service worker is currently controlling this app, in which case it will remain waiting.

▪ Before a service worker becomes active and takes control of your app, the activate event is triggered.

▪ Similar to the installing state, the activating state can also be extended by calling event.waitUntil() and passing it a promise.

▪ Refresh the page once, twice, three times. You might be surprised that your change to the service worker does not affect the page, and the background remains green.

▪ Every time a page loads with an active service worker, it checks for an update to the service worker script. If that file changed since the current service worker was registered, the new file is registered and installed. Once installation completes, it does not replace the existing service worker but instead remains in the waiting state.

▪ It stays in this state until every single tab and window in this service worker’s scope is closed or is navigated to a page not in its scope. Only when there are no more pages controlled by the active service worker open will the old active service worker move to the redundant state and the new service worker be activated.

▪ This explains why our app’s background did not change. Try closing the tab and reopening it, or just navigate to a different site and then hit the back button. This should allow the old service worker to become redundant, your new one to activate, and the background to finally change to red.

▪ Why must new service workers that finish installing have to wait for all pages under their scope to close before taking control and becoming the active service worker? Imagine having two tabs open, showing two pages controlled by the same service worker. Now, what would happen if the first tab was refreshed, downloaded a new service worker, and made that the active service worker? The second page, which loaded using one service worker, is suddenly controlled by a different one. This could cause many unexpected problems, such as the one we explored in Why Can’t a Service Worker Take Control of a Page After It Has Started Loading?.

▪ Let’s explore one potential catastrophe caused by this situation. Imagine a scenario in which you release a new version of a service worker, and this service worker’s install event deletes userdata.json from the cache, adds users.json instead, and changes the fetch event to return the new file when user data is requested. If multiple service workers controlled different pages, the ones controlled by the old service worker might look for the old userdata.json file in the cache after it was removed, causing your app to break.

▪ If we update the content of sw-index.html, how would our service worker know that it needs to download a new version of the file and store it in CacheStorage?

▪ any change to the service worker file will cause a new service worker to be installed the next time we visit any page of our app.

▪ By adding a version number to our cache name and incrementing it every time one of our files change, we achieve two goals: Any change to the service worker file, even one as minuscule as changing a single digit in the cache version number, lets the browser know it is time to install a new service worker to replace the active one. This triggers a new install event, causing the new files to be downloaded and stored in the cache. It creates a separate cache for each version of our service worker (Figure 4-5). This is important because even though we already updated the cache, until the user has closed all open pages, the old service worker is still the active one. That service worker may expect certain files to be in the cache, including files that may have been changed by the newer service worker. By letting each service worker have its own cache, we can make sure there are no unexpected surprises. 

▪ By versioning our caches and service workers, we were able to achieve a powerful system in which each version of our service worker can rely on having just the files it needs in its own dedicated cache. We can update our service worker or the files we would like to have in cache at any time and be sure that we won’t affect our users in unexpected ways.

▪ Each browser behaves differently when it comes to managing CacheStorage, allocating space in the cache for each site, and clearing out old cache entries. The amount of space allotted to your site may change for different browsers, versions, devices, and even from day to day (as the amount of free space on the device changes). In addition to a storage limit per site (also known as an origin), most browsers will also set a size limit for their entire cache. When the cache passes this limit, the browser will delete the caches of the site accessed the longest time ago (also known as the least recently used). Browsers will never delete only part of your site’s cache. Either your site’s entire cache will be deleted or none of it will be. This ensures your site never has an unpredictable partial cache.

▪ Before we can tackle this problem, we need to familiarize ourselves with two new methods of the caches object: caches.delete(cacheName) Receives a cache name as its first argument, and deletes that cache. caches.keys() A handy method for getting the names of all the caches accessible to you. Returns a promise that resolves to an array of cache names.

▪ For example, if we wanted to delete all the caches, we could use the following code: caches.keys().then(function(cacheNames) { cacheNames.forEach(function(cacheName) { caches.delete(cacheName); }); });

▪ What is true for this app isn’t necessarily true for yours. While I have decided to store all of Gotham Imperial Hotel’s assets in one cache (per version), you may decide on a different structure for your app. For example, you might decide to keep one cache for files that change very infrequently (like vendor libraries, logos, etc.) and one for files that change with every release. If you do, be sure to modify the pattern described here accordingly.

▪ Our app needs at most two caches at any time: one cache for the currently active service worker, and one for a newer service worker that is now being installed but isn’t activated yet (if it exists). Any caches belonging to redundant service workers are — redundant.

▪ Let’s take our existing service worker and add a new event listener to listen for the activate event. In serviceworker.js, rename the CACHE_NAME variable to "gih-cache-v4", and add the following code to the bottom of the file: self.addEventListener("activate", function(event) { event.waitUntil( caches.keys().then(function(cacheNames) { return Promise.all( cacheNames.map(function(cacheName) { if (CACHE_NAME !== cacheName && cacheName.startsWith("gih-cache")) { return caches.delete(cacheName); } }) ); }) ); });

▪ But before we can declare our new service worker active, we want to delete all the old caches that were used by our older service workers.

▪ We begin by extending the activate event using waitUntil. We are essentially telling the service worker to wait until we have cleaned out all the old caches before completing its activation. We do this by passing waitUntil a promise.

▪ The code for creating this promise begins by calling caches.keys(). This returns a promise that resolves to an array containing the names of all the caches we created in our app. We want to take this array and create a promise that resolves only after we have iterated over each and every one of the caches in that array. For this, we can use Promise.all() to wrap all those promises with a single promise.

▪ The only line we did not cover is the if statement surrounding our caches.delete() call. This statement makes sure we only delete caches that match both of these conditions: Their name is different than the active cache’s name. Their name begins with gih-cache. 

▪ The first condition makes sure we don’t delete the new cache we just created. The second checks for an arbitrary prefix we chose for all of our service worker’s cache names. This makes sure we do not delete caches created elsewhere by our app, unrelated to the service worker.

▪ What if when we created a new cache, we first went over our list of immutable files (files that never change, such as bootstrap.3.7.7.min.css or style-v355.css), looked for them in existing caches, and copied them directly to the new cache. Once this is done, we could go ahead and use cache.add() or cache.addAll() to fetch the remaining files (immutable files not found in older caches, and mutable files):

▪ var immutableRequests = [ "/fancy_header_background.mp4", "/vendor/bootstrap/3.3.7/bootstrap.min.css", "/css/style-v355.css" ]; var mutableRequests = [ "app-settings.json", "index.html" ]; self.addEventListener("install", function(event) { event.waitUntil( caches.open("cache-v2").then(function(cache) { var newImmutableRequests = []; return Promise.all( immutableRequests.map(function(url) { return caches.match(url).then(function(response) { if (response) { return cache.put(url, response); } else { newImmutableRequests.push(url); return Promise.resolve(); } }); }) ).then(function() { return cache.addAll(newImmutableRequests.concat(mutableRequests)); }); }) ); });

▪ Our install event first goes over all immutableRequests and looks for them in all existing caches. Any requests that are found are copied to the new cache using cache.put.1 Those that aren’t are placed into the newImmutableRequests array. Once all the requests have been checked, the code uses cache.addAll() to cache all the URLs in mutableRequests and newImmutableRequests.

▪ Because the service worker file is checked on each load, you should configure your server to serve it with a short expiration header (i.e., 1 to 10 minutes). If you give it a very long expiration time, the browser will not check it for changes and will not find out about new service worker versions or new files to cache.

▪ Imagine what would happen if your service worker always served checkout.js from cache, and you accidentally released a version of that file that had a bug in it. If you were unable to update your service worker to cache a new version, you might be unable to release a fix for hours.

▪ Luckily, the browser protects you here and defaults to an expiration time of 24 hours if you try to set a longer one.

▪ This used to be simple. A simple hard refresh done by holding the Shift key while refreshing used to ensure that the browser’s cache was ignored. But with more and more assets being stored in more and more places (CacheStorage, IndexedDB, Cookies, Local Storage, Session Storage, etc.), this is no longer enough.

▪ Luckily, the developer tools in Chrome and Opera provide a quick way to get a fresh start. In the developer tools of either browser, open the Application tab, select the Clear storage section, go over the checkboxes, and click “Clear site data.”

▪ During development, you will often find yourself needing to examine the assets that are stored in CacheStorage and IndexedDB (which we will explore in Chapter 6).

▪ You can access these stores programmatically using the console, open connections to them, and read their data — this can be quite a hassle.

▪ Firefox, Chrome, and Opera let you examine these stores directly using a graphical user interface. In Firefox you can access it through the Storage tab of the developer tools (Figure 4-7). In Chrome and Opera, you will find it under the Application tab.

▪ Remember that simulating mobile devices can only take you so far. In the end, there is no replacement for real testing on real devices. I highly recommend Alex Russel’s “Progressive Performance” talk for a reality check.

▪ Lighthouse Lighthouse is an open source tool, originally developed by Google, that you can use to automatically audit your app against a set of PWA best practices.

▪ But understanding the service worker lifecycle also opens up new opportunities to do amazing stuff. By understanding how the install event works, we were able to create install dependencies for our service worker. By understanding when our service worker moves from the installed to the activated state, we were able to create a sophisticated system that manages multiple cache versions in just a few lines of code

▪ cache.put takes a key and a value (e.g., a URL, and a response object) and creates a new entry in the cache. Unlike cache.add which only takes a URL, cache.put does not require another network request because it already contains the response to cache.

▪ It is time to stop treating a loss of connectivity as an error state in our web apps. Offline and poor connectivity are inevitable states in our apps — ones we must plan for.

▪ We embraced mobile-first once we realized we could no longer ignore the fact that users are visiting our sites on mobile screens. We had to come to terms with the fact that we can no longer build websites that only look great on a 15-inch screen. We learned to consider mobile devices first, and build the experience up from there.

▪ We have transitioned into a mobile-first world, and yet our approach to connectivity and bandwidth is still rooted in the days of the desktop. It is time to start thinking offline-first.

▪ Traditional web apps used to be entirely dependent on the server. All data, content, design, and application logic were stored on the server. The client was just there to render some HTML to the screen. But as web apps evolved, more and more logic and power was transferred to the client. Web apps started doing data manipulations, template rendering, and more. But unlike native apps, our web apps remained completely dependent on the server. Any disruption in connectivity would cause the app to fail completely.

▪ Offline-first is about accepting a simple truth: offline and low connectivity conditions are inevitable. These conditions should be treated not as a catastrophic failure, but as just another possible state in the life of your web app. A state you should plan for and handle gracefully.

▪ Embracing offline-first means accepting that while some aspects of your app might stop working when the user is offline, many others no longer have to.

▪ Traditionally, if the user visited this web app while he was offline, the browser would simply show him an error. In a native app, this horrible user experience would be unacceptable. There is no reason we shouldn’t hold the web up to the same user experience standards.

▪ A modern messaging PWA can cache its interface and logic locally, as well as the content of the most recent messages. It can then display the full interface along with the last cached content to the user. Yes, the content may be a bit stale (and it is important to communicate this to the user), but it can still be useful. This is an app that no longer handles a loss of connectivity as a catastrophic failure. It gives the user the best experience possible for his current conditions.

▪ Another fundamental aspect of offline-first is handling these changes in connectivity gracefully. Handling a dropped connection gracefully means communicating to the user that some functionality may not be available, or that the data she is looking at may be a few hours old but still exposing as much functionality as possible.

▪ Even if you have built a web app that works entirely offline, handling a change in connectivity gracefully might mean reassuring the user that she can still use the app and that her data will not be lost.

▪ Before we can decide on a caching strategy for the different parts of our site, we need to familiarize ourselves with a few of the more common design patterns used for caching.

▪ Different patterns fit different situations, and most apps would use a few different ones. For example, if we are creating a weather app, we would probably want to adopt a pattern that always loads the latest weather data from the network, and only if the network fails try to load it from the cache. On the other hand, for the icons showing the different weather conditions, we might prefer to adopt a pattern that always gets the icon from the cache first and only tries the network if they are not found in the cache.

▪ Weather conditions are an example of a rapidly changing resource. One where it is critical to show the most up-to-date data. The icon depicting a partly cloudy sky is not time sensitive nor does it change.

▪ Cache only Respond to all requests for a resource with a response from the cache. If it is not found in the cache, the request will fail. This pattern assumes that the resource has been cached before, most likely as a dependency during the service worker’s installation. This is useful for static resources that do not change between releases, such as logos, icons, and stylesheets. This does not mean you can never change them. It simply means they do not change within the lifetime of a single version of your app.

▪ If these files do change, you can update them by renaming them and storing these new files in the cache. This is similar to the classic caching practice (unrelated to service workers) of changing the names of all static files in every version (e.g., style.v1.0.3.css or main_ae3f7.js) and configuring the server to serve those files with a very long, or even indefinite, cache expiration date. If you choose not to change filenames, you can fetch and cache these files again by releasing a new version of your service worker, and caching them during the service worker’s activation event (see Chapter 4):

▪ self.addEventListener("fetch", function(event) { event.respondWith( caches.match(event.request) ); });

▪ Cache, falling back to network Similar to cache only, this pattern will respond to requests with content from the cache. If, however, the content is not found in the cache, the service worker will attempt to fetch it from the network and return that: self.addEventListener("fetch", function(event) { event.respondWith( caches.match(event.request).then(function(response) { return response || fetch(event.request); }) ); });

▪ Network only The classic model of the web. Try to fetch the request from the network. If it fails, the request fails. This is useful for things you decide never to cache (e.g., analytics pings).

▪ You will rarely use this pattern as you can perform network only requests by simply ignoring their fetch event in your service worker and letting their default behavior play out.

▪ help: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request) ); });

▪ Network, falling back to cache Always fetch the request from the network. If the request fails, return the version from the cache.

▪ If it is not found in the cache, the request will fail: self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return caches.match(event.request); }) ); });

▪ Cache, then network Display data from the cache immediately while checking the network for a more up-to-date version. As soon as a response is returned from the network, check if it is newer than the cache and update the page with the fresh content.

▪ While this may seem like a best-of-all-worlds approach, combining a fast response from the cache with up-to-date content from the network as soon as it is available, it does come with a price.

▪ You will have to modify your app to make two requests, display cached content, and finally update the page with newer content when it becomes available

▪ More importantly, this pattern might raise new UX challenges for your app. While it is easy to simply change an image with a more up-to-date one when it is available, what if the content you are updating is the text of a document the user is editing?

▪ What if you have to change the second sentence after the user has already begun editing it? What is the best way to make the change, and how do you communicate it to the user?

▪ Generic fallback When the content the user asked for could not be found in the cache, and the network is not available, this pattern returns an alternate “default fallback” from the cache instead of returning an error.

▪ One common use case for this is returning a generic image instead of a specific one. For example, when a user’s avatar is not found in cache, and the network is unavailable, displaying a generic avatar instead of leaving a broken image in your app is a great way to gracefully handle a change in connectivity. This pattern is usually used together with others as a final fallback. The following example shows how it can be used with the network, falling back to cache pattern to create a network, falling back to cache, falling back to generic pattern:

▪ self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return caches.match(event.request).then(function(response) { return response || caches.match("/generic.png"); }); }) ); });

▪ For Twitter, progressive web apps have been a boon — especially for entering emerging markets where big growth opportunities still abound.

▪ These markets are often characterized by expensive, slow, and unreliable connections. Twitter’s progressive web app combines many benefits over their native app. It weighs a mere 400 KB (about 2.5% of the Android app), uses less battery, and launches several seconds faster from the homescreen than the native app.

▪ Most importantly, it combines all of these benefits without sacrificing any of the features of the native app.

▪ All of these advantages give Twitter a significant edge in markets where slower feature phones and unreliable, costly connections are the norm.

▪ Cache on demand For resources that do not change often and that we do not want to cache during the service worker’s install event, we can extend the cache, falling back to network pattern to save requests that have been returned from the network to the cache.

▪ This effectively creates a system for caching resources on-demand. When a resource is first requested, it won’t be found in the cache. The service worker will retrieve it from the network, store it in the cache, and then return it.

▪ The next time this resource is requested again, it will be returned instantaneously from the cache: self.addEventListener("fetch", function(event) { event.respondWith( caches.open("cache-name").then(function(cache) { return cache.match(event.request).then(function(cachedResponse) { return cachedResponse || fetch(event.request).then( function(networkResponse) { cache.put(event.request, networkResponse.clone()); return networkResponse; }); }) }) ); });

▪ The Case for Cloning — Using a Response More Than Once When looking at the code for the last three patterns, you may have noticed something new. Before we saved our response to the cache, we called a method called clone on it:

▪ fetch(request).then(function(response) { cache.put(request, response.clone()); return response; });

▪ Why did we put a cloned copy of the response into the cache instead of just the response itself? This actually has nothing to do with the fact that we used cache.put(). We have already placed responses in the cache in the past and did not have to clone them first. The real reason is that we intend to use the response more than once.

▪ You can think of responses as being written on a physical piece of paper. Imagine the owner of the Gotham Imperial Hotel, heir to the Dwayne family fortune, preparing a speech and writing it on a piece of paper. Just as he is about to go on stage, he hands the speech to his assistant to place in storage. Once he gets on stage, he might find himself standing in front of a packed room holding nothing — unless he made a copy of the speech first and gave that to his assistant instead.

▪ Responses act similarly. You can pass them on from one place to the next (e.g., using a return statement), but if you intend to use them more than once (e.g., placing them in cache and responding to an event with them), make sure you have a copy of them made by using the clone command.

▪ Cache, falling back to network with frequent updates For resources that do change from time to time, but where showing the latest version is less important than returning a fast response (e.g., user avatars), we can modify the cache, falling back to network pattern to always fetch the requested resource from the network even when it is found in the cache. This pattern delivers a fast response from the cache, while fetching a more up-to-date version and caching it in the background. Any changes to the resource fetched from the network will be available the next time the user requests this resource. This combines the benefits of a fast response with a relatively up-to-date response (the content shown is as fresh as it was the last time you requested it): self.addEventListener("fetch", function(event) { event.respondWith( caches.open("cache-name").then(function(cache) { return cache.match(event.request).then(function(cachedResponse) { var fetchPromise = fetch(event.request).then(function(networkResponse) { cache.put(event.request, networkResponse.clone()); return networkResponse; }); return cachedResponse || fetchPromise; }) }) ); });

▪ What about the index.html file itself? Since this file rarely changes between versions, we might consider a cache, falling back to network pattern. This approach does come with a significant downside in our case. If this file gets updated, we will have to update our service worker as well to make sure the new file is fetched and cached.

▪ To make matters worse, our users won’t see the new version until the old service worker releases control of the page and a new service worker serving the new file becomes active. You can see how this plays out during each visit in Table 5-1.

▪ This means that even if we update the service worker with a new HTML file, it won’t be shown to the user until his next visit to our app.

▪ Let’s consider our options for caching index.html: Serve it using the cache, falling back to network pattern. This has the downside of possibly not showing the latest version available, even though it might already be cached. It is, however, a fast and bandwidth-efficient solution. Serve it using the network, falling back to cache pattern. This will always show the latest file available. The downside is that we are passing on the chance to improve the load time of an HTML file that we may already have in the cache. Serve it using the cache, falling back to network with frequent updates pattern. Similar to option 1, this always serves the index.html from the cache, providing us with a very fast response time. In addition, it also checks for an updated index.html file and updates the cache if it exists without requiring us to release a new service worker version. The next time the user loads the page, she will see the latest file. This approach combines a fast response time with an almost always up-to-date file. It does, however, use just as much bandwidth as option 2, or not having a service worker at all. 

▪ For the Gotham Imperial Hotel home page, I decided to go with option 3. This approach gives us the benefit of a home page that loads instantly, no matter what the user’s connection is. The main downside to this is that the home page shown may sometimes be an older one until the user refreshes the page (not a big deal in this case, since all dynamic data that may change is cached using patterns that will serve up the most up-to-date data).

▪ The second downside is that it fetches the HTML from the network on every visit, even though it may already be in the cache (again, not a big deal as the file is relatively small, and the server can send Expires and ETag headers to make sure it is cached in the HTTP cache).

▪ Looking further down our home page, we see a map created using the Google Maps JavaScript API. This interactive map is loaded from Google’s servers every time our page loads. Since we can’t cache all of Google Maps’ logic and data, we will update our service worker to detect when the Google Maps JavaScript file fails to load and serve an alternate JavaScript file. This file will display a static image with a map instead of a dynamic, interactive map widget. This is progressive enhancement in action.

▪ Offline users will see the map as a static image, while online users will get a fully interactive map.

▪ Our home page also loads a JSON file with a list of upcoming events taking place at the hotel. This is data that can change at any time, and we would like for our users to always see the most up-to-date version. We will use the network, falling back to cache with frequent updates pattern to serve this file. This makes sure we always serve the latest data we have access to according to network conditions: live data if the user is online, or the last version we cached if he isn’t.

▪ The events JSON file also includes references to a number of image files, each representing a different event. Since these files are not cached during the installation phase, we can use the cache on demand pattern. Every time one of these files is requested, we will attempt to fetch it from the cache. If it is not found in the cache, we will fetch it from the network, store it in the cache for next time, and return it to the page.

▪ To make sure we never have a broken image on our page, we will also modify our caching code for the event images to show a default fallback image if an image is not found in the cache, and the network is not available. This default image will be cached during the installation phase as an install dependency.

▪ Finally, we will set up a rule to make sure analytics pings are sent directly to the network without any caching or fallback. If the user is offline, these pings should fail.

▪ Replace the code in serviceworker.js with the following code: var CACHE_NAME = "gih-cache-v4"; var CACHED_URLS = [ // Our HTML "/index.html", // Stylesheets "/css/gih.css", "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css", "https://fonts.googleapis.com/css?family=Lato:300,600,900", // JavaScript "https://code.jquery.com/jquery-3.0.0.min.js", "/js/app.js", // Images "/img/logo.png", "/img/logo-header.png", "/img/event-calendar-link.jpg", "/img/switch.png", "/img/logo-top-background.png", "/img/jumbo-background.jpg", "/img/reservation-gih.jpg", "/img/about-hotel-spa.jpg", "/img/about-hotel-luxury.jpg" ];

▪ self.addEventListener("install", function(event) { event.waitUntil( caches.open(CACHE_NAME).then(function(cache) { return cache.addAll(CACHED_URLS); }) ); }); self.addEventListener("fetch", function(event) { event.respondWith( fetch(event.request).catch(function() { return caches.match(event.request).then(function(response) { if (response) { return response; } else if (event.request.headers.get("accept").includes("text/html")) { return caches.match("/index.html"); } }); }) ); }); self.addEventListener("activate", function(event) { event.waitUntil( caches.keys().then(function(cacheNames) { return Promise.all( cacheNames.map(function(cacheName) { if (CACHE_NAME !== cacheName && cacheName.startsWith("gih-cache")) { return caches.delete(cacheName); } }) ); }) ); });

▪ Let’s take it further and improve it so that index.html and all the static files required to display it load instantly, even when the user is online. Replace the code of the fetch event listener in serviceworker.js with the following: self.addEventListener("fetch", function(event) { var requestURL = new URL(event.request.url); if (requestURL.pathname === "/" || requestURL.pathname === "/index.html") { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return cache.match("/index.html").then(function(cachedResponse) { var fetchPromise = fetch("/index.html") .then(function(networkResponse) { cache.put("/index.html", networkResponse.clone()); return networkResponse; }); return cachedResponse || fetchPromise; }); }) ); } else if ( CACHED_URLS.includes(requestURL.href) || CACHED_URLS.includes(requestURL.pathname) ) { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return cache.match(event.request).then(function(response) { return response || fetch(event.request); }); }) ); } });

▪ Because fetch runs asynchronously, the response from the cache can be returned even before the fetch resolves.

▪ This pattern gives us both an instant response (a few milliseconds) from the cache, while guaranteeing a relatively up-to-date HTML file.

▪ new URL(urlString, [baseURL]) Our fetch handler’s main conditional statement decides how to handle different requests by testing their URLs. In the past, this would have involved some fairly nasty regular expressions to accomplish. Thankfully, the relatively new URL interface allows us to do this with ease:

▪ // These three statements return the same URL var url_1 = new URL("https://gothamimperial.com/index.html"); var url_2 = new URL("/index.html", "https://gothamimperial.com"); var url_3 = new URL("/index.html", url_1); // All of the following statements are true url_1.href === "https://gothamimperial.com/index.html"; url_1.protocol === "https:"; url_1.hostname === "gothamimperial.com"; url_1.pathname === "/index.html"; 

▪ var CACHE_NAME = "gih-cache-v5"; var CACHED_URLS = [ // Our HTML "/index.html", // Stylesheets "/css/gih.css", "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css", "https://fonts.googleapis.com/css?family=Lato:300,600,900", // JavaScript "https://code.jquery.com/jquery-3.0.0.min.js", "/js/app.js", "/js/offline-map.js", // Images "/img/logo.png", "/img/logo-header.png", "/img/event-calendar-link.jpg", "/img/switch.png", "/img/logo-top-background.png", "/img/jumbo-background-sm.jpg", "/img/jumbo-background.jpg", "/img/reservation-gih.jpg", "/img/about-hotel-spa.jpg", "/img/about-hotel-luxury.jpg", "/img/event-default.jpg", "/img/map-offline.jpg", // JSON "/events.json" ]; var googleMapsAPIJS = "https://maps.googleapis.com/maps/api/js?key="+ "AIzaSyDm9jndhfbcWByQnrivoaWAEQA8jy3COdE&callback=initMap"; self.addEventListener("install", function(event) { event.waitUntil( caches.open(CACHE_NAME).then(function(cache) { return cache.addAll(CACHED_URLS); }) ); }); self.addEventListener("fetch", function(event) { var requestURL = new URL(event.request.url); // Handle requests for index.html if (requestURL.pathname === "/" || requestURL.pathname === "/index.html") { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return cache.match("/index.html").then(function(cachedResponse) { var fetchPromise = fetch("/index.html") .then(function(networkResponse) { cache.put("/index.html", networkResponse.clone()); return networkResponse; }); return cachedResponse || fetchPromise; }); }) ); // Handle requests for Google Maps JavaScript API file } else if (requestURL.href === googleMapsAPIJS) { event.respondWith( fetch( googleMapsAPIJS+"&"+Date.now(), { mode: "no-cors", cache: "no-store" } ).catch(function() { return caches.match("/js/offline-map.js"); }) ); // Handle requests for events JSON file } else if (requestURL.pathname === "/events.json") { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return fetch(event.request).then(function(networkResponse) { cache.put(event.request, networkResponse.clone()); return networkResponse; }).catch(function() { return caches.match(event.request); }); }) ); // Handle requests for event images. } else if (requestURL.pathname.startsWith("/img/event-")) { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return cache.match(event.request).then(function(cacheResponse) { return cacheResponse || fetch(event.request).then(function(networkResponse) { cache.put(event.request, networkResponse.clone()); return networkResponse; }).catch(function() { return cache.match("/img/event-default.jpg"); }); }); }) ); // Handle analytics requests } else if (requestURL.host === "www.google-analytics.com") { event.respondWith(fetch(event.request)); // Handle requests for files cached during installation } else if ( CACHED_URLS.includes(requestURL.href) || CACHED_URLS.includes(requestURL.pathname) ) { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return cache.match(event.request).then(function(response) { return response || fetch(event.request); }); }) ); } }); self.addEventListener("activate", function(event) { event.waitUntil( caches.keys().then(function(cacheNames) { return Promise.all( cacheNames.map(function(cacheName) { if (CACHE_NAME !== cacheName && cacheName.startsWith("gih-cache")) { return caches.delete(cacheName); } }) ); }) ); });

▪ If you did not skip Chapter 4, you may have noticed a problem here. We only cache the events.json file when we intercept the fetch request. This only happens when the service worker already controls the page. In other words, when the user visits the page for the first time, this file isn’t cached. Only on the user’s second visit will the browser’s attempt to fetch this file be captured by the service worker. If the user was offline on his second visit, the file won’t be found in the cache. Since our service worker depends on having this file in the cache, we can solve this issue by adding events.json to the CACHED_URLS array. This ensures that it will be cached when the service worker installs. It will then be kept up-to-date on every consecutive visit by the code we just added.

▪ Because these images change frequently, and during development we have no way of knowing which events our clients at the hotel are going to be hosting, we will cache these on demand. Every time we detect a request for an event image, we begin by opening our cache and trying to find it. We then either return that image if it was found in the cache or attempt to fetch it from the network. If the image was fetched successfully, we place it in the cache for future use and return it.

▪ Just like in our last condition, this presents a problem if the user is offline on her second visit to our page. In this case, the user will have the events.json file cached and try and display the event images. Unfortunately, they haven’t been cached yet, nor can they be fetched from the network. To handle this edge case, we use the generic fallback pattern. If the image is not in the cache and cannot be fetched from the network, we fall back to a generic event image (Figure 5-1). Don’t forget to add the fallback image ("/img/event-default.jpg") to the CACHED_URLS array to make sure it is cached when the service worker installs.

▪ For the team at the Washington Post, getting people to read more articles at each visit is vital; making sure pages load as fast as possible is key to that. Using many of the patterns described, the team has been able to squeeze out many performance gains from their progressive web app, but it took some out-of-the-box thinking to find the biggest speed boost — predictive caching. When you read an article on the Washington Post, instead of caching the most popular articles on the site, or even the most popular articles from the category you are currently reading, the site’s service worker will cache the text, images, and even the first few seconds of the video you are most likely to read or watch next — namely, the ones linked directly from the current article. This change alone has allowed the team to improve the load time of the next article to around 100 ms. An improvement that directly contributes to more articles read every month, more ad views, and eventually more paying subscribers.

▪ App shell’s goal is to present the user with a meaningful experience as soon as possible. A well-designed progressive web app that implements app shell will load and show its basic interface in milliseconds.

▪ Let’s turn our attention back to our messaging app. You may decide that your app’s minimal shell is a header with the app’s logo, some basic controls, and an input field to enter new messages (Figure 5-2). The minimal shell shown on the left side of the image can load very quickly on the user’s first visit. It is then cached so that in subsequent visits it can load in mere milliseconds, regardless of the user’s connection. As soon as this shell is rendered, the app can load fresh content from the network, as well as additional scripts needed to enable the rest of the app’s functionality.

▪ This strategy allows you to create an app that responds almost instantaneously. It presents a UI to the user as soon as possible, instead of having him stare at an empty screen, waiting for the network to respond. The user may even begin typing a new message while the rest of the content and functionality loads in the background.

▪ By embracing this strategy, you will be able to create apps that load almost instantaneously, presenting a UI to the user as soon as possible, instead of having him stare at an empty page, waiting for the network to respond. You will create an experience that is more like what users have come to expect from native apps than from the web.

▪ Before including content in your initial render, ask yourself a few questions first: Will rendering potentially stale content from the cache and then updating it seconds later with fresh content from the network hurt or improve the user experience? 

▪ In the case of our sample messaging app, we may decide that storing old messages in the cache and including them as part of our initial render improves the user experience. Messages that are already cached can be quickly rendered, and the experience of older messages being pushed down by newer ones as they arrive is a part of the app’s normal flow (Figure 5-3). Chapter 6 looks at how to store data, like these messages, in a local database, and use them to populate an app shell with content.

▪ When planning our caching strategy, the first step is to look at the various components that make up our app. What parts of our app can be cached and rendered immediately as part of the application shell?

▪ The page header contains a large background image with the Gotham skyline. This is a great example of an image that can be loaded later and does not need to be a part of our app shell. 

▪ Both the data for the reservations list and the events list load using Ajax. These can be added to the page after the initial app shell loads and renders. 

▪ When a user clicks the My Account button, having the next screen load in 150 ms versus 578 ms is the difference between the feeling of navigating between web pages and the feeling of navigating between screens in a native app. In Chapter 6 we will improve this page further.

▪ These results improve both the user’s experience and reduce the amount of bandwidth used (saving money for our users and reducing our costs).

▪ There is more to building an offline-first app than simply handling changes in connectivity. As we improve support for offline functionality, new user experience challenges arise. For example: How can we communicate to an offline user that content she is looking at is served from cache and may be stale? How can we assure the user that changes she makes will not be lost even if she loses connectivity? We will explore these UX challenges in more depth in Chapter 11.

▪ Just remember that they are not rigid blueprints. Sometimes you will need to mix and match them (e.g., like our event image code that caches on demand, but also implements a generic fallback pattern), and sometimes you will have to come up with something completely different (e.g., if a generic fallback image wasn’t acceptable to our clients, we might have considered parsing the events.json file during the install event and caching the images within it).

▪ There is no preset formula to apply to your web app that will unlock an offline-first badge. When planning the strategy for your app, always consider how and when each resource is needed. Weigh the need for each resource to be up-to-date versus potential performance benefits.

▪ These patterns, as well as a few others, were first categorized and named by Jake Archibald in “The Offline Cookbook”. It is highly recommended.

▪ While our app was fully operational regardless of the user’s connection, can it truly be called offline-first when it relies so heavily on the server for even the simplest data manipulation?

▪ We need a better way to handle data persistently in the browser. One that allows us to store, read, and modify data locally, without relying on the network.

▪ Just like server-side databases, IndexedDB allows us to store data in a structured way, query it, modify it, and more. Unlike server-side databases, IndexedDB can do all of this entirely in the browser.

▪ IndexDB is transactional

▪ By grouping actions together into a single transaction, we can make sure that either all actions fail and no money gets moved, or they all succeed and the bank can charge its $6 commission.

▪ an object store database stores objects. Each database can contain multiple object stores, and each of these can contain multiple objects. These “objects” can be JavaScript objects, booleans, numbers, blobs, and most other units of data that JavaScript can handle.

▪ IndexedDB is an indexed DB Like traditional relational database systems, IndexedDB makes use of indices. You can add an index on any object store and use it to retrieve only the objects you want.

▪ IndexedDB is browser based IndexedDB runs completely in the browser.

▪ There are a number of open source libraries that make data propagation between the local database and the server easier. We explore some of them in “The IndexedDB Ecosystem”.

▪ You can create multiple databases (although most apps usually create just one). 

▪ Each database can contain multiple object stores. 

▪ IndexedDB follows the same-origin policy, ensuring that users can visit any website without worrying that it will read data written by another website. In other words, you can read and write data within your domain, but you cannot access data written into IndexedDB from a different domain. 

▪ Databases are versioned. If you would like to create an object store or modify its structure, you open a database connection with a new version number. This triggers an upgrade-needed event. Any changes to the database between this version and previous ones can be performed during this event. 

▪ Most IndexedDB actions are asynchronous. If you request a value, the API does not simply return that value. Instead you define a callback function to handle that event. When that callback function is called, it will contain the value you requested. 

▪ Browser Support for IndexedDB Historically, IndexedDB has gotten a bad rep. This was largely because of a terribly buggy implementation in Safari and iOS 8 and 9, as well as a complete lack of support in iOS WebViews. Luckily, these days IndexedDB fares much better. As of 2017, when this book was published, IndexedDB works well in most modern browsers (except Opera Mini). For those looking to support older browsers (IE version 9 or earlier, Android Browser 4.3 or earlier), “The IndexedDB Ecosystem” explores a number of libraries that improve support for older browsers by falling back to alternative technologies such as WebSQL and localStorage. Even if you choose to ignore older browsers, it is best to use feature detection before using IndexedDB. You can see this in practice in “IndexedDB in Practice”.

▪ While IndexedDB is notorious for being a bit confusing, we will take a practical, hands-on approach to quickly understand the core principals behind it and achieve concrete results in a short time.

▪ Add the following code to indexeddb.html: var request = window.indexedDB.open("my-database", 1); request.onerror = function(event) { console.log("Database error: ", event.target.error); }; request.onsuccess = function(event) { var db = event.target.result; console.log("Database: ", db); console.log("Object store names: ", db.objectStoreNames); }; 

▪ Even the most basic IndexedDB code example immediately shows the asynchronous nature of IndexedDB. Calling window.indexedDB.open() does not return a database connection. Instead, it returns a request to open a database connection. We can then listen to events on that request, such as the success and error events.

▪ As the second line in the console clearly shows, our database still doesn’t contain any object stores. Why? The answer is in the first line. The database is still in version 1, so our upgrade needed event was not triggered. Let’s update the version number in the first line of our code to version 2: var request = window.indexedDB.open("my-database", 2); 

▪ With the browser pointing at http://localhost:8443/indexeddb.html, run the following code in the browser’s console: var request = window.indexedDB.open("my-database", 2); request.onsuccess = function(event) { var db = event.target.result; var customerData = [ {"passport_number": "6651", "first_name": "Tal", "last_name": "Ater"}, {"passport_number": "7727", "first_name": "Archie", "last_name": "Stevens"} ]; var customerTransaction = db.transaction("customers", "readwrite"); customerTransaction.onerror = function(event) { console.log("Error: ", event.target.error); }; var customerStore = customerTransaction.objectStore("customers"); for (var i = 0; i < customerData.length; i++) { customerStore.add(customerData[i]); } };

▪ By defining the transaction’s scope, IndexedDB avoids race conditions between different transactions (e.g., two or more transactions that attempt to modify the same object store at the same time). If two or more readwrite transactions are created with an overlapping scope, they will enter a queue and run consecutively. If they have different scopes, or they are readonly transactions, they can run in parallel.

▪ The first error is thrown because we set the customers object store to use the passport_number value as its key. This means that it must be unique. When we attempt to add a new record with the same key as an existing record’s ID, IndexedDB throws an error.

▪ Transactions guarantee that either all actions succeed, or none do.

▪ Reading Data from an Object Store Now that we have our first two customers in our object store, let’s learn how to retrieve objects from it. There are three ways to read data. You can request a single object using its key, you can use a cursor to iterate over all the objects in your store, or you can use an index to retrieve a smaller subset of the data (and then iterate over it with a cursor).

▪ Run the following code in the browser console: var request = window.indexedDB.open("my-database", 2); request.onsuccess = function(event) { var db = event.target.result; var customerTransaction = db.transaction("customers"); var customerStore = customerTransaction.objectStore("customers"); var request = customerStore.get("7727"); request.onsuccess = function(event) { var customer = event.target.result; console.log("First name: ", customer.first_name); console.log("Last name: ", customer.last_name); }; }; 

▪ One approach for solving this challenge comes from the world of traditional databases — migrations. Migrations are a series of atomic steps, each charged with moving the database forward by one version.

▪ A different approach to upgrading the database between versions is by testing the current state of the database and making changes as they are needed. Change your onupgradeneeded method in indexeddb.html to the following, and make sure the first line of your script is set to open database version 3: request.onupgradeneeded = function(event) { var db = event.target.result; if (!db.objectStoreNames.contains("customers")) { db.createObjectStore("customers", { keyPath: "passport_number" } ); } };

▪ We already saw how we can retrieve a single object from an object store using get(). Unfortunately, that method only works when we are looking to retrieve a single object and know its exact key. In order to retrieve multiple objects, we will need to open a cursor.

▪ If you are familiar with SQL-based databases, you can think of opening a cursor as running a SELECT * FROM table query. Just like this query can be modified with a WHERE and a LIMIT, so too can the cursor be modified with an index or a boundary.

▪ Unlike the results returned by SQL, a cursor does not contain the results within it. It is simply a list of pointers to the actual objects in the object store. At any time, a cursor points at just one record in the object store, moving to the next one when you tell it to continue() or advance(). This allows us to iterate (or traverse) over large object stores without having to hold all of them in memory (Figure 6-1).

▪ If you are only interested in retrieving objects that match certain criteria, going over the entire object store isn’t very efficient or convenient. By using an index, we can “query” our object store and open a cursor that only iterates over records that match that query.

▪ The Washington Post — Taking Analytics Offline with IndexedDB When building their new progressive web app, the team at the Washington Post faced an interesting challenge. In adding offline support, they had improved their visitors’ experience, but lost the ability to measure and track those experiences. As a data-driven team, this was not a trade-off they were willing to make. Working directly with Jeff Posnick from the developer relations team at Google, they came up with a solution: a fetch handler that catches all failed requests to Google Analytics and stores them in IndexedDB. Then, the next time a fetch request to Google Analytics succeeds (meaning the connection has been restored), the service worker retries all failed requests to Analytics again. The team at Google has since released this as a helper library you can use in your own project called workbox-google-analytics.

▪ It is a relatively simple script that does a few things: Calls populateReservations(), which loads reservations.json from the server, iterating over each result and adding it to the DOM (using the renderReservations function). Adds logic to the booking button to validate form data, render a new reservation to the DOM, and send the new reservation to the server. Every five seconds, calls the checkUnconfirmedReservations function, which checks for unconfirmed reservations and contacts the server to see if their status was updated. 

▪ Now that you have had a chance to play with IndexedDB a bit, you may be starting to notice its shortcomings. As an API that predates promises, IndexedDB relies heavily on callbacks — and as they say, the road to hell is paved with callbacks.

▪ Just like with caching, as you store more and more data in IndexedDB, you need to consider the amount of storage you use on your users’ devices. For the Gotham Imperial Hotel app, this isn’t likely to become much of a problem because the amount of data it uses grows slowly and linearly. But let’s consider IndexedDB in a different context — our messaging app.

▪ The responsible approach when building this app would be to delete old messages from our object store, keeping only the latest ones. One way to do this might be to fetch messages using an index on their publication date and deleting all messages older then a certain number of days. Another approach might be to just keep the latest 100 messages and delete all the older ones.

▪ Luckily, IndexedDB is accessible from within the service worker in exactly the same way as on the page.

▪ First, our code calls the IndexedDB API using window.indexedDB. The service worker, however, doesn’t have access to the window object. It runs in a completely different context. The service worker can access IndexedDB through the global object it has access to.

▪ In order to write code that will work both in the service worker and the page, we can use self.indexedDB. In the service worker, self will refer to the global object, and in the page, self will refer to the window.

▪ Add the following line to the top of serviceworker.js: importScripts("/js/reservations-store.js"); importScripts is a special method available in service workers to load scripts.

▪ PouchDB PouchDB was created with the goal of making a JavaScript database that runs well in the browser, allowing applications to store data locally while offline.

▪ var db = new PouchDB("reservations-db"); db.put({ _id: 1, nights: 3, guests: 2 }); db.changes().on("change", function() { console.log("Reservations database changed"); }); db.replicate.to("https://db.gothamimperial.com/mydb");

▪ localForage

▪ Dexie.js

▪ IndexedDB Promised

▪ Background sync allows us to make sure any action the user takes (whether filling out a form, clicking an RSVP button, or sending a message) completes — no matter the connection. Background sync actions will complete even if the user has left our web app, never to return, and then closed her browser. This makes it one of the most valuable tools browsers have given us in recent years. It may not be as sexy as push notifications, homescreen icons, or even offline functionality. When implemented properly, its impact is invisible to the user — but background sync works tirelessly in the background, making sure your users get things done.

▪ The essence of using background sync is moving actions away from the page’s context and running them in the background.

▪ By placing these actions in the background, they are safe from the volatile nature of any individual web page. A web page can be closed, the user’s connection may come down, and even servers fail from time to time. But as long as the browser is installed on the user device, a background sync action will not go away until it completes successfully.

▪ Using background sync is relatively straightforward. Instead of performing an action on your page (such as an Ajax call), you register a sync event: navigator.serviceWorker.ready.then(function(registration) { registration.sync.register('send-messages'); });

▪ Notice how the event listener code uses waitUntil to make sure the sync event does not end until we tell it to. This gives us time to try and perform some action and either resolve the event successfully if it succeeds, or reject it. If we return a rejected promise to the sync event, the browser will queue the sync action to be tried again at a later time. The sync event named "send-messages" will keep retrying until it succeeds — even if the user has already left our app.

▪ WhatsApp’s native app demonstrates this perfectly. You can always open it (regardless of your connection), write a message, and know that it will be delivered as soon as possible (immediately, or as soon as you go online if you aren’t). Even if you close the app, you know you can trust it to deliver your message in the background. WhatsApp’s interface even communicates this in a clear and simple way. If you send a message while you are offline, it will go into the stream of messages just like any other message (reinforcing your confidence that it won’t be lost), but with a small watch icon to indicate it is scheduled to be sent. As soon as it is delivered successfully, the watch icon is replaced with a checkmark.

▪ Any interaction with sync events is done through the SyncManager. The SyncManager is an interface of service workers that allows us to register sync events and get a list of current sync registrations.

▪ Getting this registration object is a bit different whether you are trying to access it from the service worker or from the page itself. Inside a service worker, the service worker registration is easily accessible in the global object: self.registration In a page controlled by a service worker, you can access the currently active service worker’s registration by calling navigator.serviceWorker.ready, which returns a promise that resolves to the service worker registration object: navigator.serviceWorker.ready.then(function(registration) {}); 

▪ Once you have a service worker’s registration object, the rest of your interactions with the SyncManager are the same, whether you are interacting with it from a service worker or the page.

▪ Let’s go over what happens when we register a sync event. The SyncManager maintains a simple list of sync event tags. This list contains no logic of what the events are or what they do. Their implementation is left entirely up to the code that responds to the sync event in the service worker. The SyncManager just knows which events were registered, when they were called, and how to dispatch a sync event.

▪ The SyncManager will dispatch a sync event for each of the registrations in its list when any of the following happens: Immediately after a sync event was registered When the user’s status changes from offline to online Every few minutes if there are existing registrations that haven’t completed successfully 

▪ Dispatched sync events can be listened for and responded to with a promise in the service worker. If that promise resolves, that sync registration will be removed from the SyncManager. If it rejects, it will remain in the SyncManager to be retried at the next sync opportunity.

▪ Event tags are unique. If you register a sync event with a tag name that already exists in the SyncManager, the SyncManager will ignore it and not add a duplicate entry.

▪ This may seem like a limitation at first, but it is actually one of the most useful traits of the SyncManager.

▪ It allows you to group the handling of many similar actions (e.g., emails to send) into a single event. You can then register a sync event to take care of all the actions in the queue (e.g., an email outbox) every time a new action is added to it without having to check first if that event is already registered or is currently running.

▪ For example, let’s say you are building an email service. Every time a user attempts to send a message, you can save the message to an outbox in IndexedDB and register a "send-unsent-messages" background sync event. Your service worker can then include an event listener that can respond to "send-unsent-messages" by going over every message in the IndexedDB outbox, attempting to send it, and removing it from the IndexedDB queue if it was sent successfully. If even a single message was not delivered successfully, the entire sync event could be rejected. The SyncManager will then dispatch that event again later, allowing you to try and empty the outbox again, knowing that only the messages that failed to deliver on the last event (along with any new messages created since) will be sent.

▪ Using this setup, you never need to check if there are messages in the outbox or not. As long as there are unsent emails, a sync event will remain registered and periodically attempt to empty the outbox. In “Adding Background Sync to Our App”, we will look at this in practice as we maintain a list of hotel reservations made while the user was offline.

▪ If you decide that you do want individual events, you can simply give them unique names such as "send-message-432", "send-message-433", etc.

▪ You can get a full list of all sync registrations that are scheduled to run using the getTags() method of the SyncManager.

▪ Unsurprisingly, like most service worker interfaces, getTags() returns a promise. This promise resolves to an array of sync registration tag names.

▪ self.registration.sync .register("hello-sync") .then(function() { return self.registration.sync.getTags(); }) .then(function(tags) { console.log(tags); }); Running this code inside a service worker should log ["hello-sync"] to the console.

▪ We can achieve a similar result from a page controlled by a service worker, by first getting the registration object using ready: navigator.serviceWorker.ready.then(function(registration) { registration.sync .register("send-messages") .then(function() { return registration.sync.getTags(); }) .then(function(tags) { console.log(tags); }); });

▪ In some cases, the SyncManager may decide that it has tried to dispatch a sync event that keeps failing too many times. When that happens, the SyncManager will dispatch the event one last time, giving you one last chance to respond to it. You can detect when this happens using the lastChance property of the SyncEvent and deciding how to act:

▪ self.addEventListener("sync", event => { if (event.tag == "add-reservation") { event.waitUntil( addReservation() .then(function() { return Promise.resolve(); }) .catch(function(error) { if (event.lastChance) { return removeReservation(); } else { return Promise.reject(); } }) ); } });

▪ Background Sync Browser Support Background sync has been available in Chrome since version 49. At the time of writing, it was being implemented in Opera, Mozilla Firefox, and Microsoft Edge.

▪ Most actions performed in a page require some data to complete. A page calling a function that sends a message might require the text of the message. A function that favorites a post will probably need the ID of the post. But when we register a sync event, the only thing we can pass to it is the name of the event. In other words, you can tell the service worker to send a message in the background, but passing the message text to it isn’t as straightforward as passing arguments to a function.

▪ There are many approaches to dealing with this. Allow me to suggest three different ones.

▪ Perhaps the ideal way to approach this would be to have the page store the entities the user is acting on (e.g., messages, reservations, etc.) in IndexedDB before triggering the background sync action. Then the sync event code in the service worker can iterate over that object store and perform the required action on each entry.

▪ Once the action completes successfully, that entity can be removed from the object store.

▪ Going back to our messaging app, this approach would have us adding every new message to a message-queue object store and then registering a send-messages background sync event to handle them. This event will then iterate over all messages in the message-queue, send each of them to the network, and finally remove them from the message-queue. Only once all messages have been sent, and the object store is empty, will the sync event be resolved successfully.

▪ If even a single message failed to deliver, a rejected promise can be returned to the event, and the SyncManager will launch the sync event again at a later time.

▪ You will probably want to maintain separate object stores for different queues (e.g., one queue for outgoing messages and a different one for liking posts) and have different sync events to handle each of them.

▪ Our event listener listens for sync events named message-queue-sync, then uses getAllMessages() to get all the messages queued in IndexedDB, and finally returns a promise to the sync event that resolves only if all the promises within it are resolved. This promise is created by passing an array of promises to Promise.all. We create this array of promises by running map() on the messages array and returning a promise for each message (a technique explained in “Creating An Array of Promises for Promise.all()”). Each of these promises will only resolve once that message was successfully sent and removed from the queue. Later, in “Adding Background Sync to Our App”, we will look at a similar example in more detail.

▪ But assuming the network will always be available is asking for trouble. Things might appear to work great when we are testing them on our local machine, but if a user tries to make a reservation just as she lost connectivity, this logic will fail miserably. If addReservation() is called while the user is offline, the new reservation will be entered into IndexedDB, rendered to the page, but the Ajax request will fail to let our server know that a new reservation was made. The reservation will appear on the page, and thanks to IndexedDB, it will remain there even after the user refreshes her browser. No matter what she does, she will see the reservation stuck in the "Awaiting confirmation" phase indefinitely, while the server will remain completely oblivious to it. This is endlessly frustrating to our users and a major nuisance to the hotel’s shareholders.

▪ We will modify the addReservation() function to check if background sync is supported in the browser. If it is, it will register a sync-reservations sync event. If it isn’t, it will use a regular Ajax call as before. 

▪ The code that adds new reservations to IndexedDB will be modified to add new reservations with a status of "Sending". This is how they will appear to the user until they are successfully added to the server, which will return a new status for them ("Awaiting confirmation" or "Confirmed"). 

▪ We will add an event handler to the service worker to respond to sync events. When a sync event named “sync-reservations” is detected, our event handler will go over every reservation with a "Sending" status and attempt to send it to the server. Reservations that are successfully added to the server will be updated in IndexedDB with their new status. If any request to the server fails, the entire sync event will be rejected, and the browser will attempt to run it again at a later time. 

▪ example: var addReservation = function(id, arrivalDate, nights, guests) { var reservationDetails = { id: id, arrivalDate: arrivalDate, nights: nights, guests: guests, status: "Sending" }; addToObjectStore("reservations", reservationDetails); renderReservation(reservationDetails); if ("serviceWorker" in navigator && "SyncManager" in window) { navigator.serviceWorker.ready.then(function(registration) { registration.sync.register("sync-reservations"); }); } else { $.getJSON("/make-reservation", reservationDetails, function(data) { updateReservationDisplay(data); }); } }; 

▪ Now that everything is in place to handle unsent reservations in the service worker, we can go ahead and add the background sync event listener to it. First, make sure that the first line in serviceworker.js imports the reservations-store.js file. It should look like this: importScripts("/js/reservations-store.js");

▪ Next, add the following code to the bottom of serviceworker.js: var createReservationUrl = function(reservationDetails) { var reservationUrl = new URL("http://localhost:8443/make-reservation"); Object.keys(reservationDetails).forEach(function(key) { reservationUrl.searchParams.append(key, reservationDetails[key]); }); return reservationUrl; }; var syncReservations = function() { return getReservations("idx_status", "Sending").then(function(reservations) { return Promise.all( reservations.map(function(reservation) { var reservationUrl = createReservationUrl(reservation); return fetch(reservationUrl); }) ); }); }; self.addEventListener("sync", function(event) { if (event.tag === "sync-reservations") { event.waitUntil(syncReservations()); } });

▪ We use self.addEventListener to add a new event listener for sync events. This event listener will respond to events tagged “sync-reservations,” telling them to waitUntil the promise returned by syncReservations() resolves or rejects before deciding whether to resolve or reject the sync event.

▪ If the syncReservations() promise resolves, the sync-reservations sync event will be removed from the SyncManager (until we register it again). If the promise is rejected, the SyncManager will keep this sync registration and trigger the event again later.

▪ What is the promise created by syncReservations() that determines the outcome of the entire sync event? Broadly speaking, syncReservations() goes over every reservation marked "Sending" in IndexedDB, tries to send it to the server, and returns a promise that resolves only when every single reservation has been sent successfully.

▪ If you restored connectivity, have been waiting for the sync event to run, and have begun wondering if it ran already or not, you can run the following code in your browser’s console: navigator.serviceWorker.ready.then(function(registration) { registration.sync.getTags().then(function(tags) { console.log(tags); }); }); 

▪ What is perhaps most impressive about background sync is that the sync event to the server will happen even if you close the Gotham Imperial Hotel site.

▪ The SyncManager keeps track of all the pending sync registrations and tirelessly makes sure things get done in the background. 

▪ This would never have been possible without a service worker — a script that can respond to events even after the user has closed your progressive web app.

▪ This brings up one last thing that is missing from our sync event. When our sync event successfully creates a reservation, the fetch request returns a new reservation details object containing new details. This includes the final price of the reservation, as well as the updated status of the reservation.

▪ var syncReservations = function() { return getReservations("idx_status", "Sending").then(function(reservations) { return Promise.all( reservations.map(function(reservation) { var reservationUrl = createReservationUrl(reservation); return fetch(reservationUrl).then(function(response) { return response.json(); }).then(function(newReservation) { return updateInObjectStore( "reservations", newReservation.id, newReservation ); }); }) ); }); };

▪ Background sync has the potential to become one of the most important building blocks of a modern progressive web app. It is one of those technologies that can be absolutely vital to the user experience, yet completely invisible to the user — until it doesn’t work.

▪ As we move more and more logic away from the page and into the service worker, we often find ourselves needing to communicate between the two.

▪ In Chapter 7, we saw how moving important events such as network requests away from the volatile page unto the service worker can make our apps more reliable.

▪ We are using the data in that JSON file to update the reservation details in IndexedDB, but as the service worker doesn’t have access to the window, we were unable to update the details of the reservation in the DOM.

▪ Instead, the page relies on a naïve setInterval() that checks the network for the reservation’s status every few seconds and updates the DOM. If our sync event could send the updated reservation details to the page as soon as they are received, we could update the DOM immediately and avoid making this needless network request.

▪ In this chapter, we will see how we can use postMessage() to send messages and data back and forth between the page and service worker and explore several types of communication: Sending a message from the window to the service worker that controls it Sending a message from a service worker to all windows in its scope Sending a message from a service worker to a specific window Sending a message between windows (through the service worker)

▪ Before we can post a message from the page, we first need to get the service worker that controls it. We can access this service worker using navigator.serviceWorker.controller. Next, we can use the service worker’s postMessage() method that receives as its first argument the message itself.

▪ The following example shows sending a message containing a simple object from a page to the service worker: navigator.serviceWorker.controller.postMessage( {arrival: "05/11/2022", nights: 3, guests: 2} )

▪ Once a message has been posted, the service worker can catch it by listening to the message event: self.addEventListener("message", function (event) { console.log(event.data); });

▪ Besides containing the message data itself, the event object contains a number of other useful properties. Some of the most useful ones are inside of its source property. source contains information about the window that posted this message and can help us decide what to do and where to post messages in response.

▪ The following are some sample uses for the message event’s source: self.addEventListener("message", function (event) { console.log("Message received:", event.data); console.log("From a window with the id:", event.source.id); console.log("which is currently pointing at:", event.source.url); console.log("and is", event.source.focused ? "focused" : "not focused"); console.log("and", event.source.visibilityState); }); 

▪ To accomplish this, we could add code that would post a message from restaurant details pages: navigator.serviceWorker.controller.postMessage("cache-current-page");

▪ When the user visits a restaurant page, a message will be posted to the service worker. The service worker could listen for these messages and use the event’s source to determine which page to cache: self.addEventListener("message", function (event) { if (event.data === "cache-current-page") { var sourceUrl = event.source.url; if (event.source.visibilityState === "visible") { // Cache sourceUrl and related files immediately } else { // Add sourceUrl and related files to a queue to be cached later } } });

▪ It will also use that page’s current visibility state to determine which pages to fetch and cache first. This way, if the user opens a bunch of restaurants in many separate tabs, the contents of the visible one would be cached first. 

▪ In “Common Messages in Progressive Web Apps”, we will look at how to communicate back to the page once it has been cached and update its UI to let the user know that the page is now cached and available offline

▪ The preceding code should actually be rewritten to include a check for the existence of the service worker before attempting to use it: if ("serviceWorker" in navigator && navigator.serviceWorker.controller) { navigator.serviceWorker.controller.postMessage( "cache-current-page" ); }

▪ From within a service worker, we can get all of the windows (WindowClients) that are currently open in the service worker’s scope using the clients object, which is in the service worker’s global object.

▪ clients contains a matchAll() method that we can use to get all of the windows (clients) currently open in the service worker’s scope. matchAll() returns a promise that resolves to an array containing zero or more WindowClient objects: self.clients.matchAll().then(function(clients) { clients.forEach(function(client) { if (client.url.includes("/my-account")) { client.postMessage("Hi client: "+client.id); } }); });

▪ Just placing the code at the top of your service worker will not be enough. If it is placed outside of an event, it will be executed once when the service worker script loads, before the service worker installed, and before any clients are listening for it. Instead, add it inside an event, as shown in the following code example. During development, you can also use the browser’s console to run this code in the service worker’s scope. See “The Console”.

▪ We would like to assure users of the Gotham Imperial Hotel app that they can use the app whether they are online or offline. We can do this by showing them a message as soon as the service worker has installed and finished caching all the assets it needs.

▪ The following sample modifies the install event to post a message to all clients after caching has completed. The page could then respond to this event by displaying a message to the user assuring him that the app can now be used both offline and online: self.addEventListener("install", function(event) { event.waitUntil( caches.open(CACHE_NAME).then(function(cache) { return cache.addAll(CACHED_URLS); }).then(function() { return self.clients.matchAll({ includeUncontrolled: true }); }).then(function(clients) { clients.forEach(function(client) { client.postMessage("caching-complete"); }); }) ); }); 

▪ When we call clients.matchAll(), we pass it an options object, telling it to include uncontrolled clients. This is another example of how important it is for us as developers to understand the service worker’s lifecycle (as explained in Chapter 4). When a user visits our page for the first time, the service worker installs and activates. However, the page is still not controlled by the service worker. If we did not tell self.clients.matchAll() to include uncontrolled windows, our message wouldn’t have reached its destination.

▪ In addition to the matchAll() method, the clients object has another useful method that allows you to get() a single client object. By passing the ID of a known client to get(), we can receive a promise that resolves to that WindowClient object.

▪ A much more likely use case for clients.get() is one where you will store a client’s ID in the service worker so that you can access it with clients.get() later.

▪ But postMessage() can actually receive a second argument, one which can be used to keep the line of communication between the two sides open, sending messages back and forth.

▪ This communication is handled by a MessageChannel object.

▪ In MessageChannel, the two cups are called port1 and port2 (Figure 8-1). You can speak into each cup (or port) using postMessage(), and you can listen to each cup using an event listener:

▪ var msgChan = new MessageChannel(); msgChan.port1.onmessage = function(msg) { console.log("Message received at port 1:", msg.data); }; msgChan.port2.postMessage("Hi from port 2");

▪ When we communicate between a window and a service worker (or vice versa), we can create a new MessageChannel object in the window and pass one of its ports to the service worker through a posted message. This port will then be accessible in the service worker when the message arrives.

▪ The result is an open communication channel with one port in the service worker and the other in the window.

▪ The following example posts a message to the service worker and receives a response through an open MessageChannel port: // Window code var msgChan = new MessageChannel(); msgChan.port1.onmessage = function(event) { console.log("Message received in page:", event.data); }; var msg = {action: "triple", value: 2}; navigator.serviceWorker.controller.postMessage(msg, [msgChan.port2]); // Service Worker code self.addEventListener("message", function (event) { var data = event.data; var openPort = event.ports[0]; if (data.action === "triple") { openPort.postMessage(data.value*3); } });

▪ Note that postMessage accepts an array of ports as its second argument so that you can communicate through zero or more ports.

▪ This simple example shows how we can delegate mathematical calculations from the page to our service worker. Similarly, our page could ask the service worker for the existence of items in the cache, or even ask it for a count of how many other tabs showing our app are currently open. The service worker could use the reverse approach to ask a window it controls for the value of an input field, or even how far in the page a user has scrolled so that the next page ca

▪ Let’s modify the site so that when the Logout link is clicked, all open windows that are pointed at the My Account page will navigate to the home page.

▪ Modify the $(document).ready function in app.js to look like this: $(document).ready(function() { $.getJSON("/events.json", renderEvents); if ("serviceWorker" in navigator) { $("#logout-button").click(function(event) { if (navigator.serviceWorker.controller) { event.preventDefault(); navigator.serviceWorker.controller.postMessage( {action: "logout"} ); } }); } });

▪ Our code checks for service worker support, and if it is available, adds a click event listener to the Logout link. This event handler first checks that there is a service worker controlling this page, and if so, it prevents the link’s default behavior, posting a message to the service worker instead of letting the page navigate.

▪ This is a great example of progressive enhancement in action. The Logout link begins its life like any other simple HTML link (Logout) and is fully functional. We then enhance it to support logging out of multiple windows in browsers that support service workers — without breaking existing behavior in older browsers.

▪ This message object structure, containing an action to take and extra parameters for it, is completely arbitrary and was chosen because it works well for this situation. "navigate" has no specific meaning to the browser here; it is just a string I have chosen to describe the action I would like my app to take.

▪ Modify the $(document).ready function in app.js to look like this: $(document).ready(function() { $.getJSON("/events.json", renderEvents); if ("serviceWorker" in navigator) { navigator.serviceWorker.addEventListener("message", function (event) { var data = event.data; if (data.action === "navigate") { window.location.href = data.url; } }); $("#logout-button").click(function(event) { if (navigator.serviceWorker.controller) { event.preventDefault(); navigator.serviceWorker.controller.postMessage( {action: "logout"} ); } }); } });

▪ That’s it! We have just progressively enhanced a simple HTML link to cause it to navigate not just the current window, but also all other open windows that match a certain criterion (i.e., all windows that show the My Account page).

▪ If there is a service worker controlling the page, override the logout link’s default action and instead post a message to the service worker telling it to take a "logout" action. Meanwhile, the service worker listens for these messages; and when they are detected, it posts a message to all controlled windows whose URL contains "/my-account", telling them to take a "navigate" action. The pages listen for these messages; and when they are detected, they each navigate to the URL included in the message.

▪ Note how in the sample code we are not checking that a service worker is controlling the page before adding the event listener. While only pages that are currently controlled by a service worker can post a message to the service worker, any page can add an event listener for incoming messages. In the sample code in “Service Worker to All Open Windows Messaging” we saw an example of sending a message from the service worker to uncontrolled pages.

▪ While the code that predated the sync event did update the DOM as soon as the reservation was made, the new sync code waited until the next time the page requested updates from the network.

▪ Update the syncReservations() function in serviceworker.js to look like this: var syncReservations = function() { return getReservations("idx_status", "Sending").then(function(reservations) { return Promise.all( reservations.map(function(reservation) { var reservationUrl = createReservationUrl(reservation); return fetch(reservationUrl).then(function(response) { return response.json(); }).then(function(newReservation) { return updateInObjectStore( "reservations", newReservation.id, newReservation ).then(function() { postReservationDetails(newReservation); }); }); }) ); }); };

▪ In this chapter, we explored how we can use postMessage() to communicate between the service worker and the windows it controls.

▪ These web apps can launch in full-screen mode (without any of the browser’s UI) so that they are indistinguishable from native apps, can be locked to a certain screen orientation (i.e., horizontal or landscape modes), and more (Figure 9-1).

▪ Considering the wonders promised in the introduction to this chapter, the implementation details are surprisingly simple. In fact, only three steps are required: Register a service worker. Create a web app manifest file. Add a link to the manifest from the web app. 

▪ Next, add the following HTML tag to the head of index.html and my-account.html. This will let the browser know that a manifest file is available for this site: This is it!

▪ The browser will only show the web app install banner on sites that it considers to be worthy of a place on the user’s homescreen — apps that meet certain minimal criteria for providing an app-like experience.

▪ At the time of writing, these criteria are the following: The site is served over HTTPS. The site has a service worker registered. The site has a web app manifest containing at least the four mandatory fields (detailed in “Anatomy of a Web App Manifest”). 

▪ The heuristics of how the browser determines this differ from browser to browser, and between different browser versions. For example, when initially launching this feature, both Opera and Chrome showed the install banner when a user had visited the app twice over two separate days during the course of two weeks. These heuristics have since been changed to increase the frequency of install banners and are still being continuously tweaked by different browser vendors to fine-tune the user’s experience.

▪ Make sure the short_name isn’t longer than 15 characters so that it isn’t truncated on the homescreen.

▪ Let’s look at an example. If your app’s full name is relatively short, you can feel free to provide it as either the short_name or the name and just ignore the other parameter.

▪ start_url The URL to open when the icon is clicked. This could be the root of your domain or even an internal page.

▪ We are also appending a utm_source=pwa tag to the querystring, which can be used by our Analytics software to track visitors that launch from the homescreen. If you do the same in your app, make sure your service worker knows how to match a request with or without the utm_source in the querystring (the code in “Implementing App Shell” properly matches these requests because it uses pathname which does not include the querystring).

▪ display Controls the display mode the app launches in (Figure 9-3). Possible values include the following: browser — open the app in the browser. standalone — open the app without the browser’s chrome (the browser’s user interface, such as the location bar). fullscreen — open the app without any of the browser or device’s chrome (e.g., on an Android device, this would mean hiding both the browser’s UI and the status bar at the top of the screen). To use the parlance of desktop apps, you can think of standalone and fullscreen as apps that open maximized or in full-screen mode, respectively, while browser behaves like any link clicked in the browser. 

▪ For the web app install banner to show, the display property must be set to either fullscreen or standalone. 

▪ scope Defines the scope of the app. When the user is in a full-screen/standalone app and navigates to another URL that is within this scope, the URL opens within the fullscreen/standalone app. If, however, the user clicks a link that would take her to a destination outside of this scope, the link opens in a regular browser window.

▪ prefer_related_applications If you also have a native app, and you prefer that the browser offer that instead of your shiny new progressive web app, you can set prefer_related_applications to true. When set to true, and a native app for the current platform is listed in related_applications, an install banner for your native app will be shown instead of a web app install banner. A native app install banner has the same requirements of a web app install banner, except for depending on a service worker.

▪ The way your installed app’s icon is shown in Android differs greatly from the way it is shown in Windows 8 and 10, which differs greatly from how a newer MacBook Pro would show it on the Touch Bar. Even within a single platform, the icons may vary greatly based on screen resolution.

▪ Frankly, it is an ever-changing minefield. It would be impractical to attempt to keep up with the changes and cover the requirements of each platform in this book. Luckily, there are a number of great online tools which help you deal with these complexities in an elegant way — you can find them listed on https://pwabook.com/appicons.

▪ What started a few years ago as a simple add shortcut to homescreen option hidden deep in the browser’s menu has since evolved to installable web apps.

▪ These apps combine all the benefits of native while avoiding many of its downsides, including the brutal installation model, replacing it with one that progressively earns a spot on the user’s device.

▪ But with great power comes great responsibility. If we want our apps to stand shoulder to shoulder with native apps, we need to consider the kind of experience we give our users.

▪ There are few (if any) features that were as central to the gulf between native apps and web apps as the ability to send notifications to your users.

▪ Push notifications allow users to opt in to updates from apps they care about, and to get timely updates to the content and data they need. Can you even imagine using an instant messaging app that doesn’t offer notifications?

▪ It would not be an understatement to say that push notifications have been one of the biggest driving factors for the success of the native app.

▪ There are few (if any) features that can be added to your web app which can have as big an impact as the ability to send notifications to your users.

▪ Push notifications are not actually a “thing.” A push notification is actually comprised of two separate “things,” a message sent using the Push API, and a notification shown using the Notification API.

▪ The Notification API allows a web page or a service worker to create and control the display of system notifications. These notifications are shown outside the browser (on the device’s UI) and thus exist outside of the context of any single browser window or tab. As they are not dependent on any browser windows or tabs, they can be created even after a user has left your site.

▪ Before you can show notifications to a user, you will first need to ask for the user’s permission. The whole process is relatively simple and straightforward, as can be seen in this fully functional code sample: Notification.requestPermission().then(function(permission){ if (permission === "granted") { new Notification("Shiny"); } }); 

▪ Later in the chapter, we will look at adding buttons, icons, and even making the notification vibrate the user’s phone to the Star Wars theme.

▪ The Push API The Push API allows your users to subscribe to push messages from your app and lets your server send messages to their browser at any time. These messages are handled by the service worker, which listens for them and can act on them even after your users have left your app.

▪ The most common way to “act on them” is to display a notification to the user.

▪ This exposes an extraordinary amount of power to your app. Once you can send messages to your user’s device at any time, you could potentially harass him with endless messages. You could even silently track his behavior by sending messages to the service worker every few seconds and then sending a response back to your server with some compromising data.

▪ To make sure the Push API isn’t misused like this, all push messages pass through a central messaging server. This central server is maintained by the browser vendor and keeps track of all of your users’ subscriptions for you.

▪ It ensures that push messages aren’t exploited and users aren’t spammed. It also takes care of the complexities of making sure messages are delivered even if the user was unreachable when you sent it.

▪ This middleman between you and your user — along with all the encryption needed to make sure only your server can send messages to your users — makes the learning curve a bit steeper. We will unpack this process into four steps which we will tackle one at a time.

▪ The first two steps are subscribing a user to push messages and saving the details of that subscription on your server — these only need to happen once per user.

▪ The final two steps — sending a message from your server and acting on it in the browser — happen every time you want to send a message to the user. This can be immediately after creating the subscription, or even a week later.

▪ First, your web page uses the Push API to call subscribe(). This calls the central messaging server which stores the details of this new subscription and returns those details to the page. Next, your page can send the subscription details to your server where they can be stored for future use.

▪ You will often want to save these subscription details in your database — perhaps in the same table or object store where you keep the rest of the users’ details.

▪ When you decide to send a message, your server takes the subscription details it previously stored (in step 2), and uses them to send the message to the messaging server. The messaging server then forwards this message to the user’s browser. Finally, the service worker registered in the user’s browser receives the message, reads its contents, and decides what to do with it.

▪ One final note: creating a new push subscription (step 1) requires a permission from the user. Luckily, this uses the same permission required for showing a notification, so you only need to ask once for a single permission to both show notifications and send push messages.

▪ Let’s put the pieces together and see the entire process for sending a push notification to the user: Your page requests permission from the user to show notifications, and the user grants it. Your page contacts the central messaging server, asking it to create a new subscription for this user. The messaging server returns a new subscription details object in response. Your page sends the subscription details to your server. Your server stores the subscription details for future use. Time passes. Seasons change. The need to send a notification arises. Your server uses the subscription details to send a message to the user through the messaging server. The messaging server forwards that message to the user’s browser. Your service worker’s push event listener receives the message. Your service worker shows a notification with the contents of the message. 

▪ Browser Support for Push Notifications Creating simple notifications from an active window, as shown earlier in this chapter, is possible in most modern desktop browsers. Receiving push messages and showing a notification based on it requires service worker, Notification API, and Push API support. At the time of writing, this is supported on Firefox, Chrome, Chrome for Android, Samsung Internet, and Opera, and is under development for Edge. Long before the API described in this chapter was finalized, Apple created its own API for sending notifications to Safari users. You can read more about it on Apple’s developer site.

▪ before we can show notifications to the user, we need to make sure we have the user’s permission first. You can check if the current site has the permission to create notifications by checking the value of Notification.permission. The permission attribute will equal "granted" if the current page has permission to show notifications, "default" if the user hasn’t decided yet, or "denied" if the user declined the permission request: if (Notification.permission === "granted") { console.log("Notification permission was granted"); }

▪ If you do not have permission yet, you can ask the user for it by calling the requestPermission() method of the Notification API: Notification.requestPermission();

▪ requestPermission() returns a promise that resolves when the user (or the browser) makes a choice about the permission. It is important to remember that this promise will always resolve, even if the user denied the permission, or the browser automatically blocked the permission request. That is why it’s important to always check the current state of the permission after asking for it and before attempting to create a notification:

▪ Notification.requestPermission().then(function(permission) { if (permission === "granted") { console.log("Notification permission granted"); } });

▪ The permission argument in the promise returned by requestPermission() can have any of the following values: granted The current page has permission to show notifications. This can mean one of two things: requestPermission() was called, a permission dialog was shown, and the user agreed to it. requestPermission() was called, but because the permission was already granted in the past, no permission dialog had to be shown. denied The current page does not have permission to show notifications. This can mean one of two things: requestPermission() was called, a permission dialog was shown, but the user declined the permission. requestPermission() was called, but because the permission was already denied in the past, no permission dialog was shown. default The current page does not have permission to show notifications. This can only mean one thing: requestPermission() was called, a permission dialog was shown, but the user closed it without making a decision. 

▪ Putting everything together, we get the following code: if (Notification.permission === "granted") { showNotification(); } else if (Notification.permission === "denied") { console.log("Can't show notification"); } else if (Notification.permission === "default") { Notification.requestPermission().then(function(permission) { if (permission === "granted") { showNotification(); } else if (Notification.permission === "denied") { console.log("Can't show notification"); } else if (Notification.permission === "default") { console.log("Can't show notification, but can ask for permission again."); } }); }

▪ While in many cases you will want to specifically check the current status of the permission using Notification.permission before deciding how to proceed (as shown in the preceding code), in others it may be enough to just call requestPermission() and trust the browser to not show the permission dialog if it isn’t necessary.

▪ This allows us to simplify the previous code example to look like this: Notification.requestPermission().then(function(permission) { if (permission === "granted") { showNotification(); } else if (Notification.permission === "denied") { console.log("Can't show notification"); } else if (Notification.permission === "default") { console.log("Can't show notification, but can ask for permission again."); } });

▪ The Same-origin Policy The user’s choice is saved according to the same-origin policy. In other words, once the user has granted the permission, you can create new notifications from any page on your app as long as it is on the same origin. Two web pages are said to be on the same origin if they share a URI scheme (e.g., HTTPS or HTTP), hostname (e.g., www.talater.com), and port number. For example, a permission granted on https://www.talater.com/annyang can be used on https://www.talater.com/upup but not on http://www.talater.com/annyang (which uses HTTP, while the permission was granted on HTTPS) or https://www.talater.com:8443/ (which uses a different port).

▪ Once you have the user’s permission, creating a notification is simply a matter of creating a new Notification object. Let’s give it a try: Notification.requestPermission().then(function(permission) { if (permission === "granted") { new Notification("Shiny"); } }); 

▪ Changing Your Notification Setting Permissions If you did not get a permission dialog, it might be because you previously denied or granted notifications for this site. Once you make a choice in the permission dialog, the browser remembers it and will not show another notification permission dialog in this origin. During development, you might want to reset this setting from time to time. In Chrome on the desktop, this can be done by clicking the icon to the left of your site’s URL in the location bar and changing the notifications settings. In Chrome for Android, you can find the same setting by opening the browser menu, choosing Settings, and then clicking Site settings.

▪ Unfortunately, the preceding code, which works great on the desktop, won’t work on mobile devices. To understand why, consider how a notification on mobile needs to behave. When your page creates a notification, it is rendered outside the browser — on the operating system level. 

▪ To create notifications that work both on desktop and mobile, you will need to create your notifications through a service worker.

▪ With just a small modification to the code, we can call showNotification() on the service worker registration object. This receives exactly the same parameters as the Notification object method: Notification.requestPermission().then(function(permission) { if (permission === "granted") { navigator.serviceWorker.ready.then(function(registration) { registration.showNotification("Shiny"); }); } });

▪ improve our notifications: navigator.serviceWorker.ready.then(function(registration) { registration.showNotification("Quick Poll", { body: "Are progressive web apps awesome?", icon: "/img/reservation-gih.jpg", badge: "/img/icon-hotel.png", tag: "awesome-notification", actions: [ {action: "confirm1", title: "Yes", icon: "/img/icon-confirm.png"}, {action: "confirm2", title: "Hell Yes", icon: "/img/icon-cal.png"} ], vibrate:[500,110,500,110,450,110,200,110,170,40,450,110,200,110,170,40,500] }); }); The updated code demonstrates how showNotification() can receive an optional second argument containing an options object.

▪ Here is the complete list of options you can use when creating notifications. These are supported by both methods — registration.showNotification() and new Notification(): body The main body of text in the notification. icon A URL to an image that will be displayed in the notification (the photo of the city shown in Figure 10-6). ￼ Figure 10-6. Getting fancy with mobile notifications badge A URL to an image that represents the app sending the notification, or a category of notifications sent by that app. For example, a messaging app may always use its logo as the badge of all notifications, or it may choose to use different icons to represent different notifications, such as an icon for a new message notification, and a different icon when the user’s name is mentioned. The badge may be displayed when there is no room to display the entire notification, or inside the notification itself (as can be seen in Figure 10-6 in the bottom-right corner of the icon). actions By passing an array of action objects, you can add up to two buttons to the notification, allowing the user to take actions straight from the notification. This can be useful to allow the user to launch your web app or even take quick actions straight from the notification without opening the app. For example, a new message notification in a messaging app could include a Like button and a Reply button. The Like button could work without opening the app, while the Reply button would open the messaging app to the appropriate screen. We will look more closely at actions later in “Listening for Push Events and Showing Notifications”. vibrate For devices that support vibration, you can customize the vibration pattern that will play to alert the user to this new notification. vibrate receives an array of integers, each representing the number of milliseconds to vibrate and pause. For example, [200,100,300] will vibrate for 200 ms, pause for 100 ms, and then vibrate for another 300 ms. The vibration settings in the previous code example will play “The Imperial March.” tag A unique identifier representing this notification. If this tag is equal to the tag of a notification that is currently showing, the new notification will silently replace the old notification. This can often be preferable to creating multiple notifications and annoying the user. For example, if the user has one unread message in our messaging app, we might want to contain the text of that message in the notification. If five more messages arrive before the notification is dismissed, updating the notification to say “You have 6 new messages” might be preferable to showing six separate notifications. The following code demonstrates creating a notification that gets silently updated every second with a new notification containing different text. This effectively creates a notification with a counter in it: navigator.serviceWorker.ready.then(function(registration) { var count = 1; var createNotification = function() { registration.showNotification("Counter", { body: count, tag: "counter-notification" }); count += 1; }; setInterval(createNotification, 1000); }); If you were to remove the tag, or change it at every iteration, the browser would create multiple notifications. renotify As we just saw, if you use the same tag to update an existing notification, the new notification will silently replace the old one. By setting renotify to true, you can force the device to draw the user’s attention to the updated notification (on mobile this is done by vibrating the phone again). data This can be used to attach any data that you would like to send along with the notification. Later in this chapter, we will see how you can react to notification events and access this data (see “Listening for Push Events and Showing Notifications”). dir The direction in which to display the text in the notification. By default, it adopts the browser’s language setting, but it can also be set to either force rtl (for right-to-left languages such as Arabic or Hebrew), or ltr (for left-to-right languages such as English and Portuguese). lang The primary language of the notification text. For example, en-US for American English or pt-BR for Brazilian Portuguese. noscreen A boolean specifying whether the device’s screen should be turned on by this notification. A value of true means the screen won’t be turned on. At the time of writing, this was not supported in any browser and uses the default value of false. silent A boolean specifying whether this notification should be made silently (i.e., without vibration or sound). At the time of writing, this was not supported in any browser and the default of false (not silent) is used. sound A URL for an audio file to play when the notification is created. At the time of writing, this was not supported in any browser.

▪ If the user grants us that permission, we will immediately show a notification letting her know that she will receive updates to any changes to her reservation.

▪ Add the following code to my-account.js, just above the addReservation() function definition: var showNewReservationNotification = function() { navigator.serviceWorker.ready.then(function(registration) { registration.showNotification("Reservation Received", { body: "Thank you for making a reservation with Gotham Imperial Hotel.\n"+ "You will receive a notification if there are any changes to "+ "the reservation.", icon: "/img/reservation-gih.jpg", badge: "/img/icon-hotel.png", tag: "new-reservation" }); }); }; var offerNotification = function() { if ("Notification" in window && "serviceWorker" in navigator) { Notification.requestPermission().then(function(permission){ if (permission === "granted") { showNewReservationNotification(); } }); } }; 

▪ But to really benefit our users, we will want to send them a notification after they have left our app. For this, we turn to the Push API.

▪ When subscribing a user to push messages, the subscription details object returned by the messaging server contains all the information needed to send an unlimited number of messages to your users. Any malicious entity that has access to the subscription details on your server, or any malicious script or add-on in the browser that reads it while the user is subscribing, could then potentially send as many messages as it wants to your users.

▪ To make sure only your server is allowed to send messages, the messaging server only accepts messages that are signed using a secret private key that you store on your server. To verify that messages were signed by the correct key, each private key has a corresponding public key. This public key is included in your script and is sent to the messaging server when it creates a new subscription. It is then stored in the messaging server along with the subscription details.

▪ This key is only used to verify that messages sent from your server to the messaging server were signed by the correct private key.

▪ in plain English: When you create your app, you generate a public and a private key. The private key is kept secret and never leaves your server. The public key is included in your script and is sent to the messaging server when creating a subscription. The messaging server stores the public key along with the rest of the subscription details. When your server wants to send a message, it signs it using the private key, and then sends it to the messaging server. The messaging server uses the public key to verify that the message was signed with the correct private key. If it was, it sends the message to the user. 

▪ Looking at these steps, you can see that before we can even begin to create subscriptions and send push messages, we will need to generate a public and private key pair.

▪ The keys used for signing and verifying push messages are called VAPID keys. In a creative leap not commonly associated with cryptographers, VAPID is an acronym for “Voluntary Application Server Identification for Web Push.”

▪ To keep things as simple as possible, we won’t delve into the details of the cryptography going on behind the scenes, the specifics of generating VAPID keys, or how to sign payloads. Instead, we will use one of the more commonly used web-push libraries to hide this complexity from us. This book uses the web-push library for Node.js, but you can find similar libraries for many other languages (see https://pwabook.com/webpushlibs).

▪ and enter the following code in it: var webpush = require("web-push"); console.log( webpush.generateVAPIDKeys() ); 

▪ For the Gotham Imperial Hotel, I have chosen to store both private and public keys in a file called push-keys.js inside the /server directory. You might also notice that I have added this file to the project’s .gitignore file. This means that when I commit any code, my private key doesn’t end up online.

▪ Generating a GCM key Unfortunately, the VAPID keys alone are not enough to send push messages to all browsers. Before the Web Push Protocol was finalized and VAPID was agreed upon, some browsers went ahead and implemented push messages in a nonstandardized way. Between versions 42 and 51, Chrome used Google Cloud Messaging to deliver push messages, and both Opera and Samsung Browser adopted the same approach. In order for your push notifications to also work in older versions of these browsers, you will need to generate GCM API keys in addition to the VAPID keys.

▪ You can obtain GCM API keys (also known as FCM API keys) from Google through the Firebase Cloud Messaging interface (previously known as Google Cloud Messaging): Visit the Firebase console at https://pwabook.com/firebaseconsole. Log in with a Google Account. Create a new project. Once you are on your project page, click the Settings icon next to the project name and go to Project settings. Inside Project settings, choose Cloud messaging. You should now see a Project credentials area and within it a link to Generate Key. Click Generate Key, and you will be rewarded with your very own GCM server key and Sender ID (Figure 10-9). 

▪ Your updated push-keys.js file should now look something like this (but with different values): module.exports = { GCMAPIKey: "yBtCa6LClbdSb5dsPCuKM-hqx9WmOstWnvoFoh4", subject: "mailto:tal@talater.com", publicKey: "yteswBFEX-U7XsteR7x0o3nqygyR", privateKey: "IuKbrkM4inNv2MzlzVRDV4YRw4N65N" }; 

▪ Edit the site’s manifest.json file in the /public directory, and add a new setting to it with a key called gcm_sender_id, and a value equal to your GCM sender ID: { "short_name": "Gotham Imperial", "name": "Gotham Imperial Hotel", "description": "Book your next stay, manage reservations, and explore Gotham", "start_url": "/my-account?utm_source=pwa", "display": "fullscreen", "icons": [ { "src": "/img/app-icon-192.png", "type": "image/png", "sizes": "192x192" }, { "src": "/img/app-icon-512.png", "type": "image/png", "sizes": "512x512" } ], "theme_color": "#242424", "background_color": "#242424", "gcm_sender_id": "3217212971" } 

▪ We can use the service worker’s registration object to get the PushManager interface. This interface includes a number of useful methods for getting an existing subscription (getSubscription()), checking if the current page has permission to subscribe to push messages (permissionState()), and most importantly a subscribe() method for subscribing the user to push messages. All of these methods return promises: var subscribeOptions = { userVisibleOnly: true }; navigator.serviceWorker.ready.then(function(registration) { return registration.pushManager.subscribe(subscribeOptions); }).then(function(subscription) { console.log(subscription); }); 

▪ The code begins by defining a subscription options object containing a single setting — userVisibleOnly. This setting means that all push messages must be made visible to the user (i.e., you agree to generate a notification for every push message). Since accepting messages in the service worker without letting the user know might endanger the user’s privacy, no browser currently supports setting userVisibleOnly to false. If you try to create a subscription without setting this value to true, the messaging server will return an error.

▪ Next, the code gets the service worker registration object, then uses it to call the pushManager’s subscribe() method (passing it the subscription options object). This method returns a promise that resolves to an object with the subscription details sent from the messaging server.

▪ Since this code does not include the VAPID key, it will only subscribe users in browsers that support messaging through GCM, and only if we include the GCM sender ID in our manifest.json file.

▪ Let’s see what we need to do so that it works with VAPID if it is available, and GCM if it isn’t: var urlBase64ToUint8Array = function(base64String) { var padding = "=".repeat((4 - base64String.length % 4) % 4); var base64 = (base64String + padding).replace(/\-/g, "+").replace(/_/g, "/"); var rawData = window.atob(base64); var outputArray = new Uint8Array(rawData.length); for (var i = 0; i < rawData.length; ++i) { outputArray[i] = rawData.charCodeAt(i); } return outputArray; }; var subscribeOptions = { userVisibleOnly: true, applicationServerKey: urlBase64ToUint8Array("yteswBFEX-U7XsteR7x0o3nqygyR") }; navigator.serviceWorker.ready.then(function(registration) { return registration.pushManager.subscribe(subscribeOptions); }).then(function(subscription) { console.log(subscription); });

▪ We begin by modifying the subscription options object (subscribeOptions) to receive a second setting called applicationServerKey that will contain your public VAPID key (replace the random string in the code with your public key). Unfortunately, the pushManager won’t accept the VAPID key as is, and we need to convert it to a format it can understand. This conversion is up to the urlBase64ToUint8Array() function, which you can see at the top of the code. It converts the VAPID public key to a Uint8Array, which is the format pushManager requires. Unless you care deeply about cryptography, you don’t need to delve into the specifics of how it works. Just know that you call it with a string containing your VAPID public key, and it will return an array that pushManager understands.

▪ The only addition is a second attribute in the settings object containing our VAPID public key.

▪ That’s it! The user is now subscribed to push messages, and you have the details of that subscription in the subscription variable.

▪ At this point, you can send the subscription object to your server using an Ajax or fetch call and save it for future use.

▪ var offerNotification = function() { if ("Notification" in window && "PushManager" in window && "serviceWorker" in navigator) { subscribeUserToNotifications(); } };

▪ We have made two changes to offerNotification(). First, we added another condition to our if statement to make sure PushManager is supported by this browser. Next, we extracted all of the logic for requesting notification permission and for subscribing the user to push events to subscribeUserToNotifications(), a new function which we will write next.

▪ Finally, add the following code above the offerNotification() function: var urlBase64ToUint8Array = function(base64String) { var padding = "=".repeat((4 - base64String.length % 4) % 4); var base64 = (base64String + padding).replace(/\-/g, "+").replace(/_/g, "/"); var rawData = window.atob(base64); var outputArray = new Uint8Array(rawData.length); for (var i = 0; i < rawData.length; ++i) { outputArray[i] = rawData.charCodeAt(i); } return outputArray; }; var subscribeUserToNotifications = function() { Notification.requestPermission().then(function(permission){ if (permission === "granted") { var subscribeOptions = { userVisibleOnly: true, applicationServerKey: urlBase64ToUint8Array( "yteswBFEX-U7XsteR7x0o3nqygyR" // Replace with your public key ) }; navigator.serviceWorker.ready.then(function(registration) { return registration.pushManager.subscribe(subscribeOptions); }).then(function(subscription) { var fetchOptions = { method: "post", headers: new Headers({ "Content-Type": "application/json" }), body: JSON.stringify(subscription) }; return fetch("/add-subscription", fetchOptions); }); } }); }; 

▪ It begins with a call to Notification.requestPermission() that asks the user for permission and returns a promise. When that promise resolves, we first make sure the permission was granted before we do anything else. Next, we define our subscription options using our public VAPID key as applicationServerKey and setting userVisibleOnly to true. Make sure to use your own public VAPID key, which you can find in server/push-keys.js. Next, we use navigator.serviceWorker.ready to get our service worker registration, and use it to call subscribe() on the pushManager. By the time this promise resolves and the next then block runs, our user has granted us the permission, and we have successfully subscribed her to push messages.

▪ Let’s go through the entire process one more time: We make sure the browser supports service workers, the Notification API, and the Push API. We request permission for showing notifications, and continue only once it is granted. We create a new subscription with the messaging server using our VAPID public key (after converting it). Once we receive the subscription details back, we send them to our own server for safekeeping. 

▪ We now have everything we need to send a push message from our server to our users: A VAPID private and public key Used to sign messages and create subscriptions in browsers supporting VAPID. A GCM API server key and sender ID Fallbacks used to sign messages and create subscriptions in browsers that don’t yet support VAPID.

▪ A subscription details object This object was received from the messaging server and contains the details needed to send messages to a specific user subscription. These details include a public key, an authentication secret, and an endpoint — which is literally just a URL to send the message to.

▪ This can get complicated quickly as it involves setting a number of HTTP headers on the request, such as an authorization header using JWT (JSON Web Token). Luckily, we can once again bypass the complexities of encryption using the web-push library, which makes sending messages a (relative) breeze: var webpush = require("web-push"); var pushKeys = { GCMAPIKey: "yBtCa6LClbdSb5dsPCuKM-hqx9WmOstWnvoFoh4", subject: "mailto:tal@talater.com", publicKey: "yteswBFEX-U7XsteR7x0o3nqygyR", privateKey: "IuKbrkM4inNv2MzlzVRDV4YRw4N65N" }; var subscription = { endpoint: "https://fcm.googleapis.com/fcm/send/dQbqPBPWo_A:AHH91bHyhyrG9", keys: { p256dh: "BEJ_yK1xAC8DFrbXjiRKGVxCh8c8FImUyrNbm8rcVVIvDT3an18ab7011Jw=", auth: "o-hRay472334PuqppKq-lg==" } }; var message = "show-notification"; webpush.setGCMAPIKey(pushKeys.GCMAPIKey); webpush.setVapidDetails( pushKeys.subject, pushKeys.publicKey, pushKeys.privateKey ); webpush.sendNotification(subscription, message).then(function() { console.log("Message sent"); }).catch(function() { console.log("Message failed"); });

▪ Within subscriptions.js, you will see the following code: var db = require("./db.js"); var webpush = require("web-push"); var pushKeys = require("./push-keys.js"); var notify = function(pushPayload) { pushPayload = JSON.stringify(pushPayload); webpush.setGCMAPIKey(pushKeys.GCMAPIKey); webpush.setVapidDetails( pushKeys.subject, pushKeys.publicKey, pushKeys.privateKey ); var subscriptions = db.get("subscriptions").value(); subscriptions.forEach(function(subscription) { webpush.sendNotification(subscription, pushPayload).then(function() { console.log("Notification sent"); }).catch(function() { console.log("Notification failed"); }); }); };

▪ This notify() function is later called from reservations.js to send a message when a reservation is confirmed: subscriptions.notify({ type: "reservation-confirmation", reservation: reservation }); 

▪ You can see that subscriptions.js uses a local database (defined in /server/db.js) and the web-push library. It also uses an external file called push-keys.js where the keys needed to send push messages are stored (the details of how we generated this file are covered in “Generating Public and Private VAPID Keys”). You will also notice that it uses JSON.stringify() to turn the message it receives into a string. This makes sure we can pass an object as the message, as can be seen in the previous example code.

▪ As we have seen, both the Push API and the Notification API require the same permission. This means that once a push message is received in the service worker, we know we have everything we need to show a notification, and our code can be as simple as the following example: self.addEventListener("push", function() { self.registration.showNotification("Push message received"); }); 

▪ When a push message arrives at the browser, a push event is triggered in the service worker. Even if the user hasn’t visited our site in weeks, the service worker will spring to action as soon as the message arrives; giving our app the chance to re-engage users with a notification (Figure 10-10).

▪ In the push event listener, you can access the contents of the push message through the data attribute of the PushEvent object (which is passed to the event listener as its first argument): self.addEventListener("push", function(event) { var message = event.data.text(); self.registration.showNotification("Push message received", { body: message }); });

▪ As you can see in Figure 10-11, the PushEvent data attribute has a text() method that returns the message content as a simple string. It also has a json() method that will parse the message content as JSON, and return it as an object (Figure 10-12): ￼ Figure 10-11. A notification shown on push event showing event.data.text() self.addEventListener("push", function(event) { var message = event.data.json(); self.registration.showNotification("Push message received", { body: "Reservation for "+message.reservation.arrivalDate+" has been confirmed." }); });

▪ Edit serviceworker.js, adding the following code to the end of that file: self.addEventListener("push", function(event) { var data = event.data.json(); if (data.type === "reservation-confirmation") { var reservation = data.reservation; event.waitUntil( updateInObjectStore( "reservations", reservation.id, reservation) .then(function() { return self.registration.showNotification("Reservation Confirmed", { body: "Reservation for "+reservation.arrivalDate+" has been confirmed.", icon: "/img/reservation-gih.jpg", badge: "/img/icon-hotel.png", tag: "reservation-confirmation-"+reservation.id, actions: [ { action: "details", title: "Show reservations", icon: "/img/icon-cal.png" }, { action: "confirm", title: "OK", icon: "/img/icon-confirm.png" }, ], vibrate: [500,110,500,110,450,110,200,110,170,40,450,110,200,110,170,40,500] }); }) ); } });

▪ Our new event listener waits patiently for push events. When such a push message arrives at the service worker, the event listener will retrieve the data contained within the PushEvent and decide how to act based on the type attribute it contains. If that type equals "reservation-confirmation", our code knows that it needs to update the reservation in IndexedDB using updateInObjectStore() and display a notification using self.registration.showNotification() (Figure 10-13).

▪ A quick reminder: the message sent from the Gotham Imperial Hotel server has the following structure: { "type": "reservation-confirmation", "reservation": { "id": "79212418", "arrivalDate": "November 5th 2022", "nights": "3", "guests": "2", "status": "Confirmed", "bookedOn": "2016-10-31T15:40:41+02:00", "price": 636 } } 

▪ The choice to structure our push message data as an object with a type and a reservation details object was completely arbitrary. We could just as well have structured it without a type. We could even have made the entire message a simple string containing the final text of the notification, or a string such as "reservation-confirmation,79212418" which we would then parse in the service worker and get the reservation details for that ID from IndexedDB.

▪ First, you might notice that the push event listener code uses event.waitUntil() to make sure the event waits for both the IndexedDB update and the notification code to complete successfully before it considers the original push event complete. As we first saw in Chapter 3, waitUntil() extends the life of an event until the promise passed to it is resolved. In this case, we are passing it updateInObjectStore(), which returns a promise; this promise is then handed off to showNotification(), which also returns a promise.

▪ Since notifications are a UI element that renders outside the browser (at the operating-system level), and a user might act upon them hours after they were created (e.g., think of a notification that pops up in the middle of the night), it wouldn’t make sense to keep a callback or a promise waiting for an action to happen. Instead, actions taken on a notification are dispatched to the service worker as separate events. By listening to these events, we can take actions based on how the user interacted with them (dismissed them or clicked one of the buttons).

▪ Edit serviceworker.js, adding the following code to the end of that file: self.addEventListener("notificationclick", function(event) { event.notification.close(); if (event.action === "details") { event.waitUntil( self.clients.matchAll().then(function(activeClients) { if (activeClients.length > 0) { activeClients[0].navigate("http://localhost:8443/my-account"); } else { self.clients.openWindow("http://localhost:8443/my-account"); } }) ); } });

▪ This code will listen for notificationclick events. These events are dispatched every time any notification created by your app is clicked. Our event listener begins by calling event.notification.close() to dismiss the notification. Once a user has interacted with our notification, there is no point in keeping it around. This also ensures a unified experience across devices, operating systems, and browsers — some of which dismiss notifications automatically as soon as they are clicked, while some only do it when you tell them to.

▪ If the action the user clicked is details, we want to navigate to the My Account page of the app. At this point, we could simply open a new window by calling self.clients.openWindow(url), but as a way to offer a better user experience, we first check if there already is an active window showing our app. If there is, we will navigate to the My Account page on tha

▪ Here is one way we could use the notification’s tag to determine how to proceed: self.addEventListener("notificationclick", function(event) { if (event.notification.tag === "event-announcement") { self.clients.openWindow("http://localhost:8443/events"); } else if (event.notification.tag === "confirmation") { self.clients.openWindow("http://localhost:8443/my-account"); } });

▪ Another way would be to pass data along with each notification: self.addEventListener("push", function(event) { var data = event.data.json(); var reservation = data.reservation; self.registration.showNotification("Reservation Confirmed", { tag: "reservation-confirmation", data: reservation }); }); self.addEventListener("notificationclick", function(event) { event.notification.close(); if (event.notification.tag === "reservation-confirmation") { var reservation = event.notification.data; self.registration.showNotification("Notification clicked", { body: "Notification tag: "+event.notification.tag+"\n"+ "Notification reservation date: "+reservation.arrivalDate }); } }); 

▪ Progressive web apps present a true paradigm shift in the way the web works. They provide an experience that is beyond users’ expectations of the web. Users do not expect web apps to continue working when they are offline. Yet progressive web apps over-deliver on those expectations. Users do not expect web apps to send them updates when new information relevant to them is available. Yet progressive web apps over-deliver on those expectations too. Users do not expect full-screen experiences, launched from the homescreen, that look and behave just like native apps. Yet once again, progressive web apps over-deliver. On the other hand, when a user visits a web app, she expects the content that loads to be up to date. But a user who does not realize she is offline may also not realize that content shown on the screen may be hours or even days old. To her, progressive web apps seem to be under-delivering on the experience she expects.

▪ While the gap between the abilities of the web and the native app is quickly closing, the gap between the modern progressive web app’s abilities and users’ expectations and perception is still very wide. In the long run, as users use progressive web apps more and more, this gap between expectation and reality will shrink and disappear. But until that happens, this dissonance between users’ expectations and the modern progressive web app presents us with a new challenge. One that we can solve by communicating properly with our users.

▪ In many ways, as progressive web apps catch up with native apps in terms of capabilities, native’s edge over the web boils down to a matter of trust. Users trust their apps to work, no matter where they are, and won’t think twice before launching a messaging app while on a plane. Yet those same users won’t open their web browser after takeoff. Users trust their apps to keep them up to date with notifications, yet will visit a site over and over to check for updates.

▪ As the difference between the web and native becomes more about trust, it becomes more and more important for us to communicate a feeling of trust in our web apps. When a user loses connectivity while using your app, reinforce his trust by communicating to him that his work will not be lost. When your app is fully cached, consider letting your user know that she can now use your app while offline. Before asking for permission to send push notifications, let your user know exactly how he will benefit from these notifications and what they may include. Remember, trust is not just about your progressive web app’s capabilities, but also about letting your users know you won’t abuse those capabilities.

▪ We can accomplish this in two steps: In the service worker, we will detect when the user is offline and viewing cached content, and communicate that to the page. In the page, we will listen for that communication and inform the user. 

▪ This request is also a good place to detect when to communicate the message to the user, because the events data is only loaded after the page’s DOMContentLoaded event fired. If we were to try and communicate to the page from the request to the page itself (the HTML), the page might not be ready to receive our message and display the notification. In this case, we would have to modify the service worker code to wait for the page to load before sending the message.

▪ We begin coding in serviceworker.js by modifying the part of the fetch event listener that handles requests to /events.json: } else if (requestURL.pathname === "/events.json") { event.respondWith( caches.open(CACHE_NAME).then(function(cache) { return fetch(event.request).then(function(networkResponse) { cache.put(event.request, networkResponse.clone()); return networkResponse; }).catch(function() { self.clients.get(event.clientId).then(function(client) { client.postMessage("events-returned-from-cache"); }); return caches.match(event.request); }); }) ); }

▪ The only additions are the first three lines of the catch statement. When a network request to events.json fails, and the catch statement is executed, our code will post a message to the client that requested the events file. The content of the message (its data) is a simple string I have chosen for this type of event — events-returned-from-cache.

▪ We can add the following event listener to app.js: if ("serviceWorker" in navigator) { navigator.serviceWorker.addEventListener("message", function (event) { if (event.data === "events-returned-from-cache") { alert( "You are currently offline. The content of this page may be out of date" ); } }); }

▪ Progressive UI KITT is a small library that handles both the communication between the service worker and the page, as well as rendering the notifications to the user. It can handle sending notifications to one or more windows at a time, can include buttons in the notifications, and can easily be customized with your visual style or any of the visual themes that come with it.

▪ Before we begin, let’s make sure Progressive UI KITT and its stylesheet are both cached in our service worker so that we can use them even when the user is offline. In serviceworker.js, add the following files to the CACHED_URLS array: "/js/vendor/progressive-ui-kitt/themes/flat.css", "/js/vendor/progressive-ui-kitt/progressive-ui-kitt.js"

▪ Next, on the top of serviceworker.js, add the following line to import Progressive UI KITT’s service worker helper: importScripts("/js/vendor/progressive-ui-kitt/progressive-ui-kitt-sw-helper.js");

▪ Caching Complete Once a service worker has finished its installation and cached all assets needed to display the app, you might want to show the user a message letting her know the site will now work offline: self.addEventListener("install", function(event) { event.waitUntil( caches.open(CACHE_NAME).then(function(cache) { return cache.addAll(CACHED_URLS).then(function() { ProgressiveKITT.addMessage( "Caching complete! Future visits will work offline.", {hideAfter: 2000} ); return Promise.resolve(); }); }) ); });

▪ we can assure our users that the action they tried to take will be done as soon as they regain connectivity: self.addEventListener("sync", function(event) { event.waitUntil( saveChanges().catch(function() { ProgressiveKITT.addAlert( "You are currently offline, but your reservation has been saved." ); }) ); });

▪ Once a user has subscribed for push notifications, you can inform him that he will receive updates as they become available: navigator.serviceWorker.ready.then(function(registration) { return registration.pushManager.subscribe(subscribeOptions); }).then(function() { ProgressiveKITT.addMessage( "Thank you. You will be notified of any changes to your reservation.", {hideAfter: 3000} ); });

▪ In Chapter 10, we let our users sign up for push notifications as a way to inform and re-engage them. But the user experience of asking for the user’s permission was lacking. We simply opened the permission dialog without providing the user with any context or explaining how the notifications will be used. Unfortunately, we often see this kind of user experience done so poorly, and with such self-destructive results, that it is worth taking the time to consider a better alternative.

▪ Remember, you only get one chance to ask — if you ask before the user sees the value in it, you lose that chance forever.

▪ Instead of immediately triggering the native permission request, consider creating your own UI for letting the user trigger it herself. Within this UI, you can control the message — a message that should make it clear to the user what the notifications are and the type of messages he can expect. He can then choose to enable notifications, in which case you can call Notification.requestPermission(), or he may choose to decline it. Yes, this adds an extra step to the process and requires two clicks from the user to give the permission, but it almost always results in more conversions.

▪ Creating your own UI for offering notifications has two more benefits: If the user declines your offer, you can always try to offer it again in the future. If he declines the browser’s requestPermission() dialog, you can’t. You can use the same interface for subscribing to notifications to later let the user unsubscribe from those notifications. 

▪ When crafting your message, don’t just offer the feature (e.g., “Enable push notifications”). Instead, describe the benefit to the user (e.g., “Get a notification when your order ships”). Which of the messages shown in Figure 11-3 do you think will result in more conversions?

▪ Modify the offerNotification() function in my-account.js to match the following: var offerNotification = function() { if ("Notification" in window && "PushManager" in window && "serviceWorker" in navigator) { if (Notification.permission !== "granted") { showNotificationOffer(); } else { subscribeUserToNotifications(); } } };

▪ While the old code always called subscribeUserToNotifications() (which asks for permission, if it is needed, and then creates a subscription, if it is needed), we are now only calling it if the user has already granted the notification permission. If not, we do not want to immediately trigger the native permission dialog, but use our own. We call showNotificationOffer() which turns on the display of a div (#offer-notification) containing a link to turn on notifications.

▪ At the bottom of my-account.js, add the following code to make sure when the link offering notifications inside that div is clicked, subscribeUserToNotifications() will be called: $("#offer-notification a").click(function(event) { event.preventDefault(); hideNotificationOffer(); subscribeUserToNotifications(); });

▪ Your app can automatically disable or hide buttons for features that are unavailable when offline. It can even modify those buttons to help the user understand what will happen (e.g., modifying a Send button to a “Send later” button). Consider a progressive web app with a large amount of dynamic content that is cached on demand as you visit it. A user visiting this app while offline may only have some of its content available to her. How would you reflect this visually to the user?

▪ One great example comes from Housing.com, one of India’s top real estate platforms. When visitors visit Housing.com while offline, listings and cities that haven’t been cached are grayed out and cannot be selected, while those that have been cached are displayed normally. The distinction is subtle, yet clear

▪ Consider how your app’s look differs when launched in full-screen versus how it looks when viewed in a web browser. Will the lack of a location bar affect your branding? Do you have tech-savvy users who are used to copy-pasting URLs from your site? Will the lack of a visible security indication next to your HTTPS URL affect conversions? One possible way to tackle this is to add extra UI elements that can provide similar functionality. These UI elements can be made visible only when the display is set to full-screen or standalone using CSS media queries: @media all and (display-mode: fullscreen) { #back-button { display: block; } }

▪ Can your travel app work even when your users are in airplane mode? That’s a serious edge over the competition. Make sure your users know. Will getting more users to sign up for push notifications help your business re-engage more users? Make sure you properly communicate how they work and their benefits to your users.

▪ Another prompt you might want to improve on, is the web app install banner — specifically, its timing. The timing of the install prompt is completely up to the browser. Unfortunately, the browser can only guess when the best time to show the install prompt is — but it doesn’t know your app or your audience like you do

▪ Luckily, the browser gives you some control over this. While you can’t control when to initiate the install prompt, you can listen for when the browser decides to show it, intercept that event, and delay it to a later time (or cancel it completely):

▪ window.addEventListener("beforeinstallprompt", function(promptEvent) { promptEvent.preventDefault(); setTimeout(function() { promptEvent.prompt(); }, 2000); });

▪ The code listens for the beforeinstallprompt event, and when it is triggered calls preventDefault() on that event to stop the install prompt from showing. It then waits two seconds and manually initiates the display of the install prompt using the event’s prompt() method.

▪ One interesting implementation of this comes from Flipkart, one of India’s largest ecommerce retailers. The Flipkart home page contains a small + icon on the right side of the header (as seen on the left side of Figure 11-5). This icon wiggles from time to time to entice the user to try it. Once clicked, Flipkart displays an overlay instructing the user how to add a homescreen shortcut to Flipkart (shown in the center of Figure 11-5). If, however, this link is clicked after the browser tries to show an app install banner — which Flipkart blocks and stores the reference to — the browser’s app install banner is shown instead (shown on the right side of Figure 11-5).

▪ Just like with push notifications — controlling the timing and messaging is key to delivering a great experience to your users.

▪ RAIL is not a new technology, nor is it a new tool. It is simply a set of guidelines that help us understand what makes an app (native, progressive, or plain old website) feel right. And like so many great things in tech, RAIL’s name is an acronym that reminds us of the guidelines to keep in mind: response, animation, idle, and load:

▪ Response When the user takes any action, such as clicking any element on the screen, we want to respond in under 0.1 seconds. Can you show the information the user requested in that time — amazing! If not, can you begin to transition the screen toward the result the user asked for (even if it doesn’t include the actual data yet)?2 If you can’t do that, can you at least show some indication that the user’s action was detected and something is happening? This could be as simple as showing a loading indicator. As long as you can show some kind of response to the user’s action in under 100 ms, it will feel like an instant response. Strive to provide the feeling of an app that responds instantaneously to the user. Don’t leave the user wondering if she clicked the right thing or whether she should click again. Remember Newton’s paraphrased third law: for every action, there should be an instant reaction. Don’t mess with Isaac.

▪ Animation For an animation to look and feel smooth to the human eye, it needs to update at least 60 times a second. Achieving this 60 frames per second holy grail means updating the screen every 16.66 ms (1,000 / 60). And since the browser also needs some time to paint new frames to the screen, realistically you only get about 10 to 12 ms for each frame. Remember that when we talk about animation, we are also referring to how the page looks like when the user is scrolling. Having a page start to stutter when the user is scrolling is often worse than any other delays in your animations.

▪ Idle Defer nonessential work to idle time. Nonessential means anything that isn’t part of the response, animation, or load. Is the user scrolling through an endless list of items? Make sure loading and rendering the next items does not cause scrolling to freeze or look janky. Do you need to download and cache some assets for the user’s next visit? Make sure it does not slow down his current visit.

▪ Load When a user performs an action such as requesting a page on your site, aim to show the results of that action in one second or less. Ambitious? Perhaps. Possible? With service workers, CacheStorage, IndexedDB and the rest of the modern toolkit — definitely. Remember, you don’t have to load your entire app in one second. You just need to give the user the perception that the app has loaded. Sometimes just loading the content shown above the fold and deferring the rest to idle time can help you achieve this (Figure 11-6).

▪ The guiding principles of RAIL: Show some kind of response to any user action in 100 ms or less. Make sure your animations draw to the screen every 16 ms or less. Perform work when the page is idle, and in chunks of no more than 50 ms. Load and display what the user requests in under 1,000 ms. 

▪ While some things can be added to your app without much consideration of how they affect the user’s experience, others must be carefully considered before they are added. Caching static assets and always serving them from the cache is a no-brainer, but if your plan for adding push notifications simply involves adding some code to ask for permission as soon as the user hits the home page, you can expect an interesting email from management involving the words funnel, conversions, and KPIs.

▪ RAIL was coined and defined by Paul Irish and Paul Lewis https://pwabook.com/railintro

▪ This will not be a deep dive into any of these technologies, some of which are still being finalized, but a short introduction with some pointers on where to go to learn more.

▪ App stores have solved a part of this problem for developers looking to charge for apps or subscriptions. They offer a trusted, common user experience for one-click purchases. The Payment Request API brings the same experience to the web. Its goal is nothing less than eliminating long, cumbersome checkout forms.

▪ For developers, the Payment Request API offers a dramatically simplified way to integrate payments into their websites:

▪ The ability to easily accept payments for apps and subscriptions was perhaps the last edge native apps held over the web. With the Payment Request API offering a more elegant way to pay for anything, the web takes the lead again.

▪ To solve this issue, a new standard called Credential Management API has been developed. The Credential Management API lets developers simplify the user experience significantly. It allows users to sign in with just one click, signs them in automatically when their session expires, and even remembers which federated account (e.g., Facebook Connect, Google Account, etc.) they used to sign in (Figure 12-2). Credentials are stored locally in the browser and can even be synced across devices in some browsers.

▪ A common workflow would look something like this: The user clicks a sign-in button, and the site uses the Credential Management API to show a native account chooser UI. If the user successfully signs in, the site uses the Credential Management API to store the credential information for future use. If a user has signed in in the past and the session expired, the site signs the user back in automatically.

▪ These days, however, there is a standardized API for doing speech recognition in the browser. An API that provides an easy-to-use interface for us as web developers while leaving the heavy lifting up to the browser: var recognition = new SpeechRecognition(); recognition.onresult = function(event) { console.log("User said: ", event.results[event.resultIndex][0]); }; recognition.start();

▪ Since the actual speech recognition takes a lot of computing resources, only a few browsers have implemented this API so far. At the time of writing, speech recognition works beautifully in Google Chrome and Chrome for Mobile, and is soon to be available in Firefox.

▪ For speech recognition in browsers that do not yet support this API, you can use WebRTC to access the microphone and perform the speech recognition in the cloud using Microsoft’s Bing Speech API or Google’s Cloud Speech API.

▪ Two new APIs that are under development aim to make sharing content, links, and media much easier: the Web Share API and the Web Share Target API. These two APIs are essentially two sides of the same coin. Today, when users want to share something they found online, they have two options: either using a share button built into the browser’s UI (if one exists) or using the share buttons on the site — buttons that are specific to the web services chosen by the site (e.g., Like buttons, Tweet buttons, Google +1 buttons, etc.). The Web Share API levels the playing field by allowing the site to add a generic share button that will trigger the device’s native share interface — an interface populated by the apps the user has installed on his device:

▪ navigator.share({title: "Gotham Imperial", url: window.location.href});

▪ On the other side of the coin is the Web Share Target API, allowing web apps to register themselves so they can handle share events, just like any native app can. Registering an app as a share target is done via the web app manifest: { "short_name": "ImperialApp", "name": "Gotham Imperial Hotel", "supports_share": true }

▪ At this point, the app’s service worker can respond to share events, and handle the actual sharing: navigator.actions.addEventListener("share", function (event) { var url = event.data.url; var title = event.data.title; var text = event.data.text; myShareFunction(url, title, text); });

▪ The Media Session API lets you set the metadata that will be shown when media plays (and update it when the next track begins playing), including title, artist, album, and artwork. It also lets you set handlers that will be called when users click the play, pause, previous, next, or seeking controls (Figure 12-5): navigator.mediaSession.metadata = new MediaMetadata({ title: "New Year's Mix", artist: "Gotham Imperial Hotel", album: "Gotham 2017", artwork: [{ src: "newyearmix.jpg" }] }); navigator.mediaSession.setActionHandler("play", function() {}); navigator.mediaSession.setActionHandler("pause", function() {}); navigator.mediaSession.setActionHandler("seekbackward", function() {}); navigator.mediaSession.setActionHandler("seekforward", function() {}); navigator.mediaSession.setActionHandler("previoustrack", function() {}); navigator.mediaSession.setActionHandler("nexttrack", function() {}); 

▪ The web has always been about democratizing access to information and leveling the playing field — a great equalizer. But the mobile app ecosystem became anything but that. It has become overly saturated, regulated, and heavily skewed toward developers with deep pockets. But the wheel always keeps turning, and now the web is coming back to the forefront. With progressive web apps, users no longer have to install dozens of apps just to access data they need once. They no longer need to compromise on their experience if they choose not to install a native app. They no longer need to undergo long installation funnels and grant an endless list of permissions to each app. They can enjoy rich experiences that are fast loading, offline accessible, always available, and always reliable — regardless of where they are. With progressive web apps, developers no longer need to choose between bowing to the rules of the various app stores or compromising on the user’s experience. They no longer need deep pockets to stay competitive within the limited “top 10 apps” lists of the app stores. They no longer need to spend weeks and months of development, only to find out that their work was rejected by the stores for unknown reasons. They no longer need to maintain an iOS app, an Android App, and a web app.

▪ If not, you are welcome to visit the “I Don’t Want Your F***ing App” Tumblr page.

▪ In 2015, Google decided to run an experiment to answer this very question. When Google released the results of its experiments with full-page interstitials, the answer was pretty clear:1 Only 9% of users presented with a full-page interstitial clicked the “Get App” button (remember, this is just the first step in the installation funnel). 69% of users immediately abandoned the page as soon as the interstitial opened. These users neither went to the app store nor continued to the website that was just a click away. 

▪ After seeing these numbers, Google decided to run an experiment and see how replacing the interstitial with a small, unobtrusive app banner would affect actual product usage. The results were surprising: 1-day active users on the mobile website increased by 17%. Native app installs went down just 2%. 

▪ Based on this, and other experiments, Google decided to battle the door slam. In April 2015, Google announced that sites using full-page interstitials to push a native app would no longer receive a boost in ranking given to other mobile-friendly sites. This essentially means a penalty in the search results for sites using full-page door slam ads. In August 2016, Google further enforced this with additional rank penalties on all other forms of interstitial pop-ups. 1 Google Webmaster Central Blog, “Google+: A case study on App Download Interstitials”, July 23, 2015.

▪ only allowing no-cors requests, that server can ensure third-party sites are free to read data from it, but are limited in their ability to modify the requests: if (requestURL.href === googleMapsAPIJS) { event.respondWith( fetch( googleMapsAPIJS+"&"+Date.now(), { mode: "no-cors", cache: "no-store" } ).catch(function() { return caches.match("/js/offline-map.js"); }) ); }
