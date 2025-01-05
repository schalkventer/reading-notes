A Philosophy of Software Design (2018)
John Ousterhout

---


▪ The most fundamental problem in computer science is problem decomposition: how to take a complex problem and divide it up into pieces that can be solved independently.

▪ Problem decomposition is the central design task that programmers face every day, and yet, other than the work described here, I have not been able to identify a single class in any university where problem decomposition is a central topic. We teach for loops and object-oriented programming, but not software design.

▪ In addition, there is a huge variation in quality and productivity among programmers, but we have made little attempt to understand what makes the best programmers so much better or to teach those skills in our classes. I have talked with several people I consider to be great programmers, but most of them had difficulty articulating specific techniques that give them their advantage.

▪ For many years these issues have perplexed and frustrated me. I have wondered whether software design can be taught, and I have hypothesized that design skill is 

page_viii 
what separates great programmers from average ones.

▪ The principles are fairly high level and border on the philosophical (“Define errors out of existence”), so it is hard for students to understand the ideas in the abstract.

▪ Students learn best by writing code, making mistakes, and then seeing how their mistakes and the subsequent fixes relate to the principles.

▪ I recommend that you take the suggestions in this book with a grain of salt. The overall goal is to reduce complexity; this is more important than any particular principle or idea you read here. If you try an idea from this book and find that it doesn’t actually reduce complexity, then don’t feel obligated to keep using it (but, do let me know about your experience; I’d like to get feedback on what works and what doesn’t).

▪ Writing computer software is one of the purest creative activities in the history of the human race. Programmers aren’t bound by practical limitations such as the laws of physics; we can create exciting virtual worlds with behaviors that could never exist in the real world.

▪ All programming requires is a creative mind and the ability to organize your thoughts. If you can visualize a system, you can probably implement it in a computer program.

▪ This means that the greatest limitation in writing software is our ability to understand the systems we are creating. As a program evolves and acquires more features, it becomes complicated, with subtle dependencies between its components. Over time, complexity accumulates, and it becomes harder and harder for programmers to keep all of the relevant factors in their minds as they modify the system. This slows down development and leads to bugs, which slow development even more and add to its cost. Complexity increases inevitably over the life of any program. The larger the program, and the more people that work on it, the more difficult it is to manage complexity.

▪ The first approach is to eliminate complexity by making code simpler and more obvious. For example, complexity can be reduced by eliminating special cases or using identifiers in a consistent fashion.

▪ The second approach to complexity is to encapsulate it, so that programmers can work on a system without being exposed to all of its complexity at once. This approach is called modular design. In modular design, a software system is divided up into modules, such as classes in an object-oriented language. The modules are designed to be relatively independent of each other, so that a programmer can work on one module without having to understand the details of other modules.

▪ Because software is so malleable, software design is a continuous process that spans the entire lifecycle of a software system; this makes software design different from the design of physical systems such as buildings, ships, or bridges. However, software design has not always been viewed this way. For much of the history of programming, design was concentrated at the beginning of a project, as it is in other engineering disciplines.

▪ Unfortunately, the waterfall model rarely works well for software. Software systems are intrinsically more complex than physical systems; it isn’t possible to visualize the design for a large software system well enough to understand all of its implications before building anything. As a result, the initial design will have many problems. The problems do not become apparent until implementation is well underway.

▪ The incremental approach works for software because software is malleable enough to allow significant design changes partway through implementation. In contrast, major design changes are much more challenging for physical systems: for example, it would not be practical to change the number of towers supporting a bridge in the middle of construction.

▪ Incremental development means that software design is never done. Design happens continuously over the life of a system: developers should always be thinking about design issues. Incremental development also means continuous redesign. The initial design for a system or component is almost never the best one; experience inevitably shows better ways to do things

▪ The first is to describe the nature of software complexity: what does “complexity” mean, why does it matter, and how can you recognize when a program has unnecessary complexity?

▪ Unfortunately, there isn’t a simple recipe that will guarantee great software designs. Instead, I will present a collection of higher-level concepts that border on the philosophical, such as “classes should be deep” or “define errors out of existence.” These concepts may not immediately identify the best design, but you can use them to compare design alternatives and guide your exploration of the design space.

▪ It has been a challenge to find examples that are small enough to include in the book, yet large enough to illustrate 

Page 4 
problems with real systems (if you encounter good examples, please send them to me). Thus, this book may not be sufficient by itself for you to learn how to apply the principles.

▪ When applying the ideas from this book, it’s important to use moderation and discretion. Every rule has its exceptions, and every principle has its limits.

▪ If you take any design idea to its extreme, you will probably end up in a bad place. Beautiful designs reflect a balance between competing ideas and approaches.

▪ It is easier to tell whether a design is simple than it is to create a simple design, but once you can recognize that a system is too complicated, you can use that ability to guide your design philosophy towards simplicity.

▪ Over time, you will notice that certain techniques tend to result in simpler designs, while others correlate with complexity

▪ For the purposes of this book, I define “complexity” in a practical way. Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system.

▪ Complexity can take many forms. For example, it might be hard to understand how a piece of code works; it might take a lot of effort 

Page 6 
to implement a small improvement, or it might not be clear which parts of the system must be modified to make the improvement; it might be difficult to fix one bug without introducing another. If a software system is hard to understand and modify, then it is complicated; if it is easy to understand and modify, then it is simple.

▪ You can also think of complexity in terms of cost and benefit. In a complex system, it takes a lot of work to implement even small improvements. In a simple system, larger improvements can be implemented with less effort.

▪ People often use the word “complex” to describe large systems with sophisticated features, but if such a system is easy to work on, then, for the purposes of this book, it is not complex. Of course, almost all large and sophisticated software systems are in fact hard to work on, so they also meet my definition of complexity, but this need not necessarily be the case. It is also possible for a small and unsophisticated system to be quite complex.

▪ Complexity is determined by the activities that are most common. If a system has a few parts that are very complicated, but those parts almost never need to be touched, then they don’t have much impact on the overall complexity of the system.

▪ Complexity is more apparent to readers than writers. If you write a piece of code and it seems simple to you, but other people think it is complex, then it is complex. When you find yourself in situations like this, it’s worth probing the other developers to find out why the code seems complex to them; there are probably some interesting lessons to learn from the disconnect between your opinion and theirs. Your job as a developer is not just to create code that you can work with easily, but to create code that others can also work with easily.

▪ Change amplification: The first symptom of complexity is that a seemingly simple change requires code modifications in many different places.

▪ One of the goals of good design is to reduce the amount of code that is affected by each design decision, so design changes don’t require very many code modifications.

▪ Cognitive load: The second symptom of complexity is cognitive load, which refers to how much a developer needs to know in order to complete a task. A higher cognitive load means that developers have to spend more time learning the required information, and there is a greater risk of bugs because they have missed something important.

▪ For example, suppose a function in C allocates memory, returns a pointer to that memory, and assumes that the caller will free the memory. This adds to the cognitive load of developers using the function; if a developer fails to free the memory, there will be a memory leak. If the system can be restructured so that the caller doesn’t need to worry about freeing the memory (the same module that allocates the memory also takes responsibility for freeing it), it will reduce the cognitive load.

▪ System designers sometimes assume that complexity can be measured by lines of code. They assume that if one implementation is shorter than another, then it must be simpler; if it only takes a few lines of code to make a change, then the change must be easy

▪ I have seen frameworks that allowed applications to be written with only a few lines of code, but it was extremely difficult to figure out what those lines were.

▪ Sometimes an approach 

Page 8 
that requires more lines of code is actually simpler, because it reduces cognitive load.

▪ Unknown unknowns: The third symptom of complexity is that it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully

▪ Of the three manifestations of complexity, unknown unknowns are the worst. An 

Page 9 
unknown unknown means that there is something you need to know, but there is no way for you to find out what it is, or even whether there is an issue. You won’t find out about it until bugs appear after you make a change. Change amplification is annoying, but as long as it is clear which code needs to be modified, the system will work once the change has been completed. Similarly, a high cognitive load will increase the cost of a change, but if it is clear which information to read, the change is still likely to be correct. With unknown unknowns, it is unclear what to do or whether a proposed solution will even work. The only way to be certain is to read every line of code in the system, which is impossible for systems of any size.

▪ One of the most important goals of good design is for a system to be obvious.

▪ An obvious system is one where a developer can make a quick guess about what to do, without thinking very hard, and yet be confident that the guess is correct.

▪ Complexity is caused by two things: dependencies and obscurity.

▪ For the purposes of this book, a dependency exists when a given piece of code cannot be understood and modified in isolation; the code relates in some way to other code, and the other code must be considered and/or modified if the given code is changed.

▪ The signature of a method creates a dependency between the implementation of that method and the code that invokes it: if a new parameter is added to a method, all of the invocations of that method must be modified to specify 

Page 10 
that parameter.

▪ Dependencies are a fundamental part of software and can’t be completely eliminated. In fact, we intentionally introduce dependencies as part of the software design process.

▪ However, one of the goals of software design is to reduce the number of dependencies and to make the dependencies that remain as simple and obvious as possible.

▪ Consider the Web site example. In the old Web site with the background specified separately on each page, all of the Web pages were dependent on each other. The new Web site fixed this problem by specifying the background color in a central place and providing an API that individual pages use to retrieve that color when they are rendered. The new Web site eliminated the dependency between the pages, but it created a new dependency around the API for retrieving the background color. Fortunately, the new dependency is more obvious: it is clear that each individual Web page depends on the bannerBg color, and a developer can easily find all the places where the variable is used by searching for its name.

▪ The second cause of complexity is obscurity. Obscurity occurs when important information is not obvious. A simple example is a variable name that is so generic that it doesn’t carry much useful information (e.g., time). Or, the documentation for a variable might not specify its units, so the only way to find out is to scan code for places where the variable is used.

▪ Obscurity is often associated with dependencies, where it is not obvious that a dependency exists.

▪ If a system has a clean and obvious design, then it will need less documentation. The need for extensive documentation is often a red flag that the design isn’t quite right.

▪ Together, dependencies and obscurity account for the three manifestations of complexity 

Page 11 
described in Section 2.2. Dependencies lead to change amplification and a high cognitive load. Obscurity creates unknown unknowns, and also contributes to cognitive load. If we can find design techniques that minimize dependencies and obscurity, then we can reduce the complexity of software.

▪ Complexity isn’t caused by a single catastrophic error; it accumulates in lots of small chunks. A single dependency or obscurity, by itself, is unlikely to affect significantly the maintainability of a software system. Complexity comes about because hundreds or thousands of small dependencies and obscurities build up over time. Eventually, there are so many of these small issues that every possible change to the system is affected by several of them.

▪ The incremental nature of complexity makes it hard to control. It’s easy to convince yourself that a little bit of complexity introduced by your current change is no big deal. However, if every developer takes this approach for every change, complexity accumulates rapidly. Once complexity has accumulated, it is hard to eliminate, since fixing a single dependency or obscurity will not, by itself, make a big difference. In order to slow the growth of complexity, you must adopt a “zero tolerance” philosophy, as discussed in Chapter 3.

▪ In addition, developers spend more time acquiring enough information to make the change safely and, in the worst case, they can’t even find all the information they need. The bottom line is that complexity makes it difficult and risky to modify an existing code base.

▪ One of the most important elements of good software design is the mindset you adopt when you approach a programming task.

▪ Many organizations encourage a tactical mindset, focused on getting features working as quickly as possible. However, if you want a good design, you must take a more strategic approach where you invest time to produce clean designs and fix problems. This chapter discusses why the strategic approach produces better designs and is actually cheaper than the tactical approach over the long run.

▪ Most programmers approach software development with a mindset I call tactical programming. In the tactical approach, your main focus is to get something working, such as a new feature or a bug fix. At first glance this seems totally reasonable: what could be more important than writing code that works? However, tactical programming makes it nearly impossible to produce a good system design.

▪ This is how systems become complicated. As discussed in the previous chapter, 

Page 14 
complexity is incremental. It’s not one particular thing that makes a system complicated, but the accumulation of dozens or hundreds of small things.

