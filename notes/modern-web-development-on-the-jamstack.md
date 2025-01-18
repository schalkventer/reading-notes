Modern Web Development on the JAMstack (2019)

Mathias Biilmann & Phil Hawksworth

---

▪ In just the past few years, a flurry of advancements has greatly strengthened the web as a content and application platform

▪ Browsers are much more powerful. JavaScript has matured. WebAssembly is on the horizon. It certainly feels like the beginning of a new chapter for the web. You’ve likely felt this as you’ve witnessed the explosion of new frontend frameworks and API-based services.

▪ Although what’s technically possible in the browser has advanced, so too have expectations for immediacy. Videos must play instantly. Browser applications must launch faster than their desktop counterparts. Users have become increasingly mobile and increasingly impatient—we are all fed up with slow pages and we vote angrily against them with the back button.

▪ If you tend to feel delivering great websites should be more about the craft of markup and JavaScript than server setup and administration, you’ve found your book.

▪ At times, though, the effort has seemed to trade one goal for another. Wordpress, for example, became a revolution in making content easier to author—but anyone who’s scaled a high-traffic Wordpress site knows it also brings a whole set of new challenges in performance and security. Trading the simplicity of HTML files for database-powered content means facing the very real threats that sites might crash as they become popular or are hacked when nobody is watching closely.

▪ And dynamically transforming content into HTML—each and every time it’s requested—takes quite a few compute cycles. To mitigate all the overhead, many web stacks have introduced intricate and clever caching schemes at almost every level, from the database on up.

▪ But these complex setups have often made the development process feel cumbersome and fragile. It can be difficult to get any work done on a site when you can’t get it running and testable on your own laptop. (Trust us, we know.)

▪ Developer Jonathan Prozzi said it best on Twitter: “My learning journey leading to #JAMstack has re-ignited my interest and passion for web technology.”

▪ JavaScript is called out specifically as the language of the browser, but you can use as much or as little JavaScript as your project requires. Many JAMstack sites also use Python, Go, or Ruby for templating and logic. Lots of open source software has sprung up to help you create JAMstack sites, and we spend some time in this book going over a few of the more popular options.

▪ Not everything about the JAMstack is a new idea, but it’s only very recently that we’ve had the technology required to make the approach possible, especially on the edge of the network and in browsers.

▪ It’s this last point that deserves special attention. Think for a moment about today’s most common approach to serving web content: for each and every request made to a website, data is pulled from a database, rendered against a template, processed into HTML, and finally pushed across the network (and maybe even an ocean) to the browser that requested it.

▪ After all, a general rule for maximum performance is to perform the fewest steps possible.

▪ Shouldn’t new HTML be produced only when content or data changes, not every time it is requested?

▪ This approach eliminates large amounts of server and network latency. Given the efficiency and simplicity of serving prerendered content directly from a CDN, it’s no surprise JAMstack sites tend to acheive the highest possible scores on speed tests like Google Lighthouse.

▪ JAMstack sites are far from “static” and are often updated just as often as their more complex counterparts, sometimes hundreds of times daily.

▪ In the JAMstack, it’s possible and common for the content of the site, blog posts and all, to live in a Git repository right alongside the code and templates. This means that no content database is required, making JAMstack sites dramatically easier to set up, run, deploy, branch, and modify.

▪ Or take what happens on Smashing Magazine’s JAMstack site: each time a user comments on an article, a simple function commits the comment to the site’s repository and triggers a new build (as long the comment passes moderation).

▪ At the end of 2017, Smashing Magazine completely rewrote and redesigned its site to switch from a system based on several traditional, monolithic applications to the JAMstack.

▪ Web sites have traditionally been powered by monolithic architectures, with the frontend of the application tightly coupled to the backend.

▪ The freedom to do good work—to design the exact experiences we want for our users—is regularly compromised by complex monolithic applications.

▪ As it happens, monolithic apps are rarely conducive to superior site performance. They need to generate and deliver HTML every time a new visitor arrives on the site. This significantly slows down page load time.

▪ Because monolithic architecture requires the page view to be generated for every visitor, infrastructure needs to be scaled in anticipation of site traffic. Not only is that expensive, it’s also difficult to get right. Teams end up over-provisioning their infrastructure to prevent downtime or risk a crash because there is no clear separation between the infrastructure required to generate and manage the site and that required to serve the site.

