▪ That’s actually radical, and really refreshing to read. Because most designers will do anything but the expected. Then I have to tell them off on behalf of the users they’re forcing to decipher their interface. Nobody has time for that.

▪ The web is constantly changing. Browsers and devices are released at a rapid rate, each with varying features and capabilities. This is why Jeremy Keith refers to the web as a continuum, not a platform18.

▪ Not everyone in the industry agrees on the meaning of adaptive design7. Some think it means having different layouts that snap at particular sizes — in other words, not fluid. Others think it’s the same as responsive design, which is hardly surprising seeing as the words are synonyms.

▪ Adam Silver is an interaction designer with over 15 years experience working on the web for a range of companies including Tesco, BBC, Just Eat, Financial Times, the Department for Work and Pensions and many others.

▪ The web is more than just text. Whether it’s sending a CV to a recruiter by email, or adding photos to an eBay advert, we need to let users upload files. Forms have this capability baked in, of course.

▪ Nobody wants to log in to your site. They’re forced to as a security measure. Without it, everyone has access to everyone else’s stuff. Bad.

▪ However, we’re going to explore several complex problems that, in the end, will result in reusable patterns — patterns that are very much transferable to other problem domains, such as booking a cinema ticket, or even a hotel room.

▪ On one hand, uploading a file is only marginally more complex than, say, inputting text or clicking a checkbox. On the other hand, there are number of unique design challenges and opportunities that arise, especially when there’s a need to upload multiple files at the same time.

▪ Given how long login forms have been around for and how basic they are in appearance, you’d be surprised at how often they contain the same usability mistakes that stop users doing something they don’t even want to do in the first place. Add social login into the mix and things get even harder.

▪ Yes, I came from the view-source school of web design and development.

▪ In MailChimp, for example, I’ll usually start drafting an email campaign weeks before I send it. There are a number of steps to complete, and in a particular order too. First, I check the content reads well. Then I need to make sure it looks good in various email clients. Then days or weeks later, I’ll run through some final checks, decide the subject line and schedule it for release.

▪ Filters (also referred to as facet navigation or guided navigation) let users refine a large set of search results. This helps users home in on what they’re looking for.

▪ As usual, we’ll start by looking at what browsers give us for free. After that, we’ll look at adding various enhancements and the various issues that surface as a result of those enhancements. We’ll end up with a number of different ways to upload a file, appropriate for several different occasions.

▪ As much as we tried to use native form controls in their standard format, it became apparent that custom components were necessary to give users the best experience. In the end we designed four custom components:

▪ Paradoxically, in a world saturated with rule breaking and reinvention, a reverence for the straightforward, familiar, and simple becomes radical. And it’s a welcome revolution, because interfaces that are obvious are also inclusive. It’s not a bad thing to be on the nose.

▪ Every meaningful interaction that happens on the web is achieved by a form of some sort.

▪ Other tasks might be performed by several people using the same application. For example, processing a return may involve someone receiving the goods at the warehouse; then a decision maker may look at the goods to make sure it satisfies the returns policy.

▪ Without forms, the web merely becomes a passive experience — just a way to consume content.

▪ The form is made up of four fields and a submit button. Each field is made up of a control (the input) and its associated label.

▪ A file picker () is another type of form control. When clicked, it will spawn a dialog that lets users browse files on their computer or device. Once a file is selected, the dialog closes and the picker updates to reflect the file has been chosen.

▪ Letting users filter out irrelevant results is important. The ability to filter not only offers an additional dimension of control, but it does so in a way that matches each user’s own mental model.

▪ Some services, such as applying for a mortgage or registering for a bank account, involve supplying personal information, and this may involve offline processes such as sending identification documents in the post.

▪ At first glance, forms are rather easy to grasp. In less than an hour, you’ll have text boxes, radio buttons and select boxes on the page. But their low barrier to entry turns them into what Heydon Pickering refers to as a “10,000-volt electromagnet for attracting usability problems.”1

▪ In “Designing for Faceted Search,”1 Stephanie Lemieux says:

“Think of a cookbook: authors have to organize the recipes in one way only — by course or by main ingredient — and users have to work with whatever choice of organizing principle that has been made, regardless of how that fits their particular style of searching. An online recipe site using faceted search can allow users to decide how they’d like to navigate to a specific recipe [by course type, cuisine or cooking method, for example].”

▪ How can we design forms that play nicely with this complex and long-form process that can take weeks to complete? And by different people across digital and non-digital journeys?

▪ If all users need to do is upload a single file, then you can add a file picker to your form, and you’re pretty much done:

▪ You’d be forgiven for thinking you were spoiled for choice when it comes to form controls: select boxes, radio buttons, text boxes and, more recently, datalists. The choice is yours — except it isn’t. Not all of these options are suitable. Let’s look at some of the pros and cons of each.

▪ There are a number of other forms on the web that use the persistent form pattern. For example, GitHub’s “Add collaborators” form and the infamous to-do list form that many JavaScript frameworks use to demonstrate their approach1.

▪ Why Patterns?

Design patterns serve as guidance and solutions to people solving similar problems over and over. The reason for design patterns is twofold.

▪ Some niche sites, such as airlines, ask users to enter their booking reference number. In this case, use the hint pattern to tell users where they can find it.

▪ First, instead of solving the same problem from scratch every time, we can instead use previously designed, available, recognized, and well-researched solutions. This saves a lot of time. And we can use that time to solve newer and perhaps bigger problems.

▪ At first glance, filters might look similar across different sites, but their behavior varies quite widely. When and how filters should be applied, how to denote selected filters, what elements should be used, how to give users feedback, how they’ll work on mobile and desktop: all of these things need to be taken into account.

▪ One of the best ways we can help users save time is by not wasting it in the first place. One way to do that is to tell users what they need to know before they start the process.

For example, to apply for an HSBC mortgage in the UK, users must: consent to a credit check; confirm the property is in a habitable condition; and be aged 18 or over. HSBC tells users this on the first page of the application, before they start.

▪ Select boxes are often used for their space-saving qualities. What’s most interesting, though, is why we need to save space in the first place.

▪ He recounts a story from user research where someone was trying to buy a purse.

The woman was happy enough to buy the purse on the proviso she could return it. But the returns policy wasn’t on the product page, or in the FAQ. In the end, she tried typing “Refund policy” into the search box — but it didn’t return any results. That was the end of the research session.

The returns policy isn’t a product. Nor does it reside in the database. But this is what she wanted. We often hear how content is king, but the design of the search function let the content down. Wherever possible, search should search everything. And if it doesn’t, the label should be explicit. If the search function only returns products, make that clear within the interface.

▪ Second, by solving the same problem in the same way, users have a consistent and more coherent experience. The service, app, or whatever it is, becomes familiar. Familiar interfaces require less effort to operate. Think about it: every time you encounter a door, you just know that it can be opened, closed, and sometimes locked.

▪ There are two ways to let users filter: one at a time (interactive filtering), or selecting multiple filters at once (batch filtering).

▪ Prior to iOS 5, this behavior also applied to the email input. In the case of the username or email address, we certainly don’t want users to exert energy fixing mistakes they didn’t even make. So we can disable this behavior like this:



▪ That’s because clicking a label sets focus to the associated form element.

▪ In “User Intent Affects Filter Design,”2 Katie Sherwin describes an excellent way to think about this:

