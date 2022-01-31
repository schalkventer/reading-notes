Web Form Design: Filling in the Blanks

Luke Wroblewski

---

▪ Web form design. Do we really need an entire book on such a mundane topic?

- You bet we do. As arbiters of checkout, registration, and data entry, Web forms are often the lynchpins of successful Web applications.

▪ Checkout forms are how ecommerce vendors close deals—they stand between people and the products or services they want and between companies and their profits. For example, eBay’s vast inventory (it’s the 30th largest economy in the world) is driven in no small part by its Sell Your Item form.

▪ Registration forms are the gatekeepers to community membership—they allow people to define their identity within social applications. All of MySpace’s 150+ million users joined through a Web form.

▪ Data input forms allow users to contribute or share information, and they allow companies to grow their content. Most of YouTube’s huge video collection comes from its Upload Your Video form.

▪ This book is a collection of the insights and best practices for Web form design I’ve accumulated through 12 years of designing Web experiences. Wherever possible, I’ve conducted or referenced research to better understand the impact of Web form design decisions. Where no research was available, I’ve called on my own experiences and those of other designers and developers.

▪ Forms enable commerce, communities, and productivity on the Web to thrive. If you are in online retail, your goal is to sell things. But standing in the way of your products and your customers is a checkout form. If you are developing social software, your goal is to grow your community. Standing in between you and community members is a form. If you’ve built a productivity-based Web application, forms enable key interactions that let people create and manage content. See “Form Design Matters” for more information.

▪ How should I organize my Web form—within one Web page or across several?

Who is filling the form in and why? Answering this up front allows us to think about our forms as a deliberate conversation instead of the inputs for a database. When you approach forms as a conversation, natural breaks will emerge between topics.

▪ Should I top-, right-, or left-align the labels for input fields?

When you are trying to reduce completion times or if you need flexible label lengths for localization, consider top-aligned labels. When you have similar goals but vertical screen real estate constraints, consider right-aligned labels. When your form requires people to scan labels to learn what’s required or to answer a few specific questions out of many, consider left-aligned labels. See “Label Alignment”.

▪ When should I include help text on my forms?

You should consider adding help text when: forms ask for unfamiliar data; people question why they are being asked for specific data; people may be concerned about the security or privacy of their data; there are recommended ways of providing data; and certain data fields are optional or required when the bulk of the form is not. See “When to Help”.

▪ How should I indicate required input fields?

If most of the inputs on a form are required, indicate the few that are optional. If most of the inputs on a form are optional, indicate the few that are required. When indicating what form fields are either required or optional, text is the most clear. However, the * symbol is relatively well understood to mean required. See “Required Fields”.

▪ Forms suck. If you don’t believe me, try to find people who like filling them in. You may turn up an accountant who gets a rush when wrapping up a client’s tax return or perhaps a desk clerk who loves to tidy up office payroll. But for most of us, forms are just an annoyance. What we want to do is to vote, apply for a job, buy a book online, join a group, or get a rebate back from a recent purchase. Forms just stand in our way.

▪ It doesn’t help that most forms are designed from the “inside out” instead of the “outside in.”[1] Usually inside of an organization or a computer database, a specific set of information has come to define a valid record of a person, place, process, or thing. When it comes time to update or create one of these records, the organization or computer program simply says “here’s the information I need,” and that request shows up in front of people as a form.

▪ For example, a Web site’s database may be constructed in a way that defines a “member” as a unique combination of a first name, last name, email address, and password. So when a person tries to become a member of that site, up pops a form asking for that first name, last name, email address, and password. This is inside out. A set of database fields isn’t how most people think of becoming a member of an organization or service.

▪ Forms suck. We should design accordingly.

▪ On the Web, forms are the linchpins of ecommerce, social interactions, and most productivity-based applications.

▪ The form couldn’t come at a worse time. You want to buy the items you’ve found. The store wants to close the sale so it can make money. Standing between both your goals is a form and as we know—no one likes forms.

▪ However, when we’re online, each of these experiences comes to us as a form. Want to join a fun new social network? Just fill in this form (see Figure 1.5). Care to share this great video with a close friend? Just fill in a form. Want to respond to an interesting author’s blog post? You guessed it—a form. Just about everywhere people want to participate in social interactions online, forms get in the way. And since participation—number of members, number of activities completed, etc.—is how most social applications thrive, the organizations running these sites rely on forms for business success.

▪ In addition to ecommerce and social interactions, the Web is increasingly a place where people get things done. From online banking to Web-based word processing, Web applications designed for productivity are growing in number. For productivity-based Web applications, the online world doesn’t differ that much from the offline world. If filling in a survey in the physical world requires a form, the cyberspace version is not likely to be much different (see Figure 1.6).

▪ On ecommerce sites, people want to buy the things they need and businesses want to maximize sales. Standing in the way is the checkout form.

▪ On social applications, people want to join communities, chat with their friends, or share content. From a business perspective, these sites want to grow and increase engagement between people. In the way are registration and contact forms.

▪ Since Web forms broker crucial interactions like checkout and registration, it shouldn’t come as a surprise that they can have a big impact on business goals. Increased completion rates of 10–40 percent were not uncommon in many of the form redesign projects I’ve been part of.

▪ One of the biggest form redesign success stories I know of was outlined in a 2004 CHI (Computer Human Interaction) conference paper titled “A process for creating the business case for user experience projects”[2] by the eBay user experience and design team. Their registration redesign had such a positive impact on the bottom line of the company that it became a model for how design projects were evaluated and funded.

▪ Usability Testing: Observing how people interact with forms in a usability lab setting can provide valuable qualitative and quantitative information.

▪ Field Testing: Ethnographic observation of people interacting with forms in their home or office.

▪ Site Tracking: Forms can be instrumented to track any number of useful quantitative metrics.

