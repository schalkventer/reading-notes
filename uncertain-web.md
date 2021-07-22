"The best way to approach the Web today is to forgo hard-and-fast rules and design for uncertainty."

"In the early 2000s, there was basically one browser (Internet Explorer 6), one platform (Windows XP), and one screen resolution (1024 × 768) that mattered. With that setup, you could design, develop, and test the vast majority of web users with one desktop computer. The biggest question on the horizon, it seemed, was when it would be viable to design for 1280-pixel screens."

"Best practices were honed and codified into hard-and-fast rules that drove design and development. Major choices, such as the size of the basic design grid, were no longer choices. Everyone started with a static, 960-pixel grid and then sliced and diced it as needed."

"Initially, developers and designers tried to navigate this new reality by creating new rules. But the problem was that the goalposts kept moving. As soon as a new hard and fast rule was created, some new wrinkle would render it impotent."

"People designed and built iPhone sites, assuming that Apple’s dominance in the smartphone market was a permanent condition. They tested for touch capabilities and assumed that touch users would never have a mouse. As Android’s huge growth over the past few years, and the presence of Chromebooks and Windows 8 laptops with both mouse and touch capabilities have proved, those new rules have a short shelf life."

"The evolution of the Web as a development platform and the incredible growth in the number of web-enabled devices has pushed the Web into places it could never have reached before."

"The thing is, most of the time, front-line developers don’t get to spend time looking at the big picture. You know how it is—it’s usually a challenge just getting the next release out the door. Whether you’re building a site for a client, working on the latest version of your JavaScript framework, or simply trying to make sure people can read the text on your blog, there’s not a lot of time available to muse about the way the Web as a whole has changed. Instead, you focus on solutions to individual problems, because those are the ones keeping you from going home at a reasonable hour."

"Whether it’s searching for the perfect test to detect a “mouse” user versus a “touch” user or designing a responsive site for the “perfect” set of media query breakpoints, there are many developers still trying to hammer out absolute rules and rigid best practices. People are clearly looking to develop sites and applications within clearly defined boundaries. Although that can be a comforting idea and was once possible, those days are long gone. It’s time for a new approach."

"Today’s Web is a wild place. The Web has never been a static platform, no matter how much people might wish it were so. You just can’t control who’s going to request your content. You can’t control the browser or device they’re using, and you certainly can’t guarantee things like the operating system, screen resolution, bandwidth, or available system fonts. For developers coming from pretty much any other discipline, the number of things that are out of the developer’s control can be mind-boggling."

"That statement will only grow more true with every passing day. Standards are changing on, in some cases, a daily or weekly basis, new devices are coming online at a furious pace, and browser vendors are going at it tooth and nail to innovate their way to the top of the league tables. With an ecosystem like that, trying to collapse everything you do as a developer into something that can fit into a neat little box is a recipe for frustration."

"The following sites are where modern web design and development are being figured out. These sites have all directly influenced the development of this book: HTML5 Rocks—A resource for Open Web HTML5 developers LukeW Ideation + Design | Digital Product Strategy & Design QuirksMode—for all your browser quirks Web Hypertext Application Technology Working Group The Modernizr issue tracker on GitHub CSS Tricks A List Apart: For People Who Make Websites"

"The web platform is Write Once, Cry Everywhere. — Yehuda Katz "

"The thing is, while all that is great and I thank my lucky stars that I’ve had this career, what I really love about the Web is that it made good on its early promise. It might have sounded a little hokey or looked like just hype to fill a five-minute slot on the evening news, but the Web really has managed to connect people in incredible ways—ways we couldn’t even have imagined 25 years ago. Individuals who would never have had a voice can now broadcast to the world with blogs, YouTube, Twitter, and Facebook. Politicians, filmmakers, video game developers, and anyone else with an idea can tap into the power of individuals to finance their dreams, five dollars at a time."

"Lessons from the world’s great universities like Stanford and MIT, as well as lessons made directly for the Web from organizations like Khan Academy, are available for free to anyone in the world who can connect to the Web. With sites like GitHub, taking part in open source software is as easy as firing up a web browser and finding a place to help out with even the most massive open source projects like jQuery, Node.js, or Ruby on Rails. It’s only getting better. As more and more people come online, they’re exposed to these same opportunities and start to feed back into the system with a unique voice: hard work on some open source bug, adding to the coverage of breaking news (say, sharing a photo of a plane landing on the Hudson River), or something as simple as buying a business cat tie on Etsy and turning the wheels of commerce. It’s really pretty cool."

"Embracing uncertainty means that we need to make the final leap away from the search for absolutes in order to appreciate the Web for what it actually is. As we’ll examine in this chapter, it’s a place where a wide range of devices running a wide range of web browsers in the hands of many different kinds of people are all trying to find their way to something that matters to them. Whether it’s a farmer in Africa trying to figure out the score of the latest Manchester United match, a banker in Hong Kong trying to get a price for Bordeaux futures, or a small business owner in the United States setting up an Etsy shop, the Web is making important connections for people, and we need to help them on their way."

"The next, most important step is not only to accept that you can’t control the browser and device environment, but to embrace the ecosystem for what it is—a sign that the Web is a healthy platform. Tens of thousands of browser/device/OS combinations is a feature of the Web, not a problem."

"I talk to a lot of people, and there are plenty of complaints about the Web as a platform. I’m not talking about specific complaints about specific features. I’m talking about complaints about the Web itself."

"Instead of worrying about the fracture in the Web and wishing that it was something else, accept the Web for the blessing that it is. And it is a blessing. Because the core technology can run, unaltered, on billions of devices in the hands of billions of people, you have immediate access to all of those billions of people and all of those billions of devices. How great is that?"

"In the early 2000s, there was basically one browser, one platform, and one screen resolution that mattered. You could test the experience of the vast majority of your users, with excellent fidelity, simply by running Windows XP with Internet Explorer 6 and switching between a couple of different screen resolutions (i.e., 800 × 600 and 1024 × 768 pixels). Add in Internet Explorer 5 and 5.5, and you could hit, by some estimates, more than 95% of the Web. In the end, Internet Explorer held market share of near or above 90% for most of the first half of the 2000s."

"So, instead of having a couple of machines dedicated to testing and getting 95% coverage, anyone who really pays attention to this stuff can have a testing lab with 50 or more devices and still struggle to cover the same high proportion of the Web that was possible during Microsoft’s heyday."

"These streams are as follows: Microsoft’s Trident, which powers Internet Explorer "

"Browsers based on the WebKit open source project "

"Browsers based on the Blink open source project "

"Mozilla’s Gecko, which runs under the hood of Firefox "

"In addition to the rendering engine, each of these streams has an associated JavaScript engine, which completes the core platform functionality for each when packaged as a web browser."

"These JavaScript Engines are as follows: Chakra This is used in Internet Explorer."

"SquirrelFish Extreme/Nitro It’s the JavaScript engine for WebKit. "

"V8 This is the JavaScript engine used in Google Chrome and Blink-derived versions of Opera."

"SpiderMonkey It’s the JavaScript engine in Firefox. "

"Opera Mini If you don’t pay attention to the mobile browser space, it might surprise you how popular this browser is on mobile devices. Data is sent through a proxy server and compressed, saving you time and data. There are a lot of versions of this out there. You will see examples from the 4, 5, and 7* versions in the wild. "