“[…] think about how you might order appetizers at a restaurant. Say you want to order three appetizers for the table, but as soon as you name the first one, the waiter snatches the menu out of your hands and walks back to the kitchen to get the chefs started on cooking that dish. Instead, a good waiter understands that you’re still in the process of ordering and knows to give you more time before taking away the menu. A good waiter allows you time to make a batch decision, even if that might slightly delay the delivery of the first item ordered. (However, sometimes the waiter may take the appetizer order, and then give you more time to decide on the main course. A good waiter is flexible and adapts to the needs of the customers.)”

▪ In her talk “Burn Your Select Tags,”1 Alice Bartlett shares the user research she undertook at the UK’s Government Digital Service (GDS). In short, select boxes are hard to use. Besides hiding options behind an unnecessary extra click, users generally don’t understand how they work. Some users try to type into them, some confuse focused options with selected ones. And, if that weren’t enough, users can’t pinch-zoom the options on certain devices.

▪ Similarly, iOS will autocorrect words in a text input that it thinks are mistakes. Continuing with the example above: a username may contain a random string of characters that may look like a mistake but isn’t. You can disable this behavior like this:



▪ Knowing this up front not only saves users a lot of time, but it can also lower the operating costs of the service: by reducing the time and effort support teams spend working out and explaining all of this to people over the phone.

▪ Left: generic search label “Search.” Right: specific search label “Search products.”

▪ label’s for attribute should match and be unique to the page. In the case of the email field, the value is “email”:

▪ By the same token, some browsers will mark misspelled words with an underline. Again, you can disable this:



▪ A tip: use analytics to track what users are searching for. If the most popular searches retrieve empty results, make provisions to improve the experience based on data.

▪ There are a few problems with this approach to design. First, rules can be broken — occasionally. Second, evaluating problems by principle is constraining. Many go together: when talking about screen readers, for example, it often makes sense to discuss keyboard users. And sometimes you have to make trade-offs.

▪ Styling file pickers has always been tricky because browsers ignore any attempt at doing so with CSS. We have to resort to hacking, which is not usually a good idea — that’s why it’s called hacking. But let’s walk through how it could work, what can be achieved, and the pitfalls that are involved.

▪ Usability expert, Luke Wroblewksi wrote an article called “Dropdowns Should be the UI of Last Resort.”2 In it, he suggests some better alternatives, some of which we’ll discuss later in this chapter.

▪ The search form is simple enough and contains just three elements: the label, search input, and submit button.

￼

Search form.

▪ Branching involves users being asked different questions depending on previous answers. For example, if users are expensing a car, they’ll need to enter mileage; if they’re expensing a train ticket, then they’ll need to enter its price.

▪ For example, a larger hit area is crucial for motor-impaired users, but is easier to hit for those without impairments too.

▪ Interactive filters update as soon as the user clicks a filter. The advantage is that users will see the results update as they go.

▪ The placeholder attribute is intended to store a hint. It gives users extra guidance when filling out a field — particularly useful for fields that have complex rules such as a password field.

▪ One disadvantage is that each click causes a page refresh, which can cause frustration due to lag and getting scrolled back to the top of the page — something that will happen every time the user selects a filter. This is especially problematic for keyboard users as they’ll have to tab back to where they were.

▪ •The aria-expanded attribute indicates whether the calendar is currently in an open (expanded) or closed (collapsed) state by toggling between true and false values.

▪ As placeholder text is not a real value, it’s grayed out so that it can be differentiated from user-entered values.

▪ Now that it’s hidden, we can style the control’s label, which is easy to style. As described in “A Registration Form,” this works because a control’s label acts as a proxy to the control itself: clicking the label is like clicking the input.

▪ The problem with radio buttons is that they’re less suitable when there are many options. An airline could fly to hundreds of destinations, making the page long and hard to scan. This in turn means users have to scroll a lot more.

▪ In “The Psychology of Checklists,”3 Lauren Marchese explains the importance of breaking down big tasks into smaller ones, which is proven to motivate people. When we experience even small amounts of success, our brains release a chemical called dopamine, which gives us feelings of pleasure, learning, and motivation.

▪ Unlike labels, hints are optional and shouldn’t be used as a matter of course. Just because the placeholder attribute exists doesn’t mean we have to use it. You don’t need a placeholder of “Enter your first name” when the label is “First name” — that’s needless duplication.

▪ Batch filters work by letting users set a number of options before submitting and reloading the page (see above). One advantage of this approach is that it’s faster, as users just make one request for several filters.

▪ Typically, search is placed within the header. Like navigation, this makes it easily discoverable and quick to access. Putting such an integral feature elsewhere on the page would be counterintuitive and unconventional.

▪ The Add Another Pattern

Both the persistent form pattern and the one thing per page pattern suffer from the same problem — that each expense created requires at least one trip to the server, which is slow. How might we solve this problem?

▪ One disadvantage of this approach is that a combination of filters could lead to zero results.

▪ The challenge, of course, is that it’s hard to fit the search form inside the header along with everything else. The header is premium screen real estate. That is, there isn’t much room available and it’s highly sought after. The more we put into the header, the more the main content is pushed down the page.

▪ What’s really happening is that tasks seem far easier to achieve when they’re broken down. Crucially, if tasks are small enough, then we’ll get that hit of dopamine more frequently, which creates momentum. Momentum improves morale, and morale improves productivity.

▪ Give users a hint text. Users will have a greater chance of success without having to wait for a useful error message.

▪ Let users reveal their password using the password reveal pattern.

▪ The form starts with enough fields to enter one expense. However, there’s an “Add another” button, that when pressed, will instantly clone the fields so that users can enter the details of an additional expense.

▪ Some login forms, such as those found on bank sites, ask users for certain characters of their password. Or they may ask for certain digits from a security pin. In either case, users are normally given three separate text boxes or select boxes.

▪ Users need a control that lets them filter a long list of destinations. A control that marries the flexibility of a text box with the assurance of a select box. This type of control goes by many different names, including: type ahead, predictive search, and combo box; but we’ll refer to it as an autocomplete control.

▪ Let’s look at some ways to reduce the size of the search form, so that it might fit inside the header more easily. We’ll discuss various problems and considerations we need to think about with each technique.

▪ That’s a lot of problems for what is essentially just text. All content, especially a form hint, shouldn’t be considered as nice to have. So instead of using placeholders, it’s better to position hint text above the control like this:

▪ Unfortunately, most screen readers don’t differentiate between unordered and ordered lists in any meaningful way. But this shouldn’t stop us from using the most appropriate element. As support improves, the benefits will be ready and waiting.

▪ Autocomplete controls work by filtering options (destinations in this case) as the user types. As suggestions appear, users can select one quickly, automatically completing the field. This saves users having to scroll (unless they want to), while also being able to forgive small typos.

▪ The task list pattern4, as coined by the Government Digital Service (GDS), shows a page with several top level tasks.

Each top-level task is broken down into several subtasks. Each one of those takes users through a flow — whether each flow consists of one or several screens doesn’t really matter, as long as it’s achievable in a reasonable time. Once a subtask is completed, users come back to the task list view with that particular task marked as complete.

▪ By placing it inside the label it will be read out by screen readers, and further enlarges the hit area.

▪ The aria-describedby attribute is used to connect the hint by its id — just like the for attribute for labels, but in reverse. It’s appended to the control’s label and read out after a short pause. In this example, “password [pause] must contain eight plus characters with at least one number and one uppercase letter.”

▪ MailChimp’s campaign task list page showing that two tasks still need to be completed.

▪ The exact design details you choose will come down to your product’s design language and user research, but it’s key to ensure that:

•each task status is clearly marked so users can see what’s left at a glance