▪ Pretty soon the code is a mess, but by this point things are so bad that it would take months of work to clean it up. There’s no way your schedule can tolerate that kind of delay, and fixing one or two of the problems doesn’t seem like it will make much difference, so you just keep programming tactically.

▪ Almost every software development organization has at least one developer who takes tactical programming to the extreme: a tactical tornado. The tactical tornado is a prolific programmer who pumps out code far faster than others but works in a totally tactical fashion. When it comes to implementing a quick feature, nobody gets it done faster than the tactical tornado. In some organizations, management treats tactical tornadoes as heroes. However, tactical tornadoes leave behind a wake of destruction. They are rarely considered heroes by the engineers who must work with their code in the future. Typically, other engineers must clean up the messes left behind by the tactical tornado, which makes it appear that those engineers (who are the real heroes) are making slower progress than the tactical tornado.

▪ The first step towards becoming a good software designer is to realize that working code isn’t enough. It’s not acceptable to introduce unnecessary complexities in order to finish your current task faster. The most important thing is the long-term structure of the system. Most of the code in any system is written by extending the existing code 

Page 15 
base, so your most important job as a developer is to facilitate those future extensions.

▪ Writing good documentation is another example of a proactive investment.

▪ No matter how much you invest up front, there will inevitably be mistakes in your design decisions. Over time, these mistakes will become obvious. When you discover a design problem, don’t just ignore it or patch around it; take a little extra time to fix it. If you program strategically, you will continually make small improvements to the system design. This is the opposite of tactical programming, where you are continually adding small bits of complexity that cause problems in the future.

▪ The ideal design tends to emerge in bits and pieces, as you get experience with the system. Thus, the best approach is to make lots of small investments on a continual basis.

▪ I suggest spending about 10–20% of your total development time on investments. This amount is small enough that it won’t impact your schedules significantly, but large enough to produce significant benefits over time. Your initial projects will thus take 10–20% longer than they would in a purely tactical approach.

▪ In some environments there are strong forces working against the strategic approach. For example, early-stage startups feel tremendous pressure to get their early releases out quickly. In these companies, it might seem that even a 10–20% investment isn’t affordable. As a result, many startups take a tactical approach, spending little effort on design and even less on cleanup when problems pop up. They rationalize this with the thought that, if they are successful, they’ll have enough money to hire extra engineers to clean things up.

▪ If you are in a company leaning in this direction, you should realize that once a code base turns to spaghetti, it is nearly impossible to fix.

▪ Good design doesn’t come for free

▪ Fortunately, good design eventually pays for itself, and sooner than you might think.

▪ One of the most important techniques for managing software complexity is to design systems so that developers only need to face a small fraction of the overall complexity at any given time. This approach is called modular design, and this chapter presents its basic principles.

▪ In modular design, a software system is decomposed into a collection of modules that are relatively independent

▪ Modules can take many forms, such as classes, subsystems, or services.

▪ In an ideal world, each module would be completely independent of the others: a developer could work in any of the modules without knowing anything about any of the other modules. In this world, the complexity of a system would be the complexity of its worst module.

Unfortunately, this ideal is not achievable. Modules must work together by calling each others’s functions or methods. As a result, modules must know something about each other. There will be dependencies between the modules: if one module changes, other modules may need to change to match.

▪ For example, the arguments for a method create a dependency between the method and any code that invokes the method

▪ A developer working in a particular module must understand the interface and implementation of that module, plus the interfaces of any other modules invoked by the given module. A developer should not need to understand the implementations of modules other than the one he or she is working in.

▪ For the purposes of this book, a module is any unit of code that has an interface and an implementation

▪ Each class in an object-oriented programming language is a module. Methods within a class, or functions in a language that isn’t object-oriented, can also be thought of as modules: each of these has an interface and an implementation, and modular design techniques can be applied to them. Higher-level subsystems and services are also modules; their interfaces may take different forms, such as kernel calls or HTTP requests. Much of the discussion about modular design in this book focuses on designing classes, but the techniques and concepts apply to other kinds of modules as well.

▪ The best modules are those whose interfaces are much simpler than their implementations.

▪ If a module’s interface is much simpler than its implementation, there will be many aspects of the module that can be changed without affecting other modules.

▪ The interface to a module contains two kinds of information: formal and informal.

▪ For example, the formal interface for a method is its signature, which includes the names and types of its parameters, the type of its return value, and information about exceptions thrown by 

Page 21 
the method. Most programming languages ensure that each invocation of a method provides the right number and types of arguments to match its signature.

▪ The informal parts of an interface include its high-level behavior, such as the fact that a function deletes the file named by one of its arguments. If there are constraints on the usage of a class (perhaps one method must be called before another), these are also part of the class’s interface.

▪ In general, if a developer needs to know a particular piece of information in order to use a module, then that information is part of the module’s interface.

▪ The informal aspects of an interface can only be described using comments, and the programming language cannot ensure that the description is complete or accurate1.

▪ For most interfaces the informal aspects are larger and more complex than the formal aspects.

▪ An abstraction is a simplified view of an entity, which omits unimportant details.

▪ Abstractions are useful because they make it easier for us to think about and manipulate complex things.

▪ An abstraction can go wrong in two ways. First, it can include details that are not really important; when this happens, it makes the abstraction more complicated than necessary, which increases the cognitive load on developers using the abstraction. The second error is when an abstraction omits details that really are important. This results in obscurity: developers looking only at the abstraction will not have all the information they need to use the abstraction correctly.

▪ An abstraction that omits important details is a false abstraction: it might appear simple, but in reality it isn’t.

▪ We depend on abstractions to manage complexity not just in programming, but pervasively in our everyday lives. A microwave oven contains complex electronics to convert alternating current into microwave radiation and distribute that radiation throughout the cooking cavity. Fortunately, users see a much simpler abstraction, consisting of a few buttons to control the timing and intensity of the microwaves. Cars provide a simple abstraction that allows us to drive them without understanding the mechanisms for electrical motors, battery power management, anti-lock brakes, cruise control, and so on.

▪ The best modules are those that provide powerful functionality yet have simple interfaces

▪ The best modules are deep: they allow a lot of functionality to be accessed through a simple interface. A shallow module is one with a relatively complex interface, but not much functionality: it doesn’t hide much complexity.

▪ Module depth is a way of thinking about cost versus benefit. The benefit provided by a module is its functionality. The cost of a module (in terms of system complexity) is its interface

▪ All of these issues, and many more, are handled by the Unix file system implementation; they are invisible to programmers who invoke the system calls

▪ Deep modules such as Unix I/O and garbage collectors provide powerful abstractions because they are easy to use, yet they hide significant implementation complexity.

▪ The complexity of a linked list interface is nearly as great as the complexity of its implementation.

▪ Shallow modules don’t help much in the battle against complexity, because the benefit they provide (not having to learn about how they work internally) is negated by the cost of learning and using their interfaces.

▪ Small modules tend to be shallow.

▪ Providing choice is good, but interfaces should be designed to make the common case as simple as possible (see the formula on page 6).

▪ By separating the interface of a module from its implementation, we can hide the complexity of the implementation from the rest of the system.

▪ My current opinion is that an interface described in English is likely to be more intuitive and understandable for developers than one written in a formal specification language.

▪ The best form of information hiding is when information is totally hidden within a module, so that it is irrelevant and invisible to users of the module.

▪ The opposite of information hiding is information leakage. Information leakage occurs when a design decision is reflected in multiple modules. This creates a dependency between the modules: any change to that design decision will require changes to all of the 

Page 31 
involved modules

▪ Suppose two classes both have knowledge of a particular file format (perhaps one class reads files in that format and the other class writes them). Even if neither class exposes that information in its interface, they both depend on the file format: if the format changes, both classes will need to be modified. Back-door leakage like this is more pernicious than leakage through an interface, because it isn’t obvious.

▪ Information leakage is one of the most important red flags in software design. One of the best skills you can learn as a software designer is a high level of sensitivity to information leakage

▪ One common cause of information leakage is a design style I call temporal decomposition. In temporal decomposition, the structure of a system corresponds to the time order in which operations will occur.

▪ This example illustrates a general theme in software design: information hiding can often be improved by making a class slightly larger.

▪ Of course, it is possible to take the notion of larger classes too far (such as a single class for the entire application).

▪ First, they recognized that server applications don’t care whether a parameter 

Page 35 
is specified in the header line or the body of the request, so they hid this distinction from callers and merged the parameters from both locations together.

▪ The most common mistake students made in this area was inadequate defaults. Each HTTP response must specify an HTTP protocol version; one team required callers to specify this version explicitly when creating a response object.

▪ Defaults illustrate the principle that interfaces should be designed to make the common case as simple as possible

▪ Whenever possible, classes should “do the right thing” without being explicitly asked. Defaults are an example of this

▪ The examples in this chapter focused on information hiding as it relates to the externally visible APIs for classes, but information hiding can also be applied at other levels in the system, such as within a class. Try to design the private methods within a class so that each method encapsulates some information or capability and hides it from the rest of the class.

▪ When decomposing a system into modules, try not to be influenced by the order in which operations will occur at runtime; that will lead you down the path of temporal decomposition, which will result in information leakage and shallow modules.

▪ On the other hand, we know that it’s hard to predict the future needs of a software system, so a general-purpose solution might include facilities that are never actually needed. Furthermore, if you implement something that is too general-purpose, it might not do a good job of solving the particular problem you have today

▪ As a result, some might argue that it’s better to focus on today’s needs, building just what you know you need, and specializing it for the way you plan to use it today. If you take the special-purpose approach and discover additional uses later, you can always refactor it to make it general-purpose. The special-purpose approach seems consistent with an incremental approach to software development.

▪ In my experience, the sweet spot is to implement new modules in a somewhat general-purpose fashion. The phrase “somewhat general-purpose” means that the module’s functionality should reflect your current needs, but its interface should not.

▪ This API also uses a more generic type Position instead of Cursor, which reflects a specific user interface.

▪ The general-purpose approach provides a cleaner separation between the text and user interface classes, which results in better information hiding. The text class need not be aware of specifics of the user interface, such as how the backspace key is handled; these details are now encapsulated in the user interface class.

▪ One of the most important elements of software design is determining who needs to know what, and when.

▪ It is easier to recognize a clean general-purpose class design than it is to create one.

▪ If you reduce the number of methods in an API without reducing its overall capabilities, then you are probably creating more general-purpose methods. The special-purpose text API had at least three methods for deleting text: backspace, delete, and deleteSelection. The more general-purpose API had only one method for deleting text, which served all three purposes. Reducing the number of methods makes sense only as long as the API for each individual method stays simple; if you have to introduce lots of additional arguments in order to reduce the number of methods, then you may not really be simplifying things.

▪ Software systems are composed in layers, where higher layers use the facilities provided by lower layers

▪ In a well-designed system, each layer provides a different abstraction from the layers above and below it; if you follow a single operation as it moves up and down through layers by invoking methods, the abstractions change with each method call.

▪ If a system contains adjacent layers with similar abstractions, this is a red flag that suggests a problem with the class decomposition.

▪ When adjacent layers have similar abstractions, the problem often manifests itself in the form of pass-through methods

▪ A pass-through method is one that does nothing except pass its arguments to another method, usually with the same API as the pass-through method

▪ Pass-through methods indicate that there is confusion over the division of responsibility between classes.

▪ One approach, shown in Figure 7.1(b), is to expose the lower level class directly to the callers of the higher level class, removing all responsibility for the feature from the higher level class.

▪ Having methods with the same signature is not always bad. The important thing is that each new method should contribute significant functionality. Pass-through methods are bad because they contribute no new functionality.

▪ One example where it’s useful for a method to call another method with the same signature is a dispatcher. A dispatcher is a method that uses its arguments to select one of several other methods to invoke; then it passes most or all of its arguments to 

Page 48 
the chosen method.

▪ The signature for the dispatcher is often the same as the signature for the methods that it calls. Even so, the dispatcher provides useful functionality: it chooses which of several other methods should carry out each task.

▪ For example, when a Web server receives an incoming HTTP request from a Web browser, it invokes a dispatcher that examines the URL in the incoming request and selects a specific method to handle the request. Some URLs might be handled by returning the contents of a file on disk; others might be handled by invoking a procedure in a language such as PHP or JavaScript. The dispatch process can be quite intricate, and is usually driven by a set of rules that are matched against the incoming URL.