▪ When the same application that builds the page views or lets authors manage content also needs to be scaled to handle traffic spikes, it’s not possible to decouple these facilities in order to scale and protect each piece of the infrastructure according to its needs.

▪ In computer science, we recognize that the costs of writes and reads can be very different, and yet monolithic apps bundle these features together into the same application, making them difficult to design for appropriately.

▪ The approach to designing a system that allows for hundreds of millions of read operations is very different to that of a system that allows a similar number of write operations. So, is it wise to combine these capabilities into the same infrastructure and demand that the risk profile of one feature influence that of another?

▪ And are those features likely to encounter similar traffic levels?

▪ There are ways to put distance between the users visiting your site and the complexity that generates and delivers that site. Without such separation, scale can be difficult to achieve.

▪ We want to ensure that as we’re evaluating the reasons that monolithic apps are no longer serving the growth of the web, we’re careful not to insult the hundreds of thousands of development teams that chose to implement them.

▪ Monolithic apps like Wordpress, Drupal, and Joomla combine every single component and plug-in of a web project’s architecture into a single codebase. In turn, it creates a massive surface area for malware to penetrate. Not only is the attack surface area extremely large, it’s also exposed every single time the site is built because any plug-in the site uses must execute each time the page loads for a new site visitor, magnifying the risk.

▪ The JAMstack at its core, is simply an attempt to give a name to a set of widely used architectural practices. It gives us one word to communicate a large range of architectural decisions.

▪ It came about in conversations between people involved in the communities around static site generators, single-page application (SPA) frameworks, build tools, and API services as we realized much of the innovation in each of these categories was connected.

▪ An entire community grew up around the first mature generation of static site generators like Jekyll, Middleman, Metalsmith, Cactus, and Roots. Jekyll found fame as the static site generator supported natively by GitHub Pages, and others were developed in-house by agencies or startups that made them a core part of their website stack.

▪ At the same time, single-page app frameworks like Vue and React started a process of decoupling the frontend from the backend, introducing build tools like Grunt, Gulp, and later, Webpack and Babel, which all propagated the idea of a self-standing frontend with its own build pipeline and deployment process. This brought a proper software architecture to the frontend workflow and empowered frontend developers to iterate much faster on the user interface (UI) and interaction layer.

▪ When these approaches to building websites and applications intersected, a new API ecosystem began to emerge. Tools like Stripe, Disqus, and Algolia made payments, comments, and search available directly from the frontend via API-driven services.

▪ the real architectural constraints became the following:

JavaScript in the browser as the runtime

Reusable HTTP APIs rather than app-specific databases

Prebuilt markup as the delivery mechanism

▪ The World Wide Web is fundamentally just a UI and interaction layer built on top of a stateless protocol called the HyperText Transfer Protocol (HTTP). The most fundamental concept of the web is the Universal Resource Locator (URL).

▪ In the early days of the web, a website was simply a folder with HTML files exposed over HTTP by a web server. As the web evolved, we began moving to a model in which a running program on the server would build the HTML on the fly for each visit, normally after consulting a database.

This was a much slower, more complex process than serving static assets, but it was also the only viable way to work around the fact that browsers were simple document viewers at the time. Responding to any user interaction, be it a click or form submission, required an entirely new page of HTML to be assembled on the server. This was true whether you were building a comments feature for a blog, an ecommerce store, or any kind of web application. Because of this document-centric architecture, web experiences often felt much less responsive than desktop applications.

▪ In many ways this decoupled architecture is similar to the architecture of mobile apps. When the iPhone introduced mobile apps (originally because traditional web apps were not performant enough), it was simply not a consideration to build a model in which the full UI would be reloaded from a server every time the user took some action. Instead, IOS introduced a model in which each app could be distributed to users as an application package with a declarative UI, including any needed assets to communicate with JSON or XML-based web APIs from there.

▪ The simplest JAMstack sites are pure static sites: a folder with HTML and supporting assets (JavaScript, Cascading Style Sheets [CSS], images, font files) and no moving parts; plain-text files that can be edited directly in an editor of choice and kept under version control.