•users can get a feel for how long is left until completion

•previous information is saved, so that users can return easily to it later

▪ There are other differences too. First, clicking the hint (a 

in this case) won’t focus the control, which reduces the hit area. Second, despite ARIA’s growing support, it’s never going to be as well supported as native elements. In this particular case, Internet Explorer 11 doesn’t support aria-describedby4.

▪ The easiest but most problematic way to solve this would be to add the multiple boolean attribute to the file input:



This provides the same method of file selection as described above, except users can select multiple files from within the dialog.

▪ We’ll first design the checkout journey for anonymous users. Not letting users check out as a guest is just about the worst thing we can do, as Jared Spool attests to beautifully in “The $300 Million Button.”6

▪ “Sign in” is perhaps more human than “Log in.” When you visit a spa or office building, signing in grants you entry. And you sign out as you leave. It’s usually sensible to use the same language for digital experiences too.

It can, however, depend on the industry. Banks, for example, tend to use “Log in.” The notion of logging came along with computers in the 80s — the operations that users do are logged for security reasons.

▪ This is why the first rule of ARIA is not to use ARIA5:

▪ That would be it, if you ignored two significant problems.

First, users can only select files within a single folder. If they need to upload files from different folders, they can’t. Of course, users could move all the files into a single folder beforehand but this puts the onus on the user.

▪ The article tells a story of one company losing 300 million dollars because they thought forcing users to register first would help speed up subsequent purchases. While this is true, it also assumes users want to sign up in the first place.

▪ “If you can use a native HTML element or attribute with the semantics and behaviour you require already built in, instead of re-purposing an element and adding an ARIA role, state or property to make it accessible, then do so.”

▪ Float Labels

The float label pattern6 by Matt Smith is a technique that uses the label as a placeholder. The label starts inside the control, but floats above the control as the user types, hence the name. This technique is often lauded for its quirky, minimalist, and space-saving qualities.

▪ Second, not all browsers support the multiple attribute. And when support is lacking, a single file input may be found wanting. For example, take a form which asks users to submit receipts. When the multiple attribute is supported, users can upload all the relevant receipts and submit them. Without support, users can only upload a single receipt.

▪ We should design interfaces that speak in a language familiar to the user. Whichever you choose, be consistent (inclusive design principle 3). Make URLs, links, headings, and buttons match. And if users click “Log in” to log in, then they should click “Log out” to log out.

▪ Trying to meet two user needs (viewing and managing) in a single interface is partially responsible for the problem in the first place. One way to avoid the issue would be to split these needs apart using the concept of modes. This just means letting users switch between managing email and reading it.

▪ Second, the button is a fundamental part of a form — without it, it’s not clear how users are meant to perform the search. While we may be aware that forms can be submitted implicitly (by pressing Enter), not all users are.

▪ Sometimes, we deliberately make things difficult to use. A door by its very nature isn’t easy to use — it would be far easier if there was no door at all. Login forms need to be somewhat difficult to use, otherwise they wouldn’t be secure.

▪ One way to solve this problem involves giving users a way to add more files as part of the flow:

▪ The power of the web is one of reach and accessibility. Anyone with a browser and an internet connection gets to use it.

▪ Many login forms make the same mistake of showing users an error message that says “The username and password don’t match.” But as Jared Spool comically explains in “Is Design Metrically Opposed?”3:

“We know which one doesn’t match, we’re just not going to tell you, because our security people think that if we told you that it was the password, they would know they had a legal username and they would try every possible password in history.”

As noted earlier, hackers don’t actually do this. But even if they did, it’s easy to check username availability by trying to register an account with that username.

▪ •Using verbs for task names. For example, “Agree to the terms,” “Create subject line,” “Choose template.”

▪ Most forms are ephemeral — users submit a form and they’re taken to another page without a form. For example, when registering, users are taken to a confirmation screen.

▪ One of the main takeaways from chapter 1 was the need to justify the existence of each and every form field.

▪ Frank Chimero talks about this at length in “The Web’s Grain,”2 one of my favorite articles on design.

▪ Interestingly, many of the sites that omit the submit button normally find room to include a magnifying glass icon to signify its otherwise hidden affordance. In this case, they may as well place the icon inside a submit button solving both problems at the same time.

▪ Here, it’s because we can send users a receipt, which is particularly important if checking out anonymously. Additionally, the email may provide details about how to return the item, or cancel or change the order. We can tell users this transparently via the hint text.

▪ The main point of the article encourages us not to aim to tackle complexity, but do our very best to avoid it in the first place, mostly by “going with the grain” and embracing the web’s constraints.

▪ •Sizing all the tasks the same. Don’t take this too literally, but if one task is twenty questions and another is two, then take another look.

▪ “Seems like a lot of effort when you could simply put labels above inputs & get all the benefits/none of the issues.”
— Luke Wroblewski on float labels7

▪ It turns out that not only is this the easiest and cheapest way to design something, but also that users have a better time operating these simpler interfaces in the end. It’s the content and functionality users want anyway.

▪ But the label is set to “Continue,” which implies progress, and is better suited to the linear checkout flow.

▪ Like the email field, we should be asking ourselves why we’re requesting a phone number. We know the courier offers real-time text messages on the day of delivery — but the customer doesn’t. So we tell them via the hint.

▪ I can’t think of a better set of principles than the inclusive design principles3 from the Paciello Group. These principles are about good design — and good design is inclusive.

▪ Even if removing the label and submit button didn’t degrade the usability of the form, it still wouldn’t really solve the space problem enough to fit the form comfortably within the header.

Instead of messing around with pixels to this extent, we can toggle the entire form’s visibility by letting users click a button. Finding room in the header for a button is relatively straightforward. And including a visible label, a hint (if needed), and a submit button is an easy task.

▪ Remember, the hint is not just for formatting rules: it’s for anything that will help users fill out the field. This transparency builds trust, reduces effort, and promotes the feature all at the same time.

▪ •Avoid really long and complex forms if you can.

▪ Note the file input has the multiple attribute. When used in conjunction with a persistent form, the multiple attribute becomes a robust enhancement. Where supported, users can select multiple files at a time, meaning fewer requests and a streamlined experience.

However, when not supported, users can keep uploading a single file at a time, as many times as they need to until the task is finished. This solves the problem I mentioned earlier regarding uploading files from different folders.

▪ One powerful and natural way to reduce the size of a form is to use a question protocol8. It helps ensure you know why you are asking every question or including a form field.

▪ •In more complex situations, ask users a series of questions to determine the best course of action, and save their time and the operating costs of the service.

▪ People use your interface in different situations. Make sure your interface delivers a valuable experience to people regardless of their circumstances.

▪ The form initially starts out with just a single expense. There’s no “Remove” button because the user has to submit at least one expense. However, when the user adds another expense, we need to add a remove button to the first expense. To do this, when the “Add another” button is pressed, we’ll need to check whether a remove button should be added.

▪ The role="grid" attribute (and each cell’s role="gridcell" attribute) tells screen readers to treat the table as a grid. Without this, JAWS, for example, won’t let users operate the calendar with the arrow keys using JavaScript. This is because the arrow keys are reserved for operating a standard table in a special way.

▪ •Break up large tasks into smaller pieces, and allow users to save their progress so they can return later easily.

▪ •Be consistent. Use familiar conventions and apply them consistently

▪ In all likelihood, you don’t need to ask for the user’s first and last name for them to register. If you need that information later, for whatever reason, ask for it then. By removing these fields, we can halve the size of the form. All without resorting to novel and problematic patterns.

