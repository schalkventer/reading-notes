Composing Software: An Exploration of Functional Programming and Object Composition in JavaScript (2018)

Eric Elliot

---

▪ Composition: “The act of combining parts or elements to form a whole.” ~ Dictionary.com

▪ “the act of breaking a complex problem down into smaller problems, and composing simple solutions to form a complete solution to the complex problem.”

▪ One of my biggest regrets in life is that I failed to understand the significance of that lesson early on. I learned the essence of software design far too late in life.

▪ I have interviewed hundreds of developers. What I’ve learned from those sessions is that I’m not alone. Very few working software developers have a good grasp on the essence of software development.

▪ 100% have struggled to answer one or both of the most important questions in the field of software development:

▪ What is function composition?
What is object composition?

▪ The problem is that you can’t avoid composition just because you’re not aware of it. You still do it – but you do it badly

▪ We spend more time maintaining software than we do creating it from scratch, and our bugs impact billions of people all over the world.

▪ The entire world runs on software today. Every new car is a mini super-computer on wheels, and problems with software design cause real accidents and cost real human lives.

▪ In 2013, a jury found Toyota’s software development team guilty of “reckless disregard” after an accident investigation revealed spaghetti code with 10,000 global variables.

▪ We must do better.

▪ If you’re a software developer, you compose functions and data structures every day, whether you know it or not. You can do it consciously (and better), or you can do it accidentally, with duct-tape and crazy glue.

▪ The process of software development is breaking down large problems into smaller problems, building components that solve those smaller problems, then composing those components together to form a complete application.

▪ Function composition is the process of applying a function to the output of another function

▪ It’s commonly pronounced “composed with” or “after”. You can say that out-loud as “f composed with g equals f of g of x”, or “f after g equals f of g of x”. We say f after g because g is evaluated first, then its output is passed as an argument to f.

▪ Every time you write code like this, you’re composing functions:

1 const g = n => n + 1;
2 const f = n => n * 2;
3 
4 const doStuff = x => {
5 const afterG = g(x);
6 const afterF = f(afterG);
7 return afterF;
8 };
9 
10 doStuff(20); // 42

▪ Every time you write a promise chain, you’re composing functions:

▪ wait(300)
12 .then(() => 20)
13 .then(g)
14 .then(f)
15 .then(value => console.log(value)) // 42

▪ Likewise, every time you chain array method calls, lodash methods, observables (RxJS, etc…) you’re composing functions

▪ If you’re chaining, you’re composing. If you’re passing return values into other functions, you’re composing. If you call two methods in a sequence, you’re composing using this as input data.

▪ When you compose functions intentionally, you’ll do it better.

▪ Composing functions intentionally, we can improve our doStuff() function to a simple one-liner:

1 const g = n => n + 1;
2 const f = n => n * 2;
3 
4 const doStuffBetter = x => f(g(x));
5 
6 doStuffBetter(20); // 42

▪ A common objection to this form is that it’s harder to debug.

▪ First, let’s abstract that “after f”, “after g” logging into a little utility called trace():

▪ 1 const trace = label => value => {
2 console.log(`${ label }: ${ value }`);
3 return value;
4 };

▪ Now we can use it like this:

1 const doStuff = x => {
2 const afterG = g(x);
3 trace('after g')(afterG);
4 const afterF = f(afterG);
5 trace('after f')(afterF);
6 return afterF;
7 };

▪ Popular functional programming libraries like Lodash and Ramda include utilities to make function composition easier

▪ You can rewrite the above function like this:

1 import pipe from 'lodash/fp/flow';
2 
3 const doStuffBetter = pipe(
4 g,
5 trace('after g'),
6 f,
7 trace('after f')
8 );

▪ If you want to try this code without importing something, you can define pipe like this:

1 // pipe(...fns: [...Function]) => x => y
2 const pipe = (...fns) => x => fns.reduce((y, f) => f(y), x);

▪ pipe() creates a pipeline of functions, passing the output of one function to the input of another. When you use pipe() (and its twin, compose()) You don’t need intermediary variables. Writing functions without mention of the arguments is called “point-free style”.

▪ Point-free style can be taken too far, but a little bit here and there is great because those intermediary variables add unnecessary complexity to your functions.

▪ The average human has only a few shared resources for discrete quanta in working memory, and each variable potentially consumes one of those quanta. As you add more variables, our ability to accurately recall the meaning of each variable is diminished. Working memory models typically involve 4-7 discrete quanta. Above those numbers, error rates dramatically increase.

▪ Software developers tend to be better at chunking data into working memory than the average person, but not so much more as to weaken the importance of conservation.

▪ Code is the same way. More concise code expression leads to enhanced comprehension. Some code gives us useful information, and some code just takes up space. If you can reduce the amount of code you use without reducing the meaning that gets transmitted, you’ll make the code easier to parse and understand for other people who need to read it.

▪ “Favor object composition over class inheritance” the Gang of Four, “Design Patterns: Elements of Reusable Object Oriented Software”

▪ “In computer science, a composite data type or compound data type is any data type which can be constructed in a program using the programming language’s primitive data types and other composite types. […] The act of constructing a composite type is known as composition.” ~ Wikipedia

▪ Likewise, all Arrays, Sets, Maps, WeakMaps, TypedArrays, etc… are composite datatypes

▪ Any time you build any non-primitive data structure, you’re performing some kind of object composition.

▪ Note that the Gang of Four defines a pattern called the composite pattern which is a specific type of recursive object composition which allows you to treat individual components and aggregated composites identically.

▪ Some developers get confused, thinking that the composite pattern is the only form of object composition. Don’t get confused. There are many different kinds of object composition.

▪ The Gang of Four continues, “you’ll see object composition applied again and again in design patterns”, and then they catalog three kinds of object compositional relationships,

▪ delegation (when an object delegates property access to another object, as used in the state, strategy, and visitor patterns),

▪ acquaintance (when an object knows about another object by reference, usually passed as a parameter: a uses-a relationship, e.g., a network request handler might be passed a reference to a logger to log the request — the request handler uses a logger)

▪ aggregation (when child objects form part of a parent object: a has-a relationship, e.g., DOM children are component elements in a DOM node — A DOM node has children).

▪ Class inheritance can be used to construct composite objects, but it’s a restrictive and brittle way to do it.

▪ When the Gang of Four says “favor object composition over class inheritance”, they’re advising you to use flexible approaches to composite object building, rather than the rigid, tightly-coupled approach of class inheritance.

▪ They’re encouraging you to favor has-a and uses-a relationships over is-a relationships.

▪ Rather than refer to specific design patterns, we’ll use a more general definition of object composition from “Categorical Methods in Computer Science: With Aspects from Topology” (1989):

“Composite objects are formed by putting objects together such that each of the latter is ‘part of’ the former.”

▪ Another good reference is “Reliable Software Through Composite Design”, Glenford J Myers, 1975.

▪ Both books are long out of print, but you can still find sellers on Amazon or eBay if you’d like to explore the subject of object composition in more technical depth and historical context.

▪ Class inheritance is just one kind of composite object construction. All classes produce composite objects, but not all composite objects are produced by classes or class inheritance.

▪ “Favor object composition over class inheritance” means that you should form composite objects from small component parts, rather than inheriting all properties from an ancestor in a class hierarchy.

▪ The latter causes a large variety of well-known problems in object oriented design:

▪ The tight coupling problem: Because child classes are dependent on the implementation of the parent class, class inheritance is the tightest coupling available in object oriented design.

▪ The fragile base class problem: Due to tight coupling, changes to the base class can potentially break a large number of descendant classes – potentially in code managed by third parties. The author could break code they’re not aware of.

▪ The inflexible hierarchy problem: With single ancestor taxonomies, given enough time and evolution, all class taxonomies are eventually wrong for new use-cases.

▪ The duplication by necessity problem: Due to inflexible hierarchies, new use cases are often implemented by duplication, rather than extension, leading to similar classes which are unexpectedly divergent. Once duplication sets in, it’s not obvious which class new classes should descend from, or why.

▪ The gorilla/banana problem: “…the problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.” ~ Joe Armstrong, “Coders at Work”

▪ The most common form of object composition in JavaScript is known as object concatenation (aka, concatenative inheritance: informally, “mixin composition”).

▪ It works like ice-cream. You start with an object (like vanilla ice-cream), and then mix in the features you want. Add some nuts, caramel, chocolate swirl, and you wind up with nutty caramel chocolate swirl ice cream.

▪ Building composites with class inheritance:

1 class Foo {
2 constructor () {
3 this.a = 'a'
4 }
5 }
6 
7 class Bar extends Foo {
8 constructor (options) {
9 super(options);
10 this.b = 'b'
11 }
12 }
13 
14 const myBar = new Bar(); // {a: 'a', b: 'b'}

▪ Building composites with mixin composition:

1 const a = {
2 a: 'a'
3 };
4 
5 const b = {
6 b: 'b'
7 };
8 
9 const c = {...a, ...b}; // {a: 'a', b: 'b'}

▪ For now, your understanding should be:

There’s more than one way to do it.
Some ways are better than others.
You want to select the simplest, most flexible solution for the task at hand.

▪ This isn’t about functional programming (FP) vs object-oriented programming (OOP), or one language vs another. Components can take the form of functions, data structures, classes, etc… Different programming languages tend to afford different atomic elements for components. Java affords objects, Haskell affords functions, etc… But no matter what language and what paradigm you favor, you can’t get away from composing functions and data structures. In the end, that’s what it all boils down to.

▪ We’ll talk a lot about functional programming, because functions are the simplest things to compose in JavaScript, and the functional programming community has invested a lot of time and effort formalizing function composition techniques.

▪ What we won’t do is say that functional programming is better than object-oriented programming, or that you must choose one over the other. OOP vs FP is a false dichotomy. Every real Javascript application I’ve seen in recent years mixes FP and OOP extensively.

▪ We’ll use object composition to produce datatypes for functional programming, and functional programming to produce objects for OOP.

▪ No matter how you write software, you should compose it well. 

The essence of software development is composition.

▪ A software developer who doesn’t understand composition is like a home builder who doesn’t know about bolts or nails. Building software without awareness of composition is like a home builder putting walls together with duct tape and crazy glue.

▪ The trouble is, almost nobody in the industry has a good handle on the essentials. We as an industry have failed you, the software developer. It’s our responsibility as an industry to train developers better. We must improve. We need to take responsibility.

▪ Everything runs on software today, from the economy to medical equipment. There is literally no corner of human life on this planet that is not impacted by the quality of our software. We need to know what we’re doing.

▪ Functional programming is a foundational pillar of JavaScript, and immutability is a foundational pillar of functional programming. You can’t fully understand functional programming without first understanding immutability

▪ “Sometimes, the elegant implementation is just a function. Not a method. Not a class. Not a framework. Just a function.”

▪ If you have a dollar, and I give you another dollar, it does not change the fact that a moment ago you only had one dollar, and now you have two. Mutation attempts to erase history, but history cannot be truly erased. When the past is not preserved, it will come back to haunt you, manifesting as bugs in the program.

▪ Logic is thought. Effects are action. Therefore the wise think before acting, and act only when the thinking is done.

If you try to perform effects and logic at the same time, you may create hidden side effects which cause bugs in the logic. Keep functions small. Do one thing at a time, and do it well.

▪ Plan for composition. Write functions whose outputs will naturally work as inputs to many other functions. Keep function signatures as simple as possible.

▪ Lists and items make great universal abstractions.

▪ When I was about 6 years old, I spent a lot of time playing computer games with my best friend. His family had a room full of computers. To me, they were irresistible. Magic. I spent many hours exploring all the games. One day I asked my friend, “how do we make a game?”

▪ In the beginning of computer science, before most of computer science was actually done on computers, there lived two great mathematicians: Alonzo Church, and Alan Turing. They produced two different, but equivalent universal models of computation

▪ Alonzo Church invented lambda calculus.

▪ Lambda calculus is a universal model of computation based on function application.

▪ Alan Turing is known for the Turing machine. A Turing machine is a universal model of computation that defines a theoretical device that manipulates symbols on a strip of tape.

▪ “A function is effectively calculable if its values can be found by some purely mechanical process.” ~ A.M Turing, “Systems of Logic Based on Ordinals”

▪ In lamda calculus, functions are king. Everything is a function, including numbers

▪ Thinking of functions as the atomic building blocks (the legos from which we construct our creations) is a remarkably expressive and eloquent way to compose software.

▪ There are three important points that make lambda calculus special:

▪ Functions are always anonymous. In JavaScript, the right side of const sum = (x, y) => x + y
is the anonymous function expression (x, y) => x + y
.

▪ Functions in lambda calculus are always unary, meaning they only accept a single parameter. If you need more than one parameter, the function will take one input and return a new function that takes the next, and so on until all the parameters have been collected and the function application can complete.

▪ The n-ary function (x, y) => x + y
can be expressed as a unary function like: x => y => x + y

▪ This transformation from an n-ary function to a series of unary functions is known as currying.

▪ Functions are first-class, meaning that functions can be used as inputs to other functions, and functions can return functions.

▪ Together, these features form a simple, yet expressive vocabulary for composing software using functions as the primary building block.

▪ In JavaScript, anonymous functions and curried functions are optional features. While JavaScript supports important features of lambda calculus, it does not enforce them.

▪ The classic function composition takes the output from one function and uses it as the input for another function. For example, the composition f . g
can be written as:

1 const compose = (f, g) => x => f(g(x));

▪ const compose = (f, g) => x => f(g(x));
2 
3 const double = n => n * 2;
4 const inc = n => n + 1;
5 
6 const transform = compose(double, inc);
7 
8 transform(3); // 8

▪ The compose() function takes the double function as the first argument, the inc function as the second, and returns a function that combines the two. Inside the compose() function when transform() gets invoked, f is double(), g is inc(), and x is 3:

▪ Lambda calculus was hugely influential on software design, and prior to about 1980, many very influential icons of computer science were building software using function composition

▪ Lisp was created in 1958, and was heavily influenced by lambda calculus. Today, Lisp is the second-oldest language that’s still in popular use.

▪ I was introduced to it through AutoLISP: the scripting language used in the most popular Computer Aided Design (CAD) software: AutoCAD. AutoCAD is so popular, virtually every other CAD application supports AutoLISP so that they can be compatible.

▪ Lisp is also a popular teaching language in computer science curriculum for three reasons:

▪ Its simplicity makes it easy to learn the basic syntax and semantics of Lisp in about a day.

▪ Lisp is all about function composition, and function composition is an elegant way to structure applications.

▪ My favorite computer science text uses Lisp: Structure and Interpretation of Computer Programs.

▪ Somewhere between 1970 and 1980, the way that software was composed drifted away from simple algebraic math, and became a list of linear instructions for the computer to follow in languages like K&R C (1978) and the tiny BASIC interpretters that shipped with the early home computers of the 1970s and early 1980s.

▪ In 1972, Alan Kay’s Smalltalk was formalized, and the idea of objects as the atomic unit of composition took hold.

▪ Smalltalk’s great idea about component encapsulation and message passing got distorted in the 80s and 90s by C++ and Java into a horrible idea about inheritance hierarchies and is-a relationships for feature reuse.

▪ Around 2010, something great began to happen: JavaScript exploded.

▪ Before about 2006, JavaScript was widely considered a toy language used to make cute animations happen in web browsers, but it had some powerful features hidden in it.

▪ Namely, the most important features of lambda calculus. People started whispering in the shadows about this cool thing called “functional programming”.

▪ To make it simpler, the JavaScript specification got its first major upgrade of the decade and added the arrow function, which made it easier to create and read functions, currying, and lambda expressions.

▪ Arrow functions were like rocket fuel for the functional programming explosion in JavaScript.

▪ Today it’s rare to see a large application which doesn’t use a lot of functional programming techniques.

▪ Composition is a simple, elegant, and expressive way to clearly model the behavior of software. The process of composing small, deterministic functions to create larger software components and functionality produces software that is easier to organize, understand, debug, extend, test, and maintain.

▪ Clojure, a Lisp dialect, was created by Rich Hickey in 2007 and quickly gained popularity and use at major tech companies including Amazon, Apple, and Facebook.

▪ All that said, as the standard language of the web, JavaScript is the most popular programming language in the world, and JavaScript has exposed an unprecedented number of developers to the functional programming paradigm.

▪ If you’re a seasoned developer already familiar with JavaScript, or a pure functional language, maybe you’re thinking that JavaScript is a funny choice for an exploration of functional programming.

▪ Set those thoughts aside, and try to approach the material with an open mind. You may find that there is another level to JavaScript programming. One you never knew existed.

▪ Since this text is called “Composing Software”, and functional programming is the obvious way to compose software (using function composition, higher order functions, etc…), you may be wondering why I’m not talking about Haskell, ClojureScript, or Elm, instead of JavaScript.

▪ JavaScript has the most important features needed for functional programming:

▪ First class functions: The ability to use functions as data values: pass functions as arguments, return functions, and assign functions to variables and object properties. This property allows for higher order functions, which enable partial application, currying, and composition.

▪ Anonymous functions and concise lambda syntax: x => x * 2
is a valid function expression in JavaScript. Concise lambdas make it easier to work with higher-order functions.

▪ Closures: A closure is the bundling of a function with its lexical environment. Closures are created at function creation time. When a function is defined inside another function, it has access to the variable bindings in the outer function, even after the outer function exits.

▪ Closures are how partial applications get their fixed arguments. A fixed argument is an argument bound in the closure scope of a returned function. In add2(1)(2), 1 is a fixed argument in the function returned by add2(1).

▪ JavaScript is a multi-paradigm language, meaning that it supports programming in many different styles

▪ Other styles supported by JavaScript include procedural (imperative) programming (like C), where functions represent a subroutine of instructions that can be called repeatedly for reuse and organization,

▪ object-oriented programming, where objects – not functions – are the primary building blocks,

▪ and of course, functional programming.

▪ The disadvantage of a multi-paradigm language is that imperative and object-oriented programming tend to imply that almost everything needs to be mutable.

▪ Mutation is a change to data structure that happens in-place

▪ Objects usually need to be mutable so that their properties can be updated by methods. In imperative programming, most data structures are mutable to enable efficient in-place manipulation of objects and arrays.

▪ Purity: In some FP languages, purity is enforced by the language. Expressions with side-effects are not allowed.

▪ Immutability: Some FP languages disable mutations. Instead of mutating an existing data structure, such as an array or object, expressions evaluate to new data structures. This may sound inefficient, but most functional languages use trie data structures under the hood, which feature structural sharing: meaning that the old object and new object share references to the data that is the same.

▪ Recursion: Recursion is the ability for a function to reference itself for the purpose of iteration. In many FP languages, recursion is the only way to iterate. There are no loop statements like for, while, or do loops.

▪ In JavaScript, purity must be achieved by convention.

▪ It’s unfortunately easy in JavaScript to get off track by accidentally creating and using impure functions.

▪ In pure functional languages, immutability is often enforced. JavaScript lacks efficient, immutable trie-based data structures used by most functional languages, but there are libraries that help, including Immutable.js and Mori.

▪ I’m hoping that future versions of the ECMAScript spec will embrace immutable data structures

▪ It’s important to understand that const does not represent an immutable value.

▪ A const object can’t be reassigned to refer to a completely different object, but the object it refers to can have its properties mutated

▪ JavaScript also has the ability to freeze() objects, but those objects are only frozen at the root level, meaning that a nested object can still have properties of its properties mutated.

▪ Recursion: JavaScript technically supports recursion, but most functional languages have a feature called proper tail calls

▪ Proper tail calls are a language feature which allows recursive functions to reuse stack frames for recursive calls.

▪ Without proper tail calls, a call stack can grow without bounds and cause a stack overflow

▪ JavaScript technically proper tail calls in the ES6 specification. Unfortunately, only one of the major browser engines enabled it as a default feature, and the optimization was partially implemented and then subsequently removed from Babel (the most popular standard JavaScript compiler, used to compile ES6 to ES5 for use in older browsers).

▪ It still isn’t safe to use recursion for large iterations — even if you’re careful to call the function in the tail position.

