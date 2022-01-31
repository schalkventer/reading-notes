Web Workers: Multithreaded Programs in JavaScript
Ido Greeb

---

▪ Web Workers is a powerful feature of HTML5 that hasn’t received very much attention.

▪ It provides an API that allows you to run JavaScript in a separate thread that doesn’t interfere with the user interface of your web application. This JavaScript runs in parallel with the main renderer and any of your user interface scripts on it.

▪ This allows long and “processing-heavy” tasks to be executed without making the page unresponsive.

▪ Like threads in other technologies, Web Workers are relatively heavyweight. You don’t want to use them in large numbers, as each one consumes significant system resources. Web Workers are expected to handle long tasks that rely on constrained resources (e.g., CPU, network bandwidth, etc.). They have a high startup cost and a high instance of memory cost.

▪ Workers also work in mobile Safari 5+, and will be especially useful because the new iPhone 4GS has a multi-core processor.

▪ The next three chapters cover the different kinds of Web Workers (dedicated, shared, and inline), showing how to use each one of them and when it will be best to choose one over the other.

▪ Finally, because Web Workers are also used outside of a browser, you’ll see how to apply them within the server-side Node environment.

▪ Modern web applications would often run better if there was a way to perform heavy calculations in the background instead of making the user interface wait for them to complete.

▪ The Web Workers specification[1] defines an API for running computationally intensive code in a thread other than the web application user interface.

▪ Long tasks can run without affecting your interface’s memory and CPU footprint because the Worker will live in its own thread.

▪ Multi-threaded programing is a complicated subject well stocked with complex algorithms and theoretical discussion. You can find other languages (e.g., Java) that give their developers a library to mask some of the complexity[2].

▪ The good news is that Web Workers provides a nice and simple API that lets you be very productive without worrying too much about deadlocks and similar problems.

▪ If your web application needs to complete a task that takes more than 150 milliseconds, you should consider using a Web Worker. If your app needs to feel like a native one, you should even consider setting the bar at around 80 milliseconds. Timing, of course, depends on your browser and hardware. If you are building a mobile web application you should make this time even shorter, as the CPU is not as powerful as on your desktop.[3]

▪ Before you get into timing your specific application, though, you may want to contemplate tasks like the following:

▪ Encoding/decoding a large string

▪ Complex mathematical calculations (e.g., prime numbers, encryption, simulated annealing, etc.)

▪ Sorting a large array

▪ Network requests and resulting data processing

▪ Calculations and data manipulation on local storage

▪ Prefetching and/or caching data

▪ Code syntax highlighting or other real-time text analysis (e.g., spell checking)

▪ Image manipulation

▪ Analyzing or processing video or audio data (including face and voice recognition)

▪ Background I/O

▪ Polling web services

▪ Processing large arrays or huge JSON responses

▪ To create a new Worker using the Web Worker API, you just need to call its script. For example:   var worker = new Worker("worker.js");

▪ The above line will load the script located at “worker.js” and execute it in the background. You need to call the Worker() constructor with the URI of a script to execute in the Worker thread.

▪ If you want to get data from the Worker (e.g., output of processed information, notifications, etc.), you should set the Worker’s onmessage property to an appropriate event handler function. For example:

▪ var worker = new Worker('routes.js'); worker.onmessage = function(event) {   console.log("Called back by the routes-worker with the best route to the pub"); }

▪ You can also keep in touch with your Workers using addEventListener:   var worker = new Worker('routes.js'); worker.addEventListener('message', function(event) {  console.log("Called back by the routes-worker... with the best route to the pub") }, false); worker.postMessage(); // start the worker.

▪ Workers don’t have access to the DOM of the “parent” page. They can’t access any of the following:   The window object   The document object   The parent object   And, last but not least, they can’t use JavaScript libraries that depend on these objects to work, like jQuery.

▪ Web Workers can access only a limited set of JavaScript’s features because of their multi-threaded nature. Here is the set of features they can use:   The navigator object   The location object (read-only)   The XMLHttpRequest function   The atob() and btoa() functions for converting Base 64 ASCII to and from binary data   setTimeout() / clearTimeout() and setInterval() / clearInterval()   dump()   The application cache   External scripts using the importScripts() method   Spawning other Web Workers[4]  

▪ Web Workers threads run their code synchronously from top to bottom, and then enter an asynchronous phase in which they respond to events and timers. This allows roughly two types of Web Workers:

▪ Web Workers that register an onmessage event handler, for long-running tasks that need to run in the background. This Web Worker won’t exit, as it keeps listening for new messages.

▪ Web Workers that never register for onmessage events, handling single tasks that need to be offset from the main web app thread, like fetching and parsing a massive JSON object. This Web Worker will exit once the operation is over. (In some cases, where you have registered callbacks, it will wait until all of the callbacks are done.)

▪ Table 1-1 shows that most modern browsers implement basic Web Workers. Even the mobile browsers offer Web Workers. However, Table 1-2 shows less support for the shared Web Workers, which are covered in Chapter 5.

▪ Browser        Version   IE                    10.0

▪ When we wish to use a feature that is not supported in all browsers, we need to check for support. In our case, for Web Workers we need to check whether there is a Worker property on the global window object. If the browser does not support the Web Worker API, the Worker property will be undefined, and you will need to find another approach.

▪ highPrime.js, a brute force prime number calculator that can be used as a Web Worker // // A simple way to find prime numbers // var n = 1; search: while (true) {  n += 1;  for (var i = 2; i
▪ In Chrome 17+ you will get “Uncaught Error: SECURITY_ERR: DOM Exception 18”, which will be a reminder that you need to run from a local server while developing. You can see how it looks in Figure 2-1.

▪ Messages sent between our web app page and the Web Worker using postMessage() will be copied (not shared). Our main web app page and the Web Worker don’t point to the same object instance, so we have a duplicate memory footprint on each end.

▪ To load external script files or libraries into a Web Worker, use the importScripts() global function. This function takes strings as arguments for the resources to import. If you give it zero URLs nothing will be invoked. However, if you give it one or more URLs (and file names as well), then it will load and execute this JavaScript (regardless of the MIME type) in the Web Worker.

▪ This can also be written as a single line:   importScripts('script1.js', 'script2.js');

▪ The browser may fetch the scripts in any order, and in case of failure will return a NetworkError exception. After all of the fetching is done, the scripts will be run in the order in which you wrote them as arguments in importScripts(). These commands will be processed synchronously.

▪ The importScripts() function itself does not return until all the scripts have been fetched and executed.

▪ Web Worker scripts must be resources (URLs of external files) with the same scheme as their calling page. In other words, you won’t be able to load a script from a JavaScript URL. Moreover, if your web app is working on a secure HTTP (https) you will need to call the Web Worker on https:// as well.

▪ There is currently (a tiny) disagreement among browser vendors on whether or not data URIs are of the same origin; Chrome (15+) and Gecko 10.0+ permit data URIs as a valid source for Web Workers.