▪ The input’s type="tel" attribute will spawn a telephone-specific keyboard on mobile devices. This makes it easier to enter a phone number thanks to the larger keypad.

▪ •Offer choice. Consider providing different ways for people to complete tasks, especially those that are complex or non-standard

▪ Many sites design the login page with a unique, minimalist layout. For example, when users try to add a product to their basket on Tesco’s website, they’re taken to a login page with a very different layout.

▪ •Prioritize content. Help users focus on core tasks, features, and information by prioritising them within the content and layout.

▪ First, it’s not immediately obvious that dragging and dropping is even possible — there are no signifiers that make this behavior perceivable. Second, the drop zone has a small hit area, which makes it hard to use, especially for motor-impaired users.

▪ No Password Sign-In

One way to avoid asking users for a password is to use the no password sign-in pattern. It works by making use of the security of email (which already needs a password). Users enter only their email address, and the service sends a special link to their inbox. Following it logs the user into the service immediately.

▪ Each cell contains a number (the date), which is perfectly adequate for sighted users as they can see the entire calendar. But screen reader users would only hear “Seventeen,” which is ambiguous unless they carefully remember the previously announced month and year. To provide a comparable experience (inclusive design principle 1), we put the full date inside the aria-label attribute.

▪ By convention, required fields are marked with an asterisk. A legend is usually placed above the form to denote its meaning, but as Luke Wroblewski says7:

“[…] including the phrase ‘optional’ after a label is much clearer than any visual symbol you could use to mean the same thing. Someone may always wonder ‘what does this asterisk mean?’ and have to go hunting for a legend that explains things.”

▪ These principles should, at least indirectly, hold us to account throughout the design process.

▪ By looking at common form patterns through the lens of inclusivity, this book will help you learn how to apply and reuse conventions that help users complete the task, regardless of how they choose or need to use your service.

▪ Not only does this reduce the size of the form to just one field, but it also saves users having to remember another password.

▪ First, users might be less familiar with this approach, and many people are worried about online security.

▪ You might also be wondering why we’re marking optional fields, instead of required ones. In “Required Versus Optional Fields,” Jessica Enders says8:

“[…] think about what we are doing when we mark something in an interface. We are trying […] to indicate that it’s different.”

▪ It’s also worth noting that a drag-and-drop enhancement is just that — an enhancement. It should be used in conjunction with a standard file picker. First, because users can’t actually drag and drop files on mobile, for example. Second, users with dexterity problems, such as tremors, may have difficulty dragging a file.

▪ It’s conventionally styled with a dashed border. However, if your users aren’t familiar with this convention, you can add instructional text.

▪ Like the autocomplete component we designed earlier, the grid is a composite control made up of many interactive elements — as many as 31, depending on the month. As discussed earlier, composite controls should have just one tab stop: having to tab through 31 days is tiresome and inefficient.

▪ Most sites give users a way to reset their password if they forget it. The feature itself isn’t especially problematic. It’s the placement of the link within the login form that can cause usability issues. If the link is just above the password field, when users tab from the email field, it’s the link that will receive focus, not the password field. Some users will tab and start typing, not realizing what’s happened.

▪ •Maintain search text. When the user arrives at the search page, what they typed should persist. This way users can make tweaks without having to retype the entire query.

▪ Whether it’s the no password sign-in pattern or passphrases, we should only move away from convention once we’ve conducted thorough and diverse user research. You don’t want to exchange one set of problems for another unknowingly.

▪ Worse still is when the link is placed before the submit button. When keyboard and screen reader users tab from the password field and press Enter, they’ll expect the form to submit. But instead, they’ll be taken to reset their password. When they realize what’s happened, they’ll need to go back, reenter their credentials, and be careful not to make the same mistake again.

▪ •Display result count. Tell users how many results have been returned. A simple approach would be to update the page’s 

text to read “Search results for [search term]” or similar. Users can then decide what their next action is. For example, if there are many results, they may decide to filter them (more on this in the next chapter).

▪ Matteo Penzo’s eye-tracking tests10 showed that positioning the label above (as opposed to beside) the form control works best.

▪ •Let users sort. Depending on the dataset being searched, it’s often useful to let users sort by relevance, popularity, or recency, for example.

▪ I interviewed Dave House, a former designer for Gumtree, a site which uses filters extensively. Dave and his team conducted many rounds of usability tests and here’s what he said:

“On desktop, Gumtree users would select filters without submitting them. They didn’t expect to have to submit their choices. We heard a lot of feedback saying ‘Your filters are broken.’”

▪ Implicit submission lets users submit the form by pressing Enter when focus is within a field. This convention speeds up submission without having to move focus to the submit button. This is especially useful for a single field form such as a search form.

▪ But giving the postcode field the same width as every other field increases the cognitive effort needed to fill it out. This is because the width gives users a clue as to the length of the content it requires.

▪ •Don’t employ infinite scrolling by default. It’s an anti-pattern with several usability issues5. This leaves “Show more” or standard pagination. “Show more” is more appropriate for sites with a lot of user-generated content, where the location of the result is not important. Pagination is more appropriate for ecommerce sites, where users are looking for a specific item, not just browsing for entertainment.

▪ Baymard Institute’s study10 found that:

“If a field was too long or too short, [users] started to wonder if they had misunderstood the label. […] This was especially true for fields with uncommon data or a technical label like CVV [card verification value].”

▪ Having multiple submit buttons with differing actions is problematic because if the user presses Enter, which action will be taken? The answer is that browsers will choose the first button in the document source.

▪ Dragover and Dragleave Events

When the user is dragging files over the drop zone, they should be given feedback so they know that the files can be dropped.

▪ This phenomenon is known as Jakob’s law4:

“Users spend most of their time on other sites. This means that users prefer your site to work the same way as all the other sites they already know.”

▪ Sites have recently started to offer users the ability to log in with social networks, such as Facebook, Twitter, and Google. This saves users having to type credentials they may not remember.

▪ Managing Focus

When the “Add another” button is clicked, it should focus the first newly created form field. Screen readers will announce the field, prompting the user to fill out the expense.

▪ Capture+11 is a third-party plugin that lets users search for their address quickly and accurately. Instead of manually typing each part of the address in five separate boxes, users type into just one.

▪ It means that a text box should look like a text box. Empty boxes signify “fill me in” by virtue of being empty, like a coloring-in book. This happens to be part of the reason placeholders are unhelpful. They remove the perceived affordance an empty text box would otherwise provide.

▪ As the user types the first line of their address, suggestions will appear from which they can select. This reduces the number of keystrokes and therefore the chance of typos.

▪ Users are worried about their privacy. They don’t know what you’ll do automatically, and they want to feel as though their information is safe and any actions they perform are intended.

Medium does this well: on the login page it says, “We won’t post without asking,” which puts users’ minds at ease.

▪ And this may work for radio buttons and checkboxes, but what if there were text boxes that could be used to enter a price range? When would users expect the form to submit? Submitting while typing is out of the question. This leaves submitting the form on blur (tabbing or clicking out of the field), which is odd and unintuitive. We’d need a submit button just for that box.

▪ This also means that the empty space should be boxed in (bordered). Removing the border, or having only a bottom border, for example, removes the perceived affordances. A bottom border might at first appear to be a separator. Even if you know you have to fill something in, does the value go above the line or below it?

▪ If no address is found, users can change the interface back to the original address form. In doing so, we conform to inclusive design principle 5, “Offer choice.”