▪ A purist will tell you that JavaScript’s mutability is its major disadvantage, which is sometimes true. However, side effects and mutation are sometimes beneficial.

▪ In fact, it’s impossible to create most useful modern applications without effects. Pure functional languages like Haskell use effects, but camouflage them from pure functions using boxes called monads, allowing the program to remain pure even though the effects represented by the monads are impure.

▪ The trouble with monads is that, even though their use is quite simple, explaining what a monad is to somebody unfamiliar with lots of examples is a bit like explaining what the color “blue” looks like to a blind person.

▪ In it’s most basic form, a monad is simply a data type that maps and flattens in one operation (covered in much more depth later).

▪ But to get an intuition for how they’re used and the flexibility they give us, you really just need to jump in and start using them. If you’re using promises or the new Array.prototype.flatMap() method, you’re already on your way

▪ But learning them for the first time can be seriously intimidating, and the idiomatic literature on the topic isn’t helping

▪ “A monad is a monoid in the category of endofunctors, what’s the problem?” ~ James Iry, fictionally quoting Philip Wadler, paraphrasing a real quote by Saunders Mac Lane. “A Brief, Incomplete, and Mostly Wrong History of Programming Languages”

▪ “A monad in X is just a monoid in the category of endofunctors of X, with product Ã— replaced by composition of endofunctors and unit set by the identity endofunctor.” ~ Saunders Mac Lane. “Categories for the Working Mathematician”

▪ As with most things in functional programming, the impenetrable academic vocabulary is much harder to understand than the concepts

▪ While it may not be absolutely ideal for every programmming style, JavaScript is unapologetically a general-purpose language designed to be usable by various people with various programming styles and backgrounds.

▪ According to Brendan Eich, this was intentional from the beginning. Netscape had to support two kinds of programmers:

“…the component authors, who wrote in C++ or (we hoped) Java; and the ‘scripters’, amateur or pro, who would write code directly embedded in HTML.”

▪ Originally, the intent was that Netscape would support two different languages, and the scripting language would probably resemble Scheme (a dialect of Lisp).

▪ Again, Brendan Eich:

“I was recruited to Netscape with the promise of ‘doing Scheme’ in the browser.”

▪ “The diktat from upper engineering management was that the language must ‘look like Java’. That ruled out Perl, Python, and Tcl, along with Scheme.”

▪ So, the ideas in Brendan Eich’s head from the beginning were:

Scheme in the browser.
Look like Java.

It ended up being even more of a mish-mash:

▪ “I’m not proud, but I’m happy that I chose Scheme-ish first-class functions and Self-ish (albeit singular) prototypes as the main ingredients. The Java influences, especially y2k Date bugs but also the primitive vs. object distinction (e.g., string vs. String), were unfortunate.”

▪ I’d add to the list of “unfortunate” Java-like features that eventually made their way into JavaScript:

▪ Constructor functions and the new keyword, with different calling and usage semantics from factory functions.

▪ functions.
A class keyword with single-ancestor extends as the primary inheritance mechanism.

▪ The user’s tendency to think of a class as if it’s a static type (it’s not).

▪ My advice: Avoid those whenever it’s practical in your own code. When you’re contributing to code that doesn’t belong to you, adopt the “when in Rome” mantra. Do as the Romans do.

▪ We’re lucky that JavaScript ended up being such a capable language, because it turns out that the “scripting” approach won over the “component” approach (today, Java, Flash, and ActiveX extensions are unsupported in huge numbers of installed browsers).

▪ What we eventually ended up with was one language directly supported by the browser: JavaScript.

▪ That means that browsers are less bloated and less buggy, because they only need to support a single set of language bindings: JavaScript’s.

▪ You might be thinking that WebAssembly is an exception, but one of the design goals of WebAssembly is to share JavaScript’s language bindings using a compatible Abstract Syntax Tree (AST). In fact, the first demonstrations compiled WebAssembly to a subset of JavaScript known as ASM.js.

▪ The position as the only standard general purpose programming language for the web platform allowed JavaScript to ride the biggest language popularity wave in the history of software

▪ Apps ate the world, the web ate apps, and JavaScript ate the web.

By multiple measures, JavaScript is now the most popular programming language in the world.

▪ JavaScript is not the ideal tool for functional programming, but it’s a great tool for building large applications on very large, distributed teams, where different teams may have different ideas about how to build an application.

▪ Some teams may concentrate on scripting glue, where imperative programming is particularly useful. Others may concentrate on building architectural abstractions, where a bit of (restrained, careful) OO thinking may not be a bad idea. Still others may embrace functional programming, reducing over user actions using pure functions for deterministic, testable management of application state. Members on these teams are all using the same language, meaning that they can more easily exchange ideas, learn from each other, and build on each other’s work.

▪ In JavaScript, all of these ideas can co-exist, which allows more people to embrace JavaScript, which has led to the largest open-source package registry in the world (as of February, 2017), npm.

▪ Modulecounts graph: Number of packages

▪ The true strength of JavaScript is diversity of thought and users in the ecosystem. It may not be absolutely the ideal language for functional programming purists, but it may be the ideal language for working together using one language that works on just about every platform you can imagine – familiar to people coming from other popular languages such as Java, Lisp, or C. JavaScript won’t feel ideally comfortable to users with any of those backgrounds, but they may feel comfortable enough to learn the language and become productive quickly.

▪ Instead of abandoning JavaScript and its incredible ecosystem used by virtually every company in the world, why not embrace it, and make it a better language for software composition incrementally?

▪ As-is, JavaScript is already a good enough functional programming language, meaning that people are building all kinds of useful and interesting things in JavaScript, using functional programming techniques.

▪ Netflix (and every app built with Angular 2+) uses functional utilities based on RxJS. Facebook uses the concepts of pure functions, higher-order functions, and higher order components in React to build Facebook and Instagram. PayPal, KhanAcademy, and Flipkart use Redux for state management.

▪ They’re not alone: Angular, React, Redux, and Lodash are the leading frameworks and libraries in the JavaScript application ecosystem, and all of them are heavily influenced by functional programming – or in the cases of Lodash and Redux, built for the express purpose of enabling functional programming patterns in real JavaScript applications.

▪ “Why JavaScript?” Because JavaScript is the language that most real companies are using to build real software. Love it or hate it, JavaScript has stolen the title of “most popular functional programming language” from Lisp, which was the standard bearer for decades.

▪ At any given moment, there are close to a hundred thousand JavaScript job openings in the United States, and hundreds of thousands more world-wide.

▪ Learning Haskell will teach you a lot about functional programming, but learning JavaScript will teach you a lot about building production apps for real jobs.

▪ Functions may serve the following purposes:

▪ Mapping: Produce some output based on given inputs. A function maps input values to output values.

▪ Procedures: A function may be called to perform a sequence of steps. The sequence is known as a procedure, and programming in this style is known as procedural programming.

▪ I/O: Some functions exist to communicate with other parts of the system, such as the screen, storage, system logs, or network.

▪ Pure functions are all about mapping. Functions map input arguments to return values, meaning that for each set of inputs, there exists an output. A function will take the inputs and return the corresponding output.

▪ Math.max() takes numbers as arguments and returns the largest number:

▪ Math has functions, too, and they work a lot like functions in JavaScript. You’ve probably seen functions in algebra. They look something like this:

1 f(x) = 2x

▪ Which means that we’re declaring a function called f and it takes an argument called x and multiplies x by 2.

▪ To use this function, we simply provide a value for x:

1 f(2)

▪ In algebra, this means exactly the same thing as writing 4, so any place you see f(2) you can substitute 4.

▪ This property is called referential transparency.

▪ Now let’s convert that function to JavaScript:

1 const double = x => x * 2;

▪ Remember when I said that in math functions, you could replace f(2) with 4? In this case, the JavaScript engine replaces double(5) with the answer, 10.

▪ So, console.log( double(5) );
is the same as console.log(10);

▪ This is true because double() is a pure function, but if double() had side-effects, such as saving the value to disk or logging to the console, you couldn’t simply replace double(5) with 10 without changing the meaning.

▪ If you want referential transparency, you need to use pure functions.

▪ A pure function is a function which:

▪ Given the same input, will always return the same output.

▪ Produces no side effects.

▪ I recommend that you favor pure functions. Meaning, if it is practical to implement a program requirement using pure functions, you should use them over other options

▪ Pure functions take some input and return some output based on that input. They are the simplest reusable building blocks of code in a program.

▪ Pure functions are completely independent of outside state, and as such, they are immune to entire classes of bugs that have to do with shared mutable state.

▪ Their independent nature also makes them great candidates for parallel processing across many CPUs, and across entire distributed computing clusters, which makes them essential for many types of scientific and resource-intensive computing tasks.

▪ Pure functions are also extremely independent — easy to move around, refactor, and reorganize in your code, making your programs more flexible and adaptable to future changes.

▪ As Martin Odersky (creator of Scala) puts it:

“Non-determinism = parallel processing + mutable state”

▪ Program determinism is usually a desirable property in computing. Maybe you think you’re OK because JS runs in a single thread, and as such, is immune to parallel processing concerns, but as the AJAX example demonstrates, a single threaded JS engine does not imply that there is no concurrency. On the contrary, there are many sources of concurrency in JavaScript. API I/O, event listeners, web workers, iframes, and timeouts can all introduce nondeterminism into your program. Combine that with shared state, and you’ve got a recipe for bugs.

▪ With our double() function, you can replace the function call with the result, and the program will mean the same thing — double(5) will always mean the same thing as 10 in your program, regardless of context, no matter how many times you call it or when.

▪ But you can’t say the same thing about all functions. Some functions rely on information other than the arguments you pass in to produce results.

▪ Consider this example:

1 Math.random(); // => 0.4011148700956255
2 Math.random(); // => 0.8533405303023756
3 Math.random(); // => 0.3550692005082965

Even though we didn’t pass any arguments into any of the function calls, they all produced different output, meaning that Math.random() is not pure.

▪ Math.random() produces a new random number between 0 and 1 every time you run it, so clearly you couldn’t just replace it with 0.4011148700956255 without changing the meaning of the program.

▪ A function is only pure if given the same input, it will always produce the same output. You may remember this rule from algebra class: the same input values will always map to the same output value. However, many input values may map to the same output value

▪ A pure function must not rely on any external mutable state, because it would no longer be deterministic or referentially transparent

▪ JavaScript’s object arguments are references, which means that if a function were to mutate a property on an object or array parameter, that would mutate state that is accessible outside the function. Pure functions must not mutate external state.

▪ The problem with this is that we’ve just mutated some shared state. Other functions may be relying on that cart object state to be what it was before the function was called, and now that we’ve mutated that shared state, we have to worry about what impact it will have on the program logic if we change the order in which functions have been called.

▪ Refactoring the code could result in bugs popping up,

▪ Now consider this version:

1 // Pure addToCart() returns a new cart
2 // It does not mutate the original.
3 const addToCart = (cart, item, quantity) => {
4 return {
5 ...cart,
6 items: cart.items.concat([{
7 item,
8 quantity
9 }]),
10 };
11 };
12 
13 const originalCart = {
14 items: []
15 };
16 
17 const newCart = addToCart(
18 originalCart,
19 {
20 name: "Digital SLR Camera",
21 price: '1495'
22 },
23 1
24 );
25 
26 console.log(
27 // pretty print originalCart to the console
28 JSON.stringify(originalCart, undefined, 2)
29 );

▪ A pure function is a function which, given the same state, always returns the same output, and has no side-effects.

▪ Pure functions are the simplest kind of function. You should prefer them whenever they are practical. They are deterministic, which makes them easy to understand, debug, and test. Determinism also makes them immune to entire classes of bugs dealing with shared mutable state, side-effects, race conditions, and so on.

▪ An expression is referrentially transparent if you can replace the expression with its corresponding value without changing the meaning of the program

▪ Pure functions can be used to optimize software performance. For instance, rendering a view is often an expensive operation, which can be skipped if the data underlying the view has not changed. When pure functions are used for view state updates, you can check to see whether or not a view should be rerendered by comparing the previous state to the new state.

▪ Functional programming has become a really hot topic in the JavaScript world. Just a few years ago, few JavaScript programmers even knew what functional programming is, but every large application codebase I’ve seen in the past 3 years makes heavy use of functional programming ideas.

▪ Functional programming (often abbreviated FP) is a programming paradigm where applications are composed using pure functions, avoiding shared mutable state and side-effects. Functional programming is usually more declarative than imperative, meaning that we express what to do rather than how to do it.

▪ Other examples of programming paradigms include object oriented programming, where data and behaviors are colocated

▪ procedural programming, which is an imperative style grouping algorithms into procedures which tend to rely on shared mutable state.

▪ Functional code tends to be more concise, more predictable, and easier to test than imperative or object oriented code — but if you’re unfamiliar with it and the common patterns associated with it, functional code can also seem a lot more dense, and the related literature can be impenetrable to newcomers.

▪ If you start googling functional programming terms, you’re going to quickly hit a brick wall of academic lingo that can be very intimidating. To say it has a learning curve is a serious understatement. But if you’ve been programming in JavaScript for a while, chances are good that you’ve used a lot of functional programming concepts & utilities in your real software.

▪ Don’t let all the new words scare you away. It’s a lot easier than it sounds

▪ The hardest part is wrapping your head around all the unfamiliar vocabulary. There are a lot of ideas in the innocent looking definition above which all need to be understood before you can begin to grasp the meaning of functional programming:

▪ Pure functions

▪ Function composition

▪ Avoid shared state

▪ Avoid mutating state

▪ Avoid side effects

▪ Declarative vs imperative

▪ A pure function is a function which:

Given the same inputs, always returns the same output, and
Has no side-effects

▪ Pure functions have lots of properties that are important in functional programming, including referential transparency (you can replace a function call with its resulting value without changing the meaning of the program).

▪ Function composition is the process of combining two or more functions in order to produce a new function or perform some computation

▪ For example, the composition f . g (the dot means “composed with”) is equivalent to f(g(x)) in JavaScript.

▪ Understanding function composition is an important step towards understanding how software is constructed using the functional programming

▪ Shared state is any variable, object, or memory space that exists in a shared scope, or as the property of an object being passed between scopes. A shared scope can include global scope or closure scopes. Often, in object oriented programming, objects are shared between scopes by adding properties to other objects.

▪ For example, a computer game might have a master game object, with characters and game items stored as properties owned by that object. Functional programming avoids shared state — instead relying on immutable data structures and pure calculations to derive new data from existing data.

▪ The problem with shared state is that in order to understand the effects of a function, you have to know the entire history of every shared variable that the function uses or affects.

▪ Imagine you have a user object which needs saving. Your saveUser() function makes a request to an API on the server. While that’s happening, the user changes their profile picture with updateAvatar() and triggers another saveUser() request. On save, the server sends back a canonical user object that should replace whatever is in memory in order to sync up with changes that happen on the server or in response to other API calls.

Unfortunately, the second response gets received before the first response, so when the first (now outdated) response gets returned, the new profile pic gets wiped out in memory and replaced with the old one.

▪ This is an example of a race condition — a very common bug associated with shared state.

▪ Another common problem associated with shared state is that changing the order in which functions are called can cause a cascade of failures because functions which act on shared state are timing dependent. With shared state, the order in which function calls are made changes the result of the function calls:

▪ When you avoid shared state, the timing and order of function calls don’t change the result of calling the function. With pure functions, given the same input, you’ll always get the same output. This makes function calls completely independent of other function calls, which can radically simplify changes and refactoring. A change in one function, or the timing of a function call won’t ripple out and break other parts of the program.

▪ In the example above, we use object spread ({...x, val: x.val + 1}
) to copy the properties of x instead of mutating it in place.

▪ Of course, if you change the order of the composition, the output will change. Order of operations still matters. f(g(x)) is not always equal to g(f(x)), but what doesn’t matter anymore is what happens to variables outside the function — and that’s a big deal

▪ With impure functions, it’s impossible to fully understand what a function does unless you know the entire history of every variable that the function uses or affects.

▪ Remove function call timing dependency, and you eliminate an entire class of potential bugs.

▪ An immutable object is an object that can’t be modified after it’s created. Conversely, a mutable object is any object which can be modified after it’s created.

▪ In JavaScript, it’s important not to confuse const, with immutability. const creates a variable name binding which can’t be reassigned after creation. const does not create immutable objects

▪ Immutable objects can’t be changed at all. You can make a value truly immutable by deep freezing the object. JavaScript has a method that freezes an object one-level deep:

▪ As you can see, the top level primitive properties of a frozen object can’t change, but any property which is also an object (including arrays, etc.) can still be mutated — so even frozen objects are not immutable unless you walk the whole object tree and freeze every object property.

▪ In many functional programming languages, there are special immutable data structures called trie data structures (pronounced “tree”) which are effectively deep frozen — meaning that no property can change, regardless of the level of the property in the object hierarchy

▪ Tries use structural sharing to share reference memory locations for all the parts of the object which are unchanged after a “mutation”, which uses less memory, and enables significant performance improvements for some kinds of operations.

▪ For example, you can use identity comparisons at the root of an object tree for comparisons. If the identity is the same, you don’t have to walk the whole tree checking for differences.

▪ There are several libraries in JavaScript which take advantage of tries, including Immutable.js and Mori.

▪ A side effect is any application state change that is observable outside the called function other than its return value

▪ Side effects include:

▪ Modifying any external variable or object property (e.g., a global variable, or a variable in the parent function scope chain)

▪ Logging to the console

▪ Writing to the screen

▪ Writing to a file

▪ Writing to the network

▪ Triggering any external process

▪ Calling any other functions with side-effects

▪ Side effects are mostly avoided in functional programming, which makes the effects of a program easier to extend, refactor, debug, test, and maintain

▪ This is the reason that most frameworks encourage users to manage state and component rendering in separate, loosely coupled modules.

▪ A higher order function is any function which takes a function as an argument, returns a function, or both

▪ Higher order functions are often used to:

▪ Abstract or isolate actions, effects, or async flow control using callback functions, promises, monads, etc.

▪ Create utilities which can act on a wide variety of data types

▪ Partially apply a function to its arguments or create a curried function for the purpose of reuse or function composition

▪ Take a list of functions and return some composition of those input functions

▪ Functional programming tends to reuse a common set of functional utilities to process data

▪ Object oriented programming tends to colocate methods and data in objects. In most object-oriented software, those colocated methods can only operate on the type of data they were designed to operate on, and often only the data contained in that specific object instance.

▪ In functional programming, any type of data is fair game. The same map() utility can map over objects, strings, numbers, or any other data type because it takes a function as an argument which appropriately handles the given data type.

▪ JavaScript has first class functions, which allows us to treat functions as data — assign them to variables, pass them to other functions, return them from functions, etc.

▪ A functor data structure is a data structure that can be mapped over (e.g., [1,2,3].map(x => x * 2)
). In other words, it’s a container which has an interface which can be used to apply a function to the values inside it.

▪ When you see the word functor, you should think “mappable”.

▪ const double = n => n * 2;
2 const doubleMap = numbers => numbers.map(double);
3 console.log(doubleMap([2, 3, 4])); // [ 4, 6, 8 ]

▪ The concept of using abstractions like functors and higher order functions in order to use generic utility functions to manipulate any number of different data types is important in functional programming

▪ “A list expressed over time is a stream.”

▪ Arrays and functors are not the only way this concept of containers and values in containers applies. For example, an array is just a list of things. A list expressed over time is a stream — so you can apply the same kinds of utilities to process streams of incoming events — something that you’ll see a lot when you start building real software with FP.

▪ Functional programming is a declarative paradigm, meaning that the program logic is expressed without explicitly describing the flow control.

▪ Imperative programs spend lines of code describing the specific steps used to achieve the desired results — the flow control: How to do things.

▪ Declarative programs abstract the flow control process (the how gets abstracted away), and instead spend lines of code describing the data flow: What to do.