▪ For most of the life of the web, we’ve taken for granted that our CMS determines our entire development platform and couples rendering, content editing, and our plug-in ecosystem tightly together. But the advent of headless CMSs—whether they are API-driven or Git-based—means that we can think of content editing UIs as completely separated from the frameworks and tools which we use to render and deliver our websites.

▪ In the early 2000s, Microsoft discretely added a homegrown API to Internet Explorer called XMLHttpRequest (XHR). Before this happened, the only way a browser could initiate a page load was by navigating to a new URL that would load a completely new web page from scratch.

▪ In the end, the trade-off will need to be based on what’s most important: performance, uptime, and scalability, or shortening the publishing cycle.

▪ For the majority of content-driven sites, as long as a deploy can be scheduled to go live at a certain time, being able to run a build cycle in less than 10 minutes is likely not of real importance. Unless your site is truly gigantic (pages counted in millions rather than thousands), a JAMstack approach might be a more viable option than you would have once thought.

▪ It’s common for a company to require a variety of web experiences: a primary website, a blog, a documentation site, a web application, an ecommerce store, and so on. Maintaining a common look and feel across all these applications used to be extremely challenging for web teams. That’s because on traditional architectures, the frontend of each application is tightly coupled to the backend used to generate it on the server.

▪ The JAMstack solves for this in an elegant, highly scalable way. We can build one, decoupled frontend that spans across all applications. You’ll see this in action later when we present the Smashing Magazine case study.

▪ The list of projects that wouldn’t be a fit for a JAMstack architecture is continually getting shorter. Improvements in the tooling and automation, the workflows, best practices, and the ecosystem as a whole are creating more possibilities for what a JAMstack site can achieve.

▪ With server-side rendering, all possible layers of the stack are always involved in any of the requests a user makes to a site or application.

▪ To build performant and secure software, developers must deeply understand all of the layers that requests flow through, including third-party plug-ins, database drivers, and implementation details of programming languages.

▪ Decoupling the build stage completely from the runtime of the system and publishing prebaked assets constructs an unbreakable wall between the runtime environment end users interact with and the space where code runs. This makes it so much easier to design, develop, and maintain the runtime in isolation from the build stage.

▪ Separating APIs into smaller microservices with a well-defined purpose means that our ability to comprehend the particulars of each service in isolation becomes much simpler. Borders between services are completely clear.

▪ This helps us to establish clearer mental models of the system as a whole while being liberated from the need to understand the inner complexities of each individual service and system.

▪ As a result, the burden of development and maintenance of the system can be significantly lightened. The areas where we must direct our attention can be more focused with confidence that the boundaries between the services being used are robust and well defined.

▪ In recent years, the complexity of frontend architectures has exploded as browser APIs have evolved and HTML and CSS standards have grown. However, it’s very difficult for the same person to be both an expert in client-side JavaScript performance and server-side development, database query constraints, cache optimization, and infrastructure operations.

▪ When we decouple the backend and frontend, it makes it possible for developers to focus on just one area. You can run your frontend locally with an autorefreshing development server speaking directly to a production API, and make switching between staging, production, or development APIs as simple as setting an environment variable

▪ This means that we’re seeing a much broader ecosystem of ready-made APIs for authentication, comments, ecommerce, search, image resizing, and so on. We can use third-party tools to outsource complexity and rest easy in the knowledge that those providers have highly specialized teams focusing exclusively on their problem space.

▪ The more that we can prebuild, the more that we can deploy as prebaked markup with no need for dynamic code to run on our servers during a request cycle, and the better off we will be. Executing zero code will always be faster than executing some code

▪ Zero code will always be more secure than even the smallest amount of code.

▪ Assets that can be served without any moving parts will always be easier to scale than even the most highly optimized dynamic program.

▪ Fewer moving parts at runtime means fewer things that could fail at a critical moment.

▪ And the more distance we can put between our users and the complexity inherent in our systems, the greater our confidence that they will experience what we intended.

▪ Facing that complexity at build time, in an environment that will not affect the users, allows us to expose and resolve any problems that might arise safely and without a negative impact.

▪ The only reason to run server-side code at request time ought to be that we absolutely cannot avoid it.

▪ The more we can liberate ourselves from this, the better the experience will be for our users, operations teams, and our own ability to understand the projects we’re working on.