▪ Spatially, the label should be closest to its form control, not the previous field’s control. Things that appear close together suggest they belong together12.

▪ Having equal spacing might improve aesthetics, but it would be at the cost of usability.

▪ This probably means a font size of at least 16 pixels, and ideally an overall tap target of at least 44px13.

▪ Focus styles are a simpler prospect. By default, browsers put an outline around the element in focus so users, especially those who use a keyboard, know where they are. The problem with the default styling is that it is often faint and hard to see, and somewhat ugly.

▪ While this is the case, don’t be tempted to remove it, because doing so will diminish the user experience greatly for those traversing the screen by keyboard.

▪ Grouping

To group multiple controls, we must wrap them in a fieldset. The legend describes the group like a label describes the individual control.

▪ Some screen readers, such as NVDA, will read the legend out, along with the first individual radio button’s label when entering the field (in either direction). In this example, “Delivery options, Standard (Free two to three days)” is announced. In other screen readers, such as Voiceover with Safari, the legend is announced for every field.

If we omitted the fieldset and legend elements, screen reader users would only hear “Standard (Free, two to three days),” which is less clear.

▪ Barry Schwartz, author of The Paradox of Choice, presents a case study in which researchers set up two displays of jams at a gourmet food store. Customers could try samples, and were then given a coupon for a dollar off if they bought a jar. One display had 24 jams, the other had just 6. Around 30% of people exposed to the smaller selection bought a jam, but only 3% of those exposed to the larger selection did.

▪ Second, sticky menus are usually employed to solve symptoms that mask the true underlying problems; for example, that the page is often too long in the first place.

▪ type="email"

▪ You may be tempted to group all fields this way. For example, the address form from earlier could be wrapped inside a fieldset with a legend set to “Address.” While this is technically valid, it’s unnecessary and verbose, as the field labels make sense without a legend. Put another way, users don’t need to hear “Address: Address Line 1” as it doesn’t add value.

▪ Third, the items within the sticky menus are difficult to focus with the keyboard. You might be halfway down the page but the menu (which is in close proximity visually) could be a long way away via the keyboard.

▪ John Saito explains that sentence case (as opposed to title case) is generally easier to read, friendlier, and makes it easier to spot nouns.

▪ Whether you heed this advice is up to you, but whatever style you choose, be sure to use it consistently.

▪ The input’s type attribute is set to email, which triggers an email-specific onscreen keyboard on mobile devices. This gives users easy access to the @ and . (dot) symbols which every email address must contain.

▪ A radio button group, for example, is a composite control that has one tab stop. Once the first radio button is focused, users can use the arrow keys to move between the options. Pressing Tab at anytime from within the group moves focus to the next focusable control in the tab sequence.

▪ Android’s onscreen keyboard for the email field.

▪ “[…] browsers don’t know where to place focus when it has been destroyed in this way. Some maintain a sort of “ghost” focus where the item used to exist, while others jump to focus the next focusable element. Some flip out completely and default to focusing the outer document — meaning keyboard users have to crawl […] back to where the removed element was.”

▪ People using a non-supporting browser will see a standard text input (). This is a form of progressive enhancement, which is a cornerstone of designing inclusive experiences

▪ It’s all well and good having uploaded the files to the server, but at this moment the user hasn’t been given any feedback as to what’s happened. Perhaps the file couldn’t be uploaded, for example. There are a number of times we need to give users feedback: during upload, on success, and on error.

▪ Files can take a long time to upload, especially if the connection is slow. It’s important to give users feedback during upload — not just on completion.

We can show feedback with a progress bar. Each file is represented separately as there’s a separate request for each one. This way, some small files will upload quickly, while others load more slowly in parallel.

▪ We could set focus to the previous or next expense item, but this seems arbitrary and confusing. Alternatively, we could set focus to the “Add another” button, but that’s presumptuous and odd — why delete an item if you’re just going to add another one — users are better off just typing over the fields that are already there.

▪ But we discussed the problems with disabled buttons in chapter 1, “A Registration Form.” As a quick reminder, they don’t tell users why they’re disabled, and screen reader users can’t focus them.

▪ Instead, we can set focus to the heading, which puts users back to the beginning of the expense form while announcing itself (“Expenses, heading, level 1,” or similar) to screen reader users.

▪ Fortunately, a radio button’s label acts as a proxy for the radio button itself. That is, when clicked, the radio button will become checked (or unchecked, depending on state). Unfortunately, many users don’t realize they can do this14. This is hardly surprising because labels have very little to signify that clicking them would do anything different to regular copy.

To give users a better chance, we can color them gray and make them respond to the mouse on hover. However, even with these enhancements, some users may still be unaware. GDS’s research showed this to be the case, which is why they embarked on developing custom radio button controls.

▪ That’s fine, though, because users will get a text box () instead. Users can still enter an email address; they just don’t get an email-specific keyboard on mobile

▪ The problem with creating custom controls is that you have to reimplement all the behavior that is provided natively for free. This is very involved, and despite GDS’s in-depth attempts, they aren’t without their problems15.

▪ Number inputs have little spinner buttons (also called steppers), which let users increase or decrease the input’s value by a constant amount. Luke Wroblewski’s usability testing shows that users prefer them to drop down menus:

“When testing mobile flight booking forms, we found people preferred steppers for selecting the number of passengers. No dropdown menu required, especially since there’s a maximum of 8 travelers allowed and the vast majority select 1–2 travelers.”

▪ The progress bar’s inner text is also set. This is so users with a browser that lacks support for the element can still see it. That’s inclusive.

▪ Select boxes are a menu of sorts. In fact, sometimes, they’re referred to as dropdown menus, among other names.

▪ Next, we want to show users when a file has been successfully uploaded. First, the file name is converted into a link so users can download and verify the file if they wish. Second, we inject a success message of “File uploaded” and a Remove button, which is useful if the file was uploaded by mistake.

▪ The only downside is that the browser-provided spinners are tiny, which make them difficult to use. And some browsers don’t show them at all. We can solve this problem by creating our own custom stepper component.

▪ It’s possible that judicious animation effects can help users understand an interface.

But all too often, designers want to add animation for the sake of it. Users just want to get things done. Needless animation is jarring and actually detracts from the user experience. Like anything else, animation should only be used if it adds value.

▪ They’re an attractive option because, as we know, browsers supply them for free. But even though select boxes look like menus and behave like them, and even though they are sometimes referred to as menus, they aren’t true menus.

▪ The textarea is similar to a text box except it allows users to enter multiple lines of text, which is particularly appropriate for a delivery note. (Remember: the size of the field gives users a clue as to the length of content needed.)

▪ Even when animation is valuable to some users, it can be harmful to users with cognitive impairments6, such as attention deficit hyperactivity disorder (ADHD) and autism.

▪ Select boxes are for input. That’s why forms that contain select boxes — like any other input — must be accompanied by a submit button to submit the choice. Not only is this convention, but it’s also in the Web Content Accessibility Guidelines (WCAG)5.

▪ The maxlength attribute (which takes a number value) limits the amount of a text a user can type. As soon as the limit is reached, the browser will ignore the input. Support for this attribute16 on a textarea is both lacking and buggy.

▪ There are also problems for screen reader and keyboard users. For example, on Chrome (Windows), the onchange event is fired as soon as the user presses Down to select the next option. But with this approach in place, the form is immediately submitted, making it impossible to move through all the items in the menu.

▪ But even if it was well supported, it’s not recommended because some users don’t look at the screen as they type — they are focused solely on the keyboard. When a user enters a lot of text, they’ll look up to find half their entry has been truncated. Not good.