▪ 1 const doubleMap = numbers => {
2 const doubled = [];
3 for (let i = 0; i < numbers.length; i++) {
4 doubled.push(numbers[i] * 2);
5 }
6 return doubled;
7 };
8 
9 console.log(doubleMap([2, 3, 4])); // [4, 6, 8]

This declarative mapping does the same thing, but abstracts the flow control away using the functional Array.prototype.map() utility, which allows you to more clearly express the flow of data:

1 const doubleMap = numbers => numbers.map(n => n * 2);
2 
3 console.log(doubleMap([2, 3, 4])); // [4, 6, 8]

▪ Imperative code frequently utilizes statements. A statement is a piece of code which performs some action. Examples of commonly used statements include for, if, switch, throw, etc.

▪ Declarative code relies more on expressions. An expression is a piece of code which evaluates to some value.

▪ Expressions are usually some combination of function calls, values, and operators which are evaluated to produce the resulting value.

▪ Functional programming favors:

▪ Pure functions over shared state and side effects

▪ Immutability over mutable data

▪ Function composition over imperative flow control

▪ Generic utilities that act on many data types over object methods that only operate on their colocated data

▪ Declarative over imperative code (what to do, rather than how to do it)

▪ Expressions over statements

▪ The best way to learn to code is to code

▪ An expression is a chunk of code that evaluates to a value

▪ The value of an expression can be given a name. When you do so, the expression is evaluated first, and the resulting value is assigned to the name

▪ Because var tells you the least about the variable, it is the weakest signal. Since I started using ES6, I have never intentionally declared a var in a real software project.

▪ An object in JavaScript is a collection of key: value pairs

▪ If you want to assign existing variables to object property keys of the same name, there’s a shortcut for that. You can just type the variable name instead of providing both a key and a value

▪ Objects can be easily composed together into new objects

▪ Those dots are the object spread operator.

▪ In my experience, mutating an existing object rather than creating a new object is usually a bug. At the very least, it is error-prone.

▪ Destructuring

Both objects and arrays support destructuring, meaning that you can extract values from them and assign them to named variables

▪ There’s also a sloppy equality operator. It’s formally known as the “Equal” operator. Informally, “double equals”. Double equals has a valid use-case or two, but it’s almost always better to default to the === operator, instead.

▪ A ternary expression is an expression that lets you ask a question using a comparator, and evaluates to a different answer depending on whether or not the expression is truthy:

▪ JavaScript has function expressions, which can be assigned to names:

1 const double = x => x * 2;

This means the same thing as the mathematical function f(x) = 2x

▪ You can see the function definition using the .toString() method:

1 double.toString(); // 'x => x * 2'

▪ If you want to apply a function to some arguments, you must invoke it with a function call. A function call applies a function to its arguments and evaluates to a return value.

▪ Unlike some functional languages, those parentheses are meaningful. Without them, the function won’t be called:

▪ Functions have signatures, which consist of:

An optional function name.
A list of parameter types, in parentheses. The parameters may optionally be named.
The type of the return value.

▪ Type signatures don’t need to be specified in JavaScript. The JavaScript engine will figure out the types at runtime. If you provide enough clues, the signature can also be inferred by developer tools such as IDEs (Integrated Development Environment) and Tern.js using data flow analysis.

▪ JavaScript lacks its own function signature notation, so there are a few competing standards: JSDoc has been very popular historically, but it’s awkwardly verbose, and nobody bothers to keep the doc comments up-to-date with the code, so many JS developers have stopped using it.

▪ TypeScript and Flow are currently the big contenders. I’m not sure how to express everything I need in either of those, so I use Rtype, for documentation purposes only. Some people fall back on Haskell’s curry-only Hindley-Milner types. I’d love to see a good notation system standardized for JavaScript, if only for documentation purposes, but I don’t think any of the current solutions are up to the task, at present.

▪ In spite of the fact that JavaScript doesn’t require signatures to be annotated, knowing what signatures are and what they mean will still be important in order to communicate efficiently about how functions are used, and how functions are composed. Most reusable function composition utilities require you to pass functions which share the same type signature, so we need a way to express what those signatures are.

▪ Using default assignments wherever it makes sense can help you write more self-documenting code.

▪ JavaScript functions can take object literals as arguments and use destructuring assignment in the parameter signature in order to achieve the equivalent of named arguments. Notice, you can also assign default values to parameters using the default parameter feature:

▪ Rest gathers individual elements together into an array. Spread does the opposite: it spreads the elements from an array to individual elements.

▪ Arrays in JavaScript have an iterator that gets invoked when the spread operator is used. For each item in the array, the iterator delivers a value. In the expression, [...tail, head]
, the iterator copies each element in order from the tail array into the new array created by the surrounding literal notation.

▪ A curried function is a function that takes multiple parameters one at a time: It takes a parameter, and returns a function that takes the next parameter, and so on until all parameters have been supplied, at which point, the application is completed and the final value returned.

▪ There are some important differences in function behavior depending on which kind of function you use (=> lacks its own this, and can’t be used as a constructor), but we’ll get to those differences when we get there.

▪ With autocurry, you can use it in several different ways, and it will return the right thing depending on how many arguments you pass in:

▪ JavaScript lacks a built-in autocurry mechanism, but you can import one from Lodash:

1 $ npm install --save lodash

▪ Function Composition

▪ Function composition is the process of passing the return value of one function as an argument to another function

▪ In mathematical notation:

1 f . g

Which translates to this in JavaScript:

1 f(g(x))

It’s evaluated from the inside out:

▪ Arrays have some built-in methods. A method is a function associated with an object

▪ Note that we’re passing the double function as a value into map rather than calling it. That’s because map takes a function as an argument and applies it to each item in the array

▪ You can also chain method calls. Method chaining is the process of directly calling a method on the return value of a function, without needing to refer to the return value by name:

▪ 1 const arr = [1, 2, 3];
2 arr.map(double).map(double); // [4, 8, 12]

▪ A predicate is a function that returns a boolean value (true or false)

▪ The .filter() method takes a predicate and returns a new list, selecting only the items that pass the predicate (return true) to be included in the new list:

▪ const gte = cutoff => n => n >= cutoff;
2 [2, 4, 6].filter(gte(4)); // [4, 6]

▪ Note: Later in this text, you’ll see a more efficient way to select and map at the same time using something called a transducer, but there are other things to explore first

▪ Earlier we saw examples of .map() and .filter(). Both of them take a function as an argument. They’re both higher order functions

▪ A higher order function is a function that takes a function as an argument, or returns a function

▪ Higher order function is in contrast to first order functions, which don’t take a function as an argument or return a function as output.

▪ Luckily for us, JavaScript has first class functions. What does that mean? Just like numbers, strings, or objects, functions can be:

Assigned as an identifier (variable) value
Assigned to object property values
Passed as arguments
Returned from functions

▪ We can use functions just like any other value in our programs, and that makes abstraction a lot easier.

▪ If you’re paying attention, you probably know that JavaScript has already done this abstraction work for us. We have the Array.prototype methods, .reduce() and .filter() and .map() and a few more for good measure.

▪ Higher order functions are also commonly used to abstract how to operate on different data types. For instance, .filter() doesn’t have to operate on arrays of strings. It could just as easily filter numbers, because you can pass in a function that knows how to deal with a different data type.

▪ In other words, you can use higher order functions to make a function polymorphic.

▪ Generally speaking, you’ll use higher order functions in combination with very simple first order functions in your real application code.

▪ A curried function is a function that takes multiple arguments one at a time. Given a function with 3 parameters, the curried version will take one argument and return a function that takes the next argument, which returns a function that takes the third argument. The last function returns the result of applying the function to all of its arguments.

▪ To use it, we must apply both functions, using the function application syntax. In JavaScript, the parentheses () after the function reference triggers function invocation

▪ The add function takes one argument, and then returns a partial application of itself with a fixed in the closure scope

▪ A closure is a function bundled with its lexical scope. Closures are created at runtime during function creation.

▪ Fixed means that the variables are assigned values in the closure’s bundled scope.

▪ A partial application is a function which has been applied to some, but not yet all of its arguments. In other words, it’s a function which has some arguments fixed inside its closure scope. A function with some of its parameters fixed is said to be partially applied.

▪ Partial applications can take as many or as few arguments a time as desired

▪ Curried functions on the other hand always return a unary function: a function which takes one argument.

▪ All curried functions return partial applications, but not all partial applications are the result of curried functions.

▪ The unary requirement for curried functions is an important feature.

▪ Point-free style is a style of programming where function definitions do not make reference to the function’s arguments

▪ The returned function is just a specialized version of the more general add() function. We can use add() to create as many specialized versions as we want:

1 const inc10 = add(10);
2 const inc20 = add(20);
3 inc10(3); // => 13
4 inc20(3); // => 23

▪ And of course, these all have their own closure scopes (closures are created at function creation time — when add() is invoked),

▪ All curried functions are a form of higher-order function which allows you to create specialized versions of the original function for the specific use case at hand.

▪ Curried functions are particularly useful in the context of function composition.

▪ In algebra, given two functions, f and g:

￼

You can compose those functions together to create a new function

▪ const compose = (f, g) => x => f(g(x));

▪ We can write a function to compose as many functions as you like. In other words, compose() creates a pipeline of functions with the output of one function connected to the input of the next.

▪ const compose = (...fns) => x => fns.reduceRight((y, f) => f(y), x);

▪ This version takes any number of functions and returns a function which takes the initial value, and then uses reduceRight() to iterate right-to-left over each function, f, in fns, and apply it in turn to the accumulated value, y. What we’re accumulating with the accumulator, y in this function is the return value for the function returned by compose().

▪ const g = n => n + 1;
2 const f = n => n * 2;
3 
4 // replace `x => f(g(x))` with `compose(f, g)`
5 const h = compose(f, g);
6 
7 h(20); //=> 42

▪ Function composition using point-free style creates very concise, readable code, but it can come at the cost of easy debugging. What if you want to inspect the values between functions? trace() is a handy utility that will allow you to do just that

▪ It takes the form of a curried function:

1 const trace = label => value => {
2 console.log(`${ label }: ${ value }`);
3 return value;
4 };

▪ const h = compose(
16 trace('after f'),
17 f,
18 trace('after g'),
19 g
20 );

▪ compose() is a great utility, but when we need to compose more than two functions, it’s sometimes handy if we can read them in top-to-bottom order

▪ There’s another composition utility called pipe() that composes in reverse order:

▪ const pipe = (...fns) => x => fns.reduce((y, f) => f(y), x);

▪ const h = pipe(
16 g,
17 trace('after g'),
18 f,
19 trace('after f'),
20 );

▪ But the real power of curried functions is that they simplify function composition

▪ In order for functions to be composable, the output type must align with the expected input type:

▪ The reason that curried functions are so convenient for function composition is that they transform functions which expect multiple parameters into functions which can take a single argument, allowing them to fit in a function composition pipeline

▪ 13 // the trace() calls are no longer point-free,
14 // introducing the intermediary variable, `x`.
15 x => trace('after g', x),
16 f,
17 x => trace('after f', x),
18 );

▪ If you’re in a pinch, you can fix that problem with a function called flip(), which simply flips the order of two parameters:

1 const flip = fn => a => b => fn(b)(a);

▪ The style is sometimes called “data last”, which means that you should take the specializing parameters first, and take the data the function will act on last.

▪ const h = pipe(
20 g,
21 traceAfterG,
22 f,
23 trace('after f'),
24 );

▪ A curried function is a function which takes multiple parameters one at a time, by taking the first argument, and returning a series of functions which each take the next argument until all the parameters have been fixed, and the function application can complete, at which point, the resulting value is returned.

▪ A partial application is a function which has already been applied to some — but not yet all — of its arguments. The arguments which the function has already been applied to are called fixed parameters.

▪ Point-free style is a way of defining a function without reference to its arguments. Generally, a point-free function is created by calling a function which returns a function, such as a curried function.

▪ Data last functions are convenient for function composition, because they can be easily used in point-free style.

▪ The more I mature in software development, the more I value the fundamentals — insights that seemed trivial when I was a beginner, but now hold profound significance with the benefit of experience.

▪ “In the martial art of Karate […] the symbol of pride for a black belt is to wear it long enough such that the dye fades to white as to symbolize returning to the beginner state.” ~ John Maeda, “The Laws of Simplicity: Design, Technology, Business, Life”

▪ Abstraction is “the process of considering something independently of its associations, attributes, or concrete accompaniments,” according to Google dictionary.

▪ The word abstraction comes from the latin verb abstrahere, which means “to draw away”. I like this insight. Abstraction is about removing things – but what are we removing, and to what end?

▪ Abstraction lets us run on autopilot, safely. All software is automation. Given enough time, anything you do on a computer, you could do with paper, ink, and carrier pigeons. Software just takes care of all the little details that would be too time consuming to do manually.

▪ All software is abstraction, hiding away all the hard work and mindless details while we reap the benefits.

▪ A lot of software processes get repeated again and again. If, during the problem decomposition stage, we decided to reimplement the repeated stuff over and over again, that would require a lot of unnecessary work. It would be silly at the very least. In many cases, it would be impractical.

▪ Instead, we remove duplication by writing a component of some kind (a function, module, class, etc…), giving it a name (identity), and reusing it as many times as we like.

▪ Software solutions should be decomposable into their component parts, and recomposable into new solutions, without changing the internal component implementation details.

▪ “Simplicity is about subtracting the obvious and adding the meaningful.” ~ John Maeda, “The Laws of Simplicity: Design, Technology, Business, Life”

▪ The process of abstraction has two main components:

▪ Generalization is the process of finding similarities (the obvious) in repeated patterns, and hiding the similarities behind an abstraction

▪ Specialization is the process of using the abstraction, supplying only what is different (the meaningful) for each use case.

▪ Abstraction is the process of extracting the underlying essence of a concept. By exploring common ground between different problems from different domains, we learn how to step outside our headspace for a moment and see a problem from a different perspective

▪ Abstraction in software takes many forms:

Algorithms
Data structures
Modules
Classes
Frameworks

▪ “Sometimes, the elegant implementation is just a function. Not a method. Not a class. Not a framework. Just a function.” ~ John Carmack (Id Software, Oculus VR)

▪ Functions make great abstractions because they possess the properties that are essential for a good abstraction:

▪ Identity - The ability to assign a name to it and reuse it in different contexts.

▪ Composable - The ability to compose simple functions to form more complex functions.

▪ Abstraction is the key to doing more with less code.

▪ In this case, inc is just a specialized version of add. All curried functions are abstractions. In fact, all higher-order functions are generalizations that you can specialize by passing one or more arguments.

▪ For example, Array.prototype.map() is a higher-order function that abstracts the idea of applying a function to each element of an array in order to return a new array of processed values.

▪ Most software developers spend their entire careers creating and composing abstractions without a good fundamental grasp of abstraction or composition.

▪ When you create abstractions, you should be deliberate about it, and you should be aware of the good abstractions that have already been made available to you (such as the always useful map, filter, and reduce).

▪ Learn to recognize characteristics of good abstractions:

Composable
Reusable
Independent
Concise
Simple

▪ Reduce (aka: fold, accumulate) utility commonly used in functional programming that lets you iterate over a list, applying a function to an accumulated value and the next item in the list, until the iteration is complete and the accumulated value gets returned. Many useful things can be implemented with reduce

▪ Reduce takes a reducer function and an initial value, and returns the accumulated value.

▪ For Array.prototype.reduce(), the initial list is provided by this, so it’s not one of the arguments:

▪ For each element in the array, the reducer is called and passed the accumulator and the current value. The reducer’s job is to “fold” the current value into the accumulated value somehow

▪ How is not specified, and specifying how is the purpose of the reducer function. The reducer returns the new accumulated value, and reduce() moves on to the next value in the array

▪ The reducer may need an initial value to start with, so most implementations take an initial value as a parameter.

▪ In this case, we passed in an anonymous reducing function, but we can abstract it and give it a name:

▪ Normally, reduce() works left to right. In JavaScript, we also have [].reduceRight(), which works right to left.

▪ Reduce is versatile. It’s easy to define map(), filter(), forEach() and lots of other interesting things using reduce:

▪ Filter works in much the same way as map, except that we take a predicate function and conditionally append the current value to the new array if the element passes the predicate check (fn(item) returns true).

▪ Reduce is also a convenient way to compose functions.

▪ compose() is great if you want to represent the composition from the inside-out – that is, in the math notation sense

▪ What you should understand right now is that reduce() is a very powerful tool, and you really need to learn it. Just be aware that if you get very tricky with reduce, some people may have a hard time following along.

▪ You may have heard the term “reducer” used to describe the important state update bits of Redux

▪ Redux has some reducer rules you need to keep in mind:

▪ A reducer called with no parameters should return its valid initial state.

▪ If the reducer isn’t going to handle the action type, it still needs to return the state.

▪ Redux reducers must be pure functions.

▪ The cool thing about Redux is that the reducers are just standard reducers that you can plug into any reduce() implementation which respects the reducer function signature, including [].reduce().

▪ That means you can create an array of action objects and reduce over them to get a snapshot of state representing the same state you’d have if those same actions were dispatched to your store:

1 const actions = [
2 { type: 'ADD_VALUE', payload: { value: 1 } },
3 { type: 'ADD_VALUE', payload: { value: 1 } },
4 { type: 'ADD_VALUE', payload: { value: 1 } },
5 ];
6 
7 actions.reduce(summingReducer, 0); // 3

▪ That makes unit testing Redux-style reducers a breeze.

▪ You should be starting to see that reduce is an incredibly useful and versatile abstraction. It’s definitely a little trickier to understand than map or filter, but it is an essential tool in your functional programming utility belt – one you can use to make a lot of other great tools.

▪ A functor data type is something you can map over. It’s a container which has a map operation which can be used to apply a function to the values inside it. When you see a functor datatype, you should think “mappable

▪ In JavaScript, functor types are typically represented as an object with a .map() method that maps from inputs to outputs, e.g., Array.prototype.map(). A common analogy is to think of a functor data structure as a box, and map as a way to apply a function to each item contained inside the box, which creates a new box containing the outputs.

▪ In category theory, a functor is a structure preserving map from category to category, where “structure preserving” means that the relationships between objects and morphisms are retained

▪ All functor map operations must obey two axioms, called “the functor laws”

▪ The JavaScript array .map() method is a good example of a functor, but many other kinds of objects can be mapped over as well, including promises, streams, trees, objects, etc.

▪ JavaScript’s built in array and promise objects act like functors. For collections (arrays, streams, trees, etc.), .map() typically iterates over the collection and applies the given function to each value in the collection, but not all functors iterate.

▪ The point of a functor is to apply a given function to values contained within the context of the structure.

▪ Promises use .then() instead of .map(). You can usually think of .then() as an asynchronous .map() method, except when you have a nested promise, in which case it automatically unwraps the outer promise

▪ Again, for values which are not promises, .then() acts like an asynchronous .map(). For values which are promises themselves, .then() acts like the .flatMap() method from monads (sometimes also called .chain() or .bind())

▪ So, promises are not quite functors, and not quite monads, but in practice, you can usually treat them as either.

▪ In Haskell, the functor map operation is called fmap and has the signature:

1 fmap :: (a -> b) -> f a -> f b

▪ In JavaScript, it’s common to pair the data type with methods that act on the data type. In other words, the value is stored with the instance context,

▪ Functors are great for several reasons:

▪ The details of the underlying data structure implementation are abstracted away. Users don’t need to know if iteration is required, or how it’s handled if it is. You can map over arrays, streams, trees, or anything else.

▪ Functors hide the types of the data they contain, which allows you to act on the containers using generic functions, without caring about what you’re storing inside them. You don’t need special arrays for numbers, and special arrays for strings. Instead, you pass functions into map() that can deal with the type contained inside the functor.

▪ Mapping over an empty functor is the same as mapping over a functor containing many items. Switching logic is not needed in the case of an empty collection, and there’s no need to keep track of iteration state if the data structure enumerates over a collection of items.

▪ Most importantly, functors allow you to easily compose functions over the data inside.

▪ The imperative approach is more code. The iterateComments() function below doesn’t need to exist at all if we map, instead. More code = more surface area for bugs to hide in = more bugs.