"UC Browser This is a mobile, proxy browser based on the WebKit rendering engine. It’s popular in China, India, and other emerging markets. "

"It’s important to know what’s out there, and it’s imperative to test against as many of these browsers as possible, but it’s rarely useful, when you’re sitting down to develop a site, to fixate on the ins and outs of any one particular browser or to target code specifically for certain browsers or browser versions. For starters, it’s an overwhelming list, and if you try to fork your code based on every browser and version, you’ll end up playing the world’s worst game of Whack-a-Mole. Instead, for development, you need to think in terms of features. This concept, feature detection (versus browser detection) has been a common concept in web development for a long time, but now it’s more important than it’s ever been."

"the core concept is not to ask “What browser is this?” It’s to ask “Does your browser support the feature I want to use?”"

"That will help you if some new, suddenly popular browser makes an entry into this list, sometime in the future. Which is probably going to happen sooner than you think."

"Although the Web has always been a wonderfully messy and vibrant place, where sites can go from a sketch on the back of a napkin to a headline-making enterprise with a billion-dollar valuation in the course of a few months, the World Wide Web Consortium (W3C), the organization responsible for the standards that the Web is built upon, often moves more like it’s overseeing transatlantic shipping in the 1800s."

"The reality on the Open Web was different than any perception of “orderly progress.” Out in the real world, the Web was busy taking over. Fueled by a heady mixture of popular interest, maniacal hype, gobs of money, and (for many people) an honest belief in the Web as a platform with the power to change the world, the Web was very quickly being pushed and pulled in directions the standards bodies never dreamed of when they were drafting their documentation. Compare the needs of the Web of the mid-1990s, when these standards documents were being written, to the Web of the dot-com era, and you’ll see why so many problems fell to the creativity of web developers to solve. People had to be clever to bolt together solutions with the existing, somewhat limited, set of tools that were available."

"All that really needs to be said about the immediate effectiveness of the late 1990s standards work is that the era that directly followed it was dominated by Adobe Flash as the platform of choice for anything even remotely interesting on the Web."

"From organizations like the Web Standards Project (WaSP) and the wildly influential mailing list/online magazine A List Apart, and through the work of individuals like Peter Paul Koch and Eric Meyer, the fundamental technologies that drove the Web were being reevaluated, documented, and experimented with at a furious pace."

"The WHATWG was born at the W3C Workshop on Web Applications and Compound Documents in June 2004. This W3C meeting was organized around the new (at the time) W3C activity in the web application space and included representatives from all the major browser vendors, as well as other interested parties. There, in the first 10-minute presentation of session 3 on the opening day of the two-day event, representatives from Mozilla and Opera presented a joint paper describing their vision for the future of web application standards."

"It presented a set of seven guiding design principles for web application technologies. Because these principles have been followed so closely and have driven so much of what’s gone into the specifications over the last several years, they’re repeated in full here."

"The specifications are as follows:"

"Backwards compatibility, clear migration path Web application technologies should be based on technologies authors are familiar with, including HTML, CSS, DOM, and JavaScript. Basic Web application features should be implementable using behaviors, scripting, and style sheets in IE6 today so that authors have a clear migration path. Any solution that cannot be used with the current high-market-share user agent without the need for binary plug-ins is highly unlikely to be successful."

"Well-defined error handling Error handling in Web applications must be defined to a level of detail where User Agents do not have to invent their own error handling mechanisms or reverse engineer other User Agents’."

"Users should not be exposed to authoring errors Specifications must specify exact error recovery behaviour for each possible error scenario. Error handling should for the most part be defined in terms of graceful error recovery (as in CSS), rather than obvious and catastrophic failure (as in XML)."

"Practical use Every feature that goes into the Web Applications specifications must be justified by a practical use case. The reverse is not necessarily true: every use case does not necessarily warrant a new feature. Use cases should preferably be based on real sites where the authors previously used a poor solution to work around the limitation."

"Scripting is here to stay But should be avoided where more convenient declarative markup can be used. Scripting should be device and presentation neutral unless scoped in a device-specific way (e.g. unless included in XBL)."

"Device-specific profiling should be avoided Authors should be able to depend on the same features being implemented in desktop and mobile versions of the same UA."

"Open process The Web has benefited from being developed in an open environment. Web Applications will be core to the web, and its development should also take place in the open. Mailing lists, archives and draft specifications should continuously be visible to the public."

"The paper was voted down with 11 members voting against it and 8 voting for it. Thankfully, rather than packing up their tent and going home, accepting the decision, they decided to strike out on their own. They bought a domain, opened up a mailing list, and started work on a series of specifications. They started with three:"

"Web Forms 2.0 An incremental improvement of HTML4.01’s forms. Web Apps 1.0 Features for application development in HTML. Web Controls 1.0 A specification describing mechanisms for creating new interactive widgets. "

"Web Controls has since gone dormant, but the other two, Web Forms and Web Apps, eventually formed the foundation of the new HTML5 specification."

"Score one for going it alone. As was mentioned, they’ve stuck to their principles over the years. Arguably, the most important of these principles is the very open nature of the standards process in the hands of the WHATWG. Before the birth of the WHATWG, the standards process and surrounding discussion took place in a series of very exclusive mailing lists, requiring both W3C membership (which costs thousands or tens of thousands of dollars, depending on the size and type of your organization) and then specific inclusion in the particular Working Group under discussion."

"Instead of that exclusionary approach, the WHATWG made sure its activities were taking place in the open. If you subscribed to the mailing list and commented, you were suddenly part of the solution. This has led to vibrant, high-volume discussion feeding into the standards process."

"There are still many people involved who are far removed from the day-to-day business of making websites and applications, but there’s also a constant stream of input from people who are knee deep in building some of the biggest sites on the planet."

"Everyone isn’t happy all the time, but the process works. Even with the hiccups and flame wars, things move much more quickly than they did at any period before the WHATWG was founded, and there’s less confusion about how the decisions are made, even if people don’t agree with them."

"HTML and related APIs Main development of what’s referred to as the “living standard” happens with the WHATWG. The mailing list archives are also online. This work is an ongoing extension of the work done for HTML5. A so-called “snapshot specification,” HTML5 is currently a candidate recommendation at the W3C. "

"CSS CSS development has been broken down into smaller modules. CSS 2.0 was a monolithic specification that covered everything to do with CSS. For CSS3, the decision was made to break down the specification into specific features. This means there are some modules further along in the development process than others. The W3C’s big list of modules is available here. "

"ECMAScript The ECMAScript mailing list is where all the action happens. "

"Another downside is that people, in the rush to implement new features in the browser or to experiment with them on the Web, sometimes make mistakes. Whether it’s a poorly vetted specification; the well-meaning, but awkward decision to prefix experimental CSS features; the tendency of “new” HTML5 features to occasionally go away (like the loss of the hgroup element or the disappearance and subsequent reappearance of the time element); or the decision to implement an alpha feature in a site meant for human consumption, only to see it break in a later version of the target browser; the rush for the new and shiny has had its share of casualties over the past few years."