▪ If the uploaded file is too big, or in the wrong format, we’ll need to show users an error message. This is similar to the success message, but instead of showing a green success message with a tick, we’ll show a red message with a warning symbol. Note that the error markup below is the same as the error markup used to show validation errors in a standard form.

▪ Instead, we should let users type freely, and tell users how many characters they have left. This way, users can see the feedback when they finally look up at the screen and can edit their entry in response. If they don’t notice the feedback, an error will be shown when they submit the form, thanks to the validation routine (set out in chapter 1, “A Registration Form”).

▪ •The button’s aria-label attribute ensures that screen readers announce “Remove” instead of “minus symbol”. Same goes for “Add” instead of “plus symbol”.

▪ The type="password" attribute masks the input’s value by replacing what the user types with small black dots. This is a security measure that stops people seeing what you typed if they happen to be close by.

▪ •The button’s aria-describedby attribute references the label’s id, which means it combines with the label text to give screen reader users extra context. As there are three fields on the page, this stops users thinking “Remove — remove what, exactly?”

▪ Owing to the increased risk of typos, some registration forms include an additional “Confirm password” field. This is a precautionary measure that requires the user to type the same password twice, doubling the effort and degrading the user experience.

▪ Instead, it’s better to let users reveal their password, which speaks to principles 4 and 5, give control and offer choice respectively. This way users can choose to reveal their password when they know nobody is looking, reducing the risk of typos.

▪ Icons are often the source of heated debates amongst designers, mostly because they have their pros and cons.

The pros are that they save space, and internationally recognized icons overcome language barriers, which is why they’re often used in airports.

The cons are that icons can be misunderstood, and they are a poor replacement for just using text. In “The best icon is a text label,” Thomas Byttebier goes as far to say19:

▪ Recent versions of Internet Explorer and Microsoft Edge provide this behavior natively. As we’ll be creating our own solution, we should suppress this feature using CSS like this:

▪ Screen readers will normally only announce content when it is focused, but live regions announce their content when it changes. This means we can communicate to screen reader users without asking them to leave their current location. In this case, it means users can continue to type into the textarea.

▪ 

You have 100 characters remaining.



▪ Now we also have tablets, desktops, and really big desktop screens. We can browse on large screen televisions and tiny watches. If your head is spinning, don’t worry, so is mine. This is the problem that responsive design solves and adaptive design exacerbates.

▪ •The aria-live="polite" property17 and the status role18 are equivalent. Both are provided to maximize compatibility across platforms and screen readers (in some setups, only one or the other is recognized).

▪ The difference between responsive and adaptive design is both subtle and crucial. Both techniques are often based on viewport width. And both use CSS media queries to change the interface. But they are really quite different.

▪ •The equivalent alert and assertive values mean the current readout of the screen reader will be interrupted to announce the live region’s new content. In this case, interrupting the user as they’re typing is aggressive. So we can keep status and polite values, which means the contents are announced after the user stops typing for a moment.

▪ The other common understanding of adaptive design is about defining several different (parts of) layouts, made up of different HTML that’s rendered. Originally, this was based on user agent string8. Sometimes, JavaScript is used to restructure the arrangement of HTML at certain viewport widths. But more commonly these days, it’s done using CSS media queries. We’ll focus on this flavor of adaptive design from this point.

▪ The flights are represented as radio buttons — the user can select only one. Each label contains the departure time, arrival time, and ticket price: all useful information. One advantage of using radio buttons is that you can add any information inside the label and style it as you like, something you couldn’t do if you were using a select box.

▪ First, we can set a maximum height on the filter and give it an additional inner scroll bar. However, inline scroll areas are really hard to use; so much so, that Baymard Institute says they should be avoided9.

▪ Second, we can use progressive disclosure to collapse the filter categories. We’ll be looking at this in detail shortly.

▪ Removing Fields

There are a number of details on a credit or debit card: name on card, card number, valid from date, expiry date, issue number, security number; all of these are commonly found on payment forms. But not all of these details are necessary to process a payment.

▪ The password reveal interface we constructed above toggles the button’s label between “Show password” and “Hide password.” Some screen reader users can get confused when the button’s label is changed; once a user encounters a button, they expect that button to persist. Even though the button is persistent, changing the label makes it appear not to be.

▪ The aria-invalid="true" attribute is placed on the fieldset. Putting it directly on the radio button would be incorrect here, because it’s not the individual input that’s invalid — it’s the group.

▪ Where adaptive design tries to bend the web to its will, responsive design embraces it. Responsive design understands that you can’t possibly design for every device and browser individually. That’s just not how the web works. Instead, responsive design encourages us to design interfaces that work on any size screen.

▪ First, use a checkbox with a persistent label of “Show password.” The state will be signaled by the checked attribute. Screen reader users will hear “Show password, checkbox, checked” (or similar). Sighted users will see the checkbox tick mark.

▪ Additionally, we can collapse the categories. This is advantageous for a number of reasons:

1. The submit button is more likely to draw users’ attention as it will be in view.

2. Ajax-injected results will likely be in view.

3. Users shouldn’t have to scroll nearly as much, while still being able to scan the filter categories.

4. Keyboard users won’t have to tab through all the filters to get to the one they want. This is because hidden content isn’t focusable.

▪ Ed Horsford, a designer at GDS, conducted research around this for the UK’s passport renewal service, which involves users uploading a passport photo. He said that desktop users who used a file importer (such as Windows photo importer) struggled to find where the file was imported when it came to selecting it from the file picker.

▪ Or, second, change the button’s state — not the label. To convey the state to screen reader users, you can switch the aria-pressed attribute between true (pressed) and false (unpressed).

▪ Design is a team sport, and so we should treat it as one. By designing (and researching) with a diverse set of people, we’ll frequently end up producing a far better experience.

▪ 
Show password


▪ On the web, menus are sometimes opened on hover. Designers often assume that this aids discovery and saves users the effort of clicking. The thing is, there are many problems with opening a menu (or anything really) on hover and the effort of clicking a part of the interface is extremely low.

▪ When researching this section for the book, I decided to speak to Stripe to see if we could reduce the amount of fields even more. Here’s what they said:

“The bare minimum information needed to attempt a valid payment is card number, CVV, and expiration date. Additional information will allow the card-issuing bank to make a more informed decision about accepting or declining the payment, so while more information isn’t required, it will improve your chances of the payment succeeding. It will also provide you more information for verifying the payment is valid and authorized, and therefore can help reduce the likelihood of a dispute and help you with contesting the dispute if it does occur.”

▪ First, hovering is not an intention to open the menu. When a user moves over a hover menu it can obscure the content behind it, which disrupts the experience. With the inbox, as the user goes to select the first checkbox, they may accidentally end up clicking one of the items in the menu, which fails inclusive design principle 4, “Give Control.”

▪ To demarcate window seats and aisle seats for screen reader users, we can put hidden text inside the seat’s label.

▪ It’s Easier to Take a Photo on Mobile

Your photos are taken and stored on your mobile device, so it’s easier to upload them using that device: there’s no need to transfer files from elsewhere. That’s all well and good if people are using your service on mobile, but what if they’re on desktop?

▪ Second, users have to be careful to keep the cursor within the bounds of the menu, otherwise it will close. This is known as a hover tunnel, and is especially difficult to operate with motor impairments.

▪ Buttons that submit forms are “submit buttons” and they are coded typically as either or .

▪ Third, not all users use a mouse (or other types of pointing device) and touchscreen devices are usually operated without one.

