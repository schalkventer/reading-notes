Jamstack Handbook (2020)

Colby Fayock

---

▪ The Jamstack boils down to a few basic principles which represent the JAM in Jamstack: JavaScript, APIs, and Markup.

▪ Part of the reason I love working with the Jamstack architecture is the tooling. While we’re still young in the relative lifetime of the architecture, working with Jamstack projects makes the web fun again.

▪ It even includes things like automatic build previews and serverless functions that further improve the overall development experience and simplify your deployment workflows.

▪ to pay for auto scaling and you don’t need to worry about load balancing. As we discussed earlier, static hosting infinitely scales by default.

▪ request to finish loading their status as an authenticated user, enhancing the page with personalized details to reflect that.

▪ Understanding the what and why of the Jamstack is important to have context as to what benefits the Jamstack provides as well as any downsides. This will help you make more informed decisions when creating a new project for your team or understand what tradeoffs you’re making when deciding not to go with a server-side solution.

▪ like freecodecamp.org.
This architecture isn’t too far off from websites from the past.

▪ There are solutions to help relieve this stress, such as load balancing and auto scaling. You can even taking advantage of caching with a CDN. But all of these are still prone to failure depending on how quickly the traffic surges and the potential for an inconvenient purge of cache with a complex caching layer.

▪ paying for a service where you interface with their APIs. Given these services typically deal with many other customers, they’re often prepared to handle large amounts of traffic.

▪ If I have a blog with an authenticated admin dashboard, I can serve my blog content statically to unauthorized users, but provide a dynamic experience with browser-based API requests for admins to log in and update content.

▪ Reliability

Downtime means loss of money. If an ecommerce store is down, that’s precious time that potential customers could be spending purchasing products.

▪ All technologies come with a metaphorical price. While we may see some of these downsides fade as the architecture matures, there are still a lot of considerations to be made before making an investment with new projects or migrating existing ones.

▪ The concepts we’ve already gone over are probably interesting enough to dive in, but it’s helpful to understand where “Jamstack” came from and the challenges it’s trying to solve.

▪ As time goes by, we see cycles of technologies just as we might see cycles of fashion or UI design. Solutions of the past are repurposed into modern ways of thinking that ultimately provide the people visiting our projects a better user experience.

▪ That static file doesn’t require the processing and rendering time to deliver that first HTML document. Instead, that document is quickly delivered and the browser can start loading any of the dynamic pieces to enhance the experience.

▪ As a bonus, one of the dreams of freecodecamp.org’s founder Quincy
Larson is to put freeCodeCamp’s curriculum on a Raspberry Pi or
Android device to allow people without access to the internet to learn.

▪ By leveraging the built-in advantages of delivering the content statically, we can deliver websites where the first experience will quickly load, reduce the potential points of attack for bad actors, provide a page that can scale infinitely, and all while having a lower price point than running an equivalent server.

▪ Remember that basic HTML file you hand wrote when you were first learning HTML itself? Yup, that’s Jamstack.
Or how about those larger static websites using individual HTML files. The ones where you uploaded those files via FTP with some CSS and JavaScript sprinkled in that were popularized before languages like PHP and tools like WordPress existed? Yup, that’s Jamstack. So what actually “defines” a modern Jamstack site or app?

▪ Headless resources refers to those APIs that provide a means of requesting data for a static page without providing any direct rendering of a UI. This includes both APIs at compile time and APIs in the browser.

▪ To add ecommerce functionality, we’ll use Snipcart, which allows us to take advantage of it’s API and dashboard to add a shopping cart right in our app with little fuss.

▪ But it could also have more detrimental impacts if that downtime is preventing someone from refilling a prescription or preventing scientists from doing critical research.

▪ Web frameworks like Next.js and Gatsby allow us to rapidly get productive by spinning up a new React app that’s production-ready.