"Navigating this space is important, though. As you’ll see in one example in the section on responsive images in Chapter 6, following the standards discussion, learning about potential JavaScript solutions, and implementing standard stable patterns can produce great long-term benefit for your site. It’s just sometimes tough to figure out when something is really stable, so the closer you can get to the discussions, the better. Not many people have the time needed to be involved in even a single feature discussion as an active participant, forget about the mailing list as a whole, but you really should have time to at least monitor the subject lines, checking in where applicable."

"This is especially true if you have a global audience. The whole continent of Africa, home to more than one billion people, basically skipped over the desktop altogether and will only ever connect to the Internet using a mobile device on networks of unknown quality."

"With the flood of touchscreen devices, the picture became even more complicated. Everything from the size of buttons to the use of hover effects had to be reevaluated."

"The thing is, it’s not really a binary choice. From Windows 8 laptops to Chromebooks and even things like the Samsung Galaxy Note with its hover-capable and fine-grained stylus, there are many devices that can have a mouse, or mouse-like implement, in the case of a pen or stylus, and be a touchscreen at the same time."

"Producing robust interfaces that work with a keyboard, mouse, finger, or with a hand waving through the air (like it just doesn’t care) is one of the most important challenges you face as a web developer today."

"One of the legacies we’ve dealt with as we transitioned from the world of print to the world of the Web was the desire for designers to have pixel-level control over every aspect of their designs when ported to the Web. This was somewhat possible when we had a limited set of screen resolutions to deal with and people designed fixed-width designs. These days, it’s significantly more complicated as more and more designs are based on flexible grids, and the number of display resolutions has grown out of control."

"It’s down to the point where things like the question of doing any preliminary design is on the table for some applications. These days, some people rely instead on quick, iterative design and refinement to create the look and feel for a site. This won’t work for something whose sole purpose is to be a thing of beauty, I imagine, but for a lot of sites, it’s a wonderful option."

"Based on your needs and requirements, you might be perfectly justified in many different support configurations. Although I strongly believe in supporting the largest possible percentage of web users, I also recognize that reality dictates certain support strategies. For example, working in financial services or health care, two industries that I’ve done a lot of work in, might require that I treat Internet Explorer 8 as a first-class browser."

"You, on the other hand, might be working on a site that caters to web developers and designers and might not see even 1% of your visits from IE8. So, instead of treating it as a first-class experience, you could provide simplified, alternative content or even devil-may-care support to IE8 users because that’s not your audience."

" It’s useful to go examine your audience in this way whenever you’re crafting support strategies. You might think you’re comfortable with ignoring a certain browser from your testing plan, but then when you crunch the numbers and truly examine the makeup of your audience, you might realize that you’ll probably need to spend some time testing in it or even craft some sort of optimized solution."

"That might mean you don’t care because you have zero Chinese audience, but 100,000,000 users still means this is a choice you should make actively and not just with the wave of a hand because IE6 is annoying. If you’re starting a site design and you’re a global company, you have to ask yourself if you can safely ignore those users."

"Maybe you can, but it’s safer to look at the question with as much information as you can muster instead of blocking your eyes and ears and assuming it’ll all be OK. That way, when someone asks why you did or did not prepare for IE6, you can give a reasoned response."

"This isn’t to say that you are somehow required to actively support any of these browsers. Not everyone has enough resources to design and develop for, test, and fix bugs across every device and browser. That said, it is important to keep some perspective and know what it really means when you’re chewing over some of these numbers. At the end of the day, they may not matter to you, but you can’t really make that decision unless you know what decision you’re actually making."

"Also, with the number of cloud-based testing environments on the market and the fact that most design teams will have a variety of smartphones in the pockets of various members of the team, getting basic coverage isn’t that hard if you decide to go for it."

"Freaked out? Paranoid that the ground underneath you will shift at any moment? Good. Because it will. I’m not the type to predict things like space hotels and cryonic suspension in order to emigrate into the future, but I can tell you there will be new devices, form factors, Open Web Platform features, and human–computer input modes that you’ll have to deal with as a web developer for as long as the role exists. And really, this is the way it should be. The only reason everything was allowed to go dormant in the early 2000s was because competition in the space disappeared. Once true competition returned, the natural way of the Open Web, which is to be as crazy as I’ve just described it, returned with a vengeance."

"The good news is, all of these devices, form factors, and browsers all share one thing. They work on top of the Open Web Platform: HTML, CSS and JavaScript. If you seize on this shared platform and try to create the best possible experience for the broadest possible range of devices, you’ll be able to reach users in every nook and cranny of the globe."

"Additionally, it will cement these concepts if, while reading this chapter, you start to apply these concepts to the kind of problems you face in your day-to-day job."

"If you’re at an agency and building 2–25 projects a year, you’re going to have different needs than a product person who might work on 2–3 releases of the same project every year, and you’re going to seize on different aspects of this as important to you."

"The one thing that I’ll ask is that you read through this chapter with an open mind."

"We’ve already defined that the Web is a diverse place that’s getting more diverse every single day. That’s pretty much impossible to ignore. So, if you accept the Web’s diversity (and maybe even celebrate it), and you’re getting angry about one thing (maybe Internet Explorer 8) or another (the stock Android Browser), just take a minute to remind yourself that this is just the way the Web is."

"Getting yourself worked up about the Web having a spectrum of browser quality is like getting mad at the ocean for being wet. It’s the price we pay for having access to anything that can connect to the Web."

"The ability to deal with a varied environment gracefully is going to be one of your greatest strengths as a web developer."

"I’ve worked with, managed, and hired a lot of frontend engineers over the past 15 years. Without fail, the best ones were the ones that knew this intuitively."

"Even in the United States, where older versions of IE are dying off, the numbers of pre-IE8 users in health care and finance are much higher than the rest of the Web as a whole. Like the users in China locked in by the regional administration requiring IE6, these users are often locked in because of the software requirements of legacy systems. Two of the largest companies I’ve worked with as a consultant were running Internet Explorer 7 as the only supported internal web browser until 2013. With both, I was focused on a broad range of browser support on my projects, so it wasn’t like I was stuck in an IE7 time-warp, but it did factor into some of the decisions we made when building sites in those environments. I mean, if a site doesn’t work on the CEO’s computer, then it doesn’t matter how well it plays in Chrome."

"Whatever you’re doing, there are going to be types of users you’ll really focus on. It might be everyone in the whole world on any web-connected device, or it might be mobile users from emerging markets. It’ll probably be something in between."

"For example, continuing with SVG as our key feature, imagine you’re building a site to track workouts of runners. It will rely heavily on SVG in order to create interactive visualizations of the runner’s pace, heart rate, and other metrics. When you’re working through these kind of questions, you’ll want to leverage the site Can I Use… heavily (Figure 2-3). Can I Use provides simple access to support matrices for a huge number of web platform features. Popping over to the SVG support page, you learn that native support for SVG is present in everything but older Internet Explorer versions and older Android devices."

"This is a lot of work, but to really get this stuff right, you’ve got to do some hard work. That includes testing."

"Whatever your scheme, the takeaway here is to become dedicated to testing as often as you can in as many browsers and devices as you can. "

"No browser is completely dominant anymore and the landscape is completely wide open, so getting as good an experience as possible in as many browsers as possible is the way to go."