▪ When several methods provide different implementations of the same interface, it reduces cognitive load. Once you have worked with one of these methods, it’s easier to work with the others, since you don’t need to learn a new interface. Methods like this are usually in the same layer and they 

Page 49 
don’t invoke each other.

▪ The decorator design pattern (also known as a “wrapper”) is one that encourages API duplication across layers

▪ a Window class implements a simple form of window that is not scrollable, and a ScrollableWindow class decorates the Window class by adding horizontal and vertical scrollbars.

▪ However, decorator classes tend to be shallow: they introduce a large amount of boilerplate for a small amount of new functionality.

▪ Sometimes decorators make sense, but there is usually a better alternative.

▪ Another application of the “different layer, different abstraction” rule is that the interface of a class should normally be different from its implementation: the representations used internally should be different from the abstractions that appear in the interface. If the two have similar abstractions, then the class probably isn’t very deep.

▪ A character-oriented interface encapsulates the complexity of line splitting and joining inside the text class, which makes the text class deeper and simplifies higher level code that uses the class.

▪ Pass-through variables add complexity because they force all of the intermediate methods to be aware of their existence, even though the methods have no use for the variables. Furthermore, if a new variable comes into existence (for example, a system is initially built without support for certificates, but you later decide to add that support), you may have to modify a large number of interfaces and methods to pass the variable through all of the relevant paths.

▪ Eliminating pass-through variables can be challenging.

▪ One approach is to see if there is already an object shared between the topmost and bottommost methods. In the datacenter service example of Figure 7.2, perhaps there is an object containing other information about network communication, which is available to both main and m3. If so, main can store the certificate information in that object, so it needn’t be passed through all of the intervening methods on the path to m3 (see Figure 7.2(b)). However, if there is such an object, then it may itself be a pass-through variable (how else does m3 get access to it?).

▪ Another approach is to store the information in a global variable, as in Figure 7.2(c). This avoids the need to pass the information from method to method, but global variables almost always create other problems. For example, global variables make it impossible to create two independent instances of the same system in the same process, since accesses to the global variables will conflict. It may seem unlikely that you would need multiple instances in production, but they are often useful in testing.

▪ The solution I use most often is to introduce a context object as in Figure 7.2(d). A context stores all of the application’s global state (anything that would otherwise be a pass-through variable or global variable). Most applications have multiple variables in their global state, representing things such as configuration options, shared subsystems, and performance counters. There is one context object per instance of the system. The context allows multiple instances of the system to coexist in a single process, each with its own context.

▪ Unfortunately, the context will probably be needed in many places, so it can potentially become a pass-through variable. To reduce the number of methods that must be aware of it, a reference to the context can be saved in most of the system’s major objects. In the example of Figure 7.2(d), the class containing m3 stores a reference to the context as an instance variable in its objects. When a new object is created, the creating method retrieves the context reference from its object and passes it to the constructor for the new object. With this approach, the context is available everywhere, but it only appears as an explicit argument in constructors.

▪ The context object unifies the handling of all system-global information and eliminates the need for pass-through variables. If a new variable needs to be added, it can be added to the context object; no existing code is affected except for the constructor and destructor for the context. The context makes it easy to identify and manage the global state of the system, since it is all stored in one place.

▪ The context is also convenient for testing: test code can change the global configuration of the application by modifying fields in the context. It would be much more difficult to implement such changes if the system used pass-through variables.

▪ Contexts are far from an ideal solution. The variables stored in a context have most of the disadvantages of global variables; for example, it may not be obvious why a particular variable is present, or where it is used. Without discipline, a context can turn into a huge grab-bag of data that creates nonobvious dependencies throughout the system.

▪ Unfortunately, I haven’t found a better solution than contexts.

▪ Each piece of design infrastructure added to a system, such as an interface, argument, function, class, or definition, adds complexity, since developers must learn about this element. In order for an element to provide a net gain against complexity, it must eliminate some complexity that would be present in the absence of the design element. Otherwise, you are better off implementing the system without that particular element.

▪ The “different layer, different abstraction” rule is just an application of this idea: if different layers have the same abstraction, such as pass-through methods or decorators, then there’s a good chance that they haven’t provided enough benefit to compensate for the additional infrastructure they represent. Similarly, pass-through arguments require each of several methods to be aware of their existence (which adds to complexity) without contributing additional functionality.

▪ Suppose that you are developing a new module, and you discover a piece of unavoidable complexity. Which is better: should you let users of the module deal with the complexity, or should you handle the complexity internally within the module? If the complexity is related to the functionality provided by the module, then the second answer is usually the right one.

▪ Most modules have more users than developers, so it is better for the developers to suffer than the users.

▪ As a module developer, you should strive to make life as easy as possible for the users of your module, even if that means extra work for you.

▪ Another way of expressing this idea is that it is more important for a module to have a simple interface than a simple implementation.

▪ Approaches like these will make your life easier in the short term, but they amplify complexity, so that many people must deal with a problem, rather than just one person.

▪ A character-oriented interface such as the one described in Section 6.3 pulls complexity downward. The user interface software can now insert and delete arbitrary ranges of text without splitting and merging lines, so it becomes simpler.

▪ The implementation of the text class probably becomes more complex: if it represents the text internally as a collection of lines, it will have to split and merge lines to implement the character-oriented operations. This approach is better because it encapsulates the complexity of splitting and merging within the text class, which reduces the overall complexity of the system.

▪ Configuration parameters are an example of moving complexity upwards instead of down. Rather than determining a particular behavior internally, a class can export a few parameters that control its behavior, such as the size of a cache or the number of times to retry a request before giving up. Users of the class must then specify appropriate values for the parameters.

▪ When you do create configuration parameters, see if you can compute reasonable defaults automatically, so users will only need to provide values under exceptional conditions.

▪ Use discretion when pulling complexity downward; this is an idea that can easily be overdone. An extreme approach would be to pull all of the functionality of the entire application down into a single class, which clearly doesn’t make sense.

▪ Pulling complexity down makes the most sense if (a) the complexity being pulled down is closely related to the class’s existing functionality, (b) pulling the complexity down will result in many simplifications elsewhere in the application, and (c) pulling the complexity down simplifies the class’s interface.

▪ Remember that the goal is to minimize overall system complexity.

▪ In this case, pulling complexity down just resulted in information leakage.

▪ When developing a module, look for opportunities to take a little bit of extra suffering upon yourself in order to reduce the suffering of your users.

▪ One of the most fundamental questions in software design is this: given two pieces of functionality, should they be implemented together in the same place, or should their implementations be separated?

▪ This question applies at all levels in a system, such as functions, methods, classes, and services. For example, should buffering be included in the class that provides stream-oriented file I/O, or should it be in a separate class? Should the parsing of an HTTP request be implemented entirely in one method, or should it be divided among multiple methods (or even multiple classes)? This chapter discusses the factors to consider when making these decisions.

▪ When deciding whether to combine or separate, the goal is to reduce the complexity of the system as a whole and improve its modularity.

▪ It might appear that the best way to achieve this goal is to divide the system into a large number of small components: the smaller the components, the simpler each individual component is likely to be. However, the act of subdividing creates additional complexity that was not present before subdivision:

▪ Some complexity comes just from the number of components: the more components, the harder to keep track of them all and the harder to find a desired component within the large collection. Subdivision usually results in more interfaces, and every new interface adds complexity.

▪ Subdivision can result in additional code to manage the components. For example, a piece of code that used a single object before subdivision might now have to manage multiple objects.

▪ Subdivision creates separation: the subdivided components will be farther apart 

Page 60 
than they were before subdivision. For example, methods that were together in a single class before subdivision may be in different classes after subdivision, and possibly in different files.

▪ Separation makes it harder for developers to see the components at the same time, or even to be aware of their existence. If the components are truly independent, then separation is good: it allows the developer to focus on a single component at a time, without being distracted by the other components. On the other hand, if there are dependencies between the components, then separation is bad: developers will end up flipping back and forth between the components.

▪ Even worse, they may not be aware of the dependencies, which can lead to bugs.

▪ Subdivision can result in duplication: code that was present in a single instance before subdivision may need to be present in each of the subdivided components.

▪ Bringing pieces of code together is most beneficial if they are closely related. If the pieces are unrelated, they are probably better off apart.

▪ With this decomposition, both of the methods ended up with considerable knowledge of the format of HTTP requests: the first method was only trying to read the request, not parse it, but it couldn’t identify the end of the request without doing most of the work of parsing it (for example, it had to parse header lines in order to identify the header containing the overall request length).

▪ Because of this shared information, it is better to both read and parse the request in the same place; when the two classes were combined into one, the code got shorter and simpler.

▪ When two or more modules are combined into a single module, it may be possible to define an interface for the new module that is simpler or easier to use than the original interfaces

▪ In addition, when the functionality of two or more classes is combined, it may be possible to perform some functions automatically, so that most users need not be aware of them

▪ The Java I/O library illustrates this opportunity. If the FileInputStream and BufferedInputStream classes were combined and buffering were provided by default, the vast majority of users would never even need to be aware of the existence of buffering.

▪ If the same piece of code (or code that is almost the same) appears over and over again, that’s a red flag that you haven’t found the right abstractions.

▪ In general, the lower layers of a system tend to be more general-purpose and the upper layers more special-purpose

▪ For example, the topmost layer of an application consists of features totally specific to that application. The way to separate special-purpose code from general-purpose code is to pull the special-purpose code upwards, into the higher layers, leaving the lower layers general-purpose.

▪ When you encounter a class that includes both general-purpose and special-purpose features for the same abstraction, see if the class can be separated into two classes, one containing the general-purpose features, and the other layered on top of it to provide the special-purpose features.

▪ This red flag occurs when a general-purpose mechanism also contains code specialized for a particular use of that mechanism

▪ The key design decision was the one that separated the general-purpose part of the undo mechanism from the special-purpose parts and put the general-purpose part in a 

Page 70 
class by itself. Once that was done, the rest of the design fell out naturally.

▪ The issue of when to subdivide applies not just to classes, but also to methods: are there times when it is better to divide an existing method into multiple smaller methods? Or, should two smaller methods be combined into one larger one?

▪ Long methods tend to be more difficult to understand than shorter ones, so many people argue that length alone is a good justification for breaking up a method. Students in classes are often given rigid criteria, such as “Split up any method longer than 20 lines!”

▪ You shouldn’t break up a method unless it makes the overall system simpler;

▪ Long methods aren’t always bad. For example, suppose a method contains five 20-line blocks of code that are executed in order. If the blocks are relatively independent, then the method can be read and understood one block at a time; there’s not much benefit in moving each of the blocks into a separate method. If the blocks have complex interactions, it’s even more important to keep them together so readers can see all of the code at once; if each block is in a separate method, readers will have to flip back and forth between these spread-out methods in order to understand how they work together.

▪ Methods containing hundreds of lines of code are fine if they have a simple signature and are easy to read.

▪ When designing methods, the most important goal is to provide clean and simple abstractions. Each method should do one thing and do it completely. The method should have a clean and simple interface, so that users don’t need to have much information in their heads in order to use it correctly. The method should be deep: its interface should be much simpler than its implementation.

▪ The decision to split or join modules should be based on complexity. Pick the structure that results in the best information hiding, the fewest dependencies, and the deepest interfaces.

▪ Exception handling is one of the worst sources of complexity in software systems

▪ Code that deals with special conditions is inherently harder to write than code that deals with normal cases, and developers often define exceptions without considering how they will be handled

▪ This chapter discusses why exceptions contribute disproportionately to complexity, then it shows how to simplify exception handling.

▪ The key overall lesson from this chapter is to reduce the number of places where exceptions must be handled; in many cases the semantics of operations can be modified so that the normal behavior handles all situations and there is no exceptional condition to report (hence the title of this chapter).

▪ I use the term exception to refer to any uncommon condition that alters the normal flow of control in a program.

▪ Many programming languages include a formal exception mechanism that allows exceptions to be thrown by lower-level code and caught by enclosing code.