▪ It’s hard to imagine a form that could be simpler: two fields, two buttons, and one link. Yet, it turns out this form was preventing customers from purchasing products from a major ecommerce site, to the tune of $300,000,000 a year. What was even worse: The designers of the site had no clue there was even a problem.

▪ The designers fixed the problem easily. They took away the Register button. In its place, they put a Continue button with a simple message: “You do not need to create an account to make purchases on our site. Simply click Continue to proceed to checkout. To make your future purchases even faster, you can create an account during checkout.”

▪ The results: The number of customers purchasing went up by 45 percent. The extra purchases resulted in an extra $1.5 million the first month. For the first year, the site saw an additional $300,000,000.

▪ It depends on the business goals, user needs, and context of your forms. It may also depend on the issues or opportunities your usability testing, live site metrics, or other data sources illuminate. In other words, there isn’t just one right answer.

▪ Given the impact that form design can have on crucial metrics such as completion and error rates, it’s only natural to ask: How can we design good forms? Unfortunately, the right answer is a bit unsatisfying: It depends.

▪ Most
are presented as design patterns that outline how they can be applied—for example, if your goals are “x,” then a good solution may be “y.” Or similarly, if your constraints are “a,” then a worthwhile approach is “b.”

▪ It’s also worth pointing out that many of the best practices in this book have been informed by live-to-site, eye-tracking, and usability testing across a wide range of Web companies and users. In fact, we did some eye-tracking and completion studies just for this book. That doesn’t mean we have all the right answers, but there’s some real data behind these tips!

▪ Lou Carbone introduced me to the terms “inside out” and “outside in” to describe how companies think about their services in a talk at MIX07: http://www.lukew.com/ff/entry.asp?532

▪ People need to parse every question you ask them, formulate their response to that question, and then enter their response into the space you have provided. The best way to speed up that process is not to ask the question at all. That means if you want to be vigilant about optimizing your forms, put every question you are asking people to the test. Do you really need to ask this question? Is it information that you can get automatically? Is there a better time or place to get an answer from people? Though this process appears tedious, you may be surprised when you discover what you can leave off your forms.

▪ Agreeing as to which questions should remain on a form may also be a discussion among several departments in your company or organization. The marketing team may have specific questions to understand customers better. The engineering team may require specific information to identify unique individuals. The legal team might mandate certain terms and conditions that have to be accepted by new customers. And the list goes on.

▪ Take a look at Caroline Jarrett’s “Keep, cut, postpone, and explain” framework (outlined in the sidebar) for a way to decide what makes the cut.

▪ But if you’ve decided on buying something that needs to be shipped, then it would be distinctly strange if the site did not ask you for a street address. And you’ll probably take care to enter a real address accurately.

▪ You encounter a stranger who asks you: “What’s your name?” “What’s your address?” “What’s your email address?” “What’s your birth date?” Before too long you, find yourself asking: “Who is this person?” “Why does he (or she) need all this information?” “Why am I telling him (or her) all this?” Quite quickly, you become uneasy and wish the stranger would tell you something about himself or herself instead of barraging you with questions. That barrage of questions is—of course—our friend, the form.

▪ In order to keep the conversation flowing smoothly, it’s a good idea to organize the questions you’re asking people into meaningful groups. Depending on their size and context, these groups could then be presented across multiple Web pages or as sections of a single Web page.

▪ Because your forms aren’t alone on the Web, another way to decide how to structure your conversations with customers is to conduct a Web conventions survey to see if any patterns emerge. A Web conventions survey is simply a comparison of design solutions across a number of similar Web sites. It usually helps to look at the top performing sites in a specific category (like ecommerce) to ensure that the sites being compared share common measures of success.

▪ A Web conventions survey may lead you to uncover common form organization structures that have emerged on the Web. For instance, mapping out what information is asked in ecommerce shopping cart forms (see Figure 2.4) reveals some interesting insights.

▪ As these examples illustrate, communicating meaningful distinctions between content groups doesn’t require a lot of visual difference. In fact, too much contrast between content groupings often creates excessive visual noise that gets in the way of people’s ability to scan a form.

▪ A subtle background color change or thin rule is often all you need to effectively group related content in a form.

▪ Take the time to evaluate every question you are adding to your forms. Be vigilant about removing everything that isn’t necessary.

▪ When a form contains a large number of questions that are only related by a few topics, multiple Web pages are probably a good way to organize the form.

▪ Consider asking optional questions only after a form is completed. Chances are you’ll get more answers than if these questions were part of the initial form.

▪ Part of providing a clear path to completion is telling people what form they are on and what they can accomplish by filling it out. As people are unlikely to read a detailed description of what each form they encounter does, this burden mostly falls on the form’s title. As a result, it’s crucial that form titles match the calls to action that people use to access them.

▪ Removing interface elements not directly related to completing a form helps keep people on task and removes paths to abandonment. The difference between checkout and shopping on Amazon.com shown in Figure 3.6 is stark. Even the site’s logo, which usually allows people to return to the Amazon home page, is deactivated to minimize ways off this crucial form.

▪ While Amazon.com may merchandise its categories and specials through its Web site, once you are in checkout, there are no frills.

▪ The listing of the total number of pages gives people a sense of the scope of this form: How long will it take to complete and what are the different sections/steps? The indicator of current position lets people know where they are relative to the entire form.

▪ The form status indicates whether the offer was submitted or not and when it was last saved. For long forms, providing the option to save or doing so automatically is a great way to keep people on a path to completion.

▪ This illustrates an all too common problem with progress indicators. They promise a series of well-defined, linear steps but rarely deliver.

▪ The Amazon.com checkout process in Figure 3.10 makes no explicit promises about the number of steps. Instead, the progress indicator outlines the types of information you’ll need to provide. Although some people could interpret these categories as separate pages, no specific expectations are set.