"Testing on a lot of real devices can uncover improvements that will improve your site in ways that you can’t predict and will expose you to the experience your users are likely to see. "

"If the feature or design element was nonessential, my first instinct was always to push back for a simplified design in the offending browser. If there was strong resistance, even after explaining the development or performance cost of a workaround, I’d have to go into a well-practiced spiel about why it was OK to present slightly different visions of the site to different browsers. If I were smarter, I could have just thrown up Do Websites Need to Look Exactly the Same in Every Browser?, and the answer would have been seen as clear as day"

"Not that it would have made much of a difference. At one point, there was an idea, born out of print production I think, that the design of a site was an absolute thing. The look of a site in the PSD would be, to the pixel, the look of the site in every browser across every platform. As frontend developers, we were driven to extremes in order to achieve pixel perfection across browsers and operating systems, often having to explain things like the difference between scrollbars or form elements on the Mac and PC being something we couldn’t really work around."

"When you bundle in the dozens of viable browsers and devices out there, there are so many places where the look of a site can diverge that it would be practically impossible to actually design an absolute look and feel for every possible permutation. An army of Photoshop production artists would be needed to craft all those pixels. Font rendering, pixel density, web platform feature support, screen resolution, screen aspect ratio, and a slew of other factors all aid in the divergences of sites from browser to browser and device to device."

"So, as important as it was in 2008 to understand that adding rounded corners to a box in IE6 wasn’t worth the effort, understanding that things will look differently across platforms, browsers, and devices is now a fundamental concept of web design and development. You will invariably have dozens of differences in the rendering of your site on different browsers and platforms. And that’s OK."

"This idea needs to be part of your site’s DNA. Your site is not an absolute thing. There is no one true vision of it. The best possible site you can have will be the best possible site for everyone that visits it. "

"The tough part of this is getting the message across to all the different stakeholders on a project. It’s easier than it once was, because as I’ve mentioned, people are already used to seeing differences with different devices, but it’s still something that you need to prepare people for from the start."

"In general, the goal with accessibility standards is to ensure that content is served and structured in such a way that users with disabilities can access it directly, or if direct access isn’t possible because of their disability (audio content for a deaf user or a visual chart for a visually impaired user), to provide alternative content that conveys the same information."

"You’re also doing the right thing. It’s not all that difficult to create accessible sites, and the benefit for people with disabilities is enormous."

"And, if doing the right thing isn’t enough, as a bonus, creating accessible sites has the side effect of making your sites more usable by everyone and more compatible for all users."

"Unfortunately, the behavior of this feature is cranky on mobile. This text is displayed almost universally on the desktop. The behavior of mobile browsers is varied. Figure 2-5 shows Firefox, iOS Safari, Chrome, Opera Mini, and Opera displaying a page with a broken image. Only two of the five display the alternative text. This is a defect that needs to be corrected. The original bug, with WebKit, took eight years to fix (too late for the iPhone and stock Android browser in these screenshots). Hopefully, the related Blink issue will be fixed sooner rather than later (and fix Opera and Chrome)."

"Additionally, low bandwidth or bandwidth-metered users might have images turned off, which is an option that’s available in mobile browsers like Opera Mini (see Figure 2-6)."

"Alternative text is likely the accessibility you’re most familiar with, but it’s important enough to ensure that you’re using them to proper effect. This checklist from the a11y Project is a good place to start with improving your alt text."

"You want your pages to make logical sense without styles and without JavaScript. If you can satisfy both of those requirements, you’re in really good shape. One way to test how well you’ve structured your content is to view the document’s outline as defined by the HTML5 specification. If your document outline looks like a well-structured table of contents, then you’re probably on the right track."

"Many other big sites also have rich keyboard options built into their interface. Type “?” on any of your favorite sites to see if they, too, have keyboard shortcuts defined. Here’s the overlay showing GitHub’s rich selection of keyboard shortcuts (Figure 2-8). ￼ Figure 2-8. Keyboard shortcuts on GitHub.com"

"Operating a phone with one hand, in the cold, while on the move, trying to get to an appointment on time? Yeah, that’s exactly the time you want to have to sort through some random noise on a page looking for the “contact us” link."

"For someone living that experience, and we’ve all lived it, having a clearly labeled “contact us” link with a big fat button that takes users to a simple list which includes your telephone number is worth more for the customer’s experience than pretty much anything else you can do on the Web."

"USA.gov handles this without any fuss, providing a clearly labeled tel protocol link at the very top of its homepage in responsive mode. There’s no mystery here how to get in touch with them, and the telephone link is available without a second click (Figure 2-9). ￼ Figure 2-9. An easy-to-use phone link on USA.gov"

"Forms are generally neglected as a drudgery, even by browser vendors. Adding a new input for telephone numbers isn’t nearly as sexy as adding WebGL and coding a JavaScript port of Quake. The thing is, people make money on the Web with forms—filling them out for a status update or tweet or to buy a book on Amazon. The more time and care you spend on your forms, the better off you’ll be."

"The fact that the first website ever made still works is a guiding principle here. Don’t back yourself into a corner, and you’ll be sitting pretty in 2025."

"Tech folks generally have great hardware and new, high-powered smartphones and tablets. Most other people in the world don’t. Tech folks tend to forget that."

"I know what you’re thinking. Your company is super cheap. They haven’t bought you a new laptop in two years. You don’t even have a solid-state disk drive. Oh, the humanity. Cheap is a relative measure. On the hardware side, even with companies that are “cheap” with developer hardware, where the computers might be two or even three years old, you’re not doing so poorly. Those machines were high powered when they were new. They have a ton of RAM and have had a corporate IT department whacking them into shape with updates and maintenance. You probably have two huge monitors and are on a monstrous network. The average consumers are going to buy the cheapest machines they can find, and then they’ll run them into the ground. There are certainly exceptions to this—gamers come to mind—but for the most part, assuming great hardware is a mistake."

"None of these setups are anywhere close to the experience of the average user. Thinking that the typical developer and designer experience is at all “typical” and developing toward it is a longstanding problem, one made much worse by the broad variation of devices, operating systems, and browsers in the current ecosystem. There are many examples of where this can be a real problem."

"As we’ve discussed, there are underpowered mobile devices, old desktops, and old browsers aplenty out there waiting to expose problems with your site. And really, with some of these setups, it’s not just a question of poor performance. You can easily trip long-running script errors, freeze the screen, and even crash the browser if"

" It’s just that any of the latest generation browsers are so fast that, coupled with good hardware, they’re going to mask problems that older browsers or crummy hardware will choke on. It’s said so often that it’s a cliche, but the reality is that it can “work on my machine” only to fail on some other hardware/browser combination"

"I’ve done a lot of consulting and agency work for health-care companies, financial services firms, and law firms. There’s a lot of Internet Explorer in those industries. As I mentioned previously, it’s often the only browser allowed on internal networks."

"Don’t blind yourself to what your audience actually is by assuming that they are just like you. They’re not. Your average experience at work, at home, or on your phone is almost certainly an optimal view of your site. Make sure you look at it, really look at it, in every scenario you can muster."

"Sure, we’re all guilty of demoing code under the best possible circumstances. That’s natural. The thing is, that demo is the ideal vision of your site. The thing you’re actually building, the down-and-dirty version, is for people with a completely different relationship with technology than yours."