▪ However, exceptions can occur even without using a formal exception reporting mechanism, such as when a method returns a special value indicating that it didn’t complete its normal behavior. All of these forms of exceptions contribute to complexity.

▪ Large systems have to deal with many exceptional conditions, particularly if they are distributed or need to be fault-tolerant. Exception handling can account for a significant fraction of all the code in a system.

▪ Exception handling code is inherently more difficult to write than normal-case code.

▪ An exception disrupts the normal flow of the code; it usually means that something didn’t work as expected.

▪ When an exception occurs, the programmer can deal with it in two ways, each of which can be complicated. The first approach is to move forward and complete the work in progress in spite of the exception. For example, if a network packet is lost, it can be resent; if data is corrupted, perhaps it can be recovered from a redundant copy.

▪ The second approach is to abort the operation in progress and report the exception upwards.

▪ However, aborting can be complicated because the exception may have occurred at a point where system state is inconsistent (a data structure might have been partially initialized); the exception handling code must restore consistency, such as by unwinding any changes made before the exception occurred.

▪ Furthermore, exception handling code creates opportunities for more exceptions. Consider the case of resending a lost network packet. Perhaps the packet wasn’t actually lost, but was simply delayed. In this case, resending the packet will result in duplicate packets arriving at the peer; this introduces a new exceptional condition that the peer must handle. Or, consider the case of recovering lost data from a redundant copy: what if the redundant copy has also been lost? Secondary exceptions occurring during recovery are often more subtle and complex than the primary exceptions.

▪ If an exception is handled by aborting the operation in progress, then this must be reported to the caller as another exception. To prevent an unending cascade of exceptions, the developer must eventually find a way to handle exceptions without introducing more exceptions.

▪ Language support for exceptions tends to be verbose and clunky, which makes exception handling code hard to read.

▪ Just the basic try-catch boilerplate accounts for more lines of code than the code for normal-case operation, without even considering the code that actually handles the exceptions.

▪ It is hard to relate the exception handling code to the normal-case code: for example, it’s not obvious where each exception is generated.

▪ An alternative approach is to break up the code into many distinct try blocks; in the extreme case there could be a try for each line of code that can generate an exception. This would make it clear where exceptions occur, but the try blocks themselves break up the flow of the code and make it harder to read; in addition, some exception handling code might end up duplicated in multiple try blocks.

▪ It’s difficult to ensure that exception handling code really works. Some exceptions, such as I/O errors, can’t easily be generated in a test environment, so it’s hard to test the code that handles them.

▪ Exceptions don’t occur very often in running systems, so exception handling code rarely executes. Bugs can go undetected for a long time, and when the exception handling code is finally needed, there’s a good chance that it won’t work (one of my favorite sayings: “code that hasn’t been executed doesn’t work”).

▪ A recent study found that more than 90% of catastrophic failures in distributed data-intensive 

Page 78 
systems were caused by incorrect error handling1.

▪ When exception handling code fails, it’s difficult to debug the problem, since it occurs so infrequently.

▪ Programmers exacerbate the problems related to exception handling by defining unnecessary exceptions. Most programmers are taught that it’s important to detect and report errors; they often interpret this to mean “the more errors detected, the better.” This leads to an over-defensive style where anything that looks even a bit suspicious is rejected with an exception, which results in a proliferation of unnecessary exceptions that increase the complexity of the system.

▪ It’s often hard to predict exactly what state was created, particularly if the operation aborted partway through. Thus, the simplest thing is to delete all of the variables that might possibly have been created.

▪ It’s tempting to use exceptions to avoid dealing with difficult situations: rather than figuring out a clean way to handle it, just throw an exception and punt the problem to the caller. Some might argue that this approach empowers callers, since it allows each caller to handle the exception in a different way. However, if you are having trouble figuring out what to do for the particular situation, there’s a good chance that the caller won’t know what to do either.

▪ The exceptions thrown by a class are part of its interface; classes with lots of exceptions have complex interfaces, and they are shallower than classes with fewer exceptions. An exception is a particularly complex element of an interface. It can 

Page 79 
propagate up through several stack levels before being caught, so it affects not just the method’s caller, but potentially also higher-level callers (and their interfaces).

▪ Throwing exceptions is easy; handling them is hard. Thus, the complexity of exceptions comes from the exception handling code. The best way to reduce the complexity damage caused by exception handling is to reduce the number of places where exceptions have to be handled.

▪ The best way to eliminate exception handling complexity is to define your APIs so that there are no exceptions to handle: define errors out of existence.

▪ Consider the Tcl unset command discussed above. Rather than throwing an error when unset is asked to delete an unknown variable, it should have simply returned without doing anything. I should have changed the definition of unset slightly: rather than deleting a variable, unset should ensure that a variable no longer exists. With the first definition, unset can’t do its job if the variable doesn’t exist, so generating an exception makes sense. With the second definition, it is perfectly natural for unset to be invoked with the name of a variable that doesn’t exist. In this case, its work is already done, so it can simply return. There is no longer an error case to report.

▪ The Unix operating system defines file deletion more elegantly. In Unix, if a file is open when it is deleted, Unix does not delete the file immediately. Instead, it marks the file for deletion, then the delete operation returns successfully. The file name has been removed from its directory, so no other processes can open the old file and a new file with the same name can be created, but the existing file data persists.

▪ One possible approach to this problem would have been to delete the file immediately and mark all of the opens of the file to disable them; any attempts by other processes to read or write the deleted file would fail. However, this approach would create new errors for those processes to handle. Instead, Unix allows them to keep accessing the file normally; delaying the file deletion defines errors out of existence.

▪ It may seem strange that Unix allows a process to continue to read and write a doomed file, but I have never encountered a situation where this caused significant problems. The Unix definition of file deletion is much simpler to work with, both for developers and users, than the Windows definition.

▪ As a final example, consider the Java String class and its substring method. Given two indexes into a string, substring returns the substring starting at the character given by the first index and ending with the character just before the second index. However, if either index is outside the range of the string, then substring throws IndexOutOfBoundsException. This exception is unnecessary and complicates the use of this method. I often find myself in a situation where one or both of the indices may be outside the range of the string, and I would like to extract all of the characters in the string that overlap the specified range. Unfortunately, this requires me to check each of the indices and round them up to zero or down to the end of the string; a one-line method call now becomes 5–10 lines of code.

▪ When I argue for defining errors out of existence, people sometimes counter that throwing errors will catch bugs; if errors are defined out of existence, won’t that result in buggier software? Perhaps this is why the Java developers decided that substring should throw exceptions. The error-ful approach may catch some bugs, but it also increases complexity, which results in other bugs. In the error-ful approach, developers must write additional code to avoid or ignore the errors, and this increases the likelihood of bugs; or, they may forget to write the additional code, in which case unexpected errors may be thrown at runtime.

▪ Overall, the best way to reduce bugs is to make software simpler.

▪ The second technique for reducing the number of places where exceptions must be handled is exception masking.

▪ With this approach, an exceptional condition is detected and handled at a low level in the system, so that higher levels of software need not be aware of the condition.

▪ Exception masking is particularly common in distributed systems. For instance, in a network transport protocol such as TCP, packets can be dropped for various reasons such as corruption and congestion. TCP masks packet loss by resending lost packets within its implementation, so all data eventually gets through and clients are unaware of the dropped packets.

▪ The operation in progress (and hence the application) just hangs until the operation can complete successfully. If the hang lasts more than a short time, the NFS client prints messages on the user’s console of the form “NFS server xyzzy not responding still trying.”

▪ However, reporting exceptions would make things worse, not better. There’s not much an application can do if it loses access to its files. One possibility would be for the application to retry 

Page 82 
the file operation, but this would still hang the application, and it’s easier to perform the retry in one place in the NFS layer, rather than at every file system call in every application (a compiler shouldn’t have to worry about this!).

▪ The other alternative is for applications to abort and return errors to their callers. It’s unlikely that the callers would know what to do either, so they would abort as well, resulting in a collapse of the user’s working environment.

▪ If users get tired of waiting, they can always abort applications manually.

▪ Exception masking doesn’t work in all situations, but it is a powerful tool in the situations where it works. It results in deeper classes, since it reduces the class’s interface (fewer exceptions for users to be aware of) and adds functionality in the form of the code that masks the exception. Exception masking is an example of pulling complexity downward.

▪ The third technique for reducing complexity related to exceptions is exception aggregation. The idea behind exception aggregation is to handle many exceptions with a single piece of code; rather than writing distinct handlers for many individual exceptions, handle them all in one place with a single handler.

▪ When students in a software design class implemented such a server, many of them wrapped each distinct call to getParameter in a separate exception handler to catch NoSuchParameter exceptions, as in Figure 10.1. This resulted in a large number of handlers, all of which did essentially the same thing (generate an error response).

▪ A better approach is to aggregate the exceptions. Instead of catching the exceptions in the individual service methods, let them propagate up to the top-level dispatch method for the Web server, as in Figure 10.2.

▪ Thus, all conditions resulting in an error response can be handled with a single top-level exception handler. The error message can be generated at the time the exception is thrown and included as a variable in the exception record; for example

▪ This example illustrates a generally-useful design pattern for exception handling. If a system processes a series of requests, it’s useful to define an exception that aborts the current request, cleans up the system’s state, and continues with the next request.

▪ The exception is caught in a single place near the top of the system’s request-handling loop. This exception can be thrown at any point in the processing of a request to abort the request; different subclasses of the exception can be defined for different conditions.

▪ Exceptions of this type should be clearly distinguished from exceptions that are fatal to the entire system.

▪ Exception aggregation works best if an exception propagates several levels up the stack before it is handled; this allows more exceptions from more methods to be handled in the same place.

▪ This is the opposite of exception masking: masking usually works best if an exception is handled in a low-level method. For masking, the low-level method is typically a library method used by many other methods, so allowing the exception to propagate would increase the number of places where it is handled. Masking and aggregation are similar in that both approaches position an exception handler where it can catch the most exceptions, eliminating many handlers that would otherwise need to be created.

▪ One disadvantage of promoting a corrupted object into a server crash is that it increases the cost of recovery considerably. This is not a problem in RAMCloud, since object corruption is quite rare. However, error promotion may not make sense for errors that happen frequently. As one example, it would not be practical to crash a server anytime one of its network packets is lost.

▪ One way of thinking about exception aggregation is that it replaces several special-purpose mechanisms, each tailored for a particular situation, with a single general-purpose mechanism that can handle multiple situations. This provides another illustration of the benefits of general-purpose mechanisms.

▪ The fourth technique for reducing complexity related to exception handling is to crash the application

▪ In most applications there will be certain errors that it’s not worth trying to handle. Typically, these errors are difficult or impossible to handle and don’t occur very often. The simplest thing to do in response to these errors is to print diagnostic information and then abort the application.

▪ For most programs, if an I/O error occurs while reading or writing an open file (such as a disk hard error), or if a network socket cannot be opened, there’s not much the application can do to recover, so aborting with a clear error message is a sensible approach.

▪ These errors are infrequent, so they are unlikely to affect the overall usability of the application. Aborting with an error message is also appropriate if an application encounters an internal error such as an inconsistent data structure. Conditions like this probably indicate bugs in the program.

▪ Whether or not it is acceptable to crash on a particular error depends on the application. For a replicated storage system, it isn’t appropriate to abort on an I/O error. Instead, the system must use replicated data to recover any information that was lost. The recovery mechanisms will add considerable complexity to the program, but recovering lost data is an essential part of the value the system provides to its users.

▪ For the same reason that it makes sense to define errors out of existence, it also makes sense to define other special cases out of existence

▪ Special cases can result in code that is riddled with if statements, which make the code hard to understand and lead to bugs. Thus, special cases should be eliminated wherever possible. The best way to do this is by designing the normal case in a way that automatically handles the special cases without any extra code.

▪ However, this approach resulted in numerous checks to detect the “no selection” condition and handle it specially.

The selection handling code can be simplified by eliminating the “no selection” special case, so that the selection always exists. When there is no selection visible on the screen, it can be represented internally with an empty selection, whose starting and ending positions are the same. With this approach, the selection management code can be written without any checks for “no selection”. When copying the selection, if the selection is empty then 0 bytes will be inserted at the new location (if implemented correctly, there will be no need to check for 0 bytes as a special case).

