Responsive Web Design

Ethan Marcotte

---

▪ The short history of web design has already shown us the transformative power of language.

▪ When Ethan Marcotte coined the term “responsive web design” he conjured up something special. The technologies existed already: fluid grids, flexible images, and media queries. But Ethan united these techniques under a single banner, and in so doing changed the way we think about web design.

▪ Ethan has a way with words. He is, of course, the perfect person to write a book on responsive web design. But he has done one better than that: he has written the book on responsive web design.

▪ But, ultimately, the three main ingredients of a responsive design—flexible grids, fluid images, and media queries—are as relevant today as they were when I first coined the phrase. So while the structure of the book hasn’t changed that much,

▪ One thing hasn’t changed, though. You see, when I wrote an article about something called responsive web design (http://bkaprt.com/rwd2/0/) a few years ago, I didn’t think for a second I’d be lucky enough to write a book on the topic.

▪ AS I BEGIN writing this book, I realize I can’t guarantee you’ll read these words on a printed page, holding a tiny paperback in your hands. Maybe you’re sitting at your desk with an electronic copy of the book up on your screen. Perhaps you’re on your morning commute, tapping through pages on your phone, or swiping along on a tablet. Or maybe you don’t even see these words as I do: maybe your computer is simply reading this book aloud.

Ultimately, I know so little about you. I don’t know how you’re reading this. I can’t.

▪ At the end of the day, there isn’t any thing produced by designing for the web, no tangible object to hold, to cherish, to pass along to our children. But despite the oh-so-ethereal nature of our work, the vocabulary we use to talk about it is anything but: “masthead,” “whitespace,” “leading,” even the much-derided “fold.” Each of those words is directly inherited from print design: just taken down from the shelf, dusted off, and re-applied to our new, digital medium.

▪ Some of that recycling is perfectly natural. We’re creatures of habit, after all: as soon as we move into a new city, or start a new job, we’re mapping previous experiences onto the new, more foreign one, using them to gradually orient ourselves. And since the web is a young medium, it’s only natural to borrow some terms from what we know: graphic design provides us with a rich history that spans centuries, and we’d be remiss not to use its language to help shape our industry.

▪ In every other creative medium, the artist begins her work by selecting a canvas. A painter chooses a sheet of paper or fabric to work on; a sculptor might select a block of stone from a quarry. Regardless of the medium, choosing a canvas is a powerful, creative act: before the first brush stroke, before striking the chisel, the canvas gives the art a dimension and shape, a width and a height, establishing a boundary for the work yet to come.

▪ On the web, we try to mimic this process. We even call it the same thing: we create a “canvas” in our favorite image editor, a blank document with a width and height, with dimension and shape. The problem with this approach is that we’re one step removed from our actual canvas: the browser window, and all of its inconsistencies and imperfections (FIG 1.2). Because let’s face it: once they’re published online, our designs are immediately at the mercy of the people who view them—to their font settings, to the color of their displays, to the shape and size of their browser windows.

▪ So in the face of all that uncertainty, that flexibility, we begin by establishing constraints: we set our type in pixels, or create fixed-width layouts that assume a minimum screen resolution. Establishing those constraints is a bit like selecting a canvas—they give us known parameters to work from, certainties that help quarantine our work from the web’s inherent flexibility.

▪ But the best thing—and often, the worst thing—about the web is that it defies easy definition. If I were feeling especially bitter, I’d even go so far as to say it revels in its ability to shrug off whatever constraints we place around it.

▪ And the parameters we place on our designs are no different: they’re easily broken. If a browser drops even slightly below our expected minimum width (FIG 1.3), a site’s visitor might find her reading experience is altered by a horizontal scrollbar and clipped content. But our businesses and clients could be affected as well (FIG 1.4): by relying on a minimum screen resolution, the placement of critical links or elements can be incredibly fragile, clipped by a viewport that obeys the user’s preferences, not ours.

▪ More than a decade ago, John Allsopp wrote “A Dao of Web Design” (http://bkaprt.com/rwd2/3/), an article that, if you haven’t read it, you should absolutely check out now. (Seriously. I’ll wait.) It’s easily my favorite essay about designing for the web, and it’s just as relevant today as it was when it was first written. John argues that

▪ Now, John was writing during the web’s early years, a period of transition when designers transferred print-centered design principles onto this young, new medium. But much of what he wrote in the spring of 2000 still rings true today. Because the web has never felt more in flux, more variable than it does right now.

▪ The long and short of it is that we’re designing for more devices, more input types, more resolutions than ever before. The web has moved beyond the desktop, and it’s not turning back.

▪ See the word mobile in the link? The site’s owners had quarantined the “mobile experience” on a separate URL, assuming it would only ever be viewed on a narrow, handheld screen. But whenever that link is shared on Twitter, Facebook, or via email, visitors will be locked into that small-screen-friendly view, regardless of the device they use to read it. And speaking for myself, the reading experience was, well, awful on a desktop browser.

▪ That’s not to say that mobile websites are inherently flawed, or that there aren’t valid business cases for creating them. But I do think fragmenting our content across different “device-optimized” experiences is a losing proposition, or at least an unsustainable one. As the past few years have shown us, we simply can’t compete with the pace of technology. Are we really going to create a custom experience for every new browser or device that appears?

▪ I’ve been an amateur fan of architecture for as long as I can remember. And as a web designer, there’s something appealing about the number of constraints that architects seem to enjoy: from sketch to schematic, from foundation to façade, every step of the architectural process is more permanent than the one that preceded it

▪ In Parentalia, the English architect Christopher Wren wrote that “architecture aims at eternity,” and there’s something to that: an architect’s creative decisions will stand for decades, perhaps centuries.

▪ But in recent years, a relatively new design discipline called “responsive architecture” has been challenging some of the permanence at the heart of the architectural discipline. It’s a very young discipline, but this more interactive form has already manifested itself in several interesting ways.

▪ Rather than creating spaces that influence the behavior of people that pass through them, responsive designers are investigating ways for a piece of architecture and its inhabitants to mutually influence and inform each other.

▪ Rather than creating disconnected designs, each tailored to a particular device or browser, we should instead treat them as facets of the same experience. In other words, we can craft sites that are not only more flexible, but that can adapt to the media that renders them.

▪ In short, we need to practice responsive web design.

▪ Speaking purely in terms of front-end layout, it takes three core ingredients:

A flexible, grid-based layout,
Flexible images and media, and
Media queries, a module from the CSS3 specification.

▪ As we do so, we’ll have created a design that can adapt to the constraints of the browser window or device that renders it, creating a design that almost responds to the user’s needs

▪ But graphic designers of the period, like Jan Tschichold, Emil Ruder, and Josef Müller-Brockmann, popularized this concept of a typographic grid: a rational system of columns and rows, upon which modules of content could be placed (FIG 2.2). And thanks to designers like Khoi Vinh and Mark Boulton, we’ve managed to adapt this old concept to the needs of contemporary web design.

▪ In his book Grid Systems in Graphic Design, Müller-Brockmann referred to this process as “creating a typographic space on the page,” tailoring the proportions of the grid to the size of a blank piece of paper. But for a web designer, we’re missing one key component: the presence of an actual page. Our canvas, the browser window, can bend and flex to any shape or size, whether changed at the whim of the reader, or fixed by the phone or tablet they’re using to view our content.

▪ Instead of pasting the pixel values from our comp directly into our CSS, we need to express those widths in relative, proportional terms. Once we’ve done so, we’ll have a grid that can resize itself as the viewport does, but without compromising the design’s original proportions.

▪ FOR MOST of my career, I’ve been a staunch proponent of non-fixed layouts. Flexible or completely fluid, it didn’t matter: I felt that building some measure of fluidity into our designs better prepared them for the changes inherent to the web: changes in the user’s browser window size, in display or device resolution. What’s more, I’d often use words like “future-proof” and “device-agnostic” when describing the need for this flexibility. Often while standing alone at parties.

▪ Thankfully, the W3C has been wrestling with this question for some time. To better understand the solution they eventually presented, it’s worth reviewing a bit of the backstory.

▪ On occasion, however, style sheets for different media types may share a property, but require different values for that property. For example, the “font-size” property is useful both for screen and print media. The two media types are different enough to require different values for the common property; a document will typically need a larger font on a computer screen than on paper. Therefore, it is necessary to express that a style sheet, or a section of a style sheet, applies to certain media types.

▪ Ever written a print stylesheet (http://bkaprt.com/rwd2/27/)? Then you’re already familiar with the concept of designing for different kinds of media. The ideal browsing experience couldn’t differ more between desktop browsers and printers, or between handheld devices and speaking browsers.

▪ To address this the W3C created a list of media types (http://bkaprt.com/rwd2/28/), attempting to classify each browser or device under a broad, media-specific category. The recognized media types are: all, braille, embossed, handheld, print, projection, screen, speech, tty, and tv.

▪ Or perhaps creating an @media block in your stylesheet, and associating it with a particular media type:

@media screen {

body {

font-size: 100%;

}

}

▪ @media print {

body {

font-size: 15pt;

}

}

▪ Several problems with media types became evident when all these little small-screen browsers, like phones and tablets, arrived on the scene. According to the specification, designers could have targeted them simply by creating a stylesheet for the handheld media type:

▪ The problem with this approach is, well, us—at least in part. Early mobile devices didn’t have sufficiently capable browsers so we largely ignored them, choosing instead to design compelling screen- or print-specific stylesheets. And when capable small-screen browsers finally did appear, there weren’t a lot of handheld CSS files scattered about the web. As a result, many mobile browser makers decided to default to reading screen-based stylesheets.

▪ But what’s more, media types paint with an incredibly broad brush. Is one handheld stylesheet really suited to address the challenges of designing for an iPhone and a five year-old feature phone?

▪ Realizing some of the failings of media types, the W3C used their work on CSS3 to take another crack at the problem. The result was media queries (http://bkaprt.com/rwd2/29/), an incredibly robust mechanism for identifying not only types of media, but for actually inspecting the physical characteristics of the devices and browsers that render our content.

▪ @media screen and (min-width: 1024px) {

body {

font-size: 100%;

}

}

▪ But no matter how you write your queries, the result in each scenario is the same: if the browser matches the media type and meets the condition outlined in our query, it applies the enclosed CSS. Otherwise, it won’t.

▪ When Apple launched the iPhone in 2007, they created a new attribute value for Mobile Safari’s meta element: viewport (http://bkaprt.com/rwd2/31/). Why? Well, the dimensions of the iPhone’s display is 320×480, but Mobile Safari actually displays web pages at a width of 980 pixels. If you’ve ever visited Apple’s homepage (http://apple.com/) on a WebKit-enabled phone (FIG 4.9), then you’ve seen this behavior in action: Mobile Safari is drawing the page upon a 980px-wide canvas, and then shrinking it to fit within your phone’s 320×480 display.

▪ The initial-scale property sets the zoom level of the page to 1.0, or 100%, and helps ensure some consistency across small-screen, viewport-aware browsers. (For more information on how scaling works on different displays, I recommend Mozilla’s explanation: http://bkaprt.com/rwd2/32/.)

▪ Secondly, the typeface we were initially using for our headlines—our beloved League Gothic—doesn’t scale down very well to that size (FIG 4.11). So I’ve decided to change the font-family stack itself (Calibri, Candara, Segoe, "Segoe UI", Optima, Arial, Helvetica, sans-serif), which feels a bit more readable (FIG 4.12).

▪ And once we start looking beyond the desktop, to mobile phones, popular proxy browsers, and other devices, JavaScript support is notoriously scant, bordering on nonexistent in many devices. Or maybe their device supports JavaScript, but it’s on an incredibly slow or spotty network.

▪ If you’ll permit me one fanboyish outburst: media queries are downright awesome. They let us conditionally serve up CSS based on the capabilities of the device rendering our sites, allowing us to more fully tailor our design to our users’ reading environment.

▪ But this is the challenge facing us: we simply can’t keep up with the different resolutions and form factors entering the marketplace. The web is, after all, meant to be viewed everywhere. A flexible layout provides us with a foundation for the future: it allows us to step back from targeting individual resolutions, and better prepare our designs for devices that haven’t even been imagined yet.

▪ That’s because, at its most basic level, responsive design is about serving one HTML document to countless browsers and devices, using flexible layouts and media queries to ensure that design is as portable and accessible as possible.

▪ However, certain web designers argue against this approach, suggesting that different devices should always be served different markup. In a rather lengthy blog post, mobile developer James Pearce questions the merits of responsive design (http://bkaprt.com/rwd2/46/):

▪ The fact that the user has a small screen in their hand is one thing—the fact that it is in their hand at all is another. The fact that the user may be walking, driving, or lounging is yet another. In fact, it’s quite likely that they really deserve different content and services altogether—or, at least, a differently prioritized version of the default desktop experience.

▪ By and large, mobile users want different things from your product th‘an desktop users do. If you’re a restaurant, desktop users may want photos of your place, a complete menu, and some information about your history. But mobile users probably just want your address and operating hours.

▪ For what it’s worth, I agree with these arguments—but up to a point. It’s absolutely fair to assume a user’s context from their device, but it’s just that: an assumption. For example, much of my “mobile” browsing happens on the couch in my living room, flipping idly through sites on my wireless network. Now, this isn’t just another of my “Ethan doesn’t have a life” jokes: research has shown that a significant percentage of people use “the mobile web” from the comfort of their home (http://bkaprt.com/rwd2/48/, http://bkaprt.com/rwd2/49/). And it’s not just the “mobile context” that’s fuzzy, either: what does a “desktop” user look like, anyway? Sure, they might be seated at a desk, with a high-speed connection available to them—or they might be tethered to a phone, or connected to a spotty hotel network. “Mobile” and “desktop” are useful shorthand terms, but they’re just that—shorthand terms that can, if we’re not careful, mask a lot of complexity.

▪ But just because desktop users can sift through more content, does that mean they need to? In other words, why is easy access to key tasks only the domain of mobile users? Why can’t all users of our sites enjoy the same level of focused, curated content?

▪ Toward the end of 2009, designer Luke Wroblewski fired off a little challenge to our industry, suggesting a website’s mobile experience shouldn’t be an afterthought (http://bkaprt.com/rwd2/52/). Citing the explosive growth of mobile web traffic, as well as the exciting new technical capabilities of modern phones, Luke suggested that instead today’s web professionals should begin designing for mobile first.

▪ “Mobile first” is a wonderful design philosophy. What’s more, I’ve found it absolutely invaluable for the responsive design projects I’ve worked on. As more browsers and devices begin accessing our designs, and as our clients become interested in designing beyond the desktop, it’s a perfect opportunity to take a hard look at how we design for the web: our processes and vocabulary, as well as the questions we ask and the solutions we apply.

▪ Now, the prototype doesn’t have to be completely tested or production-ready. Because once that template’s somewhat finished, we start another design review—but this time, the design and development teams are reviewing code, not comps.

▪ If you design mobile first, you create agreement on what matters most. You can then apply the same rationale to the desktop/laptop version of the web site. We agreed that this was the most important set of features and content for our customers and business—why should that change with more screen space?

▪ It’s all too easy to fill a desktop browser window with social media toolbars, links to related articles, battalions of RSS links, and tag clouds galore. (This process is called “adding value,” I believe.) But when we’re forced to work with a screen that’s 80% smaller than our usual canvas, nonessential content and cruft quickly fall away, allowing us to focus on the truly critical aspects of our designs.

▪ In other words, designing for mobile devices first can enrich the experience for all users, by providing the element often missing from modern web design: focus. That’s not to say that our client’s pages are light on content, or lacking in features. But by framing our design process with that simple question, we’ve gained a handy acid test to apply when considering each proposed element, each new piece of functionality.

▪ Now, most design projects follow some version of the “waterfall” project management workflow, dividing the work into distinct, task-based phases. The specifics might change from one studio to the next, but there are usually four segments: a planning phase, a design phase, a development phase, and then, finally, delivery of the finished site. In each phase, documents or files are created—for example, a site map and wireframes during the planning phase—which the client approves before the next phase of work begins.

▪ Again, the way you manage your projects might differ slightly. But for the design phase, the design team often mocks up a number of pages in a graphics editor like Photoshop, Fireworks, or the like. And once those mockups are finished and approved, they’re handed off to the development team, ready to be produced into static HTML templates.

▪ But for a responsive site, that process can quickly become a bit unwieldy. Let’s pretend for a moment you’re redesigning a site with only one page, so you knock out a mockup in your favorite design application. But how do you communicate to your client how that page will appear on a phone? Or an iPad? Or a widescreen display? If you’ve the time, budget, and resources, it might be feasible for you to design each of those alternate views, presenting those comps to the client, gathering feedback, and then revising each as needed. But if you’re designing fifteen pages, or fifty, then it can quickly become impractical to produce every one of those mockups and their alternate views.

▪ Recently, the responsive projects I’ve worked on have had a lot of success combining design and development into one hybrid phase, bringing the two teams into one highly collaborative group. I refer to this new, Voltron-esque phase as “designopment.” (No, not really.)

▪ The goal is to get a starting point in front of the entire group, to kick off a discussion about how this design will need to accommodate different resolution ranges and input types. Questions tend to fly back and forth pretty rapidly: “How do you envision this slideshow working on a touch device?” “Is this module always going to be collapsed by default, or will widescreen users need to see more information?” “How will this element look (and function) if JavaScript isn’t available?”

▪ “Prototyping before the designs are final, you say?” Absolutely, I say. Our goal is to get beyond the pixel limitations of Photoshop, and begin building a design that can flex and grow inside a changing browser window, that can scale to different devices. So the development team quickly begins producing a responsive design: converting the fixed grid into a fluid one, discussing ways to flexibly handle different types of media, and then finally applying the media queries that adapt our design to different resolution ranges.

▪ But if browser extensions and whatnot aren’t your thing, you might try Dave Rupert’s fitWeird bookmarklet (http://bkaprt.com/rwd2/55/) or Jordan Moore’s “Responsive Roulette” viewer (http://bkaprt.com/rwd2/56/), which, in addition to being well-made tools, beautifully reinforce that your responsive design could be encountered on screens of any size.

▪ During this development process, a prototype begins to take shape. It’s based on the initial mockup supplied by the design team, of course, but as the development team codes they begin making recommendations about how the design should respond to different devices.

▪ In other words, during this collaboration the developers act as designers, too; they’re just designing in a different medium. They’re making design recommendations within the browser, rather than in Photoshop—recommendations that will be shared, tested, and vetted by the entire team.

▪ The key is to make this design/development cycle as iterative as it needs to be, with both groups constantly refining their work, and then sharing it with the group for review. For the project I’m working on, we’ve been meeting weekly for our interactive design reviews, but we’re constantly sharing sketches—whether in design or in code—via email throughout the week.

▪ Ultimately, the goal is to close the gap between the traditional “design” and “development” cycles, and let the two groups collaborate more closely to produce a finished, responsive design. This more agile approach has allowed the groups I’ve worked on to use applications like Photoshop for design direction and guidance, but then quickly move into our real canvas: the browser.

▪ During our design/development cycle, the pages are constantly being refined as we build them, with the goal of finishing the phase with production-ready templates. And as we code our responsive design, we’ve found the philosophy of “mobile first” to be incredibly important.

▪ Speaking broadly, responsive design is about starting from a reference resolution, and using media queries to adapt it to other contexts. A more responsible approach to responsive design would mean building our stylesheet with “mobile first” in mind, rather than defaulting to a desktop layout. So we’d begin by defining a layout appropriate to smaller screens, and then use media queries to progressively enhance our design as the resolution increases.

▪ No media queries? No JavaScript? No problem: designing for the small screen first means every browser is left with an accessible design, regardless of the size of its screen.

▪ Rather than hoping for graceful degradation, progressive enhancement builds documents for the least capable or differently capable devices first, then moves on to enhance those documents with separate logic for presentation, in ways that don’t place an undue burden on baseline devices but which allow a richer experience for those users with modern graphical browser software.

▪ Since Nick and Steven coined the term in 2003, progressive enhancement has been the hallmark of the responsible approach to standards-based web design. By beginning with a foundation of semantic, well-structured markup, styling with a layer of CSS, and adding DOM scripting via JavaScript as needed, we can create compelling experiences in capable browsers, while ensuring universal access to the content beneath the design.

▪ Stephen Hay reiterated the need for progressive enhancement as well, in his fantastic essay “There is no Mobile Web” (http://bkaprt.com/rwd2/65/):

▪ Because more than anything, web design is about asking the right questions. And really, that’s what responsive web design is: a possible solution, a way to more fully design for the web’s inherent flexibility.

▪ The W3C’s media query specification: http://bkaprt.com/rwd2/76/

▪ Jeremy Keith’s “One Web”: http://bkaprt.com/rwd2/84/ and “Context”: http://bkaprt.com/rwd2/85/

▪ Ethan Marcotte is an independent designer and author, based in Cambridge, Massachusetts. He coined the term “responsive web design” to describe a new way of designing for the ever-changing Web.

▪ His clientele has included New York Magazine, the Sundance Film Festival, The Boston Globe, and People Magazine. 