"Although I do think limiting the number of available tools is useful (because having everything available to everyone is just crazy), I don’t think, in this day and age, proscribing a definitive frontend stack is useful. I’m a proponent of using the right tool for the job, so the search for the “one stack to rule them all” seems like a waste of time to me. If you craft a perfect stack for creating single-page apps and then end up building a bunch of page-to-page content sites, you’ve wasted time and resources with a stack that’s not suited for the work you’re doing."

"a lot of the main differences are, so depending on your target audience and the skill level of your team, you might be able to skip it."

"In order to save those bytes, it’s an option to write raw JavaScript or potentially leverage a smaller, jQuery-like library like Zepto.js (10 KB) instead. It might seem like a small gain, but if you’re in the mindset of trying to save every possible byte, it is an option."

"MVWhatever One of the hottest areas of innovation on the frontend over the past few years has been the creation of frontend model-view-controller (MVC) style libraries and frameworks."

"Although many of them quibble about the acronym (MVVM, MVP), they all bring a common backend pattern to the frontend and enable a new approach to frontend application development."

"Angular, Backbone, and Ember are all popular entries in this space. They are powerful alternatives to the DOM-centric approach of libraries like jQuery and the general DOM-based application development we’ve been practicing for many years"

"The thing is, these libraries and frameworks are really designed for application development, so although they are super powerful tools, they shouldn’t be grabbed for in every circumstance."

"For example, using one of these libraries in place of tried-and-true server-side templating for a content site doesn’t make sense. "

"It’s very much the same sort of pattern (variables from some data source are plugged into some sort of text-based templating engine), but there are no real benefits to doing it on the frontend."

"When we first started learning about web performance, one of the fundamental lessons was that most of the performance hits on the page happened in the browser, not on the server."

"Templating on the server wasn’t a performance problem for most people. Why, then, are we rushing headlong to push functionality that was handled perfectly well by the server down to the frontend?"

"Why, when the goal is to simplify and lighten the payload in the frontend, are we willingly passing a task that was solved 15 years ago on the server to the browser?"

"Having to download a framework, as well as any other dependencies, is going to slow your site down. Downloading Ajax requests with the content data, parsing it, and inserting it into the DOM is also a performance penalty. We’ve learned to minimize the number of DOM traversals and manipulations. Why add more when the server can send a rendered page on the back of one HTTP request? It doesn’t make sense."

"Also, if, for some reason one of the JavaScript resources doesn’t load, someone visits with an old browser, or someone visits with JavaScript turned off, you might end up with nothing but a blank page. That’s just awful. Use these powerful frameworks responsibly."

"Of course, it’s usually much messier than that. Web standards can be downright ugly at times. The multiyear, multiproposal, multicontroversy responsive images slow-motion trainwreck is a prime example of that. Four sometimes acrimonious years of proposals, setbacks, counterproposals, and flame wars have finally brought us a full suite of solutions to the responsive image use case, but the journey has been a tough one."

"Hopefully this chapter has already gotten you thinking about the way you’ve approached web development up until now. I’m assuming at least half of you think I’m an idiot. If so, I must be onto something."

"Whatever percentage of these concepts you agree with or feel are applicable to you and your particular situation, the biggest takeaway is the urge to question your assumptions. The things you hand-wave away might just be fine. Or they may be a problem causing some percentage of your users to have a crummy experience. You can’t know the difference unless you take a second to really understand the issue."

"I am the last and highest court of appeal in detection. — Sherlock Holmes, The Sign of the Four "

"One of the greatest challenges in developing modern websites is managing the broad range of device and browser capabilities present in the current ecosystem."

"One of the core ways to do this is via feature detection, testing for the presence of specific web platform features. This is compared to doing browser detection by looking for specific characteristics in the user agent string and coding for some specific version of Mobile Safari or Internet Explorer. That’s the way people used to do things. There are still some use cases for doing browser detection (one is actually covered in the next chapter), but most of the time you want to think about feature detection, which is the concern of this chapter and is the more commonly recommended approach in modern web development."

"If you’re looking to do broadly available sites and applications, then mastering Modernizr is vital to your well-being."

"For a playful, but still instructive example, testing for native Emoji rendering support in browsers is more complicated than the average feature detection. Because you need to test for the full cartoon rendering of the glyph, and not just a flat character, the test fires up an instance of the Canvas 2D context to read in the Emoji character and test that a selected pixel is in color:"

"There are many other web features that require the same or even a greater level of understanding. I don’t care who you are, there are going to be examples of advanced feature detection that are going to be outside your area of expertise. If you run into one of those, like the three mentioned previously, or other examples, like testing for CSS Hyphens, formulating your own test can be a hair-pulling experience. Thankfully, there’s an answer for that complexity in the form of Modernizr."

"Modernizr.mq also allows you to test for media query support. Using a combination of Modernizr.load and Modernizr.mq would allow you to conditionally load respond.js, a media query polyfill library:"

"There are certain web features that aren’t detectable by Modernizr. There’s even a Modernizr wiki page dedicated to them. There can be different reasons for this. Performance can be one. Doing some of the video and audio element tests, for example, would require loading a video or audio file. That’s really not feasible to test before the end of the head of the document."

"For example the @font-face test includes a user agent blacklist that improves the fidelity of the Modernizr test by returning false for known problem browsers."

"This isn’t foolproof, especially because using the user agent string for browser sniffing isn’t as precise as using conditional comments (which themselves are gone in Internet Explorer 11 on), but it’s sometimes all you can do."

"In general, the idea is to always choose code patterns that allow your site to function in legacy browsers. In the case of touch and mouse input, that means ensuring you’re binding events to both touch and mouse events. With the embedded media, that means that you provide fallback markup and media formats for older browsers. Whatever technology you’re using, the goal should be to provide something functional for everyone that visits your site."

"Modernizr and feature detection are cornerstones of your web development toolbox. Being able to quickly add tests for web platform features allows you to craft fallback solutions without too much trouble."

"The control which designers know in the print medium, and often desire in the web medium, is simply a function of the limitation of the printed page. We should embrace the fact that the web doesn’t have the same constraints, and design for this flexibility. But first, we must accept the ebb and flow of things. — John Allsopp "

"One of the places where embracing uncertainty matters most and is most readily apparent to developers and designers is deciding how to handle the full depth of devices and screen resolutions out there. Users expect to be able get to your content and data with any device they’ve got in their hands."

"How you satisfy that multiscreen requirement is a major question facing any project these days. Balancing the desire for beautiful designs, world-class usability, top performance, and the maintainability of your platform are all factors that are going to come into play."

"Unless you jumped into this book starting from this chapter (if so, welcome!), then you know how skeptical I was toward the idea that one day everything would become responsive. Even then, I was wary of anything that seemed like a magical solution, and seeing several normally sober voices proclaim that responsive is “the one true way,” clarified something that had been floating around in my head for a decade—that there’s no “one true way.” There’s only the best way for the project you’re currently on. The next project might need the same tools or approach. It might not."

"There are many situations where a dedicated mobile site or some hybrid approach is by far the best choice if you have the skills and resources to execute one. For example, financial sites might have widely different use cases for mobile and desktop users. With complicated financial data, mobile users are often solely consumers of data—often in the form of reports, simple approval workflows, or visualizations—and the real work is done on the desktop."