▪ Similarly, it should be possible to design the code for deleting the selection so that the empty case is handled without any special-case checks. Consider a selection all on a single line. To delete the selection, extract the portion of the line preceding the selection and concatenate it with the portion of the line following the selection to form the new line. If the selection is empty, this approach will regenerate the original line.

▪ However, it is possible to take this idea too far. In a module for network communication, a student team masked all network exceptions: if a network error occurred, the module caught it, discarded it, and continued as if there were no problem. This meant that applications using the module had no way to find out if messages were lost or a peer server failed; without this information, it was impossible to build robust applications. In this case, it is essential for the module to expose the exceptions, even though they add complexity to the module’s interface.

▪ With exceptions, as with many other areas in software design, you must determine what is important and what is not important.

▪ Special cases of any form make code harder to understand and increase the likelihood of bugs. This chapter focused on exceptions, which are one of the most significant sources of special-case code, and discussed how to reduce the number of places where exceptions must be handled. The best way to do this is by redefining semantics to eliminate error conditions.

▪ For exceptions that can’t be defined away, you should look for opportunities to mask them at a low level, so their impact is limited, or aggregate several special-case handlers into a single more generic handler. Together, these techniques can have a significant impact on overall system complexity.

▪ Designing software is hard, so it’s unlikely that your first thoughts about how to structure a module or system will produce the best design. You’ll end up with a much better result if you consider multiple options for each major design decision: design it twice.

▪ Suppose you are designing the class that will manage the text of a file for a GUI text editor. The first step is to define the interface that the class will present to the rest of the editor; rather than picking the first idea that comes to mind, consider several possibilities. One choice is a line-oriented interface, with operations to insert, modify, and delete whole lines of text. Another option is an interface based on individual character insertions and deletions. A third choice is a string-oriented interface, which operates on arbitrary ranges of characters that may cross line boundaries. You don’t need to pin down every feature of each alternative; it’s sufficient at this point to sketch out a few of the most important methods.

▪ Try to pick approaches that are radically different from each other; you’ll learn more that way

▪ Even if you are certain that there is only one reasonable approach, consider a second design anyway, no matter how bad you think it will be. It will be instructive to think about the weaknesses of that design and contrast them with the features of other designs.

▪ After you have roughed out the designs for the alternatives, make a list of the pros and cons of each one.

▪ Does one alternative have a simpler interface than another? In the text example, all of the text interfaces are relatively simple

▪ Is one interface more general-purpose than another?

▪ Does one interface enable a more efficient implementation than another? In the text example, the character-oriented approach is likely to be significantly slower than the others, because it requires a separate call into the text module for each character.

▪ Once you have compared alternative designs, you will be in a better position to identify the best design. The best choice may be one of the alternatives, or you may discover that you can combine features of multiple alternatives into a new design that is better than any of the original choices.

▪ The design-it-twice principle can be applied at many levels in a system. For a module, you can use this approach first to pick the interface, as described above. Then you can apply it again when you are designing the implementation:

▪ The goals will be different for the implementation than for the interface: for the implementation, the most important things are simplicity and performance.

▪ It’s also useful to explore multiple designs at higher levels in the system, such as when choosing features for a user interface, or when decomposing a system into major modules. In each case, it’s easier to identify the best approach if you can compare a few alternatives.

▪ Designing it twice does not need to take a lot of extra time. For a smaller module such as a class, you may not need more than an hour or two to consider alternatives. This is a small amount of time compared to the days or weeks you will spend implementing 

Page 93 
the class.

▪ I have noticed that the design-it-twice principle is sometimes hard for really smart people to embrace. When they are growing up, smart people discover that their first quick idea about any problem is sufficient for a good grade; there is no need to consider a second or third possibility. This makes it easy to develop bad work habits. However, as these people get older, they get promoted into environments with harder and harder problems.

▪ Eventually, everyone reaches a point where your first ideas are no longer good enough; if you want to get really great results, you have to consider a second possibility, or perhaps a third, no matter how smart you are. The design of large software systems falls in this category: no-one is good enough to get it right with their first try.

▪ Perhaps they subconsciously believe that “smart people get it right the first time,” so if they try multiple designs it would mean they are not smart after all. This is not the case. It isn’t that you aren’t smart; it’s that the problems are really hard!

▪ The design-it-twice approach not only improves your designs, but it also improves your design skills. The process of devising and comparing multiple approaches will teach you about the factors that make designs better or worse. Over time, this will make it easier for you to rule out bad designs and hone in on really great ones.

▪ In-code documentation plays a crucial role in software design. Comments are essential to help developers understand a system and work efficiently, but the role of comments goes beyond this.

▪ Documentation also plays an important role in abstraction; without comments, you can’t hide complexity.

▪ Finally, the process of writing comments, if done correctly, will actually improve a system’s design. Conversely, a good software design loses much of its value if it is poorly documented.

▪ Unfortunately, this view is not universally shared. A significant fraction of production code contains essentially no comments. Many developers think that comments are a waste of time; others see the value in comments, but somehow never get around to writing them.

▪ However, even in teams that encourage documentation, comments are often viewed as drudge work and many developers don’t understand how to write them, so the resulting documentation is often mediocre.

▪ Inadequate documentation creates a huge and unnecessary drag on software development.

▪ In this chapter I will discuss the excuses developers use to avoid writing comments, and the reasons why comments really do matter.

▪ I hope these chapters will convince you of three things: good comments can make a big difference in the overall quality of software; it isn’t hard to write good comments; and (this may be hard to believe) writing comments can actually be fun.

▪ When developers don’t write comments, they usually justify their behavior with one or more of the following excuses:

“Good code is self-documenting.”
“I don’t have time to write comments.”
“Comments get out of date and become misleading.”
“The comments I have seen are all worthless; why bother?”

▪ Some people believe that if code is written well, it is so obvious that no comments are needed. This is a delicious myth, like a rumor that ice cream is good for your health: we’d really like to believe it! Unfortunately, it’s simply not true. To be sure, there are things you can do when writing code to reduce the need for comments, such as choosing good variable names (see Chapter 14). Nonetheless, there is still a significant amount of design information that can’t be represented in code.

▪ For example, only a small part of a class’s interface, such as the signatures of its methods, can be specified formally in the code.

▪ The informal aspects of an interface, such as a high-level description of what each method does or the meaning of its result, can only be described in comments.

▪ There are many other examples of things that can’t be described in the code, such as the rationale for a particular design decision, or the conditions under which it makes sense to call a particular method.

▪ Moreover, comments are fundamental to abstractions. Recall from Chapter 4 that the goal of abstractions is to hide complexity: an abstraction is a simplified view of an entity, which preserves essential information but omits details that can safely be 

Page 97 
ignored. If users must read the code of a method in order to use it, then there is no abstraction: all of the complexity of the method is exposed.

▪ Without comments, the only abstraction of a method is its declaration, which specifies its name and the names and types of its arguments and results. The declaration is missing too much essential information to provide a useful abstraction by itself.

▪ For example, a method to extract a substring might have two arguments, start and end, indicating the range of characters to extract. From the declaration alone, it isn’t possible to tell whether the extracted substring will include the character indicated by end, or what happens if start > end. Comments allow us to capture the additional information that callers need, thereby completing the simplified view while hiding implementation details.

▪ It’s also important that comments are written in a human language such as English; this makes them less precise than code, but it provides more expressive power, so we can create simple, intuitive descriptions. If you want to use abstractions to hide complexity, comments are essential.

▪ It’s tempting to prioritize comments lower than other development tasks. Given a choice between adding a new feature and documenting an existing feature, it seems logical to choose the new feature.

▪ However, software projects are almost always under time pressure, and there will always be things that seem higher priority than writing comments. Thus, if you allow documentation to be de-prioritized, you’ll end up with no documentation.

▪ The counter-argument to this excuse is the investment mindset discussed on page 15. If you want a clean software structure, which will allow you to work efficiently over the long-term, then you must take some extra time up front in order to create that structure.

▪ Furthermore, many of the most important comments are those related to abstractions, 

Page 98 
such as the top-level documentation for classes and methods.

▪ Chapter 15 will argue that these comments should be written as part of the design process, and that the act of writing the documentation serves as an important design tool that improves the overall design. These comments pay for themselves immediately.

▪ Large changes to the documentation are only required if there have been large changes to the code, and the code changes will take more time than the documentation changes.

▪ Of the four excuses, this is probably the one with the most merit. Every software developer has seen comments that provide no useful information, and most existing documentation is so-so at best. Fortunately, this problem is solvable; writing solid documentation is not hard, once you know how.

▪ The overall idea behind comments is to capture information that was in the mind of the designer but couldn’t be represented in the code. This information ranges from low-level details, such as a hardware quirk that motivates a particularly tricky piece of code, up to high-level concepts such as the rationale for a class. When other developers come along later to make modifications, the comments will allow them to work more quickly and accurately.

▪ Without documentation, future developers will have to rederive or guess at the developer’s original knowledge; this will take additional time, 

Page 99 
and there is a risk of bugs if the new developer misunderstands the original designer’s intentions.

▪ Comments are valuable even when the original designer is the one making the changes: if it has been more than a few weeks since you last worked in a piece of code, you will have forgotten many of the details of the original design.

▪ Chapter 2 described three ways in which complexity manifests itself in software systems:

Change amplification: a seemingly simple change requires code modifications in many places.

Cognitive load: in order to make a change, the developer must accumulate a large amount of information.

Unknown unknowns: it is unclear what code needs to be modified, or what information must be considered in order to make those modifications.

▪ Good documentation helps with the last two of these issues. Documentation can reduce cognitive load by providing developers with the information they need to make changes and by making it easy for developers to ignore information that is irrelevant. Without adequate documentation, developers may have to read large amounts of code to reconstruct what was in the designer’s mind.

▪ Documentation can also reduce the unknown unknowns by clarifying the structure of the system, so that it is clear what information and code is relevant for any given change.

▪ Chapter 2 pointed out that the primary causes of complexity are dependencies and obscurity. Good documentation can clarify dependencies, and it fills in gaps to eliminate obscurity.

▪ The reason for writing comments is that statements in a programming language can’t capture all of the important information that was in the mind of the developer when the code was written.

▪ The guiding principle for comments is that comments should describe things that aren’t obvious from the code.

▪ For example, when a pair of indices describe a range, it isn’t obvious whether the elements given by the indices are inside the range or out. Sometimes it’s not clear why code is needed, or why it was implemented in a particular way. Sometimes there are rules the developer followed, such as “always invoke a before b.”

▪ You might be able to guess at a rule by looking at all of the code, but this is painful and error-prone; a comment can make the rule explicit and clear.

▪ One of the most important reasons for comments is abstractions, which include a lot of information that isn’t obvious from the code.

▪ The idea of an abstraction is to provide a simple way of thinking about something, but code is so detailed that it can be hard to see the abstraction just from reading the code.

▪ Comments can provide a simpler, higher-level view (“after this method is invoked, network traffic will be limited to maxBandwidth bytes per second”).

▪ Even if this information can be deduced by reading the code, we don’t want to force users of a module to do that: reading the code is time-consuming and forces them to consider a lot of information that isn’t needed to 

Page 102 
use the module.

▪ Developers should be able to understand the abstraction provided by a module without reading any code other than its externally visible declarations. The only way to do this is by supplementing the declarations with comments.

▪ As you will see, good comments typically explain things at a different level of detail than the code, which is more detailed in some situations and less detailed (more abstract) in others.

▪ None of these conventions is perfect, but the tools provide enough benefits to make up for that.

▪ Most comments fall into one of the following categories:

▪ Interface: a comment block that immediately precedes the declaration of a module such as a class, data structure, function, or method. The comment describe’s the module’s interface. For a class, the comment describes the overall abstraction provided by the class. For a method or function, the comment describes its overall behavior, its arguments and return value, if any, any side effects or exceptions that it generates, and any other requirements the caller must satisfy before invoking the method.

▪ Data structure member: a comment next to the declaration of a field in a data structure, such as an instance variable or static variable for a class.

▪ Implementation comment: a comment inside the code of a method or function, which describes how the code works internally.