▪ type.

“Chrome autofill: used 9 billion times/month; saves an average of 12 seconds; 1.25 million days saved/month”
— Luke Wroblewski, October 24, 201721

▪ You should note that opening a menu on hover on desktop and on click for mobile isn’t recommended either. There are many large touchscreen devices and many small screen laptops. Features should never be inferred from screen size.

▪ You can read Léonie Watson’s article “Using the fieldset and legend elements”20 for more information about this.

▪ Since iOS 8, Safari lets users scan their card using the iPhone’s camera — it uses the same mechanism to automatically fill out those fields.

Not only does this drastically reduce the amount of effort to complete the form, but it also eliminates the chance of typos: two very helpful improvements to a form that has the highest drop-off rates in ecommerce.

▪ Third-Party Integration

Some digitally savvy users may already use third-party services, such as Dropbox, to store files. Giving users a way to upload or provide files from these services may well be easier for them, especially if your service is already connected with theirs.

Be warned, however, that it may be unhelpful or even confusing to users who don’t know what Dropbox is. Be sure to make the different choices clear, and test widely in user research sessions.

▪ In “Checkboxes Are Never Round,”21 Daniel De Laney says:

“Interactive things have perceived affordances; the way they look tells us what they do and how to use them. That’s why checkboxes are square and radio buttons are round. Their appearance isn’t just for show — it signals what to expect from them. Making a checkbox round is like labeling the Push side of a door Pull.”

▪ Microcopy: “Upload” or “Attach”

Generally speaking, there are two ways to communicate to users about uploading files. The first is to use “Attach,” but this seems best suited for email. In almost every other situation “Upload” seems more common, which is what we used for our generic drag-and-drop upload form earlier.

▪ A radio button tells you that just one can be selected; checkboxes tell you that more than one can. So if one person is travelling, use radio buttons; otherwise, use checkboxes.

▪ Miller’s law would have you believe that we shouldn’t present users with more than seven radio buttons at a time. If you have more than seven, traditional advice would be to use a select box22.

▪ The accept attribute takes a string that indicates which types of file the picker will accept.

▪ Adding the capture attribute without a value lets the browser decide which camera to use (if there’s one available), while the user and environment values tell the browser to prefer the front and rear cameras respectively.

▪ The button’s text is just as important as its styling. The text should explicitly describe the action being taken. And because it’s an action, it should be a verb.

▪ Up to now, we’ve only considered the interface in the context of desktop-sized screens, where there’s enough space to fit the filter next to the results. But what about the small-screen experience?

▪ The capture attribute works on Android and iOS, but is ignored on desktop. Beware that on Android this means the user will no longer have the option of choosing an existing picture as the camera app will be started directly instead, which is probably undesirable.

▪ The matchMedia API is the JavaScript equivalent of a CSS media query. Where @media() {} is for CSS, matchMedia() is for JavaScript. It’s a way of keeping behavior and style in sync, based on the same media query. In this case, when the (min-width: 45em) media query is matched, big mode is enabled. When it doesn’t match, this means the viewport width is less than 45em, and so the script calls the enableSmallMode() method which constructs a toggle menu.

▪ Despite our efforts to create an inclusive, simple, and friction-free registration experience, we can’t eliminate human error. People make mistakes and when they do, we should make fixing them as easy as possible.

▪ We can’t just put the filters first, as this will push the results down the page. And we can’t just put them after the results, as users would have to move beyond them — most users wouldn’t know they exist.

▪ We’re left with having to collapse the filters behind a toggle button. We’ve covered this behavior extensively in chapters 5 and 6. Now we’re going to focus on another related problem.

▪ HTML5 validation has been around for a while now. By adding just a few HTML attributes, supporting browsers will mark erroneous fields when the form is submitted. Non-supporting browsers fall back to server-side validation.

▪ Earlier, I mentioned part of the interview I had with Dave House, a former Gumtree designer, who conducted a lot of research on how to deal with filters. In particular, that desktop users expected the filter to update the results as the user clicked filters with Ajax. However, Gumtree’s research also showed that on mobile this wasn’t desirable because users couldn’t see the results refresh.

▪ Here’s what Dave said:

“On mobile, Ajax wasn’t desirable because users couldn’t see any visible refresh of the results.The amount of filters available in some categories meant this would have happened off-screen. To the user this would have looked like nothing had changed. We didn’t want to move focus to the results on every interaction because users often wanted to pick more than one filter. We reluctantly had to use an adaptive approach. On mobile, clicking the “Refine” menu button would reveal a fullscreen filter panel where users could build up their refinements and submit when they were done.”

▪ While HTML5 validation support20 is quite good, it’s not implemented uniformly. For example, the required attribute can mark fields as invalid from the outset, which isn’t desirable. Some browsers, such as Firefox 45.7, will show an error of “Please enter an email address” even if the user entered something in the box, whereas Chrome, for example, says “Please include an ‘@’ in the email address,” which is more helpful.

▪ Admittedly, we’ve just discussed the cons of select boxes, but it must be said that one of their redeeming qualities is that they help users enter the right information. But in the case of dates, even this quality doesn’t hold up because you can select an invalid date, such as 31 February 2017.

▪ We need to make sure that users can see the results update as they filter. We can achieve this by having the filters appear on top of the results without completely covering them. It works because users can see the results on the left, while filters are selected on the right.

▪ I found this technique described in “Mobile Faceted Search with a Tray: New and Improved Design Pattern”11 by Kathryn Whitenton, which is worth reading in full.

▪ Arguably, this standard checkbox has all the ingredients of an accessible control. It’s screen reader and keyboard accessible. It communicates through its label and change of state. Its label would be “Select all” and its state would be announced as “checked” or “unchecked.” All this behavior without any JavaScript.

▪ The first problem is that sites don’t always refer to this field as the CVC number. Sometimes it’s referred to as a security code number or card verification value (CVV). Being specified as an acronym doesn’t help either. And to top it off, on the card the number is never accompanied by a description, making it hard to reconcile the requirements.

To fix this, we should employ the hint text pattern to tell users exactly what it is and where to find it. For example: “This is the last three digits on the back of the card.”

▪ Conventionally, errors are colored red. However, relying on color alone could exclude colorblind users. To draw attention to the summary, consider also using position, size, text, and iconography.

▪ The three fields are wrapped in a fieldset. The legend (“Date of birth”) gives each text box context and would be read out as “Date of birth, day” (or similar) in screen readers.

▪ The pattern attribute is used to trigger the numeric keyboard — a little enhancement for iOS users. If you’re wondering about why we haven’t used the number input, you can refer back to the number input in “A Checkout Form.”

▪ We can enhance the experience by hiding the billing address until the user unchecks the checkbox. This is a form of progressive disclosure, which means showing information only when it becomes relevant.

▪ As usual, our first port of call is to see if there’s a date picker control that browsers provide natively for free. Good news: there is. The date input () offers a special and convenient interface for picking dates while also enforcing a standard format for the value that’s sent to the server on submission.

▪ As the date picker is provided by the browser, you’ll notice how it looks a lot like the system date picker that’s used for setting dates and times on your phone. That’s by design so that mobile browsers can outsource the problem to native components. This is good because users will be familiar with it, which speaks to inclusive design principle 3, “Be consistent.”

▪ You might be concerned that they look different in different browser vendors. Don’t be. Most users don’t notice the difference and the rest don’t care. Remember, most people use the same browser every day. They only see their platform’s implementation. Unlike us, they’re not agonizing over subtle differences during cross-browser testing.