"Progressive enhancement is an old stalwart of web development. The basic concept of progressive enhancement is to create a widely compatible baseline solution and then add on features and functionality, depending on available browser features. It differs from mobile first in that progressive enhancement can also be part of a desktop first approach to web development."

"Purity in approach doesn’t win you points with your users. Giving them the best possible experience does."

"As we’ve already started to explore, the nature of your site or application is going to be a major determining factor for your approach. On the one hand, if you are building a pure content (text and images) site (as many of the first wave of responsive sites were), then responsive is going to be a good fit. In addition to the existing body of knowledge you can tap into to get tips and tricks, pure text and images lend themselves to RWD because it’s easier to resize boxes than it is to rework interactions. On the other hand, if you’re building a more complicated application, then you may need to create an entirely different approach for small screens."

"If there’s not a one-size-fits-all approach to this, then what are you supposed to do? How do you choose which direction to go?"

"This is a spectrum, so think of these rough guidelines as notable points on the wavelength of the responsive versus mobile site spectrum. There’s not just blue and green. Teal is in there somewhere. Your solution might be the teal of web development."

"If you’re doing a content site or simple application and are a frontend developer on a small team or are a team of one and are more focused on frontend technologies, then you want to go with RWD. Properly implemented, a responsive site can provide a great experience for a vast number of users, and the entire experience can be controlled on the frontend."

"If you’re serving mostly text and image content, look to RWD, no matter what your skill set or team size. You can look to augment RWD with server-side solutions (particularly related to images and other media), but the techniques for responsive design are well established for this kind of content, so there’s no reason not to go in that direction. If you pay careful attention to image sizes and limit the JavaScript payload, in order to keep things speedy, you can provide a great content experience across devices."

"If you’re building anything but the most basic application, look to doing a dedicated mobile experience. Form entry, visualizations, and interaction patterns might all benefit from optimization for large and small screens. You may be able to do a fully RWD application, but don’t force the technique into your application if it doesn’t make sense for your end users."

"You need to take the options available to you, weigh them against the site or application you’re building, and make your decision based on that. As with anything that people are passionate about, people can get a little tribal when it comes to the polar ends of this discussion. Don’t fall in love with any solution, and you’ll be better for it. If you want to have a fully responsive solution but still use your CDN’s content negotiation to provide images optimized for the individual user agent, then go ahead and do that."

"You don’t win points for architectural purity. You win points with fast, effective sites that work in a wide range of devices. You want the best balance between compatibility, design, and functionality."

"Alternatively, if you have an application with a dedicated mobile experience that handles the most common use cases, keep in mind the occasional emergency where someone on his phone might need to access a feature only available on the desktop, even if it means working through a desktop interface with fat fingers. So, if you have a dedicated mobile experience, you need to offer a way to cross over to the desktop version. You’ve already seen this in action in the previous section. But from a design perspective, a simple link, like this one provided by the BBC (Figure 4-4) is probably sufficient. Just make sure it’s clearly labeled."

"This is a simplified example, but recognizing that you don’t have to go all-in at popular device widths and instead can work within the confines of your design is important. Your design and the requirements of your site should be the driving factors of the breakpoints you choose."

"An em is equivalent to the height of the current font. They were very popular for a brief period for all measurements on a page when the default “text increase” behavior in browsers was to simply increase the size of the text without adjusting the size of the boxes. This em-based measurement system was great as it made for layouts that would smoothly increase when the text was increased. There were certain difficulties in this approach because of the fact that the em measurement can change, depending on the size of the font in that section of the document, but they weren’t insurmountable. When the default behavior changed to zooming the entire page, they fell out of favor once again, and pixels reigned supreme. The pendulum has begun to swing back toward ems, as they can bring some benefit in responsive designs. Setting breakpoints in ems, for example, allows a zoomed-in interface to react to breakpoints even when the underlying pixel measurements haven’t changed. "

"Because of the use of relative units, rems, the breakpoints in the previous example are triggered, even though the underlying screen size (in this case, 1600 pixels) never changes (Figure 4-7)."

"The question of how to manage user input, be it by mouse, keyboard, pen, speech, or gesture, has always been tricky. This problem is made worse by the fact that developers have only recently begun to focus on the question in the correct way."

"This is one area that is going to only get more confusing in the future, so if there’s one aspect of modern development where embracing uncertainty will make your life easier, this is it."

"Forget about trying to guess what users are going to use to interact with your site. Simply be ready for them to interact, and get out of the way as best you can."

"The dawn of everyday touchscreen computing was with the iPhone. So, for at least a little while, if you were presented with a good browser (it supported media queries, for example) and it had a small screen, you could assume it was a smartphone and was therefore “touch.”"

"In December of 2013, I was excited to learn that Spotify had launched a “year in review” mini-app full of visualizations of different personal and global trends in music. I love music, I’m a Spotify user, and I love cool visualizations on the Web, so I was excited to check it out. Except I couldn’t. I clicked through and was greeted with the message in Figure 5-3. I was confused. What do I care about mobile for? I was on a laptop. I wasn’t on a mobile device. Why couldn’t I get to the good stuff?"

"If you make an interface that is usable for touch, it will be usable with a mouse. Design for the purpose of the site. You don’t have to design for a specific form factor or display. If you’re using a dedicated mobile experience, this won’t change anything for you, as you’re likely already providing a nice fat hit area. It’s on the large-screen experience where you’ll need to make changes in the way you approach design, lowering the information density overall and using larger interface elements."

"Lean Toward Finger-Friendly Interfaces for All Interfaces If you design for touchscreens and provide large hit areas for buttons, you will make life easier for touchscreen users and users with a mouse or other precise inputs won’t be adversely affected by having a large hit area. Everyone wins."

"Touch Target Sizes 44px is the standard size for iPhone buttons. This is based on the size of a human thumb. It has become the de facto standard for “touch-friendly” buttons. You can move up and down from this number, but it’s a safe baseline from which to work. Serve the same-sized buttons to everyone."

"If you’re going to hide content, make an explicit action to expose it."

"This section will examine the technical aspects of working with user input. You will learn how the events you’re familiar with, like click, work with the touch events we’ve discussed to allow interaction with the user. You’ll also learn about the new pointer events model, which I, and many others, want to be the model to take us into the future of event handling in the browser (even if the path of that future is unclear at present)."

"The Current State of Touch and Mouse Event Handling Learning the intricacies of how this works from an event-handling perspective is important. Although I hope that we’ll have a more streamlined event system for user input available in the future, dealing with the full spectrum of touch and mouse events is, for now, a requirement for every developer looking to properly handle interactions on the modern Web."

"As long as you’re not relying too heavily on hover events (mouseover and mouseout), and you’re not doing anything that tracks the mouse’s movements (mousemove), you don’t need to do anything to have a broadly compatible site or application. Smartphones and tablets were launched onto a Web that wasn’t specifically tuned for touch, so they all mimic traditional mouse events."

"First, we have two touch events (touchstart and touchend) and then a series of faked mouse events (mouseover, mousemove, mousedown, mouseup, and click). You can see how much of what you’ve coded for the mouse still works, as a full set of mouse-based events are faked and fired. There is only one mousemove event fired, so as I mentioned, if you’re tracking the mouse for some sort of animation or game play that won’t work, but otherwise, many basic operations are going to work without you having to lift a finger."