▪ Cross-module comment: a comment describing dependencies that cross module boundaries.

▪ The most important comments are those in the first two categories. Every class should have an interface comment, every class variable should have a comment, and every method should have an interface comment.

▪ Occasionally, the declaration for a variable or method is so obvious that there is nothing useful to add in a comment (getters and setters sometimes fall in this category), but this is rare; it is easier to comment everything rather than spend energy worrying about whether a comment is needed.

▪ Implementation comments are often unnecessary (see Section 13.6 below).

▪ Cross-module comments are the most rare of all and they are problematic to write, but when they are needed they are quite important;

▪ Notice that these comments are at roughly the same level of detail as the code: there is one comment per line of code, which describes that line. Comments like this are rarely useful.

▪ After you have written a comment, ask yourself the following question: could someone who has never seen the code write the comment just by looking at the code next to the comment?

▪ Comments like these are why some people think that comments are worthless.

▪ Once again, these comments could be written just by looking at the declarations, without any understanding the methods of variables; as a result, they have no value.

▪ At the same time, there is important information that is missing from the comments: for example, what is a “normalized resource name”, and what are the elements of the array returned by getNormalizedResourceNames? What does “downcast” mean? What are the units of padding, and is the padding on one side of each line or both? Describing these things in comments would be helpful.

▪ A first step towards writing good comments is to use different words in the comment from those in the name of the entity being described.

▪ For example, here is a better comment for textHorizontalPadding:

/*

 * The amount of blank space to leave on the left and

 * right sides of each line of text, in pixels.

 */

▪ This comment provides additional information that is not obvious from the declaration itself, such as the units (pixels) and the fact that padding applies to both sides of each line. Instead of using the term “padding”, the comment explains what padding is, in case the reader isn’t already familiar with the term.

▪ Comments augment the code by providing information at a different level of detail.

▪ Some comments provide information at a lower, more detailed, level than the code; these comments add precision by clarifying the exact meaning of the code.

▪ Other comments provide information at a higher, more abstract, level than the code; these comments offer intuition, such as the reasoning behind the code, or a simpler and more abstract way of thinking about the code.

▪ Comments at the same level as the code are likely to repeat the code.

▪ Comments can fill in missing details such as:

What are the units for this variable?
Are the boundary conditions inclusive or exclusive?
If a null value is permitted, what does it imply?
If a variable refers to a resource that must eventually be freed or closed, who is responsible for freeing or closing it?
Are there certain properties that are always true for the variable (invariants), such as “this list always contains at least one entry”?

▪ Some of this information could potentially be figured out by examining all of the code where the variable is used. However, this is time-consuming and error-prone; the declaration’s comment should be clear and complete enough to make this unnecessary.

▪ When I say that the comment for a declaration should describe things that aren’t obvious from the code, “the code” refers to the code next to the comment (the declaration), not “all of the code in the application.”

▪ Here are two examples of comments that aren’t precise enough:

// Current offset in resp Buffer

uint32_t offset;

// Contains all line-widths inside the document and

// number of appearances.

private TreeMap lineWidths;

In the first example, it’s not clear what “current” means. In the second example, it’s not clear that the keys in the TreeMap are line widths and values are occurrence counts. Also, are widths measured in pixels or characters? The revised comments below provide additional details:

//  Position in this buffer of the first object that hasn't

//  been returned to the client.

uint32_t offset;

//  Holds statistics about line lengths of the form 

//  where length is the number of characters in a line (including

//  the newline), and count is the number of lines with

//  exactly that many characters. If there are no lines with

Page 107 
//  a particular length, then there is no entry for that length.

private TreeMap numLinesWithLength;

▪ When documenting a variable, think nouns, not verbs. In other words, focus on what the variable represents, not how it is manipulated.

▪ The second way in which comments can augment code is by providing intuition. These comments are written at a higher level than the code. They omit details and help the reader to understand the overall intent and structure of the code. This approach is commonly used for comments inside methods, and for interface comments.

▪ The comment is too low-level and detailed. On the one hand, it partially repeats the code: “if there is a LOADING readRPC” just duplicates the test readRpc[i].status == LOADING. On the other hand, the comment doesn’t explain the overall purpose of this code, or how it fits into the method that contains it. As a result, the comment doesn’t help the reader to understand the code.

▪ This comment doesn’t contain any details; instead, it describes the code’s overall function at a higher level. With this high-level information, a reader can explain almost everything that happens in the code:

▪ Furthermore, the new comment provides a basis for readers to judge the code: does it do everything that is needed to add the key hash to an existing RPC? The original comment didn’t describe the overall intent of the code, so it’s hard for a reader to decide whether the code is behaving correctly.

▪ Higher-level comments are more difficult to write than lower-level comments because you must think about the code in a different way. Ask yourself: What is this code trying to do? What is the simplest thing you can say that explains everything in the code? What is the most important thing about this code?

▪ Engineers tend to be very detail-oriented. We love details and are good at managing lots of them; this is essential for being a good engineer. But, great software designers can also step back from the details and think about a system at a higher level. This means deciding which aspects of the system are most important, and being able to ignore the low-level details and think about the system only in terms of its most 

Page 109 
fundamental characteristics. This is the essence of abstraction (finding a simple way to think about a complex entity), and it’s also what you must do when writing higher-level comments.

▪ A good higher-level comment expresses one or a few simple ideas that provide a conceptual framework, such as “append to an existing RPC.” Given the framework, it becomes easy to see how specific code statements relate to the overall goal.

▪ Here is another code sample, which has a good higher-level comment:

▪ The first sentence is different: it explains (in high level terms) why the code is executed. Comments of the form “how we get here” are very useful for helping people to understand code. For example, when documenting a method, it can be very helpful to describe the conditions under which the method is most likely to be invoked (especially if the method is only invoked in unusual situations).

▪ One of the most important roles for comments is to define abstractions

▪ Recall from Chapter 4 that an abstraction is a simplified view of an entity, which preserves essential information but omits details that can safely be ignored.

▪ Code isn’t suitable for describing abstractions; it’s too low level and it includes implementation details that 

Page 110 
shouldn’t be visible in the abstraction. The only way to describe an abstraction is with comments.

▪ If you want code that presents good abstractions, you must document those abstractions with comments.

▪ The first step in documenting abstractions is to separate interface comments from implementation comments

▪ If interface comments must also describe the implementation, then the class or method is shallow

▪ This means that the act of writing comments can provide clues about the quality of a design; Chapter 15 will return to this idea.

▪ The interface comment for a class provides a high-level description of the abstraction provided by the class

▪ Finally, the comments describe the limitations of the class (it does not support concurrent access from multiple threads), which may be important to developers contemplating whether to use it.

▪ The comment usually starts with a sentence or two describing the behavior of the method as perceived by callers; this is the higher-level abstraction.

▪ The comment must describe each argument and the return value (if any). These comments must be very precise, and must describe any constraints on argument values as well as dependencies between arguments.

▪ If the method has any side effects, these must be documented in the interface 

Page 111 
comment.

▪ A side effect is any consequence of the method that affects the future behavior of the system but is not part of the result. For example, if the method adds a value to an internal data structure, which can be retrieved by future method calls, this is a side effect; writing to the file system is also a side effect.

▪ A method’s interface comment must describe any exceptions that can emanate from the method.

▪ If there are any preconditions that must be satisfied before a method is invoked, these must be described (perhaps some other method must be invoked first; for a binary search method, the list being searched must be sorted). It is a good idea to minimize preconditions, but any that remain must be documented.

▪ The developer should not need to read the body of the 

Page 112 
method in order to invoke it, and the interface comment provides no information about how the method is implemented, such as how it scans its internal data structures to find the desired data.

▪ Most of the first paragraph concerns the implementation, not the interface. As one example, users don’t need to know the names of the particular remote procedure calls used to communicate with the servers. The configuration parameters referred to in the second half of the first paragraph are all private variables that are relevant only to the maintainer of the class, not to its users.

▪ The main goal of implementation comments is to help readers understand what the code is doing (not how it does it).

▪ Once readers know what the code is trying to do, it’s usually easy to understand how the code works

▪ In addition to describing what the code is doing, implementation comments are also useful to explain why. If there are tricky aspects to the code that won’t be obvious from reading it, you should document them.

▪ In a perfect world, every important design decision would be encapsulated within a single class. Unfortunately, real systems inevitably end up with design decisions that affect multiple classes. For example, the design of a network protocol will affect both the sender and the receiver, and these may be implemented in different places. Cross-module decisions are often complex and subtle, and they account for many bugs, so good documentation for them is crucial.

▪ None of the pieces of code is an obvious central place to put documentation. One possibility is to duplicate parts of the documentation in each location that depends on it. However, this is awkward, and it is difficult to keep such documentation up to date as the system evolves. Alternatively, the documentation can be located in one of the places where it is needed, but in this case it’s unlikely that developers will see the documentation or know where to look for it.

▪ Then, in any piece of code that relates to one of these issues there is a short comment referring to the designNotes file:

// See "Zombies" in designNotes.

With this approach, there is only a single copy of the documentation and it is relatively easy for developers to find it when they need it. However, this has the disadvantage that the documentation is not near any of the pieces of code that depend on it, so it may be difficult to keep up-to-date as the system evolves.

▪ Some of this information can be represented in the code in a way that will already be obvious to readers, but there is a significant amount of information that can’t easily be deduced from the code. Comments fill in this information.

▪ When following the rule that comments should describe things that aren’t obvious from the code, “obvious” is from the perspective of someone reading your code for the first time (not you).

▪ If your code is undergoing review and a reviewer tells you that something is not obvious, don’t argue with them; if a reader thinks it’s not obvious, then it’s not obvious. Instead of arguing, try to understand what they found confusing and see if you can clarify that, either with better comments or better code.

▪ Selecting names for variables, methods, and other entities is one of the most underrated aspects of software design

▪ Good names are a form of documentation: they make code easier to understand. They reduce the need for other documentation and make it easier to detect errors. Conversely, poor name choices increase the complexity of code and create ambiguities and misunderstandings that can result in bugs.

▪ If different variable names had been used for the different kinds of blocks, such as fileBlock and diskBlock, it’s unlikely that the error would have happened; the programmer would have known that fileBlock couldn’t be used in that situation.

▪ When choosing a name, the goal is to create an image in the mind of the reader about the nature of the thing being named. A good name conveys a lot of information about what the underlying entity is, and, just as important, what it is not. When considering a particular name, ask yourself: “If someone sees this name in isolation, without seeing its declaration, its documentation, or any code that uses the name, how closely will they be able to guess what the name refers to? Is there some other name that will paint a clearer picture?”

▪ Of course, there is a limit to how much information you can put in a single name; names become unwieldy if they contain more than two or three words. Thus, the challenge is to find just a few words that capture the most important aspects of the entity.

▪ Names are a form of abstraction: they provide a simplified way of thinking about a more complex underlying entity. Like other forms of abstraction, the best names are those that focus attention on what is most important about the underlying entity while omitting details that are less important.

▪ Good names have two properties: precision and consistency

▪ The name cursorVisible conveys more information; for example, it allows readers to guess what a true value means (as a general rule, names of boolean variables should always be predicates). The word “blink” is no longer in the name, so readers will have to consult the documentation if they want to know why the cursor isn’t always visible; this information is less important.

▪ Like all rules, the rule about choosing precise names has a few exceptions.

▪ For example, it’s fine to use generic names like i and j as loop iteration variables, as long 

Page 125 
as the loops only span a few lines of code.

▪ If you can see the entire range of usage of a variable, then the meaning of the variable will probably be obvious from the code so you don’t need a long name.

▪ It’s clear from this code that i is being used to iterate over each of the lines in some entity. If the loop gets so long that you can’t see it all at once, or if the meaning of the iteration variable is harder to figure out from the code, then a more descriptive name is in order.

▪ It’s also possible for a name to be too specific, such as in this declaration for a method that deletes a range of text:

void delete(Range selection) {...}

The argument name selection is too specific, since it suggests that the text being deleted is always selected in the user interface. However, this method can be invoked on any range of text, selected or not. Thus, the argument name should be more generic, such as range.