▪ JAMstack sites benefit from a far simpler technical architecture. The burden of scaling a JAMstack site to satisfy large peaks in traffic typically falls on the Content Delivery Network (CDN) that is serving the site assets. Even if we were not to employ the services of a CDN, our hosting environment would still be dramatically simplified when compared to the aforementioned scenario.

▪ When the process of accessing the content and data and then populating page templates is decoupled from the requests for these pages, it means that the demands on these parts of the infrastructure is not influential to the number of visitors to the site.

▪ The size and complexity of a project’s architecture is directly proportional to the quantity of people and range of skills required to operate it. A simplified architecture with fewer servers requires fewer people and far less specialization.

▪ By having working knowledge of a larger portion of the stack and fewer discipline boundaries to cross, each developer’s mental model of the project can be more complete and, as a result, each individual can be more confident in their actions and be more productive.

▪ You can find some staggering results from web performance optimization listed on https://wpostats.com/, some showing marginal performance yielding impressive improvements, like these:

“COOK increased conversion rate by 7% after cutting average page load time by 0.85 seconds. Bounce rate also fell by 7% and pages per session increased by 10%.”

—NCC Group

“Rebuilding Pinterest pages for performance resulted in a 40% decrease in wait time, a 15% increase in SEO traffic, and a 15% increase in conversion rate to signup.”

—Pinterest Engineering

“BBC has seen that they lose an additional 10% of users for every additional second it takes for their site to load.”

—BBC

While others boast staggering results:

“Furniture retailer Zitmaxx Wonen reduced their typical load time to 3 seconds and saw conversion jump 50.2%. Overall revenue from the mobile site also increased by 98.7%.”

—Google and Zitmaxx Wonen

▪ In the frontend, we see incredible attention being given to things like the following:

Minimizing the number of HTTP requests required to deliver an interactive site

Page architectures designed to avoid render blocking or dependencies on external sources

Use of image and visualization techniques that avoid heavy videos and images

Efforts to avoid layout thrashing or slow paint operations

▪ Each area is important. Good web performance requires a concerted effort at all levels of the stack, and a site will only be as performant as its least performant link in the chain.

Critically though, the JAMstack removes tiers from that stack. It shortens that chain. Now operations on which teams used to spend large amounts of time and money to optimize in an effort to speed them up and make them more reliable don’t exist at runtime at all.

▪ However, there is no code that can run faster than zero code. This kind of simplification and separation of the building of sites from the serving of sites yields impressive results.

▪ In read-only systems, not only are scale and performance considerations improved, but our security profile is improved.

▪ We can return to the discussion of Wordpress sites as a useful comparison. A Wordpress site combines a database, layers of logic written in PHP, templates for presentation, and a user interface for configuring, populating, and managing the site. This user interface is accessed over the web via HTTP, requiring that a Wordpress site is capable of accepting HTTP POST requests, and consuming and parsing the data submitted to it in those requests.

▪ For those looking to secure a Wordpress site, it is a difficult battle to permanently, confidently win.

▪ Developer experience is an important success factor. The ability for a developer to effectively deliver on the promise of the design, the strategy, and the vision can often be the final piece of the puzzle. It’s where ideas are realized.

▪ A poor development experience can be devastating for a project. It can impede development progress and create maintenance implications that damage the long-term health of a project. It can make it more difficult to recruit and to retain the people you need to deliver a project. It can generate frustrations at slow progress or poor reliability. It can choke off any ability to innovate and make a project great.

▪ But of course, we can’t sacrifice user experience for developer experience. Jeremy Keith has deftly articulated this on a number of occasions, notably here:

Given the choice between making something my problem, and making something the user’s problem, I’ll choose to make it my problem every time.

—Jeremy Keith, Needs Must, 2018

▪ What we need is an architecture and an approach to development that somehow satisfies both of these criteria. The JAMstack can deliver this for us.

▪ It’s likely that not all your site contributors will be developers, and using Git and text files may be an unfamiliar experience. This is actually the reason why database-backed CMSs like Wordpress were originally created.

▪ After the shopper clicks the buy button, the intent to purchase is sent to a provider called CommerceLayer, whose job it is to power the shopping cart and checkout experience. Again, this happens using JavaScript to call APIs

▪ Like Contentful, CommerceLayer is also headless and makes no demands on our how application looks and behaves.

▪ In fact, you’ll find many traditional players like Shopify now offer APIs so they, too, can be consumed in a headless fashion.