▪ Amazon does not promise any number of pages, just a high-level set of tasks.

▪ Closed captioning of multimedia helps when you are watching TV in a noisy environment such as a restaurant, gym, or airport.

▪ Do not use gratuitous animation, as it can distract people with ADD.

▪ Avoid anything that flashes more than three times per second. If a user has epilepsy, this can cause an attack.

▪ There must be a way to accomplish all functionality on the page with the keyboard only. So if you have designed some fancy drag-and-drop interface, you must also provide a way to perform the same task without the mouse. Don’t let this prevent you from doing the fancy stuff, though, since that’s so much fun.

▪ If there are timing aspects of the product, allow the user to turn them off, adjust them, or extend them. For example, if the product imposes a timeout for security or performance reasons, allow the end-user to extend it without losing any work.

▪ Provide a way for a keyboard-only user to skip repetitive content at the top of each page. No matter how elegant you’ve made your navigation scheme, if you have to use the Tab key to wade through it on every page, your users will really hate you.

▪ Every time I talk about Web form design, I always ask the audience how many of them use the Tab key on their keyboard to move between the input fields of a form they are filling out. Every time, more than half the audience raise their hands. Based on this information alone, it’s a good idea to consider how people will tab between inputs to complete your form.

▪ While the nuances of form development are beyond the scope of this book, it is useful for designers to know that forms that don’t provide an explicit order to their inputs using tabindex will simply be tabbed through in the order they appear in the HTML markup. What that means is to avoid any existential jumps between input fields, it’s a good idea to talk to a developer about specifying the order in which inputs should be accessed.

▪ For mission-critical forms like checkout or registration, remove distractions and any links or content that may lead to form abandonment.

▪ Every Web form has at least three basic elements: labels, input fields, and actions. Labels are responsible for asking questions. Input fields provide a way for people to answer those questions. Actions allow people to submit the answers they have provided.

▪ While astute readers might argue that a label-less form could exist, most people would be hard-pressed to figure out how to use it.

▪ One of the most common questions asked about form design is "Should I top-, right-, or left-align the labels for input fields?" (See Figure 4.1.) So let's answer it up front. Everyone together now... "it depends."

▪ Of the three label alignment options, top-aligned labels tend to reduce form completion times the most (see Figure 4.2). Because labels and input fields are in close proximity, processing them requires little effort. Getting through the entire form is also quick and easy because people generally only need to move in one direction: down. That makes for a very clear path to completion.

▪ Top-aligned labels also have plenty of horizontal real estate to expand or contract label text without negatively impacting overall page layout. This is especially useful for forms with long labels or those being localized across many cultures.

▪ Languages like French, German, or Dutch can run twice as long as English and as a result may quickly throw off a form layout.

▪ Top-aligned labels, however, do take up additional vertical real estate. So if you're working with a small amount of vertical screen space, you might want to think twice before using top-aligned labels. It's also important to use the right amount of vertical spacing in your top-aligned layouts. Too little or too much vertical space between inputs can impede people's movement through a form. In general, it's a good idea to use 50 to 75 percent of the height of a single input field between adjacent inputs.

▪ The results of live site testing across several different geographies have also supported top-aligned labels as the quickest way to get people through forms. These studies also had higher completion rates (over 10 percent higher) than the left-aligned versions of forms they were tested against. Because of these quick completion times and high completion rates, some designers always recommend using top-aligned labels. After all, the primary goal of any form is to get it completed with a minimum amount of pain, and the speed of top-aligned labels certainly helps.

▪ In cases where screen real estate is at a premium, combining labels and input fields into a single user interface element may be appropriate. Most commonly, this requires placing input labels inside their corresponding input fields (see Figure 4.12). Though it may be tempting to always halve the amount of screen space a form requires by using this method, there are a number of considerations worth calling out.

▪ Because labels within fields need to go away when people are entering their answer into an input field, the context for the answer is gone. So if you suddenly forget what question you're answering, tough luck—the label is nowhere to be found. As such, labels within inputs aren't a good solution for long or even medium-length forms. When you're done filling in the form, all the labels are gone!

▪ That makes it a bit hard to go back and check your answers. Single-question forms (like a search box), forms with just a couple inputs, or forms asking for very familiar data (like an address book) are much better candidates.

▪ I actually haven't seen any conclusive data that mixing label placements within an application doesn't cause problems; rather, in my experience, context often wins out over consistency. But be sure to tread carefully when using different form layouts in the same application.

▪ Changing label alignments within the same form, however, should really be avoided since it can cloud the clear path to completion people seek.

▪ When you are trying to reduce completion times or if you need flexible label lengths for localization, consider top-aligned labels.
When you have similar goals but vertical screen real estate constraints, consider right-aligned labels.
When your form requires people to scan labels to learn what's required or to answer a few specific questions out of many, consider left-aligned labels.
When you are under extreme space constraints for very short forms, labels within inputs may be a good solution. Just ensure that you have the right interactions and context in place.

▪ Make sure that you distinguish clearly between labels and data, especially when using labels within input fields.

▪ Once it’s clear what questions should be on a form and how they should be presented, we need to provide people with a way to answer them. For this, we turn to input fields: checkboxes, radio buttons, drop-down menus, and text boxes of varying size.

▪ Because selecting which input field is right for a specific interaction is a fundamental interaction design problem, it’s a bit outside the scope of this book.[1] However, a quick overview of when to use checkboxes, radio buttons, drop-down menus, and text boxes within Web forms is probably in order (see Figure 5.1 and Table 5.1).

▪ Because radio buttons are mutually exclusive, they should have a default value selected (more on this later). It’s also a good idea to make sure both the radio button and its label can be selected to activate a radio button selection. 　