▪ If you find it difficult to come up with a name for a particular variable that is precise, intuitive, and not too long, this is a red flag. It suggests that the variable may not have a clear definition or purpose. When this happens, consider alternative factorings.

▪ If it’s hard to find a simple name for a variable or method that creates a clear image of the underlying object, that’s a hint that the underlying object may not have a clean design.

▪ The second important property of good names is consistency. In any program there are certain variables that are used over and over again

▪ Consistent naming reduces cognitive load in much the same way as reusing a common class: once the reader has seen the name in one context, they can reuse their knowledge and instantly make assumptions when they see the name in a different context.

▪ Consistency has three requirements: first, always use the common name for the given purpose; second, never use the common name for anything other than the given purpose; third, make sure that the purpose is narrow enough that all variables with the name have the same behavior.

▪ This third requirement was violated in the file system bug at the beginning of the chapter. The file system used block for variables with two different behaviors (file blocks and disk blocks); this led to a false assumption about the meaning of a variable, which in turn resulted in a bug.

▪ Sometimes you will need multiple variables that refer to the same general sort of thing. For example, a method that copies file data will need two block numbers, one for the source and one for the destination. When this happens, use the common name for each variable but add a distinguishing prefix, such as srcFileBlock and dstFileBlock.

▪ Not everyone shares my views about naming.

▪ Some of the developers of the Go language argue that names should be very short, often only a single character. In a presentation on name choice for Go, Andrew Gerrand states that “long names obscure what the code does.”1

▪ He presents this code sample, which uses single-letter variable names:

Page 127 
func RuneCount(b []byte) int {

       i, n := 0, 0

       for i < len(b) {

             if b[i] < RuneSelf {

                   i++

             } else {

                   _, size := DecodeRune(b[i:])

                   i += size

             }

             n++

       }

       return n

}

and argues that it is more readable than the following version, which uses longer names:

func RuneCount(buffer []byte) int {

       index, count := 0, 0

       for index < len(buffer) {

             if buffer[index] < RuneSelf {

                   index++

             } else {

                   _, size := DecodeRune(buffer[index:])

                   index += size

             }

             count++

       }

       return count

}

▪ Personally, I don’t find the second version any more difficult to read than the first. If anything, the name count gives a slightly better clue to the behavior of the variable than n. With the first version I ended up reading through the code trying to figure out what n means, whereas I didn’t feel that need with the second version.

▪ But, if n is used consistently throughout the system to refer to counts (and nothing else), then the short name will probably be clear to other developers.

▪ The Go culture encourages the use of the same short name for multiple different things: ch for character or channel, d for data, difference, or distance, and so on.

▪ To me, ambiguous names like these are likely to result in confusion and error, just as in the block example.

▪ Overall, I would argue that readability must be determined by readers, not writers. If you write code with short variable names and the people who read it find it easy to 

Page 128 
understand, then that’s fine. If you start getting complaints that your code is cryptic, then you should consider using longer names (a Web search for “go language short names” will identify several such complaints).

▪ Similarly, if I start getting complaints that long variable names make my code harder to read, then I’ll consider using shorter ones.

▪ Gerrand makes one comment that I agree with: “The greater the distance between a name’s declaration and its uses, the longer the name should be.”

▪ Developing a skill for naming is also an investment. When you first decide to stop settling for mediocre names, you may find it frustrating and time-consuming to come up with good names. However, as you get more experience you’ll find that it becomes easier; eventually, you’ll get to the point where it takes almost no extra time to choose good names, so you will get the benefits almost for free.

▪ Many developers put off writing documentation until the end of the development process, after coding and unit testing are complete. This is one of the surest ways to produce poor quality documentation.

▪ The best time to write comments is at the beginning of the process, as you write the code. Writing the comments first makes documentation part of the design process. Not only does this produce better documentation, but it also produces better designs and it makes the process of writing documentation more enjoyable.

▪ Almost every developer I have ever met puts off writing comments

▪ When asked why they don’t write documentation earlier, they say that the code is still changing. If they write documentation early, they say, they’ll have to rewrite it when the code changes; better to wait until the code stabilizes. However, I suspect that there is also another reason, which is that they view documentation as drudge work; thus, they put it off as long as possible.

▪ Unfortunately, this approach has several negative consequences. First, delaying documentation often means that it never gets written at all. Once you start delaying, it’s easy to delay a bit more; after all, the code will be even more stable in a few more weeks. By the time the code has inarguably stabilized, there is a lot of it, which means the task of writing documentation has become huge and even less attractive.

▪ There’s never a convenient time to stop for a few days and fill in all of the missing comments, 

Page 130 
and it’s easy to rationalize that the best thing for the project is to move on and fix bugs or write the next new feature. This will create even more undocumented code.

▪ Even if you do have the self-discipline to go back and write the comments (and don’t fool yourself: you probably don’t), the comments won’t be very good. By this time in the process, you have checked out mentally. In your mind, this piece of code is done; you are eager to move on to your next project. You know that writing comments is the right thing to do, but it’s no fun. You just want to get through it as quickly as possible.

▪ By now, it’s been a while since you designed the code, so your memories of the design process are becoming fuzzy. You look at the code as you are writing the comments, so the comments repeat the code. Even if you try to reconstruct the design ideas that aren’t obvious from the code, there will be things you don’t remember. Thus, the comments are missing some of the most important things they should describe.

▪ I use a different approach to writing comments, where I write the comments at the very beginning

▪ For a new class, I start by writing the class interface comment.

▪ Next, I write interface comments and signatures for the most important public methods, but I leave the method bodies empty.

▪ While writing method bodies, I usually discover the need for additional methods and instance variables. For each new method I write the interface comment before the body of the method; for instance variables I fill in the comment at the same time that I write the variable declaration.

▪ When the code is done, the comments are also done. There is never a backlog of unwritten comments.

▪ The comments-first approach has three benefits. First, it produces better comments. If you write the comments as you are designing the class, the key design issues will be fresh in your mind, so it’s easy to record them. It’s better to write the interface 

Page 131 
comment for each method before its body, so you can focus on the method’s abstraction and interface without being distracted by its implementation.

▪ During the coding and testing process you will notice and fix problems with the comments. As a result, the comments improve over the course of development.

▪ Comments are a design tool

The second, and most important, benefit of writing the comments at the beginning is that it improves the system design. Comments provide the only way to fully capture abstractions, and good abstractions are fundamental to good system design.

▪ If you write comments describing the abstractions at the beginning, you can review and tune them before writing implementation code.

▪ To write a good comment, you must identify the essence of a variable or piece of code: what are the most important aspects of this thing? It’s important to do this early in the design process; otherwise you are just hacking code.

▪ Comments serve as a canary in the coal mine of complexity.

▪ If a method or variable requires a long comment, it is a red flag that you don’t have a good abstraction.

▪ Remember from Chapter 4 that classes should be deep: the best classes have very simple interfaces yet implement powerful functions

▪ The best way to judge the complexity of an interface is from the comments that describe it. If the interface comment for a method provides all the information needed to use the method and is also short and simple, that indicates that the method has a simple interface. Conversely, if there’s no way to describe a method completely without a long and complicated comment, then the method has a complex interface.

▪ You can compare a method’s interface comment with the implementation to get a sense of how deep the method is: if the interface comment must describe all the major features of the implementation, then the method 

Page 132 
is shallow.

▪ The same idea applies to variables: if it takes a long comment to fully describe a variable, it’s a red flag that suggests you may not have chosen the right variable decomposition.

▪ Overall, the act of writing comments allows you to evaluate your design decisions early, so you can discover and fix problems.

▪ The comment that describes a method or variable should be simple and yet complete. If you find it difficult to write such a comment, that’s an indicator that there may be a problem with the design of the thing you are describing.

▪ Of course, comments are only a good indicator of complexity if they are complete and clear. If you write a method interface comment that doesn’t provide all the information needed to invoke the method, or one that is so cryptic that it’s hard to understand, then that comment doesn’t provide a good measure of the method’s depth.

▪ The third and final benefit of writing comments early is that it makes comment-writing more fun. For me, one of the most enjoyable parts of programming is the early design phase for a new class, where I’m fleshing out the abstractions and structure for the class. Most of my comments are written during this phase, and the comments are how I record and test the quality of my design decisions. I’m looking for the design that can be expressed completely and clearly in the fewest words.

▪ The simpler the comments, the better I feel about my design, so finding simple comments is a source of pride.

▪ If you are programming strategically, where your main goal is a great design rather than just writing code that works, then writing comments should be fun, since that’s how you identify the best designs.

▪ Now let’s revisit the argument for delaying comments, which is that it avoids the cost of reworking the comments as the code evolves. A simple back-of-the-envelope calculation will show that this doesn’t save much. First, estimate the total fraction of development time that you spend typing in code and comments together, including time to revise code and comments; it’s unlikely that this will be more than about 10% of all development time.

▪ Even if half of your total code lines are comments, writing comments probably doesn’t account for more than about 5% of your total development time. Delaying the comments until the end will save only a fraction of this, which isn’t very much.

▪ If you haven’t ever tried writing the comments first, give it a try. Stick with it long enough to get used to it. Then think about how it affects the quality of your comments, the quality of your design, and your overall enjoyment of software development. After you have tried this for a while, let me know whether your experience matches mine, and why or why not.

▪ A large software system develops through a series of evolutionary stages, where each stage adds new capabilities and modifies existing modules. This means that a system’s design is constantly evolving. It isn’t possible to conceive the right design for a system at the outset; the design of a mature system is determined more by changes made during the system’s evolution than by any initial conception.

▪ Previous chapters described how to squeeze out complexity during the initial design and implementation; this chapter discusses how to keep complexity from creeping in as the system evolves.

▪ Ideally, when you have finished with each change, the system will have the structure it would have had if you had designed it from the start with that change in mind.

▪ Whenever you modify any code, try to find a way to improve the system design at least a little bit in the process. If you’re not making the design better, you are probably making it worse

▪ an investment mindset sometimes conflicts with the realities of commercial software development. If refactoring the system “the right way” would take three months but a quick and dirty fix would take only two hours, you may have to take the quick and dirty approach, particularly if you are working against a tight deadline. Or, if refactoring the system would create incompatibilities that affect many other people and teams, then the refactoring may not be practical.

▪ When you change existing code, there’s a good chance that the changes will invalidate some of the existing comments

▪ It’s easy to forget to update comments when you modify code, which results in comments that are no longer accurate. Inaccurate comments are frustrating to readers, and if there are very many of them, readers begin to distrust all of the comments.

▪ Fortunately, with a little discipline and a couple of guiding rules, it’s possible to keep comments up-to-date without a huge effort.

▪ The best way to ensure that comments get updated is to position them close to the code they describe, so developers will see them when they change the code. The farther a comment is from its associated code, the less likely it is that it will be updated properly.

▪ However, users should not need to read either code or header files; they should get their information from documentation compiled by tools such as Doxygen or Javadoc. In addition, many IDEs will extract and present documentation to users, such as by displaying a method’s documentation when the method’s name is typed. Given tools such as these, the documentation should be located in the place that is most convenient for developers working on the code.

▪ In general, the farther a comment is from the code it describes, the more abstract it should be (this reduces the likelihood that the comment will be invalidated by code changes).

▪ A common mistake when modifying code is to put detailed information about the change in the commit message for the source code repository, but then not to document it in the code. Although commit messages can be browsed in the future by scanning the repository’s log, a developer who needs the information is unlikely to think of scanning the repository log. Even if they do scan the log, it will be tedious to find the right log message.

▪ An example is a commit message describing a subtle problem that motivated a code change. If this isn’t documented in the code, then a developer might come along later and undo the change without realizing that they have re-created a bug. If you want to include a copy of this information in the commit message as well, that’s fine, but the most important thing is to get it in the code.

▪ This illustrates the principle of placing documentation in the place where developers are most likely to see it; the commit log is rarely that place.

▪ The second technique for keeping comments up to date is to avoid duplication

▪ If documentation is duplicated, it is more difficult for developers to find and update all of the relevant copies. Instead, try to document each design decision exactly once.

▪ If there are multiple places in the code that are affected by a particular decision, don’t repeat the documentation at each of these points. Instead, find the most obvious single place to put the documentation.