▪ If the list of comments is very large, you have to wait for the entire list to arrive from the server before you can even begin to draw the comments to the screen. If you had used map, instead, you could swap out the array for a streaming data type and you wouldn’t need to change the UI component at all.

▪ Notice that there’s no special logic dealing with how many times to call comment in the comments div. The entire logic expression is simply comments.map(comment).

▪ Functors come from category theory: a branch of abstract algebra

▪ Objects can be anything, but it’s generally useful to think of them as sets of things, like types in programming languages.

▪ Identity: 
￼
For all objects ￼ in category ￼, there must be an identity arrow that maps back to the same object, represented as ￼ or ￼.

▪ Composition: 
￼
For all pairs of arrows 
￼
, there exists an arrow ￼.

▪ A functor is a mapping between categories. Functors must respect identity and composition.

▪ The functor laws are the axioms that ensure that identity and composition are respected.

▪ A lot of functional programming terms come from category theory, and the essence of category theory is composition

▪ Category theory is scary at first, but easy

▪ A category is a collection of objects and arrows between objects (where “object” can mean just about anything). Objects are like types in programming, meaning that they usually represent sets of things with one or more elements.

▪ Arrows are known as morphisms. Morphisms map between two objects ￼ and ￼, connecting them with an arrow ￼. They’re often represented in diagrams as ￼.

▪ All objects must have identity arrows, which are arrows pointing back to the same object, e.g., ￼. The identity arrow can also be represented as ￼ or ￼.

▪ For any group of connected objects, 
￼
, there must be a composition which goes directly from ￼.

▪ All morphisms are equivalent to compositions, e.g., given objects ￼ and an arrow ￼ between them:

▪ Functor mapping is a form of function composition. In the following code, mappable.map(g).map(f) is equivalent to mappable.map(x => f(g(x)))

▪ Build Your Own Functor

Here’s a simple example of a functor:

1 const Identity = value => ({
2 map: fn => Identity(fn(value))
3 });

▪ Here’s a simple example of a functor:

1 cons

▪ Now you can map over any data type, just like you can map over an array. You can add the map method to any custom data type.

▪ Functional programming is all about composing tiny functions to create higher level abstractions

▪ Functors data types are things we can map over. You can think of them as containers which can have functions applied to their contents to produce a new container with the results inside

▪ In category theory, a functor is a structure preserving map from category to category, where “structure preserving” means that the relationships between objects and morphisms are retained.

▪ A category is a collection of objects and arrows between objects. Arrows represent morphisms, which we can roughly think of as functions in code. Each object in a category has an identity morphism ￼. For any chain of objects ￼ there exists a composition ￼.

▪ Functors are great higher-order abstractions that allow you compose functions over the contents of a container without coupling those functions to the structure or implementation details of the functor data type

▪ Functors form the foundation of other very useful algebraic structures, such as monads.

▪ “Once you understand monads, you immediately become incapable of explaining them to anyone else” Lady Monadgreen’s curse ~ Gilad Bracha (used famously by Douglas Crockford)

▪ “Dr. Hoenikker used to say that any scientist who couldn’t explain to an eight-year-old what he was doing was a charlatan.” ~ Kurt Vonnegut’s novel Cat’s Cradle

▪ Before you begin to learn this, you should already know:

Function composition: compose(f, g) = f(g(x))
Functor basics: An understanding of the Array.prototype.map() operation.

▪ If you go searching the internet for “monad” you’re going to get bombarded by impenetrable category theory math and a bunch of people “helpfully” explaining monads in terms of burritos and space suits.

▪ Monads are simple. The language used to describe them is hard. Let’s cut to the essence.

▪ Monads map ￼ and flatten 
￼
, so that the types line up for type lifting functions like ￼, and ￼, making them composable.

▪ Given two functions, ￼ and ￼, monads let us compose them to produce ￼ where ￼ represents the Kleisli arrow operator (>=> in Haskell).

▪ JavaScript does not have a Kleisli composition operator. Attempting to use >=> in JavaScript code will result in “SyntaxError: Unexpected token >
”. JavaScript does have a .then() method on the Promise object.

▪ FlatMap maps and flattens in one operation.

▪ Functions can compose: a => b => c
becomes a => c

▪ Functors can compose functions with context: given F(a) and two functions, a => b => c
, return F(c).

▪ Monads can compose type lifting functions: a => M(b)
, b => M(c)
becomes a => M(c)

▪ But what do “flatten” and “map” and “context” mean?

▪ Map means, “apply a function to an a and return a b”. Given some input, return some output

▪ The functor map operation does that inside the context of a container called a functor data type, which returns a new container with the results.

▪ Context is the computational detail of the monad

▪ The functor or monad supplies some computation to be performed during the mapping process, such as iterating over a list of things, or waiting for a future value to resolve.

▪ The point of functors and monads is to abstract that context away so we don’t have to worry about it while we’re composing operations.

▪ Mapping inside the context means that you apply a function from a => b
(for functors) or a => Monad(b)
(for monads) to the values inside the context, and return new values of type b wrapped inside the same kind of context.

▪ Observables on the left? Observables on the right: Observable(a) => Observable(b)
. Arrays on the left side? Arrays on the right side: Array(a) => Array(b)

▪ Type lift means to lift a type into a context, wrapping values inside a data type that supplies the computational context a => M(a)

▪ Flatten can be used to unwrap an extra layer of context that might be added by applying a type lifting function using a functor map operation

▪ FlatMap is the operation that defines a monad. It combines map and flatten into a single operation used to compose type lifting functions (a => M(b)
).

▪ const x = 20; // Some data of type `a`

▪ const f = n => n * 2; // A function from `a` to `b`

▪ const arr = Array.of(x); // The type lift.
4 // JS has type lift sugar for arrays: [x]

▪ 6 // .map() applies the function f to the value x
7 // in the context of the array.

▪ const result = arr.map(f); // [40]

▪ In this case, Array is the context,

▪ x is the value we’re mapping over.

▪ But what if we have a function that takes a value and returns an array of values? For example, this echo() function will take a value and repeat it n times:

▪ const echo = n => x => Array.from({ length: n }).fill(x);

Using map() with this, we’ll end up with an array of arrays:

1 const echo = n => x => Array.from({ length: n }).fill(x);
2 
3 console.log(
4 [1, 2, 3].map( echo(3) )
5 // [[1, 1, 1], [2, 2, 2], [3, 3, 3]]
6 );

▪ That’s fine if that’s what you’re looking for, but what if you want an array of numbers instead of an array of arrays of numbers? FlatMap to the rescue!