▪ Drop-down menus 　 Allow people to select exactly one choice from two or more mutually exclusive options. When not in use, drop-down menus only display the currently selected choice. As a result, they are better candidates than radio buttons for long lists of mutually exclusive choices since they use a minimum of screen real estate. Despite this advantage, it’s generally a good idea to avoid really long lists in drop-down menus, especially when people are likely to be familiar with the options (like selecting the state they live in). 　

▪ List boxes can act as a set of radio buttons (allowing people to select exactly one choice from a set of mutually exclusive options) or as a set of checkboxes (allowing people to select any number of choices from a list of options). List boxes can be configured to show more options, like a drop-down menu, while still taking up less screen real estate than a list of radio buttons or checkboxes. Despite these advantages, the dual nature of list boxes (mutually exclusive single selection or multiple selection) tends to cause problems for many people. As a result, list boxes are rarely used in Web forms. 　

▪ One of the most challenging aspects of designing great forms is determining the most appropriate input controls. Because there is always more than one way to express a particular interaction or request a particular type of data, the form designer is invariably presented with a multiplicity of options that dramatically affect the user’s experience.

▪ In order to evaluate the range of design solutions, the design team needs to fully grasp the relative advantages and unique characteristics of each possibility. It is typical for the design team to struggle with trade-offs that pit click-efficiency against error prevention, learn-ability against efficiency, majority case against corner case, and flexibility against clarity.

▪ How these trade-offs are balanced ultimately depends on the judgment of the design team, optimizing for the specific audience and usage models involved.

▪ The specification of quantity and type is a common issue for sites that sell tickets, and it provides a useful example of this design challenge.

▪ Because of the infrequency of use, the overall audience should be considered recurring novices, meaning that the design should optimize for learn-ability, obviousness, and error prevention.

▪ One issue with this solution, since many users don’t realize they can use the Tab key to advance from one field to another, is how it leads users to skip back and forth between their mouse and keyboard. As a result, a significant number of visitors will have to bounce back and forth between their mouse and keyboard in order to complete the interaction.

▪ This basic analysis demonstrates that even seemingly simple data collection problems can be solved in multiple ways, with each solution presenting a unique combination of advantages and disadvantages. The job of the designer is to fully explore and analyze these possibilities in order to arrive at a solution that best satisfies the unique needs of the audience and application.

▪ For example, a handle on a door that looks like it should be pulled provides a valuable affordance. By virtue of its appearance, it lets people know how they can open the door: by pulling instead of pushing. Input fields can work in a similar way.

▪ Said another way, if this input field is long but my answer is short, have I misunderstood the question? Best not to make people think too much and instead use a consistent length for all the fields that don’t benefit from clear affordances.

▪ Many people will answer “It means this input is required so I have to provide an answer.” Many—but not all. As is common with all Web conventions (de facto standards that have organically emerged online), there are exceptions to this rule. In fact, some Web sites use an asterisk to indicate optional input fields (Figure 5.5) instead of required ones. In both cases, the more important question is when to indicate required or optional input fields at all (see Figure 5.6).

▪ When discussing content organization earlier, I made the point that any question that doesn’t need an answer should get dropped to make it easier for people to complete the form. So you might argue that there should never be a situation where we need to distinguish between required and optional inputs, right?

▪ Powerful design comes from the reuse of a small number of simple patterns. This is the essence of the power that a grid provides for visual designers. For example, grids with sweeping horizontal and vertical lines help designers place new elements on the page, while considering their relationship to the whole. Similarly, interaction designers have begun using consistent interaction patterns to simplify design decisions and provide global consistency.[1] So what patterns of structure underlie a form?

▪ The Core of a Form Is an Input

Inputs are atomic UI components designed to receive user feedback upon which all forms are built.

Here you see multiple inputs of different types, but with the same underlying structure.

▪ Inputs can take many shapes, but the basic pattern is the same: title, data, actions. This basic pattern repeats again and again across multiple types of inputs and at multiple levels within a form (for example, at an input, a section, a dialog, or a page).

▪ A Group is two or more inputs with some kind of relationship. Three of the most frequent types of Group inputs are Compound inputs, Related inputs, and Parent/Child inputs. These input types are important because they are each suited to different types of problems, and they handle errors and dependencies differently.

▪ For many of the questions we ask within Web forms, there’s a common way to respond. Mailing addresses, for example, have a widely known structure that can be leveraged to help people understand how to answer questions about shipping or billing locations. Other examples include first name and last name, date and time, or the parts of a phone number.

▪ Where possible, ensure that field lengths provide meaningful affordances that help people answer questions effectively.
Otherwise, utilize a consistent length that provides enough room for correct answers.

▪ Try to avoid optional input fields in forms.
If most of the inputs on a form are required, indicate the few that are optional.
If most of the inputs on a form are optional, indicate the few that are required.

▪ When indicating what form fields are either required or optional, text is the most clear. However, the * symbol is relatively well understood to mean required.
If you do use * to indicate required fields, don’t forget a legend that explains what it indicates.
Associate required or optional indicators with input labels to give people an easy way to see which questions need to be answered.

▪ If there’s a natural structure among input fields that provides a valuable clue on how to answer a question, look for ways to group these inputs visually to clearly communicate that structure.

▪ When there’s clearly more than one way to format an answer correctly, consider using a flexible input field.
Ensure that flexible inputs don’t make providing easy answers more difficult.

▪ A typical Web form usually enables several final actions (see Figure 6.1). Actions such as Submit, Save, or Continue are intended to enable completion, which is the primary goal of just about anyone who has started filling in a form. Because they enable the most important action on the form (completion), they can be referred to as primary actions.

▪ Secondary actions, on the other hand, tend to be less utilized and most often allow people to retract the data they've entered. Options like Cancel, Reset, or Go Back represent secondary actions that are counter to most people's primary goal of completing the form they began.