▪ In addition, add short comments in the other places that refer to the central location: “See the comment in xyz for an explanation of the code below.”

▪ If information is already documented someplace outside your program, don’t repeat the documentation inside the program; just reference the external documentation.

▪ For example, if you write a class that implements the HTTP protocol, there’s no need for you to describe the HTTP protocol inside your code. There are already numerous sources for this documentation on the Web; just add a short comment to your code with a URL for one of these sources.

▪ One good way to make sure documentation stays up to date is to take a few minutes before committing a change to your revision control system to scan over all the changes for that commit; make sure that each change is properly reflected in the documentation.

▪ One final thought on maintaining documentation: comments are easier to maintain if they are higher-level and more abstract than the code.

▪ Consistency is a powerful tool for reducing the complexity of a system and making its behavior more obvious.

▪ Consistency creates cognitive leverage: once you have learned how something is done in one place, you can use that knowledge to immediately understand other places that use the same approach.

▪ If a system is not implemented in a consistent fashion, developers must learn about each situation separately. This will take more time.

▪ If a system is not consistent, two situations may appear the same when in fact they are different. A developer may see a pattern that looks familiar and make incorrect assumptions based on previous encounters with that pattern.

▪ Coding style. It is common nowadays for development organizations to have style guides that restrict program structure beyond the rules enforced by compilers. Modern style guides address a range of issues, such as indentation, curly-brace placement, order of declarations, naming, commenting, and restrictions on language features considered 

Page 142 
dangerous. Style guidelines make code easier to read and can reduce some kinds of errors.

▪ Interfaces. An interface with multiple implementations is another example of consistency. Once you understand one implementation of the interface, any other implementation becomes easier to understand because you already know the features it will have to provide.

▪ Design patterns. Design patterns are generally-accepted solutions to certain common problems, such as the model-view-controller approach to user interface design.

▪ Invariants. An invariant is a property of a variable or structure that is always true. For example, a data structure storing lines of text might enforce an invariant that each line is terminated by a newline character.

▪ Invariants reduce the number of special cases that must be considered in code and make it easier to reason about the code’s behavior.

▪ Consistency is hard to maintain, especially when many people work on a project over a long time.

▪ Document. Create a document that lists the most important overall conventions, such as coding style guidelines. Place the document in a spot where developers are likely to see it, such as a conspicuous place on the project Wiki. Encourage new people joining the group to read the document, and encourage existing people to review it every once in a while.

▪ If you don’t write the conventions down, it’s unlikely that other people will follow them.

▪ Enforce. Even with good documentation, it’s hard for developers to remember all of the conventions. The best way to enforce conventions is to write a tool that checks 

Page 143 
for violations, and make sure that code cannot be committed to the repository unless it passes the checker.

▪ Code reviews provide another opportunity for enforcing conventions and for educating new developers about the conventions

▪ The most important convention of all is that every developer should follow the old adage “When in Rome, do as the Romans do.” When working in a new file, look around to see how the existing code is structured. Are all public variables and methods declared before private ones? Are the methods in alphabetical order? Do variables use “camel case,” as in firstServerName, or “snake case,” as in first_server_name? When you see anything that looks like it might possibly be a convention, follow it.

▪ Don’t change existing conventions. Resist the urge to “improve” on existing conventions. Having a “better idea” is not a sufficient excuse to introduce inconsistencies.

▪ Your new idea may indeed be better, but the value of consistency over inconsistency is almost always greater than the value of one approach over another.

▪ Consistency means not only that similar things should be done in similar ways, but that dissimilar things should be done in different ways

▪ If you become overzealous about consistency and try to force dissimilar things into the same approach, such as by using the same variable name for things that are really different or using an existing design pattern for a task that doesn’t fit the pattern, you’ll create complexity and confusion.

▪ Consistency only provides benefits when developers have confidence that “if it looks like an x, it really is an x.”

▪ Obscurity occurs when important information about a system is not obvious to new developers.

▪ If code is obvious, it means that someone can read the code quickly, without much thought, and their first guesses about the behavior or meaning of the code will be correct

▪ Obvious code needs fewer comments than nonobvious code.

▪ “Obvious” is in the mind of the reader: it’s easier to notice that someone else’s code is nonobvious than to see problems with your own code. Thus, the best way to determine the obviousness of code is through code reviews. If someone reading your code says it’s not obvious, then it’s not obvious, no matter how clear it may seem to you

▪ Comments. Sometimes it isn’t possible to avoid code that is nonobvious. When this happens, it’s important to use comments to compensate by providing the missing information. To do this well, you must put yourself in the position of the reader and figure out what is likely to confuse them, and what information will clear up that confusion.

▪ Event-driven programming. In event-driven programming, an application responds to external occurrences, such as the arrival of a network packet or the press of a mouse button.

▪ One module is responsible for reporting incoming events. Other parts of the application register interest in certain events by asking the event module to invoke a given function or method when those events occur.

▪ Event-driven programming makes it hard to follow the flow of control. The event handler functions are never invoked directly; they are invoked indirectly by the event module, typically using a function pointer or interface. Even if you find the point of invocation in the event module, it still isn’t possible to tell which specific function will be invoked: this will depend on which handlers were registered at runtime.

▪ Because of this, it’s hard to reason about event-driven code or convince yourself that it works.

▪ This example illustrates a general rule: software should be designed for ease of reading, not ease of writing.

▪ Generic containers are expedient for the person writing the code, but they create confusion for all the readers that follow.

▪ It’s better for the person writing the code to spend a few extra minutes to define a specific container structure, so that the resulting code is more obvious.

▪ If code is nonobvious, that usually means there is important information about the code that the reader does not have: in the RaftClient example, the reader might not know that the RaftClient constructor created new threads; in the Pair example, the reader might not know that result.getKey() returns the number of the current term.

▪ To make code obvious, you must ensure that readers always have the information they need to understand it. You can do this in three ways.

▪ The best way is to reduce the amount of information that is needed, using design techniques such as abstraction and eliminating special cases.

▪ Second, you can take advantage of information that readers have already acquired in other contexts (for example, by following conventions and conforming to expectations) so readers don’t have to learn new information for your code.

▪ Third, you can present the important information to them in the code, using techniques such as good names and strategic comments.

▪ Object-oriented programming is one of the most important new ideas in software development over the last 30–40 years

▪ Interface inheritance provides leverage against complexity by reusing the same interface for multiple purposes. It allows knowledge acquired in solving one problem 

Page 152 
(such as how to use an I/O interface to read and write disk files) to be used to solve other problems (such as communicating over a network socket).

▪ In order for an interface to have many implementations, it must capture the essential features of all the underlying implementations while steering clear of the details that differ between the implementations; this notion is at the heart of abstraction.

▪ The second form of inheritance is implementation inheritance. In this form, a parent class defines not only signatures for one or more methods, but also default implementations. Subclasses can choose to inherit the parent’s implementation of a method or override it by defining a new method with the same signature.

▪ However, implementation inheritance creates dependencies between the parent class and each of its subclasses. Class instance variables in the parent class are often accessed by both the parent and child classes; this results in information leakage between the classes in the inheritance hierarchy and makes it hard to modify one class in the hierarchy without looking at the others.

▪ In the worst case, programmers will need complete knowledge of the entire class hierarchy underneath the parent class in order to make changes to any of the classes.

▪ Class hierarchies that use implementation inheritance extensively tend to have high complexity.

▪ Thus, implementation inheritance should be used with caution. Before using implementation inheritance, consider whether an approach based on composition can provide the same benefits.

▪ If there is no viable alternative to implementation inheritance, try to separate the state managed by the parent class from that managed by subclasses.

▪ Although the mechanisms provided by object-oriented programming can assist in implementing clean designs, they do not, by themselves, guarantee good design. For example, if classes are shallow, or have complex interfaces, or permit external access to their internal state, then they will still result in high complexity.

▪ Agile development is an approach to software development that emerged in the late 1990’s from a collection of ideas about how to make software development more lightweight, flexible, and incremental; it was formally defined during a meeting of practitioners in 2001.

▪ As mentioned in Chapter 1, it isn’t possible to visualize a complex system well enough at the outset of a project to determine the best design. The best way to end up with a good design is to develop a system in increments, where each increment adds a few new abstractions and refactors existing abstractions based on experience. This is similar to the agile development approach.

▪ One of the risks of agile development is that it can lead to tactical programming. Agile development tends to focus developers on features, not abstractions, and it encourages developers to put off design decisions in order to produce working software as soon as possible.

▪ However, one of the tenets of agile development is that testing should be tightly integrated with development, and programmers should write tests for their own code. This practice has now become widespread.

▪ Tests, particularly unit tests, play an important role in software design because they facilitate refactoring. Without a test suite, it’s dangerous to make major structural changes to a system.

▪ Test-driven development is an approach to software development where programmers write unit tests before they write code

▪ A design pattern is a commonly used approach for solving a particular kind of problem, such as an iterator or an observer.

▪ The notion of design patterns was popularized by the book Design Patterns: Elements of Reusable Object-Oriented Software by Gamma, Helm, Johnson, and Vlissides, and design patterns are now widely used in object-oriented software development.

▪ Design patterns represent an alternative to design: rather than designing a new mechanism from scratch, just apply a well-known design pattern. For the most part, this is good: design patterns arose because they solve common problems, and because they are generally agreed to provide clean solutions.

▪ The greatest risk with design patterns is over-application. Not every problem can be solved cleanly with an existing design pattern; don’t try to force a problem into a design pattern when a custom approach will be cleaner.

▪ Using design patterns doesn’t automatically improve a software system; it only does so if the design patterns fit. As with many ideas in software design, the notion that design patterns are good doesn’t necessarily mean that more design patterns are better.

▪ The first question to address is “how much should you worry about performance during the normal development process?” If you try to optimize every statement for maximum speed, it will slow down development and create a lot of unnecessary complexity. Furthermore, many of the “optimizations” won’t actually help performance. On the other hand, if you completely ignore performance issues, it’s easy to end up with a large number of significant inefficiencies spread throughout the code; the resulting system can easily be 5–10x slower than it needs to be. In this “death by a thousand cuts” scenario it’s hard to come back later and improve the performance, because there is no single improvement that will have much impact.

▪ The best approach is something between these extremes, where you use basic knowledge of performance to choose design alternatives that are “naturally efficient” yet also clean and simple

▪ The key is to develop an awareness of which operations are fundamentally expensive.

▪ Once you have a general sense for what is expensive and what is cheap, you can use that information to choose cheap operations whenever possible. In many cases, a more efficient approach will be just as simple as a slower approach.

▪ If the only way to improve efficiency is by adding complexity, then the choice is more difficult. If the more efficient design adds only a small amount of complexity, and if the complexity is hidden, so it doesn’t affect any interfaces, then it may be 

Page 161 
worthwhile (but beware: complexity is incremental). If the faster design adds a lot of implementation complexity, or if it results in more complicated interfaces, then it may be better to start off with the simpler approach and optimize later if performance turns out to be a problem.

▪ However, if you have clear evidence that performance will be important in a particular situation, then you might as well implement the faster approach immediately.

▪ It’s tempting to rush off and start making performance tweaks, based on your intuitions about what is slow. Don’t do this! Programmers’ intuitions about performance are unreliable. This is true even for experienced developers.

▪ Dealing with complexity is the most important challenge in software design. It is what makes systems hard to build and maintain, and it often makes them slow as well.

▪ The downside of all these suggestions is that they create extra work in the early stages of a project.

▪ Furthermore, if you aren’t used to thinking about design issues, then you will slow down even more while you learn good design techniques.

▪ If the only thing that matters to you is making your current code work as soon as possible, then thinking about design will seem like drudge work that is getting in the way of your real goal.

▪ The time you spent honing your design skills will also pay for itself: as your skills and experience grow, you will find that you can produce good designs more and more quickly. Good design doesn’t really take much longer than quick-and-dirty design, once you know how.

▪ The reward for being a good designer is that you get to spend a larger fraction of your time in the design phase, which is fun. Poor designers spend most of their time chasing bugs in complicated and brittle code. If you improve your design skills, not only will you produce higher quality software more quickly, but the software development process will be more enjoyable.