▪ There’s two main approaches when dealing with APIs: precompiling a project using an API or using an API to request content right in the browser. Each approach has its advantages and disadvantages, but each can be used with the other to help leverage their strengths.

▪ While JavaScript isn’t a required ingredient in a Jamstack website, it’s really what popularized the approach. JavaScript has flourished in the modern web serving as a flexible language developers can use throughout the entire stack of a project from running Node on a server to the browser flavor we’ve all come to love.

▪ The preconnect tags send signals to the browser letting them know that they can start working on connections to Snipcart to help requests load faster.

▪ Little Caesars, a pizza company, developed their website and purchase experience with the web framework Gatsby.

▪ The word or expression “Jamstack” was coined by the Netlify team to avoid negative connotations technical or executive decision makers might associate with the term “static”.

▪ Ultimately, whatever approach you choose for your project, the end result will be an HTML file which you serve to the person visiting your website. This can range from very simple, with a hand-crafted HTML document, or to more complex, with tools like Next.js and Gatsby that allow you to scale dynamic content into large static websites and apps.

▪ Building educational platforms like the freeCodeCamp learning portal
as a static website opens the doors to that possibility by allowing
people to view the static content offline.

▪ One of those past solutions was the use of static websites to deliver content to the world. While there was never anything technically wrong with the approach, teams began to choose server-based solutions to deliver dynamic experiences.

▪ When using static storage or a CDN to serve your website or application, you're reducing the attack surface for the fundamental piece of your website.

▪ There’s also something to be said about the complexity of Jamstack solutions.

▪ When utilizing static hosting and delivery, some of the immediate advantages is having a project that’s highly available, meaning it has very little downtime, and one that infinitely scales, meaning it can handle any large influx of traffic.

▪ Unless you’re building all of these APIs on your own infrastructure, it’s common to use third party services to take advantage of their rich APIs.

▪ A common complaint amongst skeptics is the amount of time it takes to build a Jamstack project.

▪ One reason we tend to see downtime is when a website receives a surge of traffic. This could mean an ecommerce product went viral or an article received the “hug of death” from Reddit.

▪ This is an important factor to consider, but chances are, the infrastructure or services required to maintain dedicated APIs would cost less than the entire infrastructure relying on servers, especially if you’re taking advantage of serverless services.

▪ The learning curve might be a little more steep for a newcomer to onboard a project, having to deal with multiple services and entry points into a project.

▪ While Jamstack sites are derived from a static file, they can be just as dynamic as any server-based experience.

▪ Our users may experience that flash of unauthenticated content, but it’s also possible that the time it takes to both load that initial HTML page and API request is faster than a server request to render the entire page.

▪ Though there are plenty of benefits, there are also some advantages a server based solution might have that a Jamstack project ultimately might not solve.

▪ While solutions like WordPress will update content without a full rebuild, a static site generator may have to rebuild the entire project for a simple blog post update.

▪ With server based projects, routing and the way requests are handled can be complicated, leaving the extra potential for exposing secure routes or not safely sanitizing HTTP requests allowing someone to POST live code to the server.

▪ While everything talked about so far is important on its own, each benefit comes with a cost.

▪ Similar to the rest of the web, ecommerce has typically relied on a traditional website technology stack to achieve highly dynamic details such as up to date pricing on each product, how many items are in stock, and managing a checkout flow that includes what products someone has in their cart.

▪ Delivering a great user experience includes delivering a fast website, but it’s also critical from a business perspective.

▪ If you want authentication, you might look to Auth0. If you want media management, you may look to Cloudinary. And while both of those services do a fantastic job in their own rights, they’re additional services that require management of resources and billing.

▪ With an upcoming Super Bowl ad in 2020, they were faced with an surge of traffic that could easily take down any infrastructure. The Jamstack helped them survive and serve their customers with hot and ready pizza for the big game.

▪ As we’ll later learn, part of the reason Jamstack sites are so great is that delivering static HTML files to the people visiting our projects is both really fast and cheap.