▪ Because secondary actions can have negative consequences (see Figure 6.2), especially when used unintentionally, I've often argued they should be absent from forms. Imagine filling in a long form online only to hit the Reset button and have all your data erased.

▪ That said, there are situations where secondary actions make sense (such as Save for Later, Preview, Export, etc.). Perhaps the most common example involves multiple page form wizards where people can move forward and backward through Web pages. Though it may be tempting to treat Previous and Next as equal actions in these circumstances, keeping people moving forward with a primary Continue action and a secondary Back action is likely to be more productive.

▪ One way to ensure that secondary actions do not result in catastrophic losses of data is to provide an automatic Undo behavior. Rather than asking people to confirm that they'd like to reset a form when they click Reset, simply replace the Reset button with an Undo button after they select it. Of course, this requires your form to store people's data as they enter it, but that's a small price to pay for preventing catastrophic data loss.

▪ Let's assume that you've answered all the questions on a form correctly and selected the primary action to signify you're done. Then what? If nothing changes, perhaps the site didn't register your click. Is your information being processed? When in doubt, most people will try again. Depending on how a form is developed, this may lead to a duplicate submission. Now you've done what you were trying to accomplish twice!

▪ One potential solution is to include a warning that asks people not to click on a primary action twice, as seen in Figure 6.10. But this unfairly places the burden on the person who is filling in the form. It's an "inside out" solution.

▪ A better answer is to replace the active primary action with an animation or text message that lets people know their submission was accepted and is in progress (see Figure 6.11).

▪ Depending on the legal requirements of a site, the terms of service can be governed by a primary call to action that explicitly includes a legal agreement, for example, a button labeled "I agree and move forward" or one that infers it through text preceding the primary action "by clicking register below, I agree."

▪ The advantage of both these options is that they require one less explicit question for people to answer. However, the second option has the added advantage of not complicating the primary call to action. Consider the difference between "Buy Now" and "Agree & Buy Now." One is clearly more directly aligned with people's goals of buying a product than the other.

▪ Avoid secondary actions on forms whenever possible. Provide people with a single path to completion.
If secondary actions are required, ensure that there is a clear visual distinction between the primary and secondary actions.

▪ Consider opportunities to streamline legal requirements by combining terms of service agreements with primary actions.

▪ Although the way we phrase labels and display input fields can provide useful clues on how to provide answers, these elements alone are sometimes not enough. In these cases, it's common practice to resort to "telling" people how they should answer a question by including help text next to a form's labels or input fields.

▪ Help text is basically just a set of messages that help people complete forms successfully. This means that help messages are structurally similar to the error and success messages we'll look at in Chapter 8 and, as a result, share many best practices.

▪ Tempting as it may be simply to spell out how people should fill in an input field, help text isn't the holy grail of Web form completion. For starters, if excessive instructions are required to explain how to complete your form, then chances are the questions you are asking are either phrased poorly, too complex, or just plain unnecessary. Excessive help text may be an indicator that it's time to go back to the drawing board and make sure the questions you are asking people are the right ones (see Figure 7.1).

▪ Help text can also be problematic because people tend not to read instructions presented onscreen. Relying on a set of instructions to explain your form will lead to trouble when those instructions are bypassed by most people (see Figure 7.2). In fact, eye-tracking research shows that many people jump directly to the first input field when presented with a form. It seems to be a natural tendency to want to start filling things in. We just want to get this form done and move on!

▪ Yet there are cases when instructional text is appropriate. In particular, concise bits of help text are most useful in the following circumstances:

When forms ask for unfamiliar data: What's a PAC code?
When people question why they are being asked for specific data: Why do you need to know my date of birth?
When people may be concerned about the security or privacy of their data: Is my credit card number safe here?
When there are recommended ways of providing data: Separate your tags with commas, please.
When certain data fields are optional or required when the bulk of the form is not.

▪ Automatic inline help systems reveal themselves when and where the information they contain is most applicable. For example, when a person clicks or tabs to an input field, the relevant help text appears beside or below the input. The Wufoo example in Figure 7.4 shows this behavior in action.

▪ On Wufoo, help text is automatically shown as people engage with input fields.

▪ The automatic inline help system used by Form Assembly in Figure 7.5 does not require a dedicated portion of the screen for displaying help text. Instead, it displays help text directly below the input field to which it applies. The advantage here is that help text is right next to the question being answered, so there's little chance of disassociation. The disadvantage, however, is that additional input fields may be covered up by help text dialogs, as seen in Figure 7.5.

▪ One potential drawback of this type of automated help system is that people are unlikely to know any help text is available until they begin to fill out the form. As a result, people who feel they may need help to complete the form might get discouraged and not even try.

▪ A possible way to address this shortcoming is with help text within an input field. This method is essentially the opposite of automatic inline exposure because the help text is visible before someone accesses an input field but no longer visible after. Because help text is visible right away, people know help is available when they first encounter the form.

▪ Be aware that the help text is gone as soon as people start providing an answer so they immediately lose any assistance the help text provided.
Be wary of using this method for complex inputs that benefit from always visible help.

▪ Make sure that people can tell the difference between answers in input fields and help text within input fields. In the LinkedIn example in Figure 7.7, help text is gray and includes the prefix "eg:"

▪ Another way to let people know help is available up front is with a user-activated inline help system. User-activated inline help lets people explicitly access help text when they need it. This method usually makes consistent use of an icon, button, image, or text link to let people know help is available. A person can either click or point to these triggers to reveal relevant help text as needed.

▪ Adding help text to a form in this manner, however, can cause content below the inserted help text to jump further down the Web page. Too much shifting of content can leave people disoriented as the form they are filling out continues to move up and down.