▪ importScripts('http://twitter.com/statuses/user_timeline/' +       user + '.json?count=10&callback=processTweets'); . . function processTweets(data) {    // parse the json object that holds the tweets and build a html block from    // their content.    .    . }

▪ function startWorker(settings) {  var myWorker = new Worker('scripts/worker.js');  myWorker.addEventListener("message", workerListener, false);  myWorker.postMessage(settings); }

▪ Dedicated Web Workers let you run scripts in background threads. Once the Web Worker is running, it can communicate with its web app by posting messages to an event handler registered with the web app that spawned it.

▪ Dedicated Web Workers are good for tasks that consume a lot of CPU (e.g., calculating routes, 3D positions, prime numbers, etc.) and are also good for masking the latency in server connections.

▪ Having a Worker handle the connections keeps the main user interface thread freer to handle the users’ actions.

▪ A dedicated Web Worker supports two events:   onmessage Triggered when a message is received. An event object with a data member will be provided with the message. onerror Triggered when an error occurs in the Worker thread. The event provides a data member with the error information.

▪ Index.html for fetching tweets and putting them in localStorage

▪ Get a tweet from our localStorage. We could use sessionStorage if we       // wish to have this data just for our session

▪ The callback function executes processTweets(data), which takes the payload JSON and sends it to the parent (e.g., index.html). It also sends some “administrative” messages like “Worker Status:” so it will be easy to debug the code and see progress.

▪ The last phase is a loop that makes sure to call the Twitter API every 3 seconds.

▪ In addition, we can use app cache and offline capabilities to handle cases in which we have a weak network connection or no connection at all.

▪ Example 3-3 and Example 3-4 demonstrate managing our prime number–calculating Web Worker with a simple protocol of two commands: start and stop. You can, of course, have many more commands that suit the specific case you are trying to solve.

▪ It’s important to remember that in our main switch you should always keep a default and report it as an error (or warning depending on your app). The results are shown in Figure 3-2.

▪ Web Workers are great for handling long-running tasks. In modern web applications, there are many cases in which we need to handle large amounts of data. If you have a large JSON string you wish to parse and it will take ~250 milliseconds (or more), you should use Web Workers.

▪ This way, your users will love you and won’t hate the fact that the web app doesn’t feel responsive.

▪ In Firefox and Chrome (since version 13), we have the option to send ArrayBuffers to and from a Web Worker using an algorithm called structured cloning[5]. The option to use postMessage() not just for strings, but complex types like File, Blob, ArrayBuffer, and JSON objects, makes this an important enhancement.

▪ Structured cloning is a powerful algorithm for any web developer, but it’s still a copy operation that can take hundreds of milliseconds.

▪ Chrome 17+ offers another performance boost through a new message-passing approach called Transferable Objects. This implementation makes sure that the data is transferred and not copied from one context to another. It is a “move” operation and not a copy, which vastly improves the performance of sending data to a Worker.

▪ It’s similar to a pass-by-reference operation that we have in other languages. In a “normal” pass-by-reference we will have the same pointer to the data; however, here the “version” from the calling context is no longer available once the object is transferred to the new context.

▪ In other words, when we transfer an ArrayBuffer from our main web app page to the Web Worker, the original ArrayBuffer is cleared and we can no longer access it. Instead, its contents are transferred to the Worker context and are accessible only in the Web Worker’s scope.

▪ You can also send messages through the window object. This approach requires adding the targetOrigin because we can post this message to different workers.

▪ These approaches allow massive data manipulation, image processing, WebGL textures, etc., to be passed between the Web Worker and the main app with less impact on memory footprint and speed.

▪ The example below shows how we can use the new BlobBuilder[6] interface to inline your Worker code in the same HTML file.

▪  Creating an inline Worker with a javascript/worker type // This script won't be parsed by JS engines because its type is JavaScript/worker. // Simple code to calculate prime number and send it back to the parent page.       self.onmessage = function(e) {       self.postMessage("<h3>Worker: Started the calculation</h3><ul>");         var n = 1;         search: while (n < 500) {           n += 1;           for (var i = 2; i <= Math.sqrt(n); i += 1)             if (n % i == 0)               continue search;           // found a prime!           postMessage("<li>Worker: Found another prime: " + n + "</li>");         }         postMessage("</ul><h3>Worker: Done</h3>");       }

▪ In the main page, we will create a BlobBuilder with the code we have under the script Id “worker1.” Then, by using window.URL.createObjectURL we will create a new File (or Blob) that represents our data. Firefox and Chrome both have the ability to use window.URL; however, in Chrome/Safari/other WebKit browsers, we will use window.webkitURL.

▪ Example 4-2. Creating a Worker using BlobBuilder      // Creating the BlobBuilder and adding our Web Worker code to it.      var bb = new (window.BlobBuilder || window.WebKitBlobBuilder ||                    window.MozBlobBuilder)();      bb.append(document.querySelector('#worker1').textContent);      // Creates a simple URL string which can be used to reference      // data stored in a DOM File / Blob object.      // In Chrome, there's a nice page to view all of the created      // blob URLs: chrome://blob-internals/      // OurUrl enable our code to run in Chrome and Firefox.      var ourUrl = window.webkitURL || window.URL;      var worker = new Worker(ourUrl.createObjectURL(bb.getBlob()));      worker.onmessage = function(e) {        status(e.data);      }      worker.postMessage();

▪ the HTML page with some elements that show what goes on while the Web Worker is finding prime numbers. The main disadvantage to this technique is that it will be harder to debug your Web Worker JavaScript code. One way to be more productive would be to test your Web Worker as an external file. Then, only after you are happy with the results, put it back in the page as an inline Web Worker.

▪ Shared Web Workers allow multiple web application instances to communicate with a single instance of a shared Worker.

▪ Shared Web Workers will be identified by the name or the URL that you provide in their constructor. You instantiate them by creating a new SharedWorker.

▪ One way to leverage shared workers in your web application is by using a single shared Worker as a central point of communication with a server. Multiple Workers can be opened and all view the same picture through the shared Worker. Instead of directly communicating with your servers, the web app will communicate with a shared Worker that buffers changes locally and communicates with the server when online.

▪ The shared worker can also use HTML5 offline capabilities[7] to persist the state of the data and communicate it to the server, based on your web application logic.

▪ Other good uses for shared Workers include the following:   Providing a single source of truth for any type of logic that your app needs in more then one place (e.g., user identification, connection status, etc.).  

▪ Ensuring data consistency between windows of the same web app.

▪ Reducing the memory consumption of multiple web app tabs/windows, by allowing some code (e.g., server communications) to be centralized in one place.

▪ The main event that the shared Web Worker will execute when a client thread connects to it is connect. Each client connection has a port assigned to uniquely identify that connection. The post-message method and message events get pushed to the port so that the messaging is performed at the connection level.

▪ Example 5-4. inner iframe we use in SharedWorkers2.html

▪ Figure 5-2 shows how the Shared Web Worker example will look. The connection to the shared Worker is done first from the main window and then from the iframe (that mimics the case of another instance of the web app in another window or tab).

▪ Currently only FileAPI and WebSQL are supported from Web Workers. However, because IndexedDB is going to replace WebSQL I hope we will see support for it soon.

▪ The main properties in the onerror handler are the following:   message The error message itself. lineno The number of the line inside our Web Worker that caused the error. filename The name of the file inside the Worker in which the error occurred. That should be all the information you need to be able to fix your “errors,” right?

▪ Chrome (15+) facilitates debugging of Web Workers by injecting fake Workers implementations. These injections simulate Web Workers using an iframe within a Worker’s client page.

▪ The main motivation to implement Web Workers for NodeJS is to have a set of standard platform-independent concurrency APIs outside the browser. One powerful example is Peter Griess’ node-webworker module[10], and you can find others on GitHub[11].

▪ These implementations let front-end web developers carry their knowledge of Web Workers technology beyond the browser. They also let developers avoid the NodeJS primitives for managing processes. The child_process[12] provides a great deal of functionality, but is easily misinterpreted by developers who have not developed for a UNIX platform. The error reporting APIs in the Web Workers are also more full-featured and verbose than the one provided natively by child_process.

▪ In the node-webworker module each worker implements in its own node process. This is done so we won’t need a separate thread (and V8 context) in the main node process. Each node process will be self-contained.

▪ The main advantage of this approach include the following:   Performance Modern operating systems are more likely to schedule different processes on different CPUs. This might not always happen for multiple threads within the same process, and with today’s multicore processors it make sense to leverage them as we can. Fault isolation If the Worker runs out of memory or triggers an error, it will not cause glitches to other Workers. Avoiding complexity There is no need for a complicated managing layer that observes event loops in a single process.

▪ The Web Workers spec describes a message passing API.[13] The Node-based master process will create a dedicated UNIX domain socket per worker. This has much less overhead than TCP, and it allows us to enjoy some UNIX goodies like file descriptor passing. This socket’s path will be composed from /tmp/node-webworker-/.

▪ Example 7-1 starts a Worker that calculates routes (e.g., the famous problem of finding the best route from L.A. to San Francisco). The code in main.js is a generic setup to create the Worker and listen to its output, whereas in the Worker itself we calculate the routes and post the results back.

▪ The supported standard Web Worker API methods include the following:   postMessage(e) In both workers and the parent. onmessage(e) In both workers and the parent. onerror(e) In both workers and the parent. terminate() In the parent. You don’t need it in the Web Worker, as it will finish on its own.

▪ All of this book’s example code can be found on GitHub: https://github.com/greenido/Web-Workers-Examples-

▪ Live example I’ve written using Web Workers to calculate prime numbers while you can control them (start/stop) using commands: http://ido-green.appspot.com/examples/webWorkers/highPrime2.html

▪ Canvas & Web Workers demo: This app uses canvas to draw out a scene. You’ll see that when you use Web Workers this scene is drawn in pieces; this is done by telling the Web Worker to compute a slice of pixels. The Web Worker itself cannot manipulate the canvas because of the restrictions it has. It will therefore pass the computed information back to the main page and the drawing will be done from this page: http://nerget.com/rayjs-mt/rayjs.html.

▪ Thanks to Peter Griess and his important work on GitHub (https://github.com/pgriess/node-webworker). You can read more in his blog: http://blog.std.in/2010/07/08/nodejs-webworker-design/

▪ Ido is a Developer Advocate for Google Chrome OS.  