▪ We’ve alluded to a couple of them in the previous chapters, but it is worth taking a moment to clarify the differences between some of these common terms:

Client-side rendering

Server rendering

Prerendering

▪ Decoupling this rendering or generation of views from the timing (and machinery) at request time allows us to expose the risk early and tackle any unknowns of this operation far in advance of the times a request for the content is made by a user.

▪ It might seem cumbersome to generate and deploy an entirely new build each time we want to make even a small change to our sites, but because this leaves previous deployments intact, we gain the ability to switch between different versions of our site at any time.

▪ And by automating and scripting the build and deployment processes, we can drop the friction associated with building and deploying sites to close to zero, making this process far less cumbersome.

▪ With atomic deployments, we dramatically decrease the cost of an error by making it trivial to revert to a previous good state of our site.

▪ A challenge with creating multiple, immutable versions of our deployments is that the action of deploying a new version of our site, even a one-line change, requires the generation and propagation of a completely fresh instance of the entire site. This could result in the transmission of a lot of files, taking a lot of time and bandwidth

▪ intervention. A good experience for a developer might look like this:

Gain access to the project code repository.

Find up-to-date, versioned instructions on bootstrapping the project within the code repository, typically in a README file.

Clone the repository to a local development environment.

Run a single command to install project dependencies.

Run a single command to run a local build with optimizations for the designed development workflow.

Run a single command to deploy local development to suitable target environments.

▪ One of the key reasons that we need a more descriptive term than “static” to describe JAMstack projects is this rapid growth in the ecosystem rising to support and extend the power of this approach. Once, when we talked about “static” sites, we would most likely rule them out as candidates for specific use cases on the basis of some common stumbling blocks.

▪ Requirements like search, forms, notifications, or payments would rule out a static architecture for many sites.

▪ Consider products like Wufoo, Formkeep, Formcarry, or even Google Forms.

▪ Companies like SendGrid and Mailgun can add email messaging and are already trusted by a long list of technology companies that would rather not manage and integrate their own email messaging systems into their sites and services.

▪ Going further, companies like Twilio can add sophisticated messaging that goes far beyond just email. SMS, voice, video, and interactive voice response (IVR) are all possible through APIs.

▪ It is often remarked that being a web developer means that you need to always be learning new things. This pace is not slowing down. Thankfully, however, we don’t all need to be experts in all things.

▪ By embracing the specialist services available, we can take advantage of incredibly sophisticated and specialized skills that would be impossible to retain on each and every one of our projects were we to attempt to bring them all in-house.

▪ Although it might seem counterintuitive at first, by employing the specialized skills of, say, an identity provider, we can avoid the need to intimately understand, build, and maintain some of the more nuanced areas of providing identity, authentication, and authorization.

▪ The core intellectual property of your website is unlikely to reside in the code you write to implement how a user changes their password, uploads their profile picture, or signs in to your site. It is far more likely to reside in your content or your own set of services that are unique to you and your business.

▪ More and more regularly, economies of scale and domain expertise mean that providers can be more affordable and dependable than if we were to build comparable solutions ourselves.

▪ At the end of 2017, Smashing Magazine completely rewrote and redesigned its site to switch from a system based on several traditional, monolithic applications to the JAMstack.

▪ In its 10 years of operation, Smashingmagazine.com has evolved from a basic Wordpress blog to a large online estate, spanning multiple development platforms and technologies.

▪ Before the relaunch, the main magazine was run as a Wordpress blog with thousands of articles, around 200,000 comments, and hundreds of authors and categories. Additionally, the Smashing team ran an ecommerce site selling printed books, ebooks, workshops, and events through a Shopify store with a separate implementation of its HTML/CSS/JavaScript theme. The magazine also operated a Ruby on Rails app as its job board (reimplementing the Wordpress theme to work in Rails, with Embedded Ruby [ERB] templates) and a separate site built with a flat-file Content Management System (CMS) called Kirby (which brought an additional PHP stack, not necessarily in step with the PHP stack required by the main Wordpress site) for handling the online presence of Smashing Conference.

▪ All themes had to be duplicated among Wordpress, Rails, and Shopify, each of which adds its own individual requirements to the implementation;