▪ A question mark is the most common symbol for an icon that displays help content, but there are other symbols you could use (see Figure 7.11). Regardless of whether you use an icon, button, text, or a combination thereof to indicate points at which people can access help text, it's generally a good idea to include some kind of visual cue that indicates such elements are actionable—for example, a 3D bevel or underlining beneath text. It's also a good idea to place these access points next to labels rather than input fields for reasons mentioned earlier.

▪ Though many symbols have been used to represent help, the question mark icon continues to be the most recognizable.

▪ Like user-activated inline help, user-activated section help is a better fit for forms used more than once, particularly ones that ask potentially complex questions. As such, a better candidate for this type of system is eBay's Sell Your Item form (Figure 7.14). This form makes use of a Help panel that people can display or hide by clicking a global Help icon at the top of the form. The content in the Help panel updates with contextually relevant help text when a person clicks one of the Help icons next to each input field.

▪ Don't use help text to compensate for the shortcomings of your forms. Striving to minimize the amount of help text on your forms will push you toward better design solutions.

▪ Help text is best for explaining unfamiliar data requests, such as why certain questions are being asked, security and privacy concerns, recommended ways of providing answers, and indicating optional answers.

▪ Concise help text visible and adjacent to the question being asked provides the most clarity for people.

▪ Help text within input fields should only be used to provide recommended ways of answering questions.

▪ If your form is asking questions people have answers for but may be unsure how or why they should answer, consider using an automatic inline help system.

▪ If your form is asking unfamiliar or complex questions, and is likely to be reused by the same people multiple times, consider using a user-activated help system.

▪ Unless you have a lot of help text or content (graphics, charts), for each question being asked, use an inline system that avoids page-jumping and rollover problems.

▪ Be as specific as you can with help text. If help text applies to a group of related input fields instead of individual inputs, consider devoting a portion of the page to displaying help to communicate a clear association between the group of fields and the help text.

▪ Triggers for user-activated help text, such as icons, links, or buttons, should be placed next to labels and not input fields.

▪ While help text can be used to tell people how to successfully complete a form, it isn’t the most important thing we have to tell them. That honor falls to error and success messages.

▪ Error messages let people know when they cannot continue completing a form and how they can remedy the situation. Success messages tell people what they wanted to hear from the moment they starting filling in a form—they’re done!

▪ Like help text, errors and success are messages for people. As a result, a lot of the best practices and dynamic systems we looked at in Chapter 7 for help text also apply to the error and success messages discussed here.

▪ Step one for dealing with errors is letting people know they happened. Though this may seem like a trivial point, all too often error messages don’t get the attention they deserve. When present, an error message is arguably the most important element on the page. It prevents people from achieving their primary goal of completing a form. As a result, the visual presentation of an error needs to match its importance.

▪ Perhaps more concerning than the visual presentation of this error message is the lack of a clear way to resolve the error itself. The message tells us to “Please verify the number and try again.” But where is the number? How do I try again? Surfacing the error message next to the responsible elements would have made a solution much more understandable and actionable.

▪ Of course, you aren’t limited to this exact visual presentation. Anything that has a very strong contrast with the rest of the page and looks like an error (typically red text and a warning icon) could be appropriate. Differences in size, shape, position, texture, or color can be used alone or together to create additional emphasis. The key requirement is that the error be immediately noticeable because it is blocking someone’s progress.

▪ The inclusion of instructions next to the input field responsible for the error provides people with a remedy where they need it most: where the error can be fixed. Consider an alternative where the fact that an error occurred is shown in a modal dialog window (Figure 8.3) that has to be dismissed before someone can proceed. Once that dialog is gone, so is the indication of which input needs to be corrected and how.

▪ However, when you do decide on a visual treatment for the inputs responsible for an error, make sure that the style you select matches the style of any primary error messages on the form. Clear visual similarities between errors and error messages help people connect the dots.

▪ Error messages aren’t big-time fun for designers or customers. But dealing with them—and other forms of messaging within a form—is a critical part of the user experience, and handling them well or badly may make a huge difference in the overall success of a form.

▪ Error messages are the most common, the most overused, and the most likely to annoy your customers. Avoid them where possible by using input types with no error states (such as drop-down menus), inputs that have undo options, and inputs with good default values. Where you can’t avoid error messages, use them sparingly.

▪ The customer has entered something that the system can’t accept, so the customer can’t continue (for example, a mismatching username and password). This kind of message should clearly and succinctly tell the customer what happened, how to fix it, and then move on.
Something very, very bad has happened to the system, so the customer can’t continue (e.g., an essential server just got smote by lightning). This kind of message should be very apologetic and should give the customer some alternate way of contacting you.

▪ There are no other reasons to show an error message. If you show something that looks like an error message in order to market something to the customer, you are a bad person.

▪ Success messages are a nice way of thanking your customer for putting up with your tedious form and its error messages. They should be short and sweet, the visual equivalent of hearing “Have a nice day!” on your way out of the grocery store.

▪ Now, what happens when there is more than one error on a form? Or when no particular input fields are responsible for the problem, such as when a server goes down or a payment cannot be authorized? In most cases, the same structure still works well.

▪ Instead, the more common case is when one or two input fields are preventing someone from completing a form. In these instances, it is quite useful to be able to locate the responsible input field(s) quickly and easily—especially on long forms, as the example from QLC in Figure 8.6 indicates. Notice that the visual similarity (color, border, font) between the error message and responsible input fields creates a clear connection between the two.

▪ If you do choose only to utilize a prominent message and not highlight the responsible input fields, be certain that you clearly distinguish the error message from the rest of the form. This sign-up form from Boingo in Figure 8.8 does not use enough contrast, opting instead to use the same font face and color as the form title and input labels. This makes the fact that an error happened much less obvious.

▪ No Dead Ends