▪ How can we take advantage of an older methodology and augment it with modern tooling to deliver a performant, yet still dynamic experience to the people visiting our websites?

▪ That’s in contrast to approaches like Ruby on Rails, where the project might include everything already baked in, meaning someone can spend less time searching for various application concerns and understanding different service patterns requiring additional cognitive load.

▪ This is more common with websites that rely on servers to render and deliver the request to the person visiting the website

▪ Solutions like WordPress are popular for a reason. Publishers can make content changes and can more or less see those changes reflected immediately with small repercussions to the rest of the

▪ If you’re using the web application framework Next.js for instance, Next.js lets you define specific functions that capture data at compile time. You can also configure Next.js to make a request to an API and transform that dataset into new pages.

▪ But the modern web is dynamic in nature. Static content might suffice for a blog, but that won’t fly for anything that requires a dynamic experience.

▪ While Gatsby has a huge plugin ecosystem that allows you to plugand-play a lot of new features and integrate with services, teams like Stackbit are working to consolidate the entire workflow.

▪ From an education perspective, freecodecamp.org, a source for developers to learn how to code for free, rewrote their learning platform using Gatsby. This has allowed them to simplify their workflow and more easily scale their project for new people trying to learn.

▪ Premature decoupling is an expression that refers to figuring out how to split concerns in a project before understanding the impact and whether or not the way those concerns are split even make sense.

▪ Similar to the other good parts, this gets more complicated as you layer in more APIs to your project.

▪ Jamstack sites, or static sites, try to solve a few different pain points when dealing with web development projects: performance, security, reliability, and cost.

▪ While some of this might seem trivial if you’re running your own shop and manually updating these things on your website, for teams that manage high volume sales or even an entrepreneur that wants to sell a bunch of products with their logo, this can prove really challenging. If your website is showing incorrect information, you could end up with frustrated customers who will refuse to give you another chance.

▪ When serving a Jamstack project by using static storage or even better with a CDN, we’re reducing the amount of time that someone has to wait to get the first response back from the server.

▪ With static hosting, the first document that gets delivered to the person visiting your project will be highly available. This could include the entire website. But if you layer in APIs to enhance the experience with dynamic data, you could still run into similar scalability issues with a surge of traffic.

▪ To start, the tooling available to develop the projects is already fantastic. Tools like Next.js and Gatsby make it easy to spin up an entire front end project in React. Newer frameworks like RedwoodJS try to take that a step further and integrate the creation and management of services on top of the front end.

▪ These pain points are synonymous with the pillars of AWS’s WellArchitected Framework, where the goal is to provide an excellent

▪ To be clear, this only is true for how you serve the HTML document. Given the dynamic nature of client side requests to APIs, the APIs themselves may face the same security concerns you would face when serving your entire website from a server.

▪ One of the issues with static content is that it’s in fact static. Trying to “hydrate” a page with dynamic content can prove to be problematic and somewhat complex.

▪ While some people might not see past the word “static”, Jamstack sites and applications can range from a simple landing page to fullscale dynamic apps like an ecommerce store or an education platform

▪ But there’s also something to be said about the value those services bring.

▪ It’s not an excuse, but tooling isn’t currently equipped to deal with optimizing this workflow, yet another effect of an ecosystem of tooling that isn’t yet quite mature.

▪ Instead of building an authentication service on your own, which is a critical point in any infrastructure, we can trust Auth0 and their team to provide industry leading services. Rather than manage our own

▪ The advantage even in the worst case scenario though is you may have reduced functionality, but you’ll always be able to provide an experience to someone visiting your website rather than a nondescriptive default error page from the browser.

▪ Part of the issue is that when someone loads the page, if they’re logged into a website, they may not be immediately presented with a logged in state. They may have to wait a second or two for the API

▪ The good news though, you’re reducing the overall attack surface and allowing the API development to focus on how to secure those APIs for specific network requests rather than a wider range of input and 