▪ Smashing Magazine went through constant iterations of its caching setup to avoid outages when an article went viral. Even after considerable efforts, the site still struggled to reach acceptable uptime and performance goals. This effort introduced a great many plug-ins, libraries, and dependencies for Wordpress, Rails, and Kirby, resulting in a constant uphill battle to keep numerous Wordpress plug-ins, Ruby Gems, and other libraries up to date without causing breakage to themes or functionalities.

▪ Taking into account the key considerations, Smashing Magazine began exploring an architecture in which the frontend lives in just one repository and one format, all content pages are prebuilt and live on a CDN, individual microservices handle concerns like processing orders or adding comments and identity of users, and members can be delegated to one microservice. The JAMstack.

▪ Smashing Magazine evaluated several static site generators. It explored tools like Gatsby and React Static that included an asset pipeline and are based on Webpack. Those provide straightforward support for writing pure, client-side components in the same language as the templates for the content-based site. However, the performance when it came to pushing out tens of thousands of HTML pages in every build was not quite there.

▪ Ultimately, the need to achieve a rapid build time combined with the complex content model made Hugo the first choice. It was an ideal combination of performance and maturity.

▪ Many of the JavaScript-based generators are working to provide better support for incremental builds and large-site performance, but at the time of this writing, none of them could compete with Hugo in terms of its build speed, and they all fell short of the performance that Smashing felt comfortable with for a site of this volume.

▪ There are potential workarounds to the challenge of needing to generate a very large number of pages in the build, like only prebuilding some of the content and fetching the rest client side from a content API.

▪ A content-driven site needs to optimize for very fast performance on first view for all content-based parts of the site, and that means the framework must be tiny.

Preact fits that bill! It’s a 3 KB component framework (gzipped) that’s API-compatible with React. In comparison, jQuery weighs in at around 28 KB (gzipped).

▪ Some people intuitively think that something like the content from Smashing Magazine with thousands of articles and 10 years of history would be unwieldy to manage in a Git repository. But in terms of the pure number of plain-text files, something like the Linux kernel will make just about any publication seem tiny in comparison.

▪ However, Smashing Magazine also had about a terabyte worth of images and assets. It was important to keep these out of the Git repository; otherwise, anyone working with the site would have to download all of them, and each Git clone operation during the continuous deployment cycles would have been painfully slow.

▪ To work around that, Gulp was used as a way to add a few handy utilities. First, the full set of articles was added into a production-articles folder outside of the main content folder. Then, a Gulp task that could take an extract of 100 articles and move it into the actual content/articles folder was added.

▪ This way, everybody could work against a smaller subset of articles when doing local development and enjoy the instant-live reloading environment that JAMstack setups enable.

▪ For search, Smashing Magazine relies on a Software as a Service (SaaS) offering called Algolia that provides lightning-fast real-time search and integrates from JavaScript in the frontend. There are other alternatives like Lunr that don’t depend on any external services and instead generate a static index file that can be used on the client side to search for content.

▪ For large sites, however, a dedicated search engine like Algolia will perform better.

▪ Smashing Magazine ended up using a combination of Preact and Redux for all the dynamic frontend components.

▪ In general, it’s advisable to always have fallbacks where possible when JavaScript is not available, while recognizing that for modern web projects JavaScript is the main runtime, and most dynamic interactions won’t work with the runtime disabled.

▪ Git-based CMSs integrate deeper into the Git-centric workflow and bring full version control to all your content. There are inherent advantages to having all content stored in a Git repository as structured data. As developers, we can use all the tools we normally use to work on text files (scripts, editors, grep, etc.), while the CMS layer gives content editors a web-based, content-focused UI for authoring or management.

▪ Smashing Magazine chose to build the content-editing experience on the open source Netlify CMS to get the deepest integration into Git, the best local developer experience, and the fastest build times. For an authoring team as technical as Smashing Magazine, the option of sidestepping the CMS and working directly in a code editor to tweak code examples or embedded HTML is a huge advantage over any traditional, database-driven CMS.

▪ For really large sites like Smashing Magazine, this approach begins breaking down. Smashing Magazine has more than a terabyte of assets in the form of uploaded images, media files, PDFs, and others that’s much more than it would ever want to store in its Git repository. Apart from that, GitHub’s API begins breaking down for content listings when there’s more than 2,000 files in a folder—obviously the case for Smashing Magazine’s article collection.