Success messages can also include useful follow-up actions related to the task someone just completed (see Figure 8.12). Booked a flight online? Perhaps you want to forward your itinerary to family? Making these actions part of a success message on the page gives people clear and actionable next steps. Never leave ‘em hanging!

▪ After you have connected with someone on the professional networking site LinkedIn, the success page provides several relevant next steps.

▪ Clearly communicate when an error is blocking someone from completing a form. Error messages are arguably the most important element on a form when present. Make sure they appear that way!

▪ Display error messages in context so they can be resolved quickly.

▪ Provide actionable remedies that enable people to resolve errors easily.

▪ Top-level error messages should indicate an error has occurred and how it can be resolved. If multiple errors exist, they should be listed in the top-level message.

▪ Reserve red text and warning icons for error messages.

▪ Clearly communicate when a form has been completed successfully and what happened as a result using success messages.

▪ Avoid success message page dead ends.

▪ Inline validation can provide several types of feedback: confirmation that an appropriate answer was given, suggestions for valid answers, and real-time updates designed to help people stay within necessary limits. These bits of feedback usually happen when people begin, continue, or stop entering answers within input fields.

▪ Confirming appropriate answers is most useful when there is a high likelihood that people won't get the answer "right." A common example is the selection of a unique username. Chances are good that the first username to pop into people's heads is one that someone else already claimed. Providing that specific answer would yield an error because the Web site understands that it is not "valid." Someone else already has that username. Of course, it's impossible for people to know what usernames are available to them when they are filling in a registration form so they continue to guess and guess again until they stumble upon something obscure enough not to be taken.

▪ This situation becomes worse when the form does nothing to help. In the Boingo example in Figure 9.1, not only is there no feedback that helps people pick a valid answer, but the feedback that tells them an error occurred is hard to even notice as it uses the same font face and color as the form's labels (see Chapter 8 for more on error messages).

▪ Another question commonly fraught with errors is the password. I won't dwell on the fact that asking people to generate complex combinations of uppercase and lowercase letters, numerals, and symbols is another example of how our "inside out" systems create confusion for people. Instead, I'll provide a way we can help people overcome those obstacles through the use of inline validation.

▪ When we talked about usernames, a valid answer was pretty black and white. It's either a unique username or it's not. Passwords, and other questions like them, can have varying degrees of "right." A password that meets the minimum requirements for security—say one uppercase letter and one numeral—is a valid answer. However, it is not as secure as a password with one uppercase letter, two symbols, and three numerals. The latter answer is more "right." So how can you steer people toward the more secure—and therefore right answers?

▪ Given the benefits of confirming appropriate answers in real time, you might be tempted to consider using inline validation for all the questions you pose in your forms. After all, why not let people know every question they've answered is right as they answer it? By the time they complete the form, there's no chance of an error!

▪ Does validating an email address mean that it is, in fact, an email address (based on its formatting), or that it is my email address (and this site knows that somehow), or that this email address is already known to the site (especially important if I am registering or updating a customer record)? Though not everyone will think this way, why make people think at all? Use inline validation to help people with answers they aren't guaranteed to know. I know my name, so there's no need to validate it for me!

▪ If you do choose to provide inline validation for many of the questions you ask, timing is everything. The Mint sign-up form in Figure 9.5 brings up an error state immediately when someone begins providing an answer. In the example illustrated, I've only managed to enter the first letter of my email address, and I'm already faced with an error. A much better approach is to only provide feedback when it's clear someone is done providing an answer. Figure 9.6 illustrates this sequence when someone completes his or her answer on the Yahoo! registration form.

▪ Mint's registration form interrupts people when they are answering questions with immediate error messages.

▪ Yahoo!'s registration form only validates an answer once someone has indicated he or she is done by moving to the next
input field.

▪ Compared to inline confirmation, this is a different way to ensure that people provide valid answers. Instead of real-time answers that say "yes, this is valid" or "no, it is not," inline suggestions state "here are some valid answers to pick from." To further illustrate this difference, let's look again at selecting a username.

▪ In contrast to Newsvine's approach to confirming the username people select inline (Figure 9.2), Yahoo! provides a list of valid username suggestions based on the full name that people provided earlier in the form (Figure 9.8). I entered my name as "Luke Wroblewski" at the start of the form and received several relevant, valid answers to choose from.

▪ If people enter a valid phone number in a different format, we can simply change their answer to the correct one. It's crucial that this change does not happen while people are actually entering their answers. Instead it should happen after they are done.

▪ For questions without clearly defined answers but clearly defined limits, inline validation also comes in handy. The Yahoo! Local form in Figure 9.9 allows people to send an email to friends or family. To avoid spam or excessively long content, Yahoo! limits the message input to 1,000 characters. As people enter their answers, the counter below the input field provides real-time updates on how much more they can type.

▪ Consider using inline validation to confirm or suggest valid answers and to help people stay within limits.

▪ Inline confirmation works best for questions with potentially high error rates or specific formatting requirements.

▪ Inline suggestions work best when there is a large set of valid answers people can pick from.

▪ Inline quality indicators can guide people to better answers to complex questions.

▪ When validating people's answers inline, do so after they have finished providing an answer, not during the process.

▪ If you need to change people's responses into a specific format, make sure you do so after they have finished providing an answer, not during the process.

▪ Moving several optional questions out of the registration form probably required some negotiation with the people vested in their answers—marketing and trust and safety teams at the company. The impact, however, was tremendous because a lot more people registered successfully and began to use eBay. And perhaps ironically, significantly more people answered the optional questions when they were asked after they registered!

▪ It also removes the redundancy inherent in asking people for a zip code and city/state. The United States Postal Services has deliberately not removed these fields from mailing labels precisely because people often mistype one or the other.

▪ In The Paradox of Choice,[1] author Barry Schwartz discusses the impact of having too many choices in our lives and suggests some strategies for coping with the excessive options we encounter just about everywhere. In particular, he outlines the power of smart defaults—selections put in place that serve the interests of most people—as a way to help people make good choices.