"This still would “just work” and would actually work with mousemove events where touchmove would not, but it just goes to show how difficult it is to identify a “touch” device. If I were using this as a phone and then pulled out the stylus midstream, I would suddenly have a “mouse” with hover events and multiple mousemove events. "

"There is a problem with just binding to click events and wiping your hands of the whole mess. There’s a 300ms delay built into the firing of the simulated, compatibility click events that we learned about earlier in the chapter. This is due to the fact that browsers need to wait to see whether or not you’re doing a double-tap. The double-tap zooms the screen and is an important enhancement for compatibility and accessibility. The following code sample illustrates this by doing a crude timer between the firing of a touchstart event and the simulated click event:"

"This is a noticeable delay, so it can hinder the perceived responsiveness of your site if you don’t manage it properly. There are two different ways to manage this delay. For starters, the browsers themselves have started to suppress the delay if the page is not able to be zoomed by the user. Adding the viewport meta element with a value of user-scalable=no in Firefox for Android and width=device-width in Chrome 32 or later indicates to the browser that the page shouldn’t be scalable with double-tap and the delay will be suppressed."

"User Scaling Is a Feature user-scalable=no suppresses all zooming, not just double-tap to zoom. This means you lose the ability to zoom the page with pinch-zoom as well. This is a serious accessibility and usability concern. If you go this route, you have to ensure that you’re serving content that is going to be readily legible by visually impaired users."

"This technique isn’t supported in iOS or on Windows Phones, so even if you can safely take advantage of this, you need to look at other options to enhance your site performance."

"The second option is to bind actions to both click and touchstart, which ensures that touchscreen devices fire the event as soon as possible (touchstart), while still supporting the broadest range of devices with widely compatible click events still bound. You do need to call the preventDefault method of the event object in order to stop the function from being called multiple times. As you’ve already learned, touch devices call a number of events when a screen is tapped, and if you’ve bound the same function to two or more of them, the function will be called multiple times."

"To fix this, you use the e.preventDefault method (where e represents the event object passed in automatically to the function) in the beltAndSuspenders function. This stops multiple events from firing and allows you to suppress the click delay on an element safely:"

"Using this ensures that the function will only fire once, and the spy element will remain light brown."

"Use preventDefault Sparingly event.preventDafault should only be used on specific interface elements and not on the body or other parent element. Using event.preventDafault in a function bound to touchstart will kill the default scroll-by-touch and pinch-to-zoom behaviors. This is a major accessibility and usability concern. Suppressing the click delay is great, but not at the expense of users who might need or want a boost in text size."

"In addition to these fundamental solutions, there’s a small library called FastClick, from the Financial Times, which allows you to simplify the suppression of the click delay across an entire page safely. Using it is a snap. Insert the script into the page, and then FastClick intercepts all touch interactions on the body and triggers an immediate click event when it identifies the need for one:"

"At present, FastClick is the recommended path for handling click events across devices."

"Like the previous click and touchstart example, this demo listens for both mousemove and touchmove events on a canvas element. Like the previous example, bubble uses e.preventDefault to stop other events from firing. Following that is the one major difference between this and the click/touchstart example. The function tests to see if e.touches is available. If it is, it’s a touch event, and in this case at least, we just access the first touch and get the e.clientX and e.clientY of the event, which we use to set the x and y of the circle."

"If there is no e.touches, then we simply get the e.clientY and e.clientX of the single mousemove event directly:"

"As you might have inferred from the presence of the e.touches array in the previous example, handling multiple touches is also possible."

"Multitouch Events Are “Touch-Only” Interactions As soon as there are two or more touch events at one time, only the touch events are fired. Mouse compatibility events are suppressed. This makes sense if you think about it because there’s really no way to model a multitouch interaction with traditional mouse events."

"This example expands on the previous one to support multiple touches. If e.touches is available, instead of getting the first one and getting the coordinates of a single event, we loop through the entire e.touches array and draw a circle for each of the touches present:"

"Starting with Internet Explorer 10, Microsoft introduced the Pointer Events model for handling user input. Pointer Events has since moved to be a W3C specification."

"Pointer Events is modeled after traditional mouse events, except they use the concept of a pointer to apply one model across all user input, including mouse, touch, and pen."

"This allows you to write a single set of events that work across hardware capabilities. Instead of binding functions to mousemove and touchmove, you simply bind to pointermove and run one function for any input. No matter what input device appears in the future, your pointer event will fire as long as the browser and operating system correctly report the input."

"Looking at just the bubble function, you can see that it’s now down to one line. All you need to do is access the clientY and clientX of the pointer event and pass it into the circle method:"

"There is a chance that Google will reconsider its decision based on the stars and discussion on the Chromium Issue, but as of right now, we’re at an impasse in terms of browser support for Pointer Events."

"Confusion Ahead There was, unfortunately, a similarly named, but entirely separate, CSS specification named Pointer Events, which indicates whether or not an element should receive click/hover events. You may find both if you search for this topic. At present, the majority of the useful links are either from Microsoft or Patrick H. Lauke’s many presentations and articles, so if you’re looking at one of their links, you’re probably on the right track."

"A Matter of Semantics You’re probably thinking—didn’t we already see an example of using different images at different resolutions and different crops when we initially talked about RWD? We did. There, however, we used CSS background images. This larger issue is about the primary content images you would see in a news site, blog, or shopping site. These images are primary content, will be implemented in the DOM as elements on their own, and need to use standard markup in order to fit into the existing infrastructure of screen readers, search engines, browsers, and content management systems."

"Take Advantage of the Browser Preloader All modern web browsers use a technique where the browser skips ahead, while simultaneously reading through the document and building out the DOM, and reads through the document looking for additional assets that it can go ahead and start to download. If, for example, you’ve got a data table that might take hundreds of milliseconds to render, this preloading can help as an image or JavaScript file later in the DOM can start to download even while the browser is still reading and rendering the complicated table markup. Ilya Grigorik of Google says this can improve performance up to 20%. For performance’s sake, therefore, it’s important that any image solution you use can take advantage of the preloader. This means you should look to semantic, markup-based solutions wherever possible"

"Serving the Correct Format If you’re looking to take advantage of Google’s new WebP image format, you need to be able to easily serve WebP images to browsers that support them and serve PNGs or JPEGs to browsers that don’t."

"Now that we’re once again dealing with dial-up era speeds in some cases on mobile devices, progressive JPEGs have made a comeback."

"Figure 6-4 shows two versions of the same uncompressed image. One, on the left, is set to baseline rendering. The other, on the right, is set to progressive. You can see the difference as each loads slowly in the browser. The baseline image loads line by line at full resolution. The progressive image, on the other hand, loads a lower resolution version almost immediately and then fills in detail as more data is downloaded."

"Because of the popularity of Portable Network Graphics (PNGs), a patent-free alternative to GIF that has gained popularity over the past 10 years, GIFs have fallen out of favor for web production—with the grand exception of animated GIFs. Animated GIFs allow you to store multiple frames of an animation in a single file. These low-quality loops have earned a beloved place in the toolbox of goofballs across the Web."