▪ Every architectural decision we make as developers has some trade-offs. When we work with a Git-based architecture, we might need to supplement our toolchain with asset stores, external search engines, and the like, but few developers would voluntarily agree to the trade-offs that come with storing all their code in an SQL database.

▪ When working with traditional monolithic applications, we typically have a built-in concept of a user that’s backed by a database collection and integrated throughout the monolithic application.

▪ This was one of the challenges of Smashing Magazine’s previous architecture: each of the monolithic applications it relied on (Wordpress, Shopify, Kirby, Rails) had its own competing concept of a user.

▪ An important part of the answer to this is the concept of stateless authentication. Traditionally, authentication was stateful in the sense that when doing a page request to a server-rendered app, we would set a cookie with a session ID and then the application would check that against the current state in the database and decide the role, display name, and so on of the user based on this lookup.

▪ Stateless authentication takes a different approach. Instead of passing a session ID when we call a microservice, it passes a representation of the user. This could look something like the following:

{
"sub": "1234",
"email": "matt@netlify.com",
"user_metadata": {
"name": "Matt Biilmann"
},
"app_metadata": {
"roles": ["admin", "cms"],
"subscription": {
"id": "4321",
"plan": "smashing"
}
}
}

▪ Now each microservice can look at this payload and act accordingly. If an action requires an admin role, the service can check whether app_metadata.roles in the user payload includes an admin role. If the service needs to send an order confirmation to the user, it can rely on the email property.

▪ This means that each microservice can look for the payload information it needs without having any concept of a central database with user information and without caring about which system was used to authenticate the user.

▪ JSON Web Token (JWT) is a standard for passing along this kind of user payload while making it possible to verify that the payload is legitimate.

▪ This means that any microservice that knows the secret (or has a corresponding public key) can verify that the token is legitimate and trust the payload.

▪ Normally, a JWT will always have an exp property that sets the expiration time for the token. A short expiration time ensures that if a token is leaked in some way, there’s at most a short time window to exploit it and it can’t simply be used to take over the role of a user.

▪ For that reason, JWTs are typically paired with a refresh token that can be used to retrieve a new JWT from the authentication service as long as the user is still logged in.

▪ The Auth0 team that pioneered this standard maintains a useful resource where you can find more in-depth information and debugging tools for inspecting and verifying tokens.

▪ With a naive approach to stateless authentication, every microservice in the Smashing Magazine system would need to know the same secret in order to verify the user payload. This increases the risk of leaking the secret and means that every service would be capable of issuing its own valid JWTs instead of limiting the capability to just the main identity service.

▪ One approach to get around this is to use a signing algorithm that relies on private/public cryptographic keypairs. Then, all the services will need to look up a public key and use it to verify that the signature was generated with a private part of the key pair. This is efficient but can introduce quite a bit of complexity around having to fetch and cache public keys and gracefully handle public key rotations.

▪ Another approach is to have an API gateway between the client and the different microservices. This way, only the gateway needs to share the secret with the identity service and can then re-sign the JWT with a secret specific to each individual microservice. It allows the system to rotate secrets independently for different services without running the risk of sharing secrets across multiple services (where some might even be owned by third parties).

▪ User sessions are saved in localStorage, so the UI can access the user payload and use it to show the user’s name where it makes sense or pass on the JWT to other microservices where it makes sense.

▪ Pulling this off does require a high level of maturity in automation, API routing, secrets management, and orchestration of your serverless code, with a viable workflow and a solid, maintainable stack.

▪ Smashing Magazine moved from a system built from four traditional monolithic applications, with four independent frontend implementations of the same visual theme that had been adapted to the quirks of each platform, to a setup in which the entire implementation was driven by and based on one single static frontend talking to a set of different microservices using a few serverless functions as the glue in the middle.

▪ Anyone can run the full production site locally just by doing a Git clone of the repository and spinning up a development server, with no need to set up development databases. Any pull request to the site is built to a new preview URL where it can be browsed and tested before being merged in—including any new article that the team is preparing to publish.

▪ Though tools like Netlify CMS or the GoCommerce store admin are not currently as mature as the tools with 15-plus years of history, and there are still some rough edges to be worked out, it’s without a doubt that the Smashing Magazine team has benefited significantly from this shift. And perhaps more important, so have its readers. 