▪ Schwartz references organ donor programs as an example. In the United States, 90 percent of Americans approve of organ donation but only 25 percent are organ donors. In several European countries, over 80 percent of people are donors. The difference comes down to a default choice. In the U.S., the organ donor option is defaulted off. Elsewhere, it is defaulted on.

▪ Because these choices result in the least amount of overhead for most sellers on eBay, they are smart defaults that simplify the decision-making process. Not sure what shipping service to use? Standard delivery is the most common. Don’t know if you need to charge sales tax? Looks like you don’t have to. Smart defaults provide answers to questions for you.

▪ Because of the power of smart defaults, it is tempting to opt people into situations advantageous for business but potentially less so for customers. For example, it’s common to encounter forms that opt customers into mailing lists or extra features by default (see Figure 10.6).

▪ If possible, try to ensure that the defaults you include in forms align with your customers’ interests. When people are defaulted into services or options they don’t like, it casts doubt and suspicion on your service. I’ve seen several instances where a default choice made potential customers wary enough to pack up their bags and not complete a form.

▪ To address this behavior, a lot of radio button inputs don’t include an initial selection (see Figure 10.7). Either the form designers aren’t sure what the right default should be, or they want people to explicitly make a selection.

▪ Smart defaults don’t work very well when there isn’t a clear option that applies to most people. The Vox registration form in Figure 10.9 defaults the birth date to Jan 1, 1975—probably not the birthday of everyone who tries to register for the site. A better solution simply would be to ask people to explicitly select the month, day, and year they were born. And while you’re at it, let them know why you are asking. eBay in Figure 10.9 tells you that it isn’t being nosey; you just can’t sell on eBay unless you are 18.

▪ Smart defaults can also come from people’s implicit behaviors. For instance, if you know someone is accessing your form from the United States, you might consider defaulting the “Country” input field to “United States.” If you know that 90 percent of your customers live in the U.S., you might do the same.

▪ Smart defaults can also be personally relevant to individuals. For instance, if I always use Federal Express as my Shipping Service when I sell items on eBay, the Shipping Service selection we saw earlier could be defaulted to my personal choice. Keeping selections active for returning customers is often referred to as making them “sticky,” which basically means sticking with the choice a customer made before.

▪ Look for patterns in how people answer questions that allow you to infer answers accurately.

▪ Smart defaults can help people answer questions by putting default selections in place that serve the interests of most people.

▪ Personally relevant default selections enable return customers to complete forms faster because their answers are “sticky.”

▪ Inline Additions

Inline additions provide additional input fields to the people that need them without getting in the way of people that don’t. These input fields are often thought of as advanced or additional options, but they don’t have to be any more complicated than a normal set of choices presented in the form by default.

▪ Page jumping pushes existing content down the form and can sometimes disrupt people’s awareness of their position on the page. As a result, it’s always a good idea to try and minimize the amount of page jumping within a form. When using inline additions that expose additional input fields below an action, try to avoid very large sets of input fields that will push the content on a Web page down substantially.

▪ Another way to display additional options is to use an overlay: a set of additional input fields that sits on top of a form like a dialog window on your computer’s desktop. Perhaps the most common example of these is the calendar widget that allows people to select specific dates as answers to questions posed by a form.

▪ However, only Kayak provides an indicator that this will happen by including a small calendar icon within the input field (Figure 11.4). This visual cue helps to set expectations that a calendar will be made available. And while both the Orbitz and Kayak input fields still allow people to enter a date without using the calendar overlay, the Kayak overlay does not cover the input field and thereby gets in people’s way when they do so.

▪ The advanced notification preferences on the Renkoo profile form are displayed in a modal dialog window.

When additional inputs are activated, a modal dialog window appears that allows people to specify detailed notification settings. It’s important that the selections made within an overlay are visible on the original form once the overlay is closed. In the case of the calendar widget, we placed a date into the appropriate input field. In the Renkoo example in Figure 11.7, the notification settings people select are listed on the form when the modal overlay is closed.

▪ One of the drawbacks of this solution, however, is that all 30 options are never shown at once so people don’t have the ability to see all possible choices without clicking through each of the top-level categories—perhaps an efficiency versus engagement trade-off. Another efficiency stumbling point is that the number of clicks required to pick a category is higher than the single click you’d need to pick from a set of radio buttons.

▪ Occasionally, additional inputs can be utilized to expose a set of options in a more engaging way than a typical set of input fields might. For instance, if you need your customers to select a category for their event from a list of a dozen or more potential options, a common solution would be to place the options into a single drop-down menu or perhaps several columns of radio buttons. In fact, the popular video site YouTube has used both solutions (Figure 11.9) when asking people to select a category for their videos.

▪ Additional inputs can be used to provide added or advanced options to the people who need them without getting in the way of people who don’t.

▪ You should map additional inputs to prioritized customer needs. Primary use cases should be up front and visible; secondary use cases may be a click away.

▪ As crucial components of ecommerce, online communication, and Web applications, Web forms aren’t going anywhere just yet. Though as I hope you’ve seen in this book, there’s lots of room for improvement in how we design and manage forms online. As we move forward, there are even more ways we could do better still.

▪ To truly master form construction on the Web, you’ll need to get past all of that. You’ll need to embrace the eccentricities of form controls, and maybe even be a little Zen-like about the strange characteristics they exhibit. After all, it’s not their fault—they’re just rendered that way.

▪ Just be sure to keep in mind that form controls render quite differently across different browsers and operating systems, so don’t spend too much time trying to achieve pixel-perfection.

▪ I was a founding board member of the Interaction Design Association (IxDA), and I spoke at numerous conferences and companies around the world about Web design and strategy. 