▪ Even though we’ve collected all the information required to process the order, we should first let users review their order. As counterintuitive as this may sound, adding an extra step in the flow actually reduces effort and likely increases conversion.

▪ “Nobody cares about your website as much as you do.”
— Goran Peuc, “Nobody Wants To Use Your Product”13

▪ However, if users are likely to stay on the page for a long time after, research might show that dismissing a message is valuable after all. Offer that functionality with a button. When clicked, it hides the message.

▪ Confirming versus Undoing

▪ Remember, filling out forms and checking information are two different mental contexts.

This also saves your (client’s) business time and money. If Jack wants to cancel the order, then handling calls and processing would be costly — especially if the business offers free returns.

▪ As a safety measure, some roads have speed bumps. They compel drivers to slow down on roads that are more likely to cause accidents. We can create a digital speed bump by asking users to confirm their action by asking them if they’re sure.

▪ Like the hint pattern mentioned earlier, the error message is injected inside the label. When the field is focused, screen reader users will hear the message in context, so they can freely move through the form without having to refer to the summary.

▪ This shows that relying solely on completion time as a metric for success is dangerous. You should also look at how accurate people’s orders are by checking how often items are returned.

▪ This is fine for infrequent tasks, but it quickly becomes tedious when that action needs to be performed more often. Continuing with the driving analogy, then: it’s a bit like putting speed bumps on the motorway. They’d probably cause more accidents than they’d stop.

▪ As this is the final step in the flow, the button’s text should be set to “Place order” or similar. Leaving it as “Continue” would mislead the user into thinking there is another step to complete, which is likely to result in more cancelled orders and strain on the customer service department. This would increase operating costs and shows that good design is also good for business.

▪ An alternative approach would be to let users perform the action immediately, without any warning. Then, along with the success message, give users the chance to undo the action. Clicking “Undo” would reverse the action by restoring the emails back to the inbox. If only we could undo accidents on the road.

▪ The date input will change into a basic text input — this is known as graceful degradation. While users won’t get the convenience of a date picker, they’ll still be able to enter a date. This is an example of HTML’s inherently resilient nature. When things fails, they don’t break.

▪ To give both sighted and non-sighted users an equivalent experience, we can use the well-supported aria-invalid attribute. When the user focuses the input, it will now announce “Invalid” (or similar) in screen readers.

▪ Making Changes

Every piece of information gathered during checkout should be represented on the review page. Users shouldn’t have to go back to check information — that would defeat the purpose of the page. Users should only need to go back if they spot a mistake.

▪ A success message panel with “Undo” button

▪ 

▪ Confirmation pages are so much more than just confirming the order. Neglecting the user experience here is a great way to lose out on future business.

▪ •Using checkboxes and select boxes for buttons and menu components.

▪ You should tell users what happens next, such as when delivery will take place, and what to do if something goes wrong.

It’s also the best time to ask users to sign up (if they checked out anonymously). As we have most of the information to hand, we only need to ask for a password, making this step both optional and easy. Users should have had a good experience up to now, which should naturally encourage sign-up.

▪ By giving users value, they’ll hopefully want to sign up. By value, I mean something as simple as offering a faster checkout next time, or offering them a discount on their next order. Depending on the service, you might even ask users to tweet or Instagram their purchase in return for a voucher

▪ “It takes one line of code to take a phone number and strip out all the dashes and parentheses and spaces, and it takes ten lines of code to write an error message that you left them in.”

▪ The addValidator method (shown above) demonstrates how to design validation rules so they forgive trivial mistakes. The first rule, for example, trims the value before checking its length, reducing the burden on the user.

▪ Here’s a checklist of things to consider including on the confirmation page:

•a reference number

•contact details

•what happens next and when

•what to do if something goes wrong

•ask users to sign up in return for something

•ask users to spread the word to get a voucher

•links to further information, if they might be useful

•a link to your feedback page

▪ I’ve made so many purchases with Amazon that I can’t even remember Amazon’s first-time experience. That is to say, I’ve made hundreds of purchases as a second-time user, and only one as a first-time user.

▪ For entries that require a certain number of characters, the first keystroke will always constitute an invalid entry. This means users will be interrupted early, which can cause them to switch mental contexts, from entering information to fixing it.

▪ We can bypass most of the steps by sending users straight to the review page. This way, users get a reminder of their default preferences with the chance to make amends should they wish to.

▪ Alternatively, we could wait until the user enters enough characters before showing an error. But this means users only get feedback after they have entered a correct value, which is somewhat pointless.

▪ We could wait until the user leaves the field (onblur), but this is too late as the user has mentally prepared for (and often started to type in) the next field. Moreover, some users switch windows or use a password manager when using a form. Doing so will trigger the blur event, causing an error to show before the user is finished. All very frustrating.

▪ Remember, there’s no problem with giving users feedback without a page refresh. Nor is there a problem with putting the error messages inline (next to fields) — we’ve done this already. The problem with live feedback is that it interrupts users either too early or too late, which often results in a jarring experience.

▪ Usually, checkout pages are given a special and more streamlined layout that helps reduce noise and keep users on-task. For example, the header usually contains a logo, security note, and accepted cards.

▪ By omitting navigation and search, users can focus on checking out, which speaks to inclusive design principle 6, “Prioritize content.”

▪ Progress bars or indicators are often used within checkout because — at least in theory — they give users an idea of where they are and how long’s left. Despite the sound reasoning, there isn’t much evidence to show that progress bars are all that useful or even noticed. For example, the UK government’s Carer’s Allowance team removed a 12-step progress bar with no effect on completion rates or times26.

▪ A variation of live validation involves ticking off rules (marking them as complete) as the user types. This is less invasive than live validation but isn’t suited to every type of field. Here’s an example of MailChimp’s sign-up form, which employs this technique for the password field.

▪ Progress bars pose some practical design challenges too. First, they take up a lot of space at the top of the page, which is particularly important on mobile where they can push the main content down. Second, fitting an accessible progress bar with clear labeling into a small viewport is nigh on impossible.

▪ MailChimp’s password field with instructions that get marked as the user meets the requirements.

▪ If that weren’t enough, they’re even trickier to design when the journey consists of conditional steps. Imagine a checkout that offers collection or delivery. If the user chooses to collect, they’re taken down a different path where they won’t need to give their payment details (as they’ll pay in-store).

▪ Some forms are designed to disable the submit button until all the fields become valid. There are several problems with this.

▪ In any case, having meticulously designed the journey to be as simple as possible, users should get to the end quickly, which reduces the need for the progress bar.

▪ Some forms are especially long — a lot longer than a checkout flow. In this case, you might need some indication of progress, which is something we’ll look at in chapter 10, “A Really Long and Complicated Form.”

▪ Progress Step Text

If you decide to give users an indication of progress, first try adding the step number inside the heading:

Payment (Step 3 of 4)



▪ “The system should always keep users informed about what is going on, through appropriate feedback.”
— Jakob Nielsen, “10 Usability Heuristics for User Interface Design”27

▪ •Use plain language. Error messages are not an opportunity to promote your brand’s humorous tone of voice.

▪ As the user is following a linear flow, we need to consider the need to step back. The browser’s back button provides this functionality for free, but some people mistrust it because of bad past experiences when their data was lost.

▪ Research might show you that it’s useful to include a back link within the interface itself, and that users will be more inclined to trust it. In this case, position the link at the top left of the page. By placing it at the top of the page, users can see that they can go back if they need to. And they’re less likely to fill out the form before hitting back and losing their data.