1 const echo = n => x => Array.from({ length: n }).fill(x);
2 
3 console.log(
4 [1, 2, 3].flatMap(echo(3))
5 // => [1, 1, 1, 2, 2, 2, 3, 3, 3]

▪ You’re probably already using monads.

▪ Regardless of your skill level or understanding of category theory, using monads makes your code easier to work with. Failing to take advantage of monads may make your code harder to work with (e.g., callback hell, nested conditional branches, and potentially a lot more

▪ Remember, the essence of software development is composition, and monads make composition easier.

▪ The whole reason functions exist is so you can compose them. Functions help you break down complex problems into simple problems that are easier to solve in isolation, so that you can compose them in various ways to form your application.

▪ Function composition creates pipelines that your data flows through. You put some input in the first stage of the pipeline, and some data pops out of the last stage of the pipeline, transformed. But for that to work, each stage of the pipeline must be expecting the data type that the previous stage returns.

▪ Composing simple functions is easy, because the types all line up easily. Just match output type b to input type b and you’re in business:

▪ Composing with functors is also easy if you’re mapping F(a) => F(b)
because the types line up:

▪ But if you want to compose functions from a => F(b)
, b => F(c)
, and so on, you need monads

▪ => M(c)
. Using the flatMap operation, we can compose monad-returning functions with the same kinds of declarative tools we use to compose normal functions

▪ For example, if you want to compose promise-returning functions, you can swap pipe for asyncPipe and everything else stays the same.

▪ Monads are needed because lots of functions aren’t simple mappings from a => b
. Some functions need to deal with side effects (promises, streams), handle branching (Maybe), deal with exceptions (Either), etc…

▪ Here’s a more concrete example. What if you need to fetch a user from an asynchronous API, and then pass that user data to another asynchronous API to perform some calculation?:

1 getUserById(id: String) => Promise(User)
2 hasPermision(User) => Promise(Boolean)

▪ const getUserById = id => id === 3 ?
6 Promise.resolve({ name: 'Kurt', role: 'Author' }) :
7 undefined

▪ const hasPermission = ({ role }) => (
12 Promise.resolve(role === 'Author')
13 );

▪ 15 // Try to compose them. Warning: this will fail.
16 const authUser = compose(hasPermission, getUserById);

▪ When we try to compose hasPermission() with getUserById() to form authUser() we run into a big problem because hasPermission() is expecting a User object and getting a Promise(User) instead

▪ To fix this, we need to swap out compose() for composePromises() — a special version of compose that knows it needs to use .then() to accomplish the function composition:

▪ const composeM = flatMap => (...ms) => (
3 ms.reduce((f, g) => x => g(x)[flatMap](f))
4 );

▪ const composePromises = composeM('then');

▪ const authUser = composePromises(hasPermission, getUserById);

▪ A monad is based on a simple symmetry:

▪ of: A type lift a => M(a)

▪ map: The application of a function a => M(b)
inside the monad context, which yields M(M(b))

▪ flatten: The unwrapping of one layer of monadic context: M(M(b)) => M(b)

▪ 1 const Monad = value => ({
2 flatMap: f => f(value),
3 map (f) {
4 return this.flatMap(a => Monad.of(f(a)));
5 }
6 });

▪ So, if you define .of() and .flatMap() for your monad, you can infer the definition of .map().

▪ The lift is the factory/constructor and/or constructor.of() method. In category theory, it’s called “unit”. All it does is lift the type into the context of the monad. It turns an a into a Monad of a.

▪ In Haskell, it’s called return, which can be awkward when you try to talk about it out-loud because nearly everyone confuses it with function returns.

▪ I almost always call it “lift” or “type lift” in prose, and .of() in code.

▪ The flattening process (without the map in .flatMap()) is usually called flatten() or join().

▪ Frequently (but not always), flatten()/join() is omitted completely because it’s built into .flatMap()

▪ Flattening is often associated with composition, so it’s frequently combined with mapping.

▪ But the unwrapping part is also where the weird stuff like side effects, error branching, or waiting for async I/O typically hides. In all software development, composition is where all the real interesting stuff happens.

▪ For example, with promises, .flatMap() is called .then(). Calling promise.then(f) won’t invoke f() right away. Instead, it will wait for the promise to resolve, and then call f() (hence the name).

▪ With promises, .then() is used instead of .flatMap(), but it’s almost the same thing.

▪ You may have heard that a promise is not strictly a monad. That’s because it will only unwrap the outer promise if the value is a promise to begin with. Otherwise, .then() behaves like .map().

▪ But because it behaves differently for promise values and other values, .then() does not strictly obey all the mathematical laws that all functors and/or monads must satisfy for all given values. In practice, as long as you’re aware of that behavior branching, you can usually treat them as either.

▪ 1 const composeM = method => (...ms) => (
2 ms.reduce((f, g) => x => g(x)[method](f))
3 );

Hidden in that weird reducer is the algebraic definition of function composition: f(g(x)).

▪ What this means is that we could write a generalized compose utility that should work for all functors which supply a .map() method (e.g., arrays):

▪ For synchronous, eager function applications over array data, this is overkill.

▪ However, lots of things are asynchronous or lazy, and lots of functions need to handle messy things like branching for exceptions or empty values.

That’s where monads come in. Monads can rely on values that depend on previous asynchronous or branching actions in the composition chain.

▪ In those cases, you can’t get a simple value out for simple function compositions. Your monad-returning actions take the form a => Monad(b)
instead of a => b

▪ Whenever you have a function that takes some data, hits an API, and returns a corresponding value, and another function that takes that data, hits another API, and returns the result of a computation on that data, you’ll want to compose functions of type a => Monad(b)
.

▪ Because the API calls are asynchronous, you’ll need to wrap the return values in something like a promise or observable. In other words, the signatures for those functions are a => Monad(b)
, and b => Monad(c)
, respectively.

▪ Remember our composeMap() function? All you need to do is change the .map() call to .then(). Promise.then() is basically an asynchronous .map().

▪ Inside .then(), there’s an unwrapping process that goes from Promise(b) -> b
. That operation is called flatten (aka join).

▪ Now we can write the specialized implementations like this:

1 const composePromises = composeM('then');
2 const composeMap = composeM('map');
3 const composeFlatMap = composeM('flatMap');

▪ All three of these diagrams are expressing the same general concept. The fact that monads obey the category laws is intentional. Monads form categories where objects are arrows and morphisms are functors between arrows (remember, functors map from category to category).

▪ Monads are a way to compose type lifting functions: g: a => M(b)
, f: b => M(c)
. To accomplish this, monads must flatten M(b) to b before applying f().

▪ In other words, functors are things you can map over. Monads are things you can flatMap over:

▪ Examples of monads you might encounter in every day JavaScript code include promises and observables.

▪ You don’t have to understand or worry about what’s going on inside monads to reap the simplifying benefits that monads can provide, but now that you know more about what’s under the hood, taking a peek under the hood isn’t such a scary prospect.

▪ “The Web as I envisaged it, we have not seen it yet. The future is still so much bigger than the past.” ~ Tim Berners-Lee

▪ Since the early 1990s, one style of programming has dominated the thinking of software development teams: OOP. But do we really understand what OOP is, where it came from, or the goals and trade-offs that shaped its development?

▪ If you want to learn about something, it often helps to take a closer look at it in the historical context that shaped it.

▪ Most of the programming paradigms we use today were first explored mathematically in the 1930s with lambda calculus and the Turing machine, which are alternative formulations of universal computation (formalized systems which can perform general computation).

▪ The Church Turing Thesis showed that lambda calculus and Turing machines are functionally equivalent — that anything that can be computed using a Turing machine can be computed using lambda calculus, and vice versa.

▪ There is a common misconception that Turing machines can compute anything computable. There are classes of problems (e.g., the halting problem) that can be computable for some cases, but are not generally computable for all cases using Turing machines.

▪ Lambda calculus represents a top-down, function application approach to computation, while the ticker tape/register machine formulation of the Turing machine represents a bottom-up, imperative (step-by-step) approach to computation.

▪ Low level languages like machine code and assembly appeared in the 1940s, and by the end of the 1950s, the first popular high-level languages appeared

▪ Lisp dialects are still in common use today, including Clojure, Scheme, AutoLISP, etc.

▪ FORTRAN and COBOL both appeared in the 1950s and are examples of imperative high-level languages still in use today, though C-family languages have replaced both COBOL and FORTRAN for most applications.

▪ Both imperative programming and functional programming have their roots in the mathematics of computation theory, predating digital computers

▪ “Object-Oriented Programming” (OOP) was coined by Alan Kay circa 1966 or 1967 while he was at grad school, but what we think of as OOP today is not the OOP that Alan Kay had in mind.

▪ Ivan Sutherland’s seminal Sketchpad application was an early inspiration for OOP. It was created between 1961 and 1962 and published in his Sketchpad Thesis in 1963. The “objects” were data structures representing graphical images displayed on an oscilloscope screen, and featured inheritance via dynamic delegates, which Ivan Sutherland called “masters” in his thesis. Any object could become a master, and additional instances of the objects were called “occurrences”. Many occurrences could then be composed together to form a drawing. Sketchpad’s masters share a lot in common with JavaScript’s prototypes.

▪ It was possible in Sketchpad to run simulations of things like how a bridge might behave under heavy loads or strong winds. Sketchpad was not just a drawing program — it was a dynamic simulation of object interactions.

▪ “The constraints and their integrated solvers presented ‘programming a computer’ in terms of ‘whats’ rather than ‘hows’. The Sketchpad ‘programmer’ could influence values and histories, but only the internals of Sketchpad could effect the ‘hows’.

▪ Life scales because the system dynamics of very large systems can be treated much more effectively by abandoning ‘clockwork’ and embracing dynamic reformulations and ‘error attenuation.’” ~ Alan Kay in a 2018 email exchange.

▪ Simula, specified in 1965 was another early influence on OOP. Alan Kay encountered Simula I the same week he learned about Sketchpad, in 1966. Like Sketchpad, Simula I could produce complex simulations from relatively little code. It also featured objects without class inheritance. Eventually, Simula 67 introduced class inheritance, subclasses, and virtual methods, which later appeared in languages like C++ and Java.

▪ A virtual method is a method defined on a class which is designed to be overridden by subclasses. Virtual methods allow a program to call methods that may not exist at the moment the code is compiled by employing dynamic dispatch to determine what concrete method to invoke at runtime.

▪ JavaScript features dynamic types and uses the delegation chain to determine which methods to invoke, so does not need to expose the concept of virtual methods to programmers. Put another way, all methods in JavaScript use runtime method dispatch, so methods in JavaScript don’t need to be declared “virtual” to support the feature.

▪ “I made up the term ‘object-oriented’, and I can tell you I didn’t have C++ in mind.” ~ Alan Kay, OOPSLA ‘97

▪ Alan Kay coined the term “object oriented programming” at grad school in 1966 or 1967

▪ The big idea was to use encapsulated mini-computers in software which communicated via message passing rather than direct data sharing — to stop breaking down programs into separate “data structures” and “procedures”.

▪ “The basic principal of recursive design is to make the parts have the same power as the whole.” ~ Bob Barton, the main designer of the B5000, a mainframe optimized to run Algol-60.

▪ “For the first time I thought of the whole as the entire computer and wondered why anyone would want to divide it up into weaker things called data structures and procedures. Why not divide it up into little computers, as time sharing was starting to? But not in dozens. Why not thousands of them, each simulating a useful structure?” ~ Alan Kay, “The Early History of Smalltalk”

▪ Smalltalk was developed by Alan Kay, Dan Ingalls, Adele Goldberg, and others at Xerox PARC. Smalltalk was more object-oriented than Simula — everything in Smalltalk is an object, including classes, integers, and blocks (closures). The original Smalltalk-72 did not feature subclassing. That was introduced in Smalltalk-76 by Dan Ingalls.

▪ While Smalltalk supported classes and eventually subclassing, Smalltalk was not about classes or subclassing things. It was a functional language inspired by more by Sketchpad and Lisp than Simula.

▪ Alan Kay considers the industry’s focus on subclassing to be a distraction from the true benefits of object oriented programming.

▪ “I’m sorry that I long ago coined the term ‘objects’ for this topic because it gets many people to focus on the lesser idea. The big idea is messaging.” ~ Alan Kay

▪ In a 2003 email exchange, Alan Kay clarified what he meant when he called Smalltalk “object-oriented”:

“OOP to me means only messaging, local retention and protection and hiding of state-process, and extreme late-binding of all things.” ~ Alan Kay

▪ In other words, according to Alan Kay, the essential ingredients of OOP are:

Message passing
Encapsulation
Dynamic binding

▪ Notably, inheritance and subclass polymorphism were NOT considered essential ingredients of OOP by Alan Kay.

▪ The combination of message passing and encapsulation serve some important purposes:

▪ Encapsulating state by isolating other objects from local state changes. The only way to affect another object’s state is to ask (not command) that object to change it by sending a message. State changes are controlled at a local, cellular level rather than exposed to shared access.

▪ Decoupling objects from each other — the message sender is only loosely coupled to the message receiver, through the messaging API.

▪ Runtime adaptability via late binding. Runtime adaptability provides many great benefits that Alan Kay considered essential to OOP.

▪ These ideas were inspired by biological cells and networked computers via Alan Kay’s background in biology and influence from the design of Arpanet (an early version of the internet).

▪ Even that early on, Alan Kay imagined software running on a giant, distributed computer (like the internet), where individual computers acted like biological cells, operating independently on their own isolated state, and communicating via message passing. But he also thought that a local program could look like thousands of networked computers, too. The small parts could function the same way the large network functions, like a fractal.

▪ “I realized that the cell/whole-computer metaphor would get rid of data[…]” ~ Alan Kay

▪ By “get rid of data”, Alan Kay was surely aware of shared mutable state problems and tight coupling caused by shared dataâ€Š—â€Šcommon themes today.

▪ But in the late 1960s, ARPA programmers were frustrated by the need to choose a data model representation for their programs in advance of building software. Procedures that were too tightly coupled to particular data structures were not resilient to change or reusable. They wanted a more homogenous treatment of data.

▪ ”[…] the whole point of OOP is not to have to worry about what is inside an object. Objects made on different machines and with different languages should be able to talk to each other[…]” ~ Alan Kay

▪ Objects can abstract away and hide data structure implementations. The internal implementation of an object could change without breaking other parts of the software system. In fact, with extreme late binding, an entirely different computer system could take over the responsibilities of an object, and the software could keep working.

▪ Objects, meanwhile, could expose a standard interface that works with whatever data structure the object happened to use internally.

▪ Alan Kay also saw objects as algebraic structures, which make certain mathematically provable guarantees about their behaviors:

“My math background made me realize that each object could have several algebras associated with it, and there could be families of these, and that these would be very very useful.”

This has proven to be true, and forms the basis for objects such as promises and lenses, both inspired by category theory.

▪ In programmer lingo, algebras are like abstractions made up of functions (operations) accompanied by specific laws enforced by unit tests those functions must pass (axioms/equations).

▪ Like JavaScript and Smalltalk before it, most modern OO languages are becoming more and more multi-paradigm languages. There is no reason to choose between functional programming and OOP. When we look at the historical essence of each, they are not only compatible, but complementary ideas.

▪ Because they share so many features in common, I like to say that JavaScript is Smalltalk’s revenge on the world’s misunderstanding of OOP.

▪ Both Smalltalk and JavaScript support:

Objects
First-class functions and closures
Dynamic types
Late binding (functions/methods changeable at runtime)
OOP without class inheritance

▪ What is essential to OOP?

Encapsulation
Message passing
Dynamic binding (the ability for the program to evolve/adapt at runtime)

▪ What is non-essential?

Classes
Class inheritance
Special treatment for objects/functions/data
The new keyword
Polymorphism
Static types
Recognizing a class as a “type”

▪ If your background is Java or C#, you may be thinking static types and Polymorphism are essential ingredients, but Alan Kay preferred dealing with generic behaviors in algebraic form.

▪ Functor is math jargon that essentially means “supporting the map operation”. If you’re familiar with [].map() in JavaScript, you already know what that means.

▪ The .map() method is generic in the sense that a and b can be any type, and .map() handles it just fine because arrays are data structures that implement the algebraic functor laws.

▪ The types don’t matter to .map() because it doesn’t try to manipulate them directly, instead applying a function that expects and returns the correct types for the application.

▪ 3 const matches = control => input => input === control;
4 
5 const strings = ['foo', 'bar', 'baz'];
6 
7 const results = strings.map(matches('bar'));
8 
9 console.log(results);
10 // [false, true, false]

▪ This generic type relationship is difficult to express correctly and thoroughly in a language like TypeScript, but was pretty easy to express in Haskell’s Hindley Milner types with support for higher kinded types (types of types).

▪ In other words, static types frequently make it harder to write composable software.

▪ If you’re a fan of static types and you don’t mind the restrictions, more power to you, but if you find some of the advice in this text difficult because it’s hard to type composed functions and composite algebraic structures, blame the type system, not the ideas

▪ If restrictions make your code simpler, great! But if restrictions force you to write more complicated code, perhaps the restrictions are wrong.

▪ Objects have clearly taken on a lot of connotations over the years. What we call “objects” in JavaScript are simply composite data types, with none of the implications from either class-based programming or Alan Kay’s message-passing.

▪ In JavaScript, those objects can and frequently do support encapsulation, message passing, behavior sharing via methods, even subclass polymorphism (albeit using a delegation chain rather than type-based dispatch).

▪ You can assign any function to any property. You can build object behaviors dynamically, and change the meaning of an object at runtime.

▪ JavaScript also supports encapsulation using closures for implementation privacy.

▪ Our current idea of an object is simply a composite data structure, and does not require anything more to be considered an object. But programming using these kinds of objects does not make your code “object-oriented” any more than programming with functions makes your code “functional”.

▪ Because “object” in modern programming languages means much less than it did to Alan Kay

▪ I’m using “component” instead of “object” to describe what could be. Many objects are owned and manipulated directly by other code in JavaScript, but components should encapsulate and control their own state.

▪ Characteristics of Message Passing

▪ Program with components (Alan Kay’s “object”)

▪ Encapsulate component state

▪ Use message passing for communication

▪ Add/change/replace components at runtime

▪ Inheritance is not needed. Components can reuse behaviors from shared functions and modular imports without sharing their data.

▪ In most modern software, there is some UI responsible for managing user interactions, some code managing application state (user data), and code managing system or network I/O.

Each of those systems may require long-lived processes, such as event listeners, state to keep track of things like the network connection, UI element status, and the application state itself.

Instead of all of these systems reaching out and directly manipulating each other’s state, the system communicates with other components via message dispatch.

▪ When the user clicks on a save button, a "SAVE" message might get dispatched, which an application state component might interpret and relay to a state update handler (such as a pure reducer function). Perhaps after the state has been updated, the state component might dispatch a "STATE_UPDATED" message to a UI component, which in turn will interpret the state, reconcile what parts of the UI need to be updated, and relay the updated state to the subcomponents that handle those parts of the UI.

▪ These systems don’t need to know about the details of the other parts of the system. Only about their individual, modular concerns

▪ The system components are decomposable and recomposable. They implement standardized interfaces so that they are able to interoperate. As long as the interface is satisfied, you could substitute replacements which may do the same thing in different ways, or completely different things with the same messages. You may even do so at runtime, and everything would keep working properly.

▪ Components of the same software system may not even need to be located on the same machine. The system could be decentralized. The network storage might shard the data across a decentralized storage system like IPFS, so that the user is not reliant on the health of any particular machine to ensure their data is safely stored.

▪ OOP was partially inspired by Arpanet, and one of the goals of Arpanet was to build a decentralized network that could be resilient to network failures or attacks: An “Intergalactic Network” to hook all the ARPA project computers (and friends) together. According to director of DARPA during Arpanet development, Stephen J. Lukasik (“Why the Arpanet Was Built”):

“The goal was to exploit new computer technologies to meet the needs of military command and control against nuclear threats, achieve survivable control of US nuclear forces, and improve military tactical and management decision making.”

▪ Note: The primary impetus of Arpanet was convenience rather than nuclear threat, and its obvious defense advantages emerged later. ARPA was using three separate computer terminals to communicate with three separate computer research projects. Bob Taylor wanted a single computer network to connect each project with the others.

▪ It’s possible using encapsulation and message passing to simulate the internet’s robustness using components that are hot-swappable while the application is running. It could continue to work if the user is on a cell phone and they go offline because they entered a tunnel. It could continue to function if a hurricane knocks out the power to one of the data centers where servers are located.

It’s possible, using these principles, to build more flexible, more resilient, better-composed software, using objects and functional programming in harmony.

▪ “If I have seen further it is by standing on the shoulders of Giants.” ~ Isaac Newton

It often feels to me as if we’ve slipped off the giants’ shoulders and got lost a bit too much in the implementation details of our OOP systems. I don’t advocate going back to Smalltalk, but I wonder how much further we could see if we climb back on top of those shoulders.

▪ “Object Composition Assembling or composing objects to get more complex behavior.” ~ Gang of Four, “Design Patterns: Elements of Reusable Object-Oriented Software”

▪ “Favor object composition over class inheritance.” ~ Gang of Four, “Design Patterns”.

▪ One of the most common mistakes in software development is the tendency to overuse class inheritance

▪ Class inheritance is a code reuse mechanism where instances form is-a relations with base classes. If you’re tempted to model your domain using is-a relations (e.g., a duck is-a bird) you’re bound for trouble, because class inheritance is the tightest form of coupling available in object-oriented design, which leads to many common problems, including (among others):

▪ The fragile base class problem

▪ The gorilla/banana problem

▪ The duplication by necessity problem

▪ Class inheritance accomplishes reuse by abstracting a common interface away into a base class that subclasses can inherit from, add to, and override.

▪ There are two important parts of abstraction:

▪ Generalization The process of extracting only the shared properties and behaviors that serve the general use case

▪ Specialization The process of providing the implementation details required to serve the special case

▪ There are lots of ways to accomplish generalization and specialization in code. Some good alternatives to class inheritance include simple functions, higher order functions, modules, and object composition

▪ Unfortunately, object composition is very misunderstood, and many people struggle to think in terms of object composition, and even fail to recognize it when they see it and use it on a daily basis

▪ “In computer science, a composite data type or compound data type is any data type which can be constructed in a program using the programming languageâ€™s primitive data types and other composite types. […] The act of constructing a composite type is known as composition.” ~ Wikipedia

▪ One of the reasons for the confusion surrounding object composition is that any assembly of primitive types to form a composite object is a form of object composition, but inheritance techniques are often discussed in contrast to object composition as if they are mutually exclusive things, e.g., “favor object composition over class inheritance.” They’re not.

▪ Class inheritance is a subset of object composition. The difference is more about intent than technique: Are we inheriting from a monolithic base class, or assembling smaller components to form a new composite?

▪ When discussing object composition vs class inheritance, we’re not talking about specific techniques: We’re talking about the semantic relationships and degree of coupling between the component objects. We’re talking about meaning as opposed to technique. People often fail to make the distinction and get mired in the technique details. They can’t see the forest for the trees

▪ There are many different ways to compose objects. Different forms of composition will produce different composite structures and different relationships between the objects. When objects depend on the objects they’re related to, those objects are coupled, meaning that changing one object could break the other.

▪ The Gang of Four advice to “favor object composition over class inheritance” invites us to think of our objects as a composition of smaller, loosely coupled objects rather than wholesale inheritance from a monolithic base class

▪ The GoF describes tightly coupled objects as “monolithic systems, where you can’t change or remove a class without understanding and changing many other classes. The system becomes a dense mass that’s hard to learn, port, and maintain.”

▪ Another source of confusion is that in most OO languages, a big distinction is made between data and functions. In most functional languages, functions and data get passed around interchangably.

▪ The reason this distinction is important is because objects as Alan Kay described them for Smalltalk (which influenced all major OO languages that followed, including C++, Java, Objective C and C#) exist to solve the problem of shared mutable state. They accomplish that goal by controlling access to data via encapsulation (where functions outside the object can’t directly observe or manipulate the object’s private state), and message passing (the mechinism we use to communicate with objects - method calls are the simplest form).

▪ When we asseble objects via composition, we don’t care about any of that. We’re just assembling data structures, treating methods and properties as data.

▪ In “Design Patterns”, the Gang of Four states, “you’ll see object composition applied again and again in design patterns”, and goes on to describe various types of compositional relationships, including aggregation and delegation

▪ The authors of “Design Patterns” were primarily working with C++ and Smalltalk (later Java). In those languages, it was relatively difficult to build objects up by extending them at runtime, so the GoF have little to say about dynamic object extension, AKA concatenation. However, it is one of the most common object composition techniques in JavaScript.

▪ There are many kinds of objects and many data structures can be created using object composition, but there are three fundamental techniques that form the basis of all other forms of object composition:

▪ Aggregation When an object is formed from an enumerable collection of subobjects. In other words, an object which contains other objects. Each subobject retains its own reference identity, such that it could be destructured from the aggregation without information loss.

▪ Concatenation When an object is formed by adding new properties to an existing object. Properties can be concatenated one at a time or copied from existing objects, e.g., jQuery plugins are created by concatenating new methods to the jQuery delegate prototype, jQuery.fn.

▪ Delegation When an object forwards or delegates to another object. e.g., Ivan Sutherland’s Sketchpad (1962) included instances with references to “masters” which were delegated to for shared properties. Photoshop includes “smart objects” that serve as local proxies which delegate to an external resource. JavaScript’s prototypes are also delegates: Array instances forward built-in array method calls to Array.prototype, objects to Object.prototype, etc…

▪ It’s important to note that these different forms of composition are not mutually exclusive. It’s possible to implement delegation using aggregation, and class inheritance is implemented using delegation in JavaScript. Many software systems use more than one type of composition, e.g., jQuery’s plugins use concatenation to extend the jQuery delegate prototype, jQuery.fn. When client code calls a plugin method, the request is delegated to the method that was concatenated to the delegate prototype.

▪ Reduce is a higher order function which takes a function and applies it over a collection of items. In the case of object composition, the items in question are source objects, and we’re reducing the collection of source objects to a single target object for output.

▪ With each iteration, the new current value gets folded into the accumulator, where “fold” is not a single, well defined operation, but the operation suplied by the reducer function body.

▪ Aggregation

▪ Aggregation is when an object is formed from an enumerable collection of subobjects. An aggregate is an object which contains other objects

▪ Each subobject in an aggregation retains its own reference identity, and could be losslessly destructured from the aggregate.

▪ Aggregates can be represented in a wide variety of structures.

▪ Arrays
Maps
Sets
Graphs

▪ Trees 
DOM nodes (a DOM node may contain child nodes)
UI components (a component may contain child components)

▪ When to use

Whenever there are collections of objects which need to share common operations, such as iterables, stacks, queues, trees, graphs, state machines, or the composite pattern (when you want a single item to share the same interface as many items).

▪ Considerations

Aggregations are great for applying universal abstractions, such as applying a function to each member of an aggregate (e.g., array.map(fn)), transforming vectors as if they’re single values, and so on. If there are potentially hundreds of thousands or millions of subobjects, however, stream processing or delegation may be more efficient.

▪ Linked lists form the basis of lots of other data structures and aggregations, such as arrays, strings, and various kinds of trees. The DOM tree is based on linked lists, with DOM nodes pointing to children, children nodes pointing back to parents, and delegated references to sibling nodes. There are many other possible kinds of aggregation. We won’t cover them all in-depth here.

▪ Concatenation

Concatenation is when an object is formed by adding new properties to an existing object

▪ Examples

Plugins are added to jQuery.fn via concatenation
State reducers (e.g., Redux)
Functional mixins

▪ Any time it would be useful to progressively assemble data structures at runtime, e.g., merging JSON objects, hydrating application state from multiple sources, creating updates to immutable state (by merging previous state with new data), etc…

▪ Be careful mutating existing objects. Shared mutable state is a recipe for many bugs.

▪ It’s possible to mimic class hierarchies and is-a relations with concatenation. The same problems apply. Think in terms of composing small, independent objects rather than inheriting props from a “base” instance and applying differential inheritance.

▪ Beware of implicit inter-component dependencies.

▪ Property name collisions are resolved by concatenation order: last-in wins. This is useful for defaults/overrides behavior, but can be problematic if the order shouldn’t matter.

▪ Delegation

Delegation is when an object forwards or delegates to another object.

▪ JavaScript’s built-in types use delegation to forward built-in method calls up the prototype chain. e.g., [].map() delegates to Array.prototype.map(), obj.hasOwnProperty() delegates to Object.prototype.hasOwnProperty() and so on.

▪ jQuery plugins rely on delegation to share built-in and plugin methods among all jQuery object instances.

▪ Sketchpad’s “masters” were dynamic delegates. Modifications to the delegate would be reflected instantly in all of the object instances.

▪ Photoshop uses delegates called “smart objects” to refer to images and resources defined in separate files. Changes to the object that smart objects refer to are reflected in all instances of the smart object.

▪ Conserve memory: Any time there may be potentially many instances of an object and it would be useful to share identical properties or methods among each instance which would otherwise require allocating more memory

▪ Dynamically update many instances: Any time many instances of an object need to share identical state which may need to be updated dynamically and changes instantaneously reflected in every instance, e.g., Sketchpad’s “masters” or Photoshop’s “smart objects”.

▪ Delegation is commonly used to imitate class inheritance in JavaScript (wired up by the extends keyword), but is very rarely actually needed.

▪ Delegation can be used to exactly mimic the behavior and limitations of class inheritance. In fact, class inheritance in JavaScript is built on top of static delegates via the prototype delegation chain. Avoid is-a thinking.

▪ Delegate props are non-enumerable using common mechanisms such as Object.keys(instanceObj).

▪ Delegation saves memory at the cost of property lookup performance, and some JS engine optimizations get turned off for dynamic delegates (delegates that change after they’ve been created). However, even in the slowest case, property lookup performance is measured in millions of ops per second – chances are good that this is not your bottleneck unless you’re building a utility library for object operations or graphics programming, e.g., RxJS or three.js.

▪ Need to differentiate between instance state, and delegate state.

▪ Shared state on dynamic delegates is not instance safe. Changes are shared between all instances. Shared state on dynamic delegates is commonly (but not always) a bug.

▪ ES6 classes don’t create dynamic delegates in ES6. They may seem to work in Babel, but will fail hard in real ES6 environments.

▪ All objects made from other objects and language primitives are composite objects.

▪ The act of creating a composite object is known as object composition.

▪ The relationships and dependencies we form when we compose objects differ depending on how objects are composed.

▪ Is-a relations (the kind formed by class inheritance) are the tightest form of coupling in OO design, and should generally be avoided when its practical.

▪ The Gang of Four admonishes us to compose objects by assembling smaller features to form a larger whole, rather than inheriting from a monolithic base class or base object. “Favor object composition over class inheritance.”

▪ Aggregation composes objects into enumerable collections where each member of the collection retains its own identity, e.g., arrays, DOM tree, etc…

▪ Delegation composes objects by linking together an object delegation chain where an object forwards or delegates property lookups to another object. e.g., [].map() delegates to Array.prototype.map()

▪ Concatenation composes objects by extending an existing object with new properties

▪ The definitions of different kinds of object composition are not mutually exclusive. Delegation is a subset of aggregation, concatenation can be used to form delegates and aggregates, and so on…

▪ These are not the only three kinds of object composition. It’s also possible to form loose, dynamic relationships between objects through acquaintance/association relationships where objects are passed as parameters to other objects (dependency injection), and so on.

▪ All software development is composition. There are easy, flexible ways to compose objects, and brittle, arthritic ways. Some forms of object composition form loosely coupled relations between objects, and others form very tight coupling.

▪ If you think you need class inheritance, chances are very good that there’s a better way to do it.

▪ A factory function is any function which is not a class or constructor that returns a (presumably new) object

▪ In JavaScript, any function can return an object. When it does so without the new keyword, it’s a factory function.

▪ Factory functions have always been attractive in JavaScript because they offer the ability to easily produce object instances without diving into the complexities of classes and the new keyword.

▪ JavaScript provides a very handy object literal syntax. It looks something like this:

1 const user = {
2 userName: 'echo',
3 avatar: 'echo.png'
4 };

▪ Like JSON (which is based on JavaScript’s object literal notation), the left side of the : is the property name, and the right side is the value.

▪ You can access computed property names using square bracket notation:

▪ If you have variables in-scope with the same name as your intended property names, you can omit the colon and the value in the object literal creation:

▪ Object literals support concise method syntax. We can add a .setUserName() method:

1 const userName = 'echo';
2 const avatar = 'echo.png';
3 
4 const user = {
5 userName,
6 avatar,
7 setUserName (userName) {
8 this.userName = userName;
9 return this;
10 }
11 };

▪ In concise methods, this refers to the object which the method is called on.

▪ To call a method on an object, simply access the method using object dot notation and invoke it by using parentheses, e.g., game.play() would apply .play() to the game object

▪ You can also apply a method to any other arbitrary object using the function prototype methods, .call(), .apply(), or .bind().

▪ In this case, user.setUserName('Foo') applies .setUserName() to user, so this === user
.

▪ Literals for One, Factories for Many

▪ If you need to create many objects, you’ll want to combine the power of object literals and factory functions.

▪ With a factory function, you can create as many user objects as you want. If you’re building a chat app, for instance, you can have a user object representing the current user, and also a lot of other user objects representing all the other users who are currently signed in and chatting, so you can display their names and avatars, too.

▪ Let’s turn our user object into a createUser() factory:

1 const createUser = ({ userName, avatar }) => ({
2 userName,
3 avatar,
4 setUserName (userName) {
5 this.userName = userName;
6 return this;
7 }
8 });

▪ Arrow functions (=>) have an implicit return feature: if the function body consists of a single expression, you can omit the return keyword: () => 'foo'
is a function that takes no parameters, and returns the string, "foo".

▪ Be careful when you return object literals. By default, JavaScript assumes you want to create a function body when you use braces, e.g., { broken: true }
. If you want to use an implicit return for an object literal, you’ll need to disambiguate by wrapping the object literal in parentheses:

1 const noop = () => { foo: 'bar' };
2 console.log(noop()); // undefined

▪ const createFoo = () => ({ foo: 'bar' });
5 console.log(createFoo()); // { foo: "bar" }

▪ In the createFoo() example, the parentheses force the braces to be interpreted as an expression to be evaluated, rather than a function body block.

▪ Destructuring

▪ Since we don’t know the name of the key, we need to compute the property name in order to set the key/value pair on the object. For that, we borrow the idea of square bracket notation from computed property accessors, and reuse it in the context of building an object literal:

1 { [key]: value }

▪ After the interpolation is done, we end up with the final object:

1 { "foo": "bar" }

▪ Users are able to omit parameters with suitable defaults

▪ The function is more self-documenting because default values supply examples of expected input.

▪ } = {}) => ({

The last = {}
bit just before the parameter signature closes means that if nothing gets passed in for this parameter, we’re going to use an empty object as the default

▪ When you try to destructure values from the empty object, the default values for properties will get used automatically, because that’s what default values do: replace undefined with some predefined value.

▪ JavaScript does not have any native type annotations as of this writing, but several competing formats have sprung up over the years to fill the gaps, including JSDoc (in decline due to the emergence of better options), Facebook’s Flow, and Microsoft’s TypeScript.

▪ At the time of this writing, there is no clear winner for type annotations. None of the alternatives have been blessed by the JavaScript specification, and there seem to be clear shortcomings in all of them.

▪ Tern.js is a popular type inference tool for JavaScript that has plugins for many code editors and IDEs.

Microsoft’s Visual Studio Code doesn’t need Tern because it brings the type inference capabilities of TypeScript to regular JavaScript code.

▪ Factories are great at cranking out objects using a nice calling API.

▪ Usually, they’re all you need, but once in a while, you’ll find yourself building similar features into different types of objects, and you may want to abstract those features into functional mixins so you can reuse them more easily.

▪ That’s where functional mixins shine. Let’s build a withConstructor mixin to add the .constructor property to all object instances.

1 // withConstructor.js
2 const withConstructor = constructor => o => ({
3 // create the delegate [[Prototype]]
4 __proto__: {
5 // add the constructor prop to the new [[Prototype]]
6 constructor
7 },
8 // mix all o's props into the new object
9 ...o
10 });

▪ const withFlying = o => {
8 let isFlying = false;
9 return {
10 ...o,
11 fly () {
12 isFlying = true;
13 return this;
14 },
15 land () {
16 isFlying = false;
17 return this;
18 },
19 isFlying: () => isFlying
20 }
21 };

▪ const withBattery = ({ capacity }) => o => {
24 let percentCharged = 100;
25 return {
26 ...o,
27 draw (percent) {
28 const remaining = percentCharged - percent;
29 percentCharged = remaining > 0 ? remaining : 0;
30 return this;
31 },
32 getCharge: () => percentCharged,
33 getCapacity () {
34 return capacity;
35 }
36 };
37 };

▪ As you can see, the reusable withConstructor() mixin is simply dropped into the pipeline with other mixins

▪ withBattery() could be used with other kinds of objects, like robots, electric skateboards, or portable device chargers.

▪ withFlying() could be used to model flying cars, rockets, or air balloons.

▪ Composition is more of a way of thinking than a particular technique in code. You can accomplish it in many ways. Function composition is just the easiest way to build it up from scratch, and factory functions are a simple way to wrap a friendly API around the implementation details.

▪ ES6 provides a convenient syntax for dealing with object creation and factory functions. Most of the time, that’s all you’ll need, but because this is JavaScript, there’s another approach that makes it feel more like Java: the class keyword.

▪ In JavaScript, classes are more verbose & restrictive than factories, and a bit of a minefield when it comes to refactoring, but they’ve also been embraced by major front-end frameworks like React and Angular, and there are a couple of rare use-cases that make the complexity worthwhile.

▪ “Sometimes, the elegant implementation is just a function. Not a method. Not a class. Not a framework. Just a function.” ~ John Carmack

▪ Start with the simplest implementation, and move to more complex implementations only as required.

▪ Functional mixins are composable factory functions which connect together in a pipeline; each function adding some properties or behaviors like workers on an assembly line. Functional mixins don’t depend on or require a base factory or constructor: Simply pass any arbitrary object into a mixin, and an enhanced version of that object will be returned.

▪ Functional mixin features:

▪ Data privacy/encapsulation

▪ Inheriting private state

▪ Inheriting from multiple sources

▪ No diamond problem (property collision ambiguity) – last in wins

▪ No base-class requirement

▪ All modern software development is really composition: We break a large, complex problem down into smaller, simpler problems, and then compose solutions to form an application.

▪ The atomic units of composition are one of two things:

Functions
Data structures

▪ Application structure is defined by the composition of those atomic units.

▪ Often, composite objects are produced using class inheritance, where a class inherits the bulk of its functionality from a parent class, and extends or overrides pieces. The problem with that approach is that it leads to is-a thinking, e.g., “an admin is an employee”, causing lots of design problems:

▪ The tight coupling problem: Because child classes are dependent on the implementation of the parent class, class inheritance is the tightest coupling available in object oriented design.

▪ The fragile base class problem: Due to tight coupling, changes to the base class can potentially break a large number of descendant classes — potentially in code managed by third parties. The author could break code they’re not aware of.

▪ The inflexible hierarchy problem: With single ancestor taxonomies, given enough time and evolution, all class taxonomies are eventually wrong for new use-cases.

▪ The duplication by necessity problem: Due to inflexible hierarchies, new use cases are often implemented by duplication, rather than extension, leading to similar classes which are unexpectedly divergent. Once duplication sets in, it’s not obvious which class new classes should descend from, or why.

▪ The gorilla/banana problem: “…the problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.” ~ Joe Armstrong, “Coders at Work”

▪ If an admin is an employee, how do you handle a situation where you hire an outside consultant to perform administrative duties temporarily?

▪ If you knew every requirement in advance, perhaps class inheritance could work, but I’ve never seen that happen. Given enough usage, applications and requirements inevitably grow and evolve over time as new problems and more efficient processes are discovered.

▪ Mixins offer a more flexible approach.

▪ “Favor object composition over class inheritance” the Gang of Four, “Design Patterns: Elements of Reusable Object Oriented Software”

▪ Mixins are a form of object composition, where component features get mixed into a composite object so that properties of each mixin become properties of the composite object.

▪ The term “mixins” in OOP comes from mixin ice cream shops. Instead of having a whole lot of ice-cream flavors in different pre-mixed buckets, you have vanilla ice cream, and a bunch of separate ingredients that could be mixed in to create custom flavors for each customer.

▪ Object mixins are similar: You start with an empty object and mix in features to extend it.

▪ Because JavaScript supports dynamic object extension and objects without classes, using object mixins is trivially easy in JavaScript – so much so that it is the most common form of inheritance in JavaScript by a huge margin.

▪ const iceCream = {...chocolate, ...caramelSwirl, ...pecans};

▪ Functional inheritance is the process of inheriting features by applying an augmenting function to an object instance. The function supplies a closure scope which you can use to keep some data private

▪ The augmenting function uses dynamic object extension to extend the object instance with new properties and methods.

▪ Let’s look at an example from Douglas Crockford, who coined the term:

▪ 1 // Base object factory
2 function base(spec) {
3 var that = {}; // Create an empty object
4 that.name = spec.name; // Add it a "name" property
5 return that; // Return the object
6 }
7 
8 // Construct a child object, inheriting from "base"
9 function child(spec) {
10 var that = base(spec); // Create the object through the "base" constructor
11 that.sayHello = function() { // Augment that object
12 return 'Hello, I\'m ' + that.name;
13 };
14 return that; // Return it
15 }
16 
17 // Usage
18 var result = child({ name: 'a functional object' });
19 console.log(result.sayHello()); // 'Hello, I'm a functional object'

▪ Because child() is tightly coupled to base(), when you add grandchild(), greatGrandchild(), etc…, you’ll opt into most of the common problems from class inheritance.

▪ Functional mixins are composable functions which mix new properties or behaviors into existing objects.

▪ Functional mixins don’t depend on or require a base factory or constructor: Simply pass any arbitrary object into a mixin, and it will be extended.

▪ Of course, this is standard function composition, and we already know some better ways to do that using compose() or pipe()

▪ const pipe = (...fns) => x => fns.reduce((y, f) => f(y), x);
2 // OR...
3 // import pipe from `lodash/fp/flow`;
4 
5 const createDuck = quack => pipe(
6 flying,
7 quacking(quack)
8 )({});

▪ You should always use the simplest possible abstraction to solve the problem you’re working on. Start with a pure function. If you need an object with persistent state, try a factory function. If you need to build more complex objects, try functional mixins.

▪ Here are some good use-cases for functional mixins:

▪ Application state management, e.g., something similar to a Redux store.

▪ Certain cross-cutting concerns and services, e.g., a centralized logger.

▪ React users: class is fine for lifecycle hooks because callers aren’t expected to use new, and documented best-practice is to avoid inheriting from any components other than the React-provided base components

▪ Most problems can be elegantly solved using pure functions. The same is not true of functional mixins. Like class inheritance, functional mixins can cause problems of their own. In fact, it’s possible to faithfully reproduce all of the features and problems of class inheritance using functional mixins.

▪ Favor pure functions > factories > functional mixins > classes

▪ Avoid the creation of is-a relationships between objects, mixins, or data types

▪ Avoid implicit dependencies between mixins – wherever possible, functional mixins should be self-contained, and have no knowledge of other mixins

▪ “Functional mixins” doesn’t mean “functional programming”

▪ There may be side-effects when you access a property using Object.assign() or object spread syntax ({...object}). You’ll also skip any non-enumerable properties. ES2017 added Object.getOwnPropertyDescriptors() to get around this problem.

▪ I rely mostly on function composition to compose behavior and application structure, and only rarely use functional mixins. I never use class inheritance unless I’m inheriting directly from a third-party base class such as React.Class. I never build my own inheritance hierarchies

▪ Class inheritance is very rarely (perhaps never) the best approach in JavaScript, but that choice is sometimes made by a library or framework that you don’t control

▪ In that case, using class is sometimes practical, provided the library:

Does not require you to extend your own classes (i.e., does not require you to build multi-level class hierarchies), and
Does not require you to directly use the new keyword – in other words, the framework handles instantiation for you

▪ Both Angular 2+ and React meet those requirements, so you can safely use classes with them, as long as you don’t extend your own classes.

▪ In some browsers, classes may provide JavaScript engine optimizations that are not available otherwise. In almost all cases, those optimizations will not have a significant impact on your app’s performance

▪ In fact, it’s possible to go many years without ever needing to worry about class performance differences.

▪ Object creation and property access is always very fast (millions of ops/sec), regardless of how you build your objects.

▪ That said, authors of general purpose utility libraries similar to RxJS, Lodash, etc… should investigate possible performance benefits of using class to create object instances

▪ Unless you have measured a significant bottleneck that you can provably and substantially reduce using class, you should optimize for clean, flexible code instead of worrying about performance.

▪ The factory only needs to know about withConfig now...
27 const createConfig = ({ initialConfig, logger }) =>
28 withConfig({ initialConfig, logger })({})
29 ;

▪ API contract should be made explicitly clear in the function signature and API documentation.

▪ If you’re using TypeScript or Flow, it’s probably better to declare an explicit interface for your o requirements

▪ Functional” in the context of functional mixins does not always have the same purity connotations as “functional programming”. Functional mixins are commonly used in OOP style, complete with side-effects. Many functional mixins will alter the object argument you pass to them. Caveat emptor.

▪ By the same token, some developers prefer a functional programming style, and will not maintain an identity reference to the object you pass in. You should code your mixins and the code that uses them assuming a random mix of both styles.

▪ That means that if you need to return the object instance, always return this instead of a reference to the instance object in the closure – in functional code, chances are those are not references to the same objects.

▪ Additionally, always assume that the object instance will be copied by assignment using Object.assign() or {...object, ...spread}
syntax.

▪ By the same token, if you’re using functional mixins that you didn’t create in your functional code, don’t assume the code is pure. Assume that the base object may be mutated, and assume that there may be side-effects & no referential transparency guarantees, i.e., it is frequently unsafe to memoize factories composed of functional mixins.

▪ Functional mixins are composable factory functions which add properties and behaviors to objects like stations in an assembly line. They are a great way to compose behaviors from multiple source features (has-a, uses-a, can-do), as opposed to inheriting all the features of a given class (is-a).

▪ Be aware, “functional mixins” doesn’t imply “functional programming” – it simply means, “mixins using functions”. Functional mixins can be written using a functional programming style, avoiding side-effects and preserving referential transparency, but that is not guaranteed. There may be side-effects and nondeterminism.

▪ Unlike simple object mixins, functional mixins support true data privacy (encapsulation), including the ability to inherit private data.

▪ Unlike single-ancestor class inheritance, functional mixins also support the ability to inherit from many ancestors, similar to class decorators, traits, or multiple inheritance.

▪ Unlike multiple inheritance in C++, the diamond problem is rarely problematic in JavaScript, because there is a simple rule when collisions arise: The last mixin added wins.

▪ Unlike class decorators, traits, or multiple inheritance, no base class is required.

▪ Favor the simplest implementation over more complex constructions:

Pure functions > factory functions > functional mixins > classes

▪ Now we’re going to look at classes in more detail, and examine how the mechanics of class get in the way of composition.

▪ We’ll also take a look at the good use-cases for classes and how to use them safely.

▪ ES6 includes a convenient class syntax, so you may be wondering why we should care about factories at all. The most obvious difference is that constructors and class require the new keyword

▪ But what does new actually do?

Creates a new object and binds this to it in the constructor function.
Implicitly returns this, unless you explicitly return another object.
Sets the instance [[Prototype]], instance.__proto__ to Constructor.prototype, so that Object.getPrototypeOf(instance) === Constructor.prototype
and instance.__proto__ === Constructor.prototype
.

▪ Sets the instance.constructor === Constructor
.

▪ You can still achieve composition using class, but it’s a much more complex process, and as you’ll see, the additional costs are usually not worth the extra effort.

▪ You may eventually need to refactor from a class to a factory function, and if you require callers to use the new keyword, that refactor could break client code you’re not even aware of in a couple of ways

▪ First, unlike classes and constructors, factory functions don’t automatically wire up a delegate prototype link.

▪ The [[Prototype]] link is used for prototype delegation, which is a convenient way to conserve memory if you have millions of objects, or to squeeze a micro-performance boost out of your program if you need to access tens of thousands of properties on an object within a 16 ms render loop cycle.

▪ If you don’t need to micro-optimize memory or performance, the [[Prototype]] link can do more harm than good

▪ The prototype chain powers the instanceof operator in JavaScript, and unfortunately instanceof lies for two reasons:

▪ In ES5, the Constructor.prototype link was dynamic and reconfigurable, which could be a handy feature if you need to create an abstract factory — but if you reassign the prototype, instanceof will give you false negatives if the Constructor.prototype does not currently reference the same object in memory that the instance [[Prototype]] references:

▪ const currentUser = new User({
9 userName: 'Foo',
10 avatar: 'foo.png'
11 });
12 
13 User.prototype = {};
14 
15 console.log(
16 currentUser instanceof User,

▪ Chrome solves the problem by making the Constructor.prototype property configurable: false
in the property descriptor. However, Babel (a popular JavaScript compiler) does not currently mirror that behavior, so Babel compiled code will behave like ES5 constructors. V8 silently fails if you attempt to reconfigure the Constructor.prototype property. Either way, you won’t get the results you expected. Worse: the behavior is inconsistent, and code that works now in Babel is likely to break in the future.

▪ I don’t recommend reassigning Constructor.prototype.

▪ A more common problem is that JavaScript has multiple execution contexts called realms — memory sandboxes where the same code will access different physical memory locations. For example, if you have a constructor in a parent frame and the same constructor in an iframe, the parent frame’s Constructor.prototype will not reference the same memory location as the Constructor.prototype in the iframe.

▪ Object values in JavaScript are memory references under the hood, and different frames point to different locations in memory, so === checks will fail.

▪ Another problem with instanceof is that it is a nominal type check rather than a structural type check, which means that if you start with a class and later switch a factory, all the calling code using instanceof won’t understand new implementations even if they satisfy the same interface contract.

▪ They’ll fail when they should succeed. Sharable interfaces in other languages solve this problem by allowing a class to declare that it implements a specific interface. That’s not currently possible in JavaScript.

▪ The best way to deal with instanceof in JavaScript is to break the delegate prototype link if it’s not required, and let instanceof fail for every call. That way you won’t get a false sense of reliability. Don’t listen to instanceof, and it will never lie to you.

▪ The .constructor Property

The .constructor property is a rarely used feature in JavaScript, but it could be very useful, and it’s a good idea to include it on your object instances

▪ It’s mostly harmless if you don’t try to use it for type checking (which is unsafe for the same reasons instanceof is unsafe).

▪ In theory, .constructor could be useful to make generic functions which are capable of returning a new instance of whatever object you pass in.

▪ What we would need to make this work is to have a standard way to pass a value into a new instance using a standard factory function that doesn’t require new.

▪ There is a specification for that: a static method on any factory or constructor called .of(). The .of() method is a factory that returns a new instance of the data type containing whatever you pass into .of().

▪ Unfortunately, the static .of() method is just beginning to gain support in JavaScript. The Promise object does have a static method that acts like .of(), but it’s called .resolve() instead, so our generic empty() won’t work with promises:

▪ Likewise, there’s no .of() for strings, numbers, objects, maps, weak maps, or sets in JavaScript as of this writing.

▪ It’s easy to add support for .constructor and .of() to a factory:

1 const createUser = ({
2 userName = 'Anonymous',
3 avatar = 'anon.png'
4 } = {}) => ({
5 userName,
6 avatar,
7 constructor: createUser
8 });
9 createUser.of = createUser;

▪ Factories allow increased flexibility because they:

▪ Decouple instantiation details from calling code.

▪ Allow you to return arbitrary objects — for instance, to use an object pool to tame the garbage collector.

▪ Don’t pretend to provide any type guarantees, so callers are less tempted to use instanceof and other unreliable type checking measures, which might break code across execution contexts, or if you switch to an abstract factory.

▪ Can dynamically swap implementations for abstract factories. e.g., a media player that swaps out the .play() method for different media types.

▪ Adding capability with composition is easier with factories.

▪ While it’s possible to accomplish most of these goals using classes, it’s easier to do so with factories. There are fewer potential bug pitfalls, less complexity to juggle, and a lot less code.

▪ You can read more about it in “Refactoring: Improving the Design of Existing Code” by Martin Fowler, Kent Beck, John Brant, William Opdyke, and Don Roberts.

▪ Due to the fact that new changes the behavior of a function being called, changing from a class or constructor to a factory function is a potentially breaking change

▪ In other words, forcing callers to use new could unwittingly lock callers into the constructor implementation, so new leaks potentially breaking implementation details into the calling API.

▪ In ES6+, arrow functions are commonly used to create factories, but because arrow functions don’t have their own this binding in JavaScript, invoking an arrow function with new throws an error:

1 const foo = () => ({});
2 
3 // TypeError: foo is not a constructor
4 const bar = new foo();

▪ But, if you compile arrow functions to standard functions, it will fail to fail

▪ Absence of the [[Prototype]] link from factory instances will break caller instanceof checks.

▪ Absence of the .constructor property from factory instances could break code that relies on it.

▪ Callers using new could begin to throw errors or experience unexpected behavior after switching to a factory.

▪ The class keyword is supposed to be a nicer syntax for object creation patterns in JavaScript, but it falls short in several ways:

▪ The primary purpose of class was to provide a friendly syntax to mimic class from other languages in JavaScript. The question we should ask ourselves though is, does JavaScript really need to mimic class from other languages?

▪ JavaScript’s factory functions provide a friendlier syntax out of the box, with much less complexity. Often, an object literal is good enough. If you need to create many instances, factories are a good next step.

▪ In Java and C++, factories are more complicated than classes, but they’re often worth building anyway because they provide enhanced flexibility. In JavaScript, factories are less complicated and more flexible than classes.

▪ Compare the class:

1 class User {
2 constructor ({userName, avatar}) {
3 this.userName = userName;
4 this.avatar = avatar;
5 }
6 }
7 
8 const currentUser = new User({
9 userName: 'Foo',
10 avatar: 'foo.png'
11 });

Vs the equivalent factory:

1 const createUser = ({ userName, avatar }) => ({
2 userName,
3 avatar
4 });
5 
6 const currentUser = createUser({
7 userName: 'Foo',
8 avatar: 'foo.png'
9 });

▪ With JavaScript and arrow function familiarity, factories are clearly less syntax and easier to read

▪ Maybe you prefer to see the new keyword, but there are good reasons to avoid new.

▪ class offers two kinds of performance optimizations: shared memory for properties stored on the delegate prototype, and property lookup optimizations.

▪ Good use cases for delegate prototypes are rare. class syntax is a little nicer than the equivalent syntax for ES5 constructor functions, but the primary purpose is to hook up the delegate prototype chain, and good use cases for delegate prototypes are rare. It really boils down to performance.

▪ The delegate prototype memory optimization is available to both factories and classes.

▪ A factory can set the prototype by setting the __proto__ property in an object literal or by using Object.create(proto).

▪ Even so, most modern devices have RAM measured in gigabytes. Before using a delegate prototype, you should profile and make sure it’s really needed.

▪ class property lookup optimizations are tiny microoptimizations.

▪ Any type of closure scope or property access is measured in hundreds of thousands or millions of ops/second, so performance differences are rarely measurable in the context of an application, let alone impactful.

▪ There are exceptions, of course. RxJS used class instances because they were faster than closure scopes when they profiled, but RxJS is a general purpose utility library that might be used in the context of hundreds of thousands operations that need to be squeezed into a 16ms render loop.

▪ ThreeJS uses classes, but ThreeJS is a 3d rendering library which might be used for game engines manipulating thousands of objects every 16ms.

▪ It makes sense for libraries like ThreeJS and RxJS to go to extremes optimizing wherever they can.

▪ In the context of applications, we should avoid premature optimization, and focus our efforts only where they’ll make a large impact

▪ For most applications, that means our network calls and payloads, animations, asset caching strategies, etc.

▪ Don’t micro-optimize for performance unless you’ve noticed a performance problem, profiled your application code, and pinpointed a real bottleneck.

Instead, you should optimize code for maintenance and flexibility.

▪ Classes in JavaScript are dynamic, and instanceof checks don’t work across execution contexts, so type checking based on class is a non-starter. It’s unreliable. It’s likely to cause bugs and make your application unnecessarily rigid.

▪ Class inheritance causes several well-known problems that bear repeating

▪ Tight coupling: Class inheritance is the tightest form of coupling available in object-oriented design

▪ Inflexible hierarchies: Given enough time and users, all class hierarchies are eventually wrong for new use cases, but tight coupling makes refactors difficult.

▪ Gorilla/Banana problem: No selective inheritance. “You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.” ~ Joe Armstrong in “Coders at Work”

▪ Duplication by necessity: Due to inflexible hierarchies and the gorilla/banana problem, code reuse is often accomplished by copy/paste, violating DRY (Don’t Repeat Yourself) and defeating the entire purpose of inheritance in the first place.

▪ The only purpose of extends is to create single-ancestor class taxonomies.

▪ Some clever hacker will read this and say, “Ah hah! Not so! You can do class composition!” To which I would answer, “ah, but now you’re using object composition instead of class inheritance, and there are easier, safer ways to do that in JavaScript without extends.”

▪ Avoid instanceof — it lies because JavaScript is dynamic and has multiple execution contexts, and instanceof fails in both situations. It can also cause problems if you switch to an abstract factory down the road.

▪ Avoid extends — don’t extend a single hierarchy more than once. “Favor object composition over class inheritance.” ~ “Design Patterns: Elements of Reusable Object-Oriented Software”

▪ Avoid exporting your class. Use class internally for performance gains, but export a factory that creates instances in order to discourage users from extending your class and avoid forcing callers to use new.

▪ Avoid new. Try to avoid using it directly whenever it makes sense, and don’t force your callers to use it. (Export a factory, instead).

▪ You need to optimize performance. Just remember to export a factory so callers don’t have to use new and don’t get lured into the extends trap

▪ In JavaScript, the easiest way to compose is function composition, and a function is just an object you can add methods to. In other words, you can do this:

1 const t = value => {
2 const fn = () => value;
3 
4 fn.toString = () => `t(${ value })`;
5 
6 return fn;
7 };
8 
9 
10 const someValue = t(2);
11 
12 console.log(
13 someValue.toString() // "t(2)"
14 );

▪ It doesn’t matter what shape your data takes, as long as there is some composition operation that makes sense. For lists or strings, it could be concatenation. For Digial Signal Processing (DSP), it could be signal summing. Of course lots of different operations might make sense for the same data. The question is, which operation best represents the concept of composition?

▪ In other words, which operation would benefit most expressed like this?:

1 const result = compose(
2 value1,
3 value2,
4 value3
5 );

▪ Moneysafe solves the problem by lifting dollar amounts to cents:

▪ 1 import { $ } from 'moneysafe';
2 
3 $(.1) + $(.2) === $(.3).cents; // true

▪ The ledger syntax takes advantage of the fact that Moneysafe lifts values into composable functions

▪ 1 import { $ } from 'moneysafe';
2 import { $$, subtractPercent, addPercent } from 'moneysafe/ledger';
3 
4 $$(
5 $(40),
6 $(60),
7 // subtract discount
8 subtractPercent(20),
9 // add tax
10 addPercent(10)
11 ).$; // 88

▪ The result is an intuitive interface for performing ledger-style money calculations.

▪ Lenses

▪ A lens is a composable pair of pure getter and setter functions which focus on a particular field inside an object, and obey a set of axioms known as the lens laws

▪ Think of the object as the whole and the field as the part.

▪ The getter takes a whole and returns the part of the object that the lens is focused on.

▪ The setter takes a whole, and a value to set the part to, and returns a new whole with the part updated

▪ Unlike a function which simply sets a value into an object’s member field, Lens setters are pure functions:

▪ Note: In this text, we’re going to use some naive lenses in the code examples just to give you a beneath-the-hood peek at the general concept. For production code, you should look at a well tested library like Ramda, instead. The API differs between different lens libraries, and it’s possible to express lenses in more composable, elegant ways than they are presented here.

▪ To get or set each field individually, you might create three lenses. One for each axis. You could manually create getters which focus on each field:

1 const getX = ([x]) => x;
2 const getY = ([x, y]) => y;
3 const getZ = ([x, y, z]) => z;

▪ Likewise, the corresponding setters might look like this:

1 const setY = ([x, _, z]) => y => ([x, y, z]);
2 
3 console.log(
4 setY([10, 10, 10])(999) // [10, 999, 10]
5 );

▪ Lenses allow you to abstract state shape behind getters and setters. Instead of littering your codebase with code that dives deep into the shape of a particular object, import a lens

▪ If you later need to change the state shape, you can do so in the lens, and none of the code that depends on the lens will need to change.

▪ In 1985, “Structure and Interpretation of Computer Programs” described getter and setter pairs (called put and get in the text) as a way to isolate an object’s shape from the code that uses the object

▪ The text shows how to create generic selectors that access parts of a complex number independent of how the number is represented. That isolation is useful because it breaks state shape dependencies.

▪ These getter/setter pairs were a bit like referenced queries which have existed in relational databases for decades.

▪ Lenses took the concept further by making getter/setter pairs more generic and composable. They were popularized after Edward Kmett released the Lens library for Haskell. He was influenced by Jeremy Gibbons and Bruno C. d. S. Oliveira, who demonstrated that traversals express the iterator pattern, Luke Palmer’s “accessors”, Twan van Laarhoven, and Russell O’Connor.

▪ Note: An easy mistake to make is to equate the modern notion of a functional lens with Anamorphisms, based on Erik Meijer, Maarten Fokkinga, and Ross Paterson’s “Functional Programming with Bananas, Lenses, Envelopes and Barbed Wire” in 1991.

▪ “The term ‘lens’ in the functional reference sense refers to the fact that it looks at part of a whole. The term ‘lens’ in a recursion scheme sense refers to the fact that [( and )] syntactically look kind of like concave lenses.

▪ Lens Laws

The lens laws are algebraic axioms which ensure that the lens is well behaved.

▪ view(lens, set(lens, value, store))
￼ value — If you set a value into the store, and immediately view the value through the lens, you get the value that was set.

▪ set(lens, b, set(lens, a, store))
￼ set(lens, b, store)
— If you set a lens value to a and then immediately set the lens value to b, it’s the same as if you’d just set the value to b.

▪ set(lens, view(lens, store), store)
￼ store — If you get the lens value from the store, and then immediately set that value back into the store, the value is unchanged.

▪ Before we dive into code examples, remember that if you’re using lenses in production, you should probably be using a well tested lens library. The best one I know of in JavaScript is Ramda

▪ We’re going to skip that for now and build some naive lenses ourselves, just for the sake of learning:

▪ 1 // Pure functions to view and set which can be used with any lens:
2 const view = (lens, store) => lens.view(store);
3 const set = (lens, value, store) => lens.set(value, store);

▪ 23 const aLens = lensProp('a');
24 const bLens = lensProp('b');

▪ Lenses are composable. When you compose lenses, the resulting lens will dive deep into the object, traversing the full object path.

▪ Let’s import the more full-featured lensProp from Ramda to demonstrate:

1 import { compose, lensProp, view } from 'ramda';

▪ const lensProps = [
4 'foo',
5 'bar',
6 1
7 ];
8 
9 const lenses = lensProps.map(lensProp);

▪ const truth = compose(...lenses);

▪ const obj = {
14 foo: {
15 bar: [false, true]
16 }
17 };
18 
19 console.log(
20 view(truth, obj)
21 );

▪ The lens map operation is commonly called “over” in JavaScript libraries

▪ We’ve barely scratched the surface of lenses here, but it should be enough to get you started. For a lot more, detail, Edward Kmett has spoken a lot on the topic, and many people have written much more in-depth explorations.

▪ Transducers

Prior to taking on transducers, you should first have a strong understanding of both reducers and function composition.

▪ Transduce: Derived from the 17th century scientific latin, “transductionem” means “to change over, convert”. It is further derived from “transducere/traducere”, which means “to lead along or across, transfer”.

▪ A transducer is a composable higher order reducer. It takes a reducer as input, and returns another reducer

▪ Transducers are:

Composable using simple function composition

▪ Efficient for large collections or infinite streams: Only enumerates over the signal once, regardless of the number of operations in the pipeline

▪ Able to transduce over any enumerable source (e.g., arrays, trees, streams, graphs, etc…)

▪ Usable for either lazy or eager evaluation with no changes to the transducer pipeline

▪ Reducers fold multiple inputs into single outputs, where “fold” can be replaced with virtually any binary operation that produces a single output, such as:

1 // Sums: (1, 2) = 3
2 const add = (a, c) => a + c;

▪ Transducers do much the same thing, but unlike ordinary reducers, transducers are composable using normal function composition

▪ Normal reducers can’t compose, because they expect two arguments, and only return a single output value, so you can’t simply connect the output to the input of the next reducer in the series.

▪ Since all the functions in the pipeline accept a reducer and return a reducer, the input and output types always line up for easy composition.

▪ Often, when we process data, it’s useful to break up the processing into multiple independent, composable stages. For example, it’s very common to select some data from a larger set, and then process that data

▪ This only works for arrays. What about potentially infinite streams of data coming in from a network subscription, or a social graph with friends-of-friends?

▪ Each time you use the dot chaining syntax on an array, JavaScript builds up a whole new intermediate array before moving onto the next operation in the chain. If you have a list of 2,000,000 “friends” to wade through, that could slow things down by an order of magnitude or two.

▪ With dot chaining, you have to build different implementations of standard operations, like .filter(), .map(), .reduce(), .concat(), and so on.

▪ Transducers don’t do anything until you tell them to start and feed them some data to process, which is why we need toArray().

▪ It supplies the transducable process and tells the transducer to transduce the results into a new array.

▪ You could tell it to transduce to a stream, or an observable, or anything you like, instead of calling toArray().

▪ In hardware signal processing systems, a transducer is a device which converts one form of energy to another, e.g., audio waves to electrical, as in a microphone transducer. In other words, it transforms one kind of signal into another kind of signal. Likewise, a transducer in code converts from one signal to another signal.

▪ Use of the word “transducers” and the general concept of composable pipelines of data transformations in software date back at least to the 1960s, but our ideas about how they should work have changed from one language and context to the next

▪ Many software engineers in the early days of computer science were also electrical engineers. The general study of computer science in those days often dealt both with hardware and software design. Hence, thinking of computational processes as “transducers” was not particularly novel.

▪ It’s possible to encounter the term in early computer science literature — particularly in the context of Digital Signal Processing (DSP) and data flow programming.

▪ In the 1960s, groundbreaking work was happening in graphical computing in MIT’s Lincoln Laboratory using the TX-2 computer system, a precursor to the US Air Force SAGE defense system. Ivan Sutherland’s famous Sketchpad, developed in 1961-1962, was an early example of object prototype delegation and graphical programming using a light pen.

▪ Instead of arrays and array processing, everything is represented as a stream of values in a continuously running, interactive program loop. Each value is processed by each node as it arrives at the parameter input.

▪ You can find similar systems today in Unreal Engine’s Blueprints Visual Scripting Environment or Native Instruments’ Reaktor, a visual programming environment used by musicians to build custom audio synthesizers.

▪ Pipeline of connected graphical operators from Bert Sutherland’s paper

▪ As far as I’m aware, the first book to popularize the term “transducer” in the context of general purpose software-based stream processing was the 1985 MIT text book for a computer science course called “Structure and Interpretation of Computer Programs” (SICP) by Harold Abelson and Gerald Jay Sussman, with Julie Sussman.

▪ However, the use of the term “transducer” in the context of digital signal processing predates SICP.

▪ Note: SICP is still an excellent introduction to computer science coming from a functional programming perspective. It remains my favorite book on the topic.

▪ More recently, transducers have been independently rediscovered and a different protocol developed for Clojure by Rich Hickey (circa 2014), who is famous for carefully selecting words for concepts based on etymology. In this case, I’d say he nailed it, because Clojure transducers fill almost exactly the same niche as transducers in SICP, and they share many common characteristics. However, they are not strictly the same thing.

▪ Transducers as a general concept (not specifically Hickey’s protocol specification) have had considerable impact on important branches of computer science including data flow programming, signal processing for scientific and media applications, networking, artificial intelligence, etc.

▪ As we develop better tools and techniques to express transducers in our application code, they are beginning to help us make better sense of every kind of software composition, including user interface behaviors in web and mobile apps, and in the future, could also serve us well to help manage the complexity of augmented reality, autonomous devices and vehicles, etc.

▪ For the purpose of this discussion, when I say “transducer”, I’m not referring to SICP transducers, though it may sound like I’m describing them if you’re already familiar with transducers from SICP. I’m also not referring specifically to Clojure’s transducers, or the transducer protocol that has become a de facto standard in JavaScript (supported by Ramda, Transducers-JS, RxJS, etc…).

▪ I’m referring to the general concept of a higher-order reducer — a transformation of a transformation

▪ The transducers that I will describe here should be considered pseudo-code to express the concepts

▪ If you want to learn how to use a particular library’s transducers, refer to the library documentation. I’m writing them this way to lift up the hood and let you see how they work without forcing you to learn the protocol at the same time.

▪ If you’re among the large number of software developers who are also musicians, a music analogy may be useful: You can think of transducers like signal processing gear (e.g., guitar distortion pedals, EQ, volume knobs, echo, reverb, and audio mixers).

▪ To record a song using musical instruments, we need some sort of physical transducer (i.e., a microphone) to convert the sound waves in the air into electricity on the wire. Then we need to route that wire to whatever signal processing units we’d like to use. For example, adding distortion to an electric guitar, or reverb to a voice track. Eventually this collection of different sounds must be aggregated together and mixed to form a single signal (or collection of channels) representing the final recording.

▪ In more general terms, you could express it like this:

1 [ Enumerator ] -> [ Transducer ] -> [ Transducer ] -> [ Accumulator ]

▪ You may be experienced with something that behaves a little bit like a transducer if you’ve ever used the map method on arrays. For example, to double a series of numbers:

1 const double = x => x * 2;
2 const arr = [1, 2, 3];
3 
4 const result = arr.map(double);

▪ But what if you want to filter and double a potentially infinite stream of numbers, such as a drone’s telemetry data?

▪ Arrays can’t be infinite, and each stage in the array processing requires you to process the entire array before a single value can flow through the next stage in the pipeline

▪ That same limitation means that composition using array methods will have degraded performance because a new array will need to be created and a new collection iterated over for each stage in the composition.

▪ The alternative is to flow a value directly from the filtered output to the mapping transformation without creating and iterating over a new, temporary array in between.

▪ There are two ways to do that:

Pull: lazy evaluation, or
Push: eager evaluation

▪ A pull API waits until a consumer asks for the next value. A good example in JavaScript is an Iterable, such as the object produced by a generator function. Nothing happens in the generator function until you ask for the next value by calling .next() on the iterator object it returns.

▪ A push API enumerates over the source values and pushes them through the tubes as fast as it can. A call to array.reduce() is a good example of a push API. array.reduce() takes one value at a time from the array and pushes it through the reducer, resulting in a new value at the other end.

▪ For eager processes like array reduce, the process is immediately repeated for each element in the array until the entire array has been processed, blocking further program execution in the meantime.

▪ Transducers don’t care whether you pull or push. Transducers have no awareness of the data structure they’re acting on. They simply call the reducer you pass into them to accumulate new values.

▪ Transducers are higher order reducers: Reducer functions that take a reducer and return a new reducer.

▪ Rich Hickey describes transducers as process transformations, meaning that as opposed to simply changing the values flowing through transducers, transducers change the processes that act on those values.

▪ Generally speaking though, most transducers will need to be partially applied to some arguments to specialize them.

▪ In other words, a map transducer takes a mapping function (called a transform) and a reducer (called the step function), and returns a new reducer. The step function is a reducer to call when we’ve produced a new value to add to the accumulator in the next step.

▪ map applies a function to the values inside some context. In this case, the context is the transducer pipeline. It looks roughly like this:

1 const map = f => step =>
2 (a, c) => step(a, f(c));

▪ You can use it like this:

1 const double = x => x * 2;
2 
3 const doubleMap = map(double);
4 
5 const step = (a, c) => console.log(c);
6 
7 doubleMap(step)(0, 4); // 8
8 doubleMap(step)(0, 21); // 42

The zeros in the function calls at the end represent the initial values for the reducers.

▪ Filter takes a predicate function and only passes through the values that match the predicate. Otherwise, the returned reducer returns the accumulator, unchanged.

▪ Since both of these functions take a reducer and return a reducer, we can compose them with simple function composition:

1 const compose = (...fns) => x => fns.reduceRight((y, f) => f(y), x);

▪ If this seems like a lot of work, keep in mind there are already functional programming libraries that supply common transducers along with utilities such as compose, which handles function composition, and into, which transduces a value into the given empty value, e.g.:

1 const xform = compose(
2 map(inc),
3 filter(isEven)
4 );
5 
6 into([], xform, [1,2,3,4]); // [2, 4]

▪ With most of the required tools already in the tool belt, programming with transducers is really intuitive.

▪ Some popular libraries which support transducers include Ramda, RxJS, and Mori.

▪ Transducers wrap around other transducers under composition. In other words, a transducer says “I’m going to do my thing, and then call the next transducer in the pipeline”, which has the effect of turning the execution stack inside out.

▪ The examples above are naive because they ignore the rules that transducers must follow for interoperability.

▪ As with most things in software, transducers and transducing processes need to obey some rules:

▪ Initialization: Given no initial accumulator value, a transducer must call the step function to produce a valid initial value to act on. The value should represent the empty state. For example, an accumulator that accumulates an array should supply an empty array when its step function is called with no arguments.

▪ Early termination: A process that uses transducers must check for and stop when it receives a reduced accumulator value. Additionally, a transducer step function that uses a nested reduce must check for and convey reduced values when they are encountered.

▪ Completion (optional): Some transducing processes never complete, but those that do should call the completion function to produce a final value and/or flush state, and stateful transducers should supply a completion operation that cleans up any accumulated resources and potentially produces one final value.

▪ Remember this rule: When called with no arguments, a reducer should always return a valid initial (empty) value for the reduction. It’s generally a good idea to obey this rule for any reducer function, including reducers for React or Redux.

▪ It’s possible to signal to other transducers in the pipeline that we’re done reducing, and they should not expect to process any more values. Upon seeing a reduced value, other transducers may decide to stop adding to the collection, and the transducing process (as controlled by the final step() function) may decide to stop enumerating over values. The transducing process may make one more call as a result of receiving a reduced value: The completion call mentioned above. We can signal that intention with a special reduced accumulator value.

▪ What is a reduced value? It could be as simple as wrapping the accumulator value in a special type called reduced. Think of it like wrapping a package in a box and labelling the box with messages like “Express” or “Fragile”. Metadata wrappers like this are common in computing. For example: http messages are wrapped in containers called “request” or “response”, and those container types have headers that supply information like status codes, expected message length, authorization parameters, etc…

▪ The only parts that are strictly required are:

▪ The type lift: A way to get the value inside the type (e.g., the reduced function, in this case)

▪ Type identification: A way to test the value to see if it is a value of reduced (e.g., the isReduced getter)

▪ Value extraction: A way to get the value back out of the type (e.g., valueOf())

▪ With transduce() defined, we can easily create a function that transduces to an array.

▪ First, we need a reducer that reduces to an array:

1 const concatArray = (a, c) => a.concat([c]);

▪ Transducers are not really a single function. They’re made from 3 different functions.

▪ In computer science, the arity of a function is the number of arguments a function takes.

▪ In the case of transducers, there are two arguments to the reducer function, the accumulator and the current value.

▪ JavaScript transducers are a function that take a transducer and return a transducer. The transducer is an object with three methods:

▪ init Return a valid initial value for the accumulator (usually, just call the next step()).

▪ step Apply the transform, e.g., for map(f): step(accumulator, f(current))

▪ result If a transducer is called without a new value, it should handle its completion step (usually step(a), unless the transducer is stateful).

▪ The transducer protocol in JavaScript uses @@transducer/init, @@transducer/step, and @@transducer/result, respectively.

▪ Transducers are composable higher order reducers which can reduce over any underlying data type.

▪ Transducers produce code that can be orders of magnitude more efficient than dot chaining with arrays, and handle potentially infinite data sets without creating intermediate aggregations.

▪ Note: Transducers aren’t always faster than built-in array methods. The performance benefits tend to kick in when the data set is very large (hundreds of thousands of items), or pipelines are quite large (adding significantly to the number of iterations required using method chains). If you’re after the performance benefits, remember to profile.

▪ In production, you can use transducers from Ramda, RxJS, transducers-js, or Mori.

▪ Whenever I need to combine a number of operations, such as map, filter, chunk, take, and so on, I reach for transducers to optimize the process and keep the code readable and clean. Give them a try

▪ In 1920, “The Elements of Style” by William Strunk Jr. was published, which set guidelines for English language style that have lasted the test of time

▪ The following are guidelines, not immutable laws. There may be valid reasons to deviate from them if doing so clarifies the meaning of the code, but be vigilant and self-aware.

▪ The essence of software development is composition. We build software by composing modules, functions, and data structures together.

▪ Modules are simply collections of one or more functions or data structures, and data structures are how we represent program state, but nothing interesting happens until we apply a function.

▪ In JavaScript, there are three kinds of functions:

▪ Communicating functions: Functions which perform I/O.

▪ Procedural functions: A list of instructions, grouped together.

▪ Mapping functions: Given some input, return some corresponding output.

▪ One job for each function: If your function is for I/O, don’t mix that I/O with mapping (calculation). If your function is for mapping, don’t mix it with I/O. By definition, procedural functions violate this guideline.

▪ Whether you realize it or not, you use function composition all the time. You use it whenever you chain methods like .map() or promise.then(), for example. In it’s most basic form, it looks like this: f(g(x)). In algebra this composition is usually written f ∘ g
(often pronounced, “f after g” or “f composed with g”).

▪ You can do the same thing with any functor. A functor is anything you can map over, e.g., arrays (array.map()) or promises (promise.then()).

▪ Virtually every functional programming library has at least two versions of compose utilities: compose(), which applies functions right-to-left, and pipe(), which applies functions left-to-right.

▪ Lodash calls them compose() and flow(). When I use them from Lodash, I always import it like this:

1 import pipe from 'lodash/fp/flow';
2 pipe(g, f)(20); // 42

▪ Name predicates and booleans as if they are yes or no questions:

▪ isActive(user) is better than getActiveStatus(user)

▪ isFirstRun = false;
is better than firstRun = false;

▪ Event handlers and lifecycle methods are an exception to the verb rule because they’re used as qualifiers; instead of expressing what to do, they express when to do it. They should be named so that they read, “, ”.

▪ element.onClick(handleClick) is better than element.click(handleClick)

▪ component.onDragStart(handleDragStart) is better than component.startDrag(handleDragStart)

▪ In the second forms, it looks like we’re trying to trigger the event, rather than respond to it.

▪ I like to name functional mixins using adjectives. You can often use “ing” or “able” suffixes to find useful adjectives. Examples:

▪ const duck = composeMixins(flying, quacking);

▪ const box = composeMixins(iterable, mappable);

▪ Developers frequently string together sequences of events in a procedure; a group of loosely related statements designed to run one after the other. An excess of procedures is a recipe for spaghetti code.

▪ Consider the following sequence:

1 const drawUserProfile = ({ userId }) => {
2 const userData = loadUserData(userId);
3 const dataToDisplay = calculateDisplayData(userData);
4 renderProfileData(dataToDisplay);
5 };

This function is really handling three different things: loading data, calculating view state from loaded data, and rendering.

▪ In most modern front-end application architectures, each of these concerns is considered separately. By separating these concerns, we can easily mix and match different functions for each concern.

▪ Separating the functions allows you to test units in isolation from each other.

▪ The result is software with responsibilities more clearly delineated: Each component can reuse the same structure and lifecycle hooks, and the software performs better; we don’t repeat work that doesn’t need to be repeated in subsequent cycles.

▪ Many frameworks and boilerplates prescribe a method of program organization where files are grouped by technical type. This is fine if you’re building a small calculator or To Do app, but for larger projects, it’s usually better to group files together by feature.

▪ For example, consider two alternative file hierarchies for a To Do app by type and feature.

Grouped by type:

1 .
2 ├── components
3 │ ├── todos
4 │ └── user
5 ├── reducers
6 │ ├── todos
7 │ └── user
8 └── tests
9 ├── todos
10 └── user

▪ Grouped by feature:

1 .
2 ├── todos
3 │ ├── component
4 │ ├── reducer
5 │ └── test
6 └── user
7 ├── component
8 ├── reducer
9 └── test

▪ When you group files together by feature, you avoid scrolling up and down in your file list to find all the files you need to edit to get a single feature working.

Colocate files related by feature

▪ If Statements

1 if (err) return reject(err);
2 // do something...

…is better than:

1 if (!err) {
2 // ... do something
3 } else {
4 return reject(err);
5 }

▪ Prefer strong negative statements.

Sometimes we only care about a variable if it’s missing, so using a positive name would force us to negate it with the ! operator. In those cases, prefer a strong negative form. The word “not” and the ! operator create weak expressions.

if (missingValue)
is better than if (!hasValue)
if (anonymous)
is better than if (!user)
if (isEmpty(thing))
is better than if (notDefined(thing))

▪ Avoid null and undefined arguments in function calls.

Don’t require function callers to pass undefined or null in place of an optional parameter. Prefer named options objects instead:

▪ Identify the parts that are the same, and build an abstraction that allows you to supply only the parts that are different. This is exactly what libraries and frameworks do for us.

▪ UI components are a great example. Less than a decade ago, it was common to mingle UI updates using jQuery with application logic and network I/O. Then people began to realize that we could apply MVC to web apps on the client-side, and people began to separate models from UI update logic.

Eventually, web apps landed on a component model approach, which lets us declaratively model our components using things like JSX or HTML templates.

▪ What we ended up with is a way of expressing UI update logic the same way for every component, rather than different imperative code for each one.

▪ For those familiar with components, it’s pretty easy to see how each component works: There’s some declarative markup expressing the UI elements, event handlers for hooking up behaviors, and lifecycle hooks for attaching callbacks that will run when we need them to.

▪ Code should be simple, not simplistic.

▪ Assume the reader knows nothing about the implementation, but do not assume that the reader is stupid, or that the reader doesn’t know the language.

▪ Be clear, but don’t dumb it down. To dumb things down is both wasteful and insulting. Make the investment in practice and familiarity in order to gain a better programming vocabulary, and a more vigorous style.

▪ One of the biggest complaints I hear about TDD and unit tests is that people struggle with all of the mocking required to isolate units.

▪ On the other end of the spectrum, it’s common to see developers get so sucked into the dogma of TDD that they think they absolutely must achieve 100% code coverage, by any means necessary, even if that means they have to make their codebase more complex to pull it off.

▪ I frequently tell people that mocking is a code smell, but most developers pass through a stage in their TDD skills where they want to achieve 100% unit test coverage, and can’t imagine a world in which they do not use mocks extensively. In order to squeeze mocks into their application, they tend to wrap dependency injection functions around their units or (worse), pack services into dependency injection containers.

▪ Angular takes this to an extreme by baking dependency injection right into all Angular component classes, tempting users to view dependency injection as the primary means of decoupling. But dependency injection is not the best way to accomplish decoupling.

▪ The process of learning effective TDD is the process of learning how to build more modular applications.

▪ TDD tends to have a simplifying effect on code, not a complicating effect. If you find that your code gets harder to read or maintain when you make it more testable, or you have to bloat your code with dependency injection boilerplate, you’re doing TDD wrong.

▪ Maximizing code coverage brings diminishing returns – the closer you get to 100% coverage, the more you have to complicate your application code to get even closer, which can subvert the important goal of reducing bugs in your application.

▪ “A code smell is a surface indication that usually corresponds to a deeper problem in the system.” ~ Martin Fowler

▪ A code smell does not mean that something is definitely wrong, or that something must be fixed right away. It is a rule of thumb that should alert you to a possible opportunity to improve something.

▪ A mock is a test double that stands in for real implementation code during the unit testing process

▪ The term “mock” is also used more generally to refer to the use of any kind of test double. For the purpose of this text, we’ll use the words “mock” and “test double” interchangeably to match popular usage

▪ What is a unit test?

Unit tests test individual units (modules, functions, classes) in isolation from the rest of the program.

▪ Contrast unit tests with integration tests, which test integrations between two or more units, and functional tests, which test the application from the point of view of the user, including complete user interaction workflows from simulated UI manipulation, to data layer updates, and back to the user output (e.g., the on-screen representation of the app).

▪ Functional tests are a subset of integration tests, because they test all of the units of an application, integrated in the context of the running application.

▪ In general, units are tested using only the public interface of the unit (aka “public API” or “surface area”). This is referred to as black box testing. Black box testing leads to less brittle tests, because the implementation details of a unit tend to change more over time than the public API of the unit.

▪ If you use white box testing, where tests are aware of implementation details, any change to the implementation details could break the test, even if the public API continues to function as expected. In other words, white-box testing leads to wasted rework.

▪ Code coverage refers to the amount of code covered by test cases.

▪ Coverage reports can be created by instrumenting the code and recording which lines were exercised during a test run. In general, we try to produce a high level of coverage, but code coverage starts to deliver diminishing returns as it gets closer to 100%.

▪ In my experience, increasing coverage beyond ~90% seems to have little continued correlation with lower bug density.

▪ What most people don’t realize is that there are two kinds of coverage:

▪ Code coverage: how much of the code is exercised, and

▪ Case coverage: how many of the use-cases are covered by the test suites

▪ Because use-cases may involve the environment, multiple units, users, and networking conditions, it is impossible to cover all required use-cases with a test suite that only contains unit tests

▪ Unit tests by definition test units in isolation, not in integration, meaning that a test suite containing only unit tests will always have close to 0% case coverage for integration and functional use-case scenarios.

▪ 100% code coverage does not guarantee 100% case coverage.

▪ Coupling is the degree to which a unit of code (module, function, class, etc…) depends upon other units of code. Tight coupling, or a high degree of coupling, refers to how likely a unit is to break when changes are made to its dependencies. In other words, the tighter the coupling, the harder it is to maintain or extend the application. Loose coupling reduces the complexity of fixing bugs and adapting the application to new use-cases.

▪ Coupling takes different forms:

▪ Subclass coupling: Subclasses are dependent on the implementation and entire hierarchy of the parent class: the tightest form of coupling available in OO design

▪ Control dependencies: Code that controls its dependencies by telling them what to do, e.g., passing method names, etc… If the control API of the dependency changes, the dependent code will break.

▪ Mutable state dependencies: Code that shares mutable state with other code, e.g., can change properties on a shared object. If relative timing of mutations change, it could break dependent code.

▪ State shape dependencies: Code that shares data structures with other code, and only uses a subset of the structure. If the shape of the shared structure changes, it could break the dependent code.

▪ Event/message coupling: Code that communicates with other units via message passing, events, etc…

▪ Tight coupling has many causes:

▪ Mutation vs immutability

▪ Side-Effects vs purity/isolated side-effects

▪ Responsibility overload vs Do One Thing (DOT)

▪ Procedural instructions vs describing structure

▪ Imperative composition vs declarative composition

▪ Imperative and object-oriented code is more susceptible to tight coupling than functional code. That doesn’t mean that programming in a functional style makes your code immune to tight coupling, but functional code uses pure functions as the elemental unit of composition, and pure functions are less vulnerable to tight coupling by nature.

▪ Structure, not instructions: Pure functions can be safely memoized, meaning that, if the system had infinite memory, any pure function could be replaced with a lookup table that uses the function’s input as an index to retrieve a corresponding value from the table.

▪ The essence of all software development is the process of breaking a large problem down into smaller, independent pieces (decomposition) and composing the solutions together to form an application that solves the large problem (composition).

▪ When you use generic composition utilities, each element of the composition can be unit tested in isolation without mocking the others

▪ You can compose functions manually (imperatively), or automatically (declaratively). In languages without first-class functions, you don’t have much choice. You’re stuck with imperative. In JavaScript (and almost all the other major popular languages), you can do it better with declarative composition.

▪ Message passing/pubsub

▪ Ironically, most of the sources of coupling are mechanisms originally designed to reduce coupling. That makes sense, because in order to recompose our smaller problem solutions into a complete application, they need to integrate and communicate somehow.

▪ There are good ways, and bad ways. The sources that cause tight coupling should be avoided whenever it’s practical to do so. The loose coupling options are generally desirable in a healthy application.

▪ You might be confused that I classified dependency injection containers and dependency injection parameters in the “tight coupling” group, when so many books and blog post categorize them as “loose coupling”.

▪ That bears repeating:

Don’t unit test I/O. I/O is for integrations. Use integration tests, instead.

It’s perfectly OK to mock and fake for integration tests.

▪ I’m hopeful that we’ll someday get a nice set of immutable datatypes similar to Clojure’s in JavaScript, but I’m not holding my breath.

▪ Pure functions can also be memoized, meaning that you don’t have to build the whole object again if you’ve seen the same inputs before. You can trade computation complexity for memory and store pre-calculated values in a lookup table. For computationally expensive processes which don’t require unbounded memory, this may be a great optimization strategy.

▪ Another property of pure functions is that, because they have no side-effects, it’s safe to distribute complex computations over large clusters of processors, using a divide-and-conquer strategy.

▪ In other words, mutation isn’t always faster, and it is often orders of magnitude slower because it prevents these kinds of macro-optimizations.

▪ There are several strategies that can help you isolate side-effects from the rest of your program logic. Here are some of them:

▪ Use pub/sub to decouple I/O from views and program logic. Rather than directly triggering side-effects in UI views or program logic, emit an event or action object describing an event or intent.

▪ Isolate logic from I/O e.g., compose functions which return promises using asyncPipe().

▪ Use objects that represent future computations rather than directly triggering computation with I/O, e.g., call() from redux-saga doesn’t actually call a function

▪ Instead, it returns an object with a reference to a function and its arguments, and the saga middleware calls it for you. That makes call() and all the functions that use it pure functions, which are easy to unit test with no mocking required.

▪ Pub/sub is short for the publish/subscribe pattern. In the publish/subscribe pattern, units don’t directly call each other. Instead, they publish messages that other units (subscribers) can listen to.

▪ Publishers don’t know what (if any) units will subscribe, and subscribers don’t know what (if any) publishers will publish.

▪ Pub/sub is baked into the Document Object Model (DOM). Any component in your application can listen to events dispatched from DOM elements, such as mouse movements, clicks, scroll events, keystrokes, and so on.

▪ Pub/sub is also baked into Redux. In Redux, you create a global model for application state (called the store). Instead of directly manipulating models, views and I/O handlers dispatch action objects to the store.

▪ An action object has a special key, called type which various reducers can listen for and respond to.

▪ Additionally, Redux supports middleware, which can also listen for and respond to specific action types. This way, your views don’t need to know anything about how your application state is handled, and the state logic doesn’t need to know anything about the views.

▪ It also makes it trivial to patch into the dispatcher via middleware and trigger cross-cutting concerns, such as action logging/analytics, syncing state with storage or the server, and patching in realtime communication features with servers and network peers.

▪ The idea is that logic and I/O don’t mix well, so we want to remove the logic from the I/O dependent code

▪ The strategy used by redux-saga is to use objects that represent future computations. The idea is similar to returning a monad, except that it doesn’t always have to be a monad that gets returned

▪ Monads are capable of composing functions with the chain operation, but you can manually chain functions using imperative-style code, instead.

▪ All this stuff about using better architecture is great, but in the real world, we have to use other people’s APIs, and integrate with legacy code, and there are lots of APIs that aren’t pure

▪ The server definition file for an express app is by definition the app’s main integration point. Testing an express handler is by definition testing an integration between your program logic, express, and all the handlers for that express app. You absolutely should not skip integration tests even if you can achieve 100% unit test coverage

▪ Instead of trying to unit test this file, isolate your program logic into separate units, and unit test those files. Write real integration tests for the server file, meaning you’ll actually hit the network, or at least create the actual http messages, complete with headers using a tool like supertest.

▪ Because integration tests test collaborative integrations between units, it’s perfectly OK to fake servers, network protocols, network messages, and so on in order to reproduce all the various conditions you’ll encounter during communication with other units, potentially distributed across clusters of CPUs or separate machines on a network.

▪ Sometimes you’ll want to test how your unit will communicate with a 3rd party API, and sometimes those API’s are prohibitively expensive to test for real.

▪ There are lots of useful integration testing tools that throttle network bandwidth, introduce network lag, produce network errors, and otherwise test lots of other conditions that are impossible to test using unit tests which mock away the communication layer.