"PNG PNG was developed in the late 1990s in direct response to the Unisys GIF patent controversy mentioned earlier. The PNG format was initially designed for the same use cases as GIF images—basically serving 8-bit flat graphics over the Web. The designers of the format eventually amped it up a little. The 8-bit PNG solves the same problems as an 8-bit GIF, using only 256 colors and on/off transparency, but there is an enhanced 24-bit version of PNG, which has two big advantages: Like a JPEG, PNG 24 supports the full true color spectrum. A map provides different levels of transparency for every pixel, which allows for softer, anti-aliased edges."

"Additionally, PNGs tend to compress to a smaller file size than their GIF equivalent. All of these benefits, mixed with the spark of the GIF patent scare all those years ago, mean that PNG is the format of choice for limited color graphics."

"WebP Offered here as a bit of a novelty for the present, WebP is Google’s answer to the question of images on the Web. WebP is a new image format created by the Internet giant that offers significant file size gains over the existing contenders. Google says “WebP is a new image format that provides lossless and lossy compression for images on the Web. WebP lossless images are 26% smaller in size compared to PNGs. WebP lossy images are 25–34% smaller in size compared to JPEG images at equivalent SSIM index.” Sounds great. Except no one but the Blink browsers are looking to support WebP any time soon. So, although it’s an interesting technology to explore and potentially use as an enhancement if you’re enterprising, it’s not yet ready to replace JPEGs or PNGs. This is especially true because the current tooling for outputting images to WebP isn’t as robust as the other common formats. There are a handful of command-line and utility tools available, but WebP support isn’t yet in popular authoring programs like Adobe Fireworks or Photoshop without a plug-in, so adoption isn’t as easy as telling the production staff to “output WebP” when cutting graphics. It requires automation or the use of a manual utility to get WebP images prepped for the Web."

"Definitely try to take advantage of the speed benefits of a CDN. They also allow you to “shard” across different domains, pipelining requests and improving performance. A CDN will be the foundation upon which all your other image delivery enhancements are built."

"Use only that which works, and take it from any place you can find it. — Bruce Lee (as quoted in Bruce Lee:Fighting Spirit by Bruce Thomas) "

"One of the most important early drivers for adoption of HTML5 was Apple’s decision against supporting Adobe Flash on iOS devices. Picking the most important side effect of that decision would be difficult, but one of the biggest was certainly the mad scramble to produce web video that could play on the iPhone. This, of course, meant the HTML5 video element was suddenly important. It was so important, for a time at least, that it was common for people to say simply “HTML5” when they were really discussing serving video with the video element."

"Video is the best current example of a web technology that, because of one factor or another, fails to live up to its promise. Because of that failure, it’s much easier to move away from a pure standards-based approach to one that solves the issue in a practical matter. No matter how well designed the element might be, or how easy the API is to use, commercial and technical hurdles make the practical business of web video difficult to manage without a lot of expertise. It’s so difficult, in fact, that I’m happy to pass off the video heavy lifting to third parties without a second thought to how technically clean their solution might be."

"Boolean attributes, which are new to HTML5, are attributes whose mere presence indicates that the value is true. So, instead of saying required=true, you can just write required. The attributes here, controls and autoplay, indicate that there should be controls (play and pause buttons, etc.) in the video interface and that the video should automatically play when the page loads."

"I’m Intentionally Ignoring Audio I’m ignoring both the audio element and the audio codec component of web video. This is partially because I want to keep your heads from exploding. That and there are standard audio codecs that pair with each of the video codecs you’ll learn about later. Basically, if you don’t do anything funky when you export your video, you will end up with a combination of audio codec and video codec that makes sense from a support perspective. So when I talk about MP4, I’m really talking about the h.264 video codec with the AAC audio codec; when I talk about OGM, I’m really talking about the Theora video code with the Vorbis Audio codec; and when I talk about WebM, I’m talking about the VP8 video codec with the Vorbis audio codec. Have I mentioned this is a rat’s nest? It’s a rat’s nest."

"Serving video is a big deal. There are complexities in serving anything optimally on the Web, but serving video has taken it to an entirely new level. It’s complicated, and the penalties for getting it wrong can very easily produce a failing or just plain terrible end-user experience. This section won’t go into absolute detail, because it’s a thorny, evolving subject, but it will go over the issues at play at a really high level so that you’ll at least know where to look if you want to upgrade your video experience and keep the end-to-end experience in-house."

"Although there are resources out there to help you stream audio and video, including setting up adaptive media sources, the fractured nature of support across the various components of web video, the performance penalties for getting it wrong and the strength and maturity of the online video community make it mighty tempting to just leave it to the pros. You may not come to the same conclusion I have, and you might want to go it alone. But I think it’s important that you consider forgoing the granular control you might be used to with other web platform technologies in order to take advantage of the features, functionality, and performance benefits offered by outfits that focus exclusively on video (e.g., YouTube, Vimeo, Brightcove, or Kaltura). Their goal is the same as ours—broad compatibility with whatever the Web can throw at them."

"In this chapter, you’ve seen what can happen when good specifications go bad once they hit the mean streets. From the clear beginnings of the video element as a replacement for plug-in-based video on the Web to today’s nasty mosaic of options to sort through in order to get video on the Web, we’re looking at a present where a modern Web standards-based solution isn’t necessarily better than what came before. Although having to use a proprietary technology like Flash isn’t part of the ideal Web I really want, I also want a Web that’s easy to manage from a workflow perspective and doesn’t add multiple layers of complexity to my life just to get my job done. "

"Whether you decide to go it alone or if you decide to leverage one of the many third parties, this is one situation where it’s best to just hold your nose and make decisions based on what’s best for your users, rather than what might be the best possible solutions from a pure web standards perspective."

"More importantly, in the context of this book at least, the overall complexity of video reinforces the idea that no matter what the intentions are of the standards bodies, the real world can throw a spanner in the works really quickly. When it does and market forces or the commercial interests of browser vendors get in the way, it’s better to acknowledge that issue early on and move ahead with the best practical solution. Being a champion for web standards is a great thing, as long as it’s not at the expense of your end users."

"The Web as I envisaged it, we have not seen it yet. The future is still so much bigger than the past. — Tim Berners-Lee "

"It may not seem like it at times, but we’re all on the same side. We need to trust in the process and in one another. But that trust has to come along with a commitment from the web developer community that we’re going to help them along the way with constructive feedback and a desire to roll up our sleeves and get to work. We’re getting way better at this, but we can do more."

"I’m all for awesome experiences, and there are plenty of places where the experience can be the whole purpose of a site. That kind of work is vital to ensure that the techniques we’re using stay fresh and that we really pound on new technologies to know where they break. That said, the power of the Web is that it’s universal. There’s no app store. Everything is available to everyone, or at least it should be. We’ve got to strive to make that the default for the way that we build for the Web. We should ensure that even in the worst circumstances, something useful is there for the user. We should ensure that even in the best circumstances, we focus our attention on serving our user’s needs and not our own vanity."

"The Web, if we do it right, is there for everybody as soon as they fire up a web browser and unlike trying to catch lighting in a bottle to simply get noticed in an Apple or Google-shaped sandbox, building for the Web means you’re only limited by what you want to do and whom you want to reach."
