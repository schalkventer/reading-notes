Data-Oriented Programming: Reduce Software Complexity (2022)

Yehonathan Sharvit

───────────────

▪ Every programming principle, every design method, every architecture style, and even most language features are about organizing complexity while allowing adaptation.

▪ Two characteristics—immutable data and turning parts of the program into data inside the program itself—drew me to Clojure in 2009 and more recently to Yehonathan Sharvit’s Data-Oriented Programming.

▪ Data-oriented programming, as you will see, promises to reduce accidental complexity, and raise the level of abstraction you work at.

▪ If we let data be data, we get simpler code and far fewer dependencies on hundred-megabyte framework libraries.

▪ So, whatever happened to the OOP virtues of encapsulation, inheritance, and polymorphism? It turns out we can decomplect these and get each of them à la carte.

▪ (In my opinion, inheritance of implementations is the least important of these, even though it is often the first one taught. I now prefer inheritance of interfaces via protocols and shared function signatures.)

▪ Data-oriented programming offers polymorphism of the “traditional” kind: dispatch to one of many functions based on the type of the first argument (in an OO language, this is a disguise for the method’s first argument. It just happens it goes before the “.”).

▪ And as for encapsulation, we must still apply it to the organizing logic of our program. We encapsulate subsystems, not values

▪ In the words of Alan Perlis, “It is better to have one hundred functions operate on one data structure than ten functions on ten data structures.”

▪ Projects were thrilling at the start. I loved the feeling of plugging pieces together and seeing the app come to life. But once I got it working, I ran into problems. I couldn’t change one part without keeping all the other models in mind.

▪ He was explaining functional programming and contrasting it with OO, which he derisively called “place-oriented programming.”

▪ Something about how it’s easier to build systems that manipulate data literals (like maps and arrays) instead of custom objects

▪ good design is about pulling things apart. It’s not just about getting the code to work, no matter how ugly. It’s about untangling the parts from each other so you can change one thing without breaking everything else.

▪ For me, it also went further. It pulled apart a way of programming from a specific language. I might never make that switch to Clojure, and I don’t feel like I have to anymore. Data-Oriented Programming helped me see new possibilities in the languages I know and the multitude of new frameworks appearing every day.

▪ I have been a software engineer since 2000. For me, there is clearly a “before” and an “after” 2012. Why 2012? Because 2012 is the year I discovered Clojure.

▪ Together, we discovered that what was so special about Clojure was not features, but principles.

▪ Data-Oriented Programming was written to help developers reduce the complexity of the systems they build

▪ The ideas in this book are mostly applicable to systems that manipulate information—systems like frontend applications, backend web servers, or web services.

▪ Data-Oriented Programming is for frontend, backend, and full stack developers with a couple of years of experience in a high-level programming language like Java, C#, C++, Ruby, or Python

▪ For object-oriented programming developers, some ideas presented in this book might take them out of their comfort zone and require them to unlearn some of the programming paradigms they feel so much at ease with. For functional programming developers, this book will be a little easier to digest but should deliver some nice surprises as well.

▪ JavaScript supports both functional programming and object-oriented programming styles

▪ The tendency of OOP to increase system complexity

▪ What makes OOP systems hard to understand

▪ The cost of mixing code and data together into objects

▪ This complexity is not related to the syntax or the semantics of a specific OOP language. It is something that is inherent to OOP’s fundamental insight—programs should be composed from objects, which consist of some state, together with methods for accessing and manipulating that state.

▪ Over the years, OOP ecosystems have alleviated this complexity by adding new features to the language (e.g., anonymous classes and anonymous functions) and by developing frameworks that hide some of this complexity, providing a simpler interface for developers (e.g., Spring and Jackson in Java). Internally, the frameworks rely on the advanced features of the language such as reflection and custom annotations.

▪ Before rushing to his laptop to code the system, Theo grabs a sheet of paper, much bigger than a napkin, and starts to draw a UML class diagram of the system that will implement the Klafim prototype.

▪ Theo is an object-oriented programmer. For him, there is no question—every business entity is represented by an object, and every object is made from a class.

▪ ►Note The design presented here doesn’t pretend to be the smartest OOP design: experienced OOP developers would probably use a couple of design patterns to suggest a much better design. This design is meant to be naive and by no means covers all the features of the system.

▪ There are four types of arrows in my class diagram: composition, association, inheritance, and usage.

▪ In a composition relation, when one object dies, the other one also dies. While in an association relation, each object has an independent life cycle.

▪ A composition relation is represented by a plain diamond at one edge and an optional star at the other edge.

▪ Dashed arrows indicate usage relations (figure 1.4), for instance, when a class uses a method of another class.

▪ Plain arrows with empty triangles represent class inheritance (figure 1.5), where the arrow points towards the superclass.

▪ ►Note In this book, we use the terms code and behavior interchangeably.

▪ OOP has a tendency to create complex systems.

▪ Throughout this book, the type of complexity I refer to is that which makes systems hard to understand as defined in the paper, “Out of the Tar Pit,” by Ben Moseley and Peter Marks (2006), available at http://mng.bz/enzq.

▪ Keep in mind that complexity and simplicity (like hard and easy) are not absolute but relative concepts. We can compare the complexity of two systems and determine whether system A is more complex (or simpler) than system B.

▪ Complexity in the context of this book means hard to understand.

▪ According to DOP, the main sources of complexity in Theo’s system (and of many traditional OOP systems) are that

Code and data are mixed.

Objects are mutable.

Data is locked in objects as members.

Code is locked into classes as methods.

▪ This analysis is similar to what functional programming (FP) thinks about traditional OOP.

▪ However, as we will see throughout the book, the data approach that DOP takes in order to reduce system complexity differs from the FP approach

▪ DOP is compatible both with OOP and FP.

▪ In OOP, code and data are mixed together in classes: data as members and code as methods.

▪ From a system analysis perspective, the fact that code and data are mixed together makes the system complex in the sense that entities tend to be involved in many relations

▪ In figure 1.11, we take a closer look at the Member class. Member is involved in five relations: two data relations and three code relations

▪ Imagine for a moment that we were able, somehow, to split the Member class into two separate entities:

MemberCode for the code

MemberData for the data

▪ A system where every class is split into two independent parts, code and data, is simpler than a system where code and data are mixed.

▪ The fact that the two subsystems are independent means that each subsystem can be understood separately and in any order

▪ The resulting system not simpler by accident ; it is a logical consequence of separating code from data.

▪ A system made of multiple simple independent parts is less complex than a system made of a single complex part.

▪ The correct answer is ... in a single-threaded environment, it displays true, while in a multi-threaded environment, it’s unpredictable.

▪ In fact, with a slight modification, the same kind of code unpredictability could occur even in a single-threaded environment like JavaScript, when data is modified via asynchronous code

▪ This unpredictable behavior of the second listing is one of the annoying consequences of OOP

▪ We will see later in the book that DOP treats every piece of data in the same way: both primitive types and collection types are immutable values. This value treatment for all citizens brings serenity to DOP developers’ minds, and more brain cells are available to handle the interesting pieces of the applications they build.

▪ One way to avoid writing the same code twice in OOP involves class inheritance. Indeed, when every requirement of the system is known up front, you design your class hierarchy is such a way that classes with common behavior derive from a base class.

▪ pay attention to the diamond problem VIPMember introduced in his class diagram due to multiple inheritance: VIPMember extends both Member and UserWithBookItemRight, which both extend User.

▪ Theo suddenly notices that he has three diamonds in his class diagram—not gemstones but three “Deadly Diamonds of Death” as OOP developers sometimes name the ambiguity that arises when a class D inherits from two classes B and C, where both inherit from class A!

▪ In OOP, prefer composition over class inheritance

▪ Complexity in the context of this book means hard to understand.

▪ In a composition relation, when one object dies, the other one also dies.

▪ In an association relation, each object has an independent life cycle.

▪ The first insight of DOP is that we can decrease the complexity of our systems by separating code from data

▪ Principle #1 Separate code from data such that the code resides in functions, whose behavior doesn’t depend on data that is somehow encapsulated in the function’s context.

▪ ve never heard of data-oriented programming. Is it a new concept?

    JOE   Yes and no. Most of the foundational ideas of data-oriented programming, or DOP as we like to call it, are well known to programmers as best practices. The novelty of DOP, however, is that it combines best practices into a cohesive whole.

▪ Take, for instance, the first insight of DOP. It’s about the relations between code and data.

▪ Actually, DOP is against data encapsulation.

  THEO   Why is that? I thought data encapsulation was a positive programming paradigm.

▪ DOP is against data encapsulation.

▪ So, if I want to adopt DOP, do I need to get rid of object-oriented programming and learn functional programming?

▪ No, DOP principles are language-agnostic. They can be applied in both object-oriented and functional programming languages.

▪ That’s a relief! I was afraid that you were going to teach me about monads, algebraic data types, and higher order functions.

▪ Data is represented by data entities that only hold members.

▪ Code is aggregated into modules where all functions are stateless.

▪ What do you mean by data entities?

    JOE   I mean the parts of your system that hold information.

▪ Data entities are the parts of your system that hold information.

▪ One way to discover the data entities of a system is to look for nouns and noun phrases in the requirements of the system.

▪ The most precise way to visualize the data entities of a DOP system is to draw a data entity diagram with different arrows for association and composition

▪ One way to think about that is to identity the functionality of your system.

Theo looks again at Nancy’s requirements. This time he highlights the verb phrases that represent functionality.

Highlighting terms in the requirements that correspond to functionality

▪ Now, tell me what functionality needs to be exposed to the outside world?

  THEO   What do you mean by exposed to the outside world?

    JOE   Imagine that the Library Management System exposes an API over HTTP. What functionality would be exposed by the HTTP endpoints?

▪ Now give each exposed function a short name and gather them together in a module box called Library.

▪ The first step in designing the code part of a DOP system is to aggregate the exposed functions into a single module

▪ To me it looks like a class. What’s the difference between a module and a class?

▪ A module is an aggregation of functions. In OOP, a module is represented by a class, but in other programming languages, it might be a package or a namespace.

▪ The important thing about DOP code modules is that they contain only stateless functions.

  THEO   You mean like static methods in Java?

    JOE   Yes, and the classes of these static methods should not have any data members.

▪ So, how do the functions know what piece of information they operate on?

    JOE   Easy. We pass that as the first argument to the function.

▪ In traditional OOP, the state of the object is an implicit argument to the methods of the object.

▪ In DOP, functions of a code module are stateless. They receive the data that they manipulate as an explicit argument, which is usually the first argument

▪ What’s a high-level design in DOP?

    JOE   A high-level design in DOP is the definition of modules and the interaction between them.

▪ Are there any guidelines to help me define the modules?

    JOE   Definitely. The high-level modules of the system correspond to the high-level data entities.

  THEO   You mean the data entities that appear in the data mind map?

    JOE   Exactly!

▪ There is a clear separation of concerns between the code and the data.

▪ There is a single kind of relation between DOP modules—the usage relation. A module uses code from another module. There’s no association, no composition, and no inheritance between modules. That’s what makes a DOP module diagram easy to understand.

▪ I understand why there is no association and no composition between DOP modules. After all, association and composition are data relations.

▪ Functions receive the data they manipulate as their first argument.

▪ It’s Theo’s first piece of DOP code and passing around all those data objects—libraryData, libraryData.userManagement, and libraryData.catalog—feels a bit awkward. But he did it! Joe looks at Theo’s code and seems satisfied.

▪ DOP systems are flexible. Quite often they adapt to changing requirements without changing the system design.

▪ For now, it’s OK to think about bookItemInfo as an object. Later on, I will show you how to we represent data in DOP.

▪ DOP principles are language-agnostic.

▪ DOP principle #1 is to separate code from data

▪ Data entities are the parts of your system that hold information

▪ DOP is against data encapsulation.

▪ When code is separated from data, we have the freedom to design code and data in isolation.

▪ We discover the data entities of our system and sort them into high-level groups, either as a nested list or as a mind map.

▪ A DOP system is easier to understand than a traditional OOP system because the system is split into two parts: data entities and code modules.

▪ In DOP, a code module is an aggregation of stateless functions.

▪ The high-level modules of a DOP system correspond to high-level data entities.

▪ The only kind of relation between code modules is the usage relation.

▪ The only kinds of relation between data entities are the association and the composition relation.

▪ For a discussion of polymorphism in DOP, see chapter 13.

▪ In contrast to traditional OOP, where system design tends to involve a rigid class hierarchy, DOP prescribes that we represent our data model as a flexible combination of maps and arrays (or lists), where we can access each piece of information via an information path.

▪ Principle #2 Represent data entities with generic data structures.

▪ We increase system flexibility when we represent records as string maps and not as objects instantiated from classes

▪ Data becomes a first-class citizen powered by generic functions to add, remove, or rename fields.

▪ We refer to maps that have strings as keys as string maps.

▪ The dependency between the code that manipulates data and the data is a weak dependency.

▪ The code only needs to know the keys of specific fields in the record it wants to manipulate. The code doesn’t even need to know about all the keys in the record, only the ones relevant to it.

▪ When we design the data part of our system, we’re free to do it in isolation

▪ Oh, right. I remember you telling me how that makes a DOP system simpler than OOP. Separation of concerns is a design principle I’m used to in OOP.

▪ By positional collection, we mean a collection where the elements are in order (like a list or an array). By index, we mean a collection where the elements are accessible via a key (like a hash map or a dictionary).

▪ Can you tell me what the three kinds of data aggregations are in your diagram (and, in fact, in any data entity diagram)?

  THEO   Let’s see ... we have positional collections like authors in Book. We have indexes like booksByIsbn in Catalog. I can’t find the third one.

    JOE   The third kind of data aggregation is what we’ve called, until now, an “entity” (like Library, Catalog, Book, etc.), and the common term for entity in computer science is record.

▪ A record is a data structure that groups together related data items. It’s a collection of fields, possibly of different data types.

▪ Is it correct to say that a data entity diagram consists only of records, positional collections, and indexes?

    JOE   That’s correct.

▪ Code consists of static functions that receive data as an explicit argument.

▪ Data entities are modeled as records, and the relations between records are represented by positional collections and indexes.

▪ In dynamically-typed languages like JavaScript, Python, and Ruby, data representation feels natural. While in statically-typed languages like Java and C#, it is a bit more cumbersome.

▪ What do you mean by a homogeneous map?

    JOE   I mean that all the values of the map are of the same kind. For example, in a Book index, all the values are Book, and in an author index, all the values are Author, and so forth.

▪ A homogeneous map is a map where all the values are of the same type. A heterogeneous map is a map where the values are of different types.

▪ And, if I’m in Java?

    JOE   It’s a bit more tedious, but still doable with the immutable Map and List static factory methods.

▪ In classic OOP, the fact that data is instantiated only via classes brings safety. But this safety comes at the cost of flexibility.

▪ There’s a tradeoff between flexibility and safety in a data model.

▪ there are third-party libraries that provide data-manipulation facilities. A popular data manipulation library in the JavaScript ecosystem is Lodash.

▪ Lodash has been ported to Java, C#, Python, and Ruby.

▪ See how straightforward it is to visualize any part of the system data inside a program? The reason is that data is represented as data!

▪ Oh, does it? I’m not so sure! In OOP, data is usually represented by objects, which makes it more challenging to visualize data inside a program

▪ Great question! In fact, in a DOP system, every piece of information has an information path from which we can retrieve the information.

▪ In DOP, you can retrieve every piece of information via a path and a generic function.

▪ The important thing is not that the code is concise, but that the code contains no abstractions. It’s just data manipulation!

Joe responds with a smile that says, “You got it, my friend!”

▪ In DOP, many parts of our code base tend to be just about data manipulation with no abstractions.

▪ Instead of maintaining type information about a record, use a feature field (e.g., isVIP).

▪ From what you taught me today, I understand that in DOP, we are encouraged to treat data as data without the filter of our classes.

▪ DOP principle #2 is to represent data entities with generic data structures.

▪ We refer to maps that have strings as keys as string maps.

▪ By positional collection, we mean a collection where the elements are in order (like a list or an array).

▪ A record is a data structure that groups together related data items. It’s a collection of fields, possibly of different data types.

▪ A homogeneous map is a map where all the values are of the same type.

▪ A heterogeneous map is a map where the values are of different types.

▪ In DOP, we represent a record as a heterogeneous string map.

▪ A data entity diagram consists of records whose values are either primitives, positional collections, or indexes.

▪ The relation between records in a data entity diagram is either composition or association.

▪ There is a tradeoff between flexibility and safety in a data model.

▪ We manipulate data with generic functions

▪ Generic functions are provided either by the language itself or by third-party libraries like Lodash.

▪ The weak dependency between code and data makes it is easier to adapt to changing requirements.

▪ When data is represented as data, it is straightforward to visualize system data.

▪ Instead of maintaining type information about a record, we use a feature field.

▪ There is no significant performance hit for accessing a field in a map instead of a class member.

▪ In DOP, you can retrieve every piece of information via an information path and a generic function.

▪ In DOP, many parts of our code base tend to be just about data manipulation with no abstractions.

▪ 1 A lapalissade is an obvious truth—a truism or tautology—that produces a comical effect.

▪ In this chapter, we illustrate how DOP deals with mutations (requests that change the system state).

▪ Instead of updating the state in place, we maintain multiple versions of the system data

▪ At a specific point in time, the system state refers to a specific version of the system data.

▪ Principle #3 Data is immutable.

▪ The maintenance of multiple versions of the system data requires the data to be immutable. This is made efficient both in terms of computation and memory via a technique called structural sharing, where parts of the data that are common between two versions are shared instead of being copied

▪ In DOP, a mutation is split into two distinct phases:

In the calculation phase, we compute the next version of the system data.

In the commit phase, we move the system state forward so that it refers to the version of the system data computed by the calculation phase.

▪ This distinction between calculation and commit phases allows us to reduce the part of our system that is stateful to its bare minimum. Only the code of the commit phase is stateful, while the code in the calculation phase of a mutation is stateless and is made of generic functions similar to the code of a query.

▪ A mutation is an operation that changes the state of the system.

▪ We adopt a multi-version state approach, similar to what a version control system like Git does; we manage different versions of the system data. At a specific point in time, the state of the system refers to a version of the system data. After a mutation is executed, we move the reference forward.

▪ The data is immutable, but the state reference is mutable.

▪ In a simple application, previous versions are automatically removed by the garbage collector. But, in some cases, we maintain historical references to previous versions of the data.

▪ Structural sharing provides an efficient way (both in terms of memory and computation) to create a new version of the data by recursively sharing the parts that don’t need to change.

▪ To me, it’s a bit weird that immutable functions return an updated version of the data instead of changing it in place.

    JOE   It was also weird for me when I first encountered immutable data in Clojure seven years ago.

  THEO   How long did it take you to get used to it?

    JOE   A couple of weeks.

▪ It’s not well-known by programmers yet, but it’s quite a powerful programming paradigm. From what I’ve seen so far, it makes programming much simpler.

▪ The answer is that mutating data via the native hash map setter is forbidden. All the data manipulation must be done via immutable functions

▪ All data manipulation must be done with immutable functions. It is forbidden to use the native hash map setter.

▪ When you say “forbidden,” you mean that it’s up to the developer to make sure it doesn’t happen. Right?

    JOE   Exactly.

▪ Yes, there is a way to ensure the immutability of the data at the level of the data structure. It’s called persistent data structures

▪ Are persistent data structures also efficient in terms of memory and computation?

    JOE   Actually, the way data is organized inside persistent data structures make them even more efficient than immutable functions.

▪ Persistent data structures are immutable at the level of the data. There is no way to mutate them, even by mistake.

▪ He shows it to Theo:

Immutable.js in JavaScript at https://immutable-js.com/

Paguro in Java at https://github.com/GlenKPeterson/Paguro

Immutable Collections in C# at http://mng.bz/y4Ke

Pyrsistent in Python at https://github.com/tobgu/pyrsistent

Hamster in Ruby at https://github.com/hamstergem/hamster

▪ Why not use persistent data structures instead of immutable functions?

    JOE   The drawback of persistent data structures is that they are not native. This means that working with them requires conversion from native to persistent and from persistent to native.

▪ That’s one of the reasons why I love Clojure—the native data structures of the language are immutable!

▪ The commit phase moves the system state forward

▪ The responsibility of the commit phase is to move the system state forward to the version of the state returned by the calculation phase.

▪ The code is made of two classes: System, a singleton stateful class that implements the mutations, and SystemState, a singleton stateful class that manages the system state.

▪ For now, the important thing to notice is that the code of the calculation phase is stateless and is decoupled from the code of the commit phase, which is stateful.

▪ In DOP, we validate the system data as a whole. Data validation is decoupled from data manipulation

▪ Another advantage of the multi-version state approach with immutable data that is manipulated via structural sharing is that we can keep track of the history of all the versions of the data without exploding the memory of our program.

▪ Structural sharing allows us to keep many versions of the system state without exploding memory use

▪ DOP principle #3 states that data is immutable.

▪ A mutation is an operation that changes the state of the system.

▪ In a multi-version approach to state management, mutations are split into calculation and commit phases.

▪ All data manipulation must be done via immutable functions. It is forbidden to use the native hash map setter.

▪ Structural sharing allows us to create new versions of data efficiently (in terms of memory and computation), where data that is common between the two versions is shared instead of being copied.

▪ Structural sharing creates a new version of the data by recursively sharing the parts that don’t need to change

▪ A mutation is split in two phases: calculation and commit

▪ We validate the system data as a whole. Data validation is decoupled from data manipulation

▪ The fact that the code for the commit phase is common to all the mutations allows us to validate the system state in a central place before we update the state

▪ Restoring the system to one of its previous states is straightforward due to the clear separation between the calculation phase and the commit phase.

▪ Usually, in a production system, mutations occur concurrently. Moving the state forward naively like we did in the previous chapter is not appropriate.

▪ In DOP, because only the code of the commit phase is stateful, that allows us to use an optimistic concurrency control strategy that doesn’t involve any locking mechanism.

▪ The modifications to the code are not trivial, as we have to implement an algorithm that reconciles concurrent mutations. But the modifications impact only the commit phase.

▪ This chapter requires more of an effort to grasp. The flow of the reconciliation algorithm is definitely not trivial, and the implementation involves a nontrivial recursion.

▪ Locks hit performance, and if you’re not careful, your system could get into a deadlock.

▪ In DOP, we use a lock-free strategy called optimistic concurrency control. It’s a strategy that allows databases like Elasticsearch to be highly scalable.

▪ Optimistic concurrency control and DOP fit together well. As you will see in a moment, optimistic concurrency control is super efficient when the system data is immutable.

▪ Optimistic concurrency control with immutable data is super efficient.

▪ Optimistic concurrency control occurs when we let mutations ask forgiveness instead of permission.

▪ The calculation phase does its calculation as if it were the only mutation running. The commit phase is responsible for reconciling concurrent mutations when they don’t conflict or for aborting the mutation.

▪ Dealing with state is never trivial. But the good news is that the code for the reconciliation logic in the commit phase is universal.

▪ Does that mean that the same code for the commit phase can be used in any DOP system?

    JOE   Definitely. The code that implements the commit phase assumes nothing about the details of the system except that the system data is represented as an immutable map.

▪ The implementation of the commit phase in optimistic concurrency control is universal. It can be used in any system where the data is represented by an immutable hash map.

▪ Another cool thing is that handling concurrency doesn’t require any changes to the code in the calculation phase

▪ From the calculation phase perspective, the next version of the system data is computed in isolation as if no other mutations were running concurrently.

▪ Could you give me some examples of conflicting concurrent mutations?

    JOE   Sure. One example would be two members trying to borrow the same book copy. Another example might be when two librarians update the publication year of the same book.

▪ What do you mean exactly by reconciliation logic?

    JOE   It’s quite similar to what could happen in Git when you merge a branch back into the main branch.

▪ In DOP, the reconciliation algorithm in the commit phase is quite similar to a merge in Git, except instead of a manual conflict resolution, we abort the mutation.

▪ There are three possibilities to reconcile between possible concurrent mutations: fast-forward, three-way merge, or abort.

▪ If we are in a situation where the current state is the same as the previous state, it means that no mutations run concurrently

▪ We have to check for conflicts in a way similar to the three-way merge used by Git. The difference is that instead of comparing lines, we compare fields of the system hash map.

▪ We calculate the diff between previous and next and between previous and current. If the two diffs have no fields in common, then there is no conflict between the mutations that have run concurrently.

▪ In a three-way merge, we calculate the diff between previous and next, and we apply it to current.

▪ What if there is a conflict?

    JOE   Then we abort the mutation.

  THEO   Aborting a user request seems unacceptable.

▪ In fact, in a user-facing system, conflicting concurrent mutations are fairly rare. That’s why it’s OK to abort and let the user run the mutation again.

▪ In a user-facing system, conflicting concurrent mutations are fairly rare.

▪ In the implementation of the diff algorithm, we’re going to reduce collections.

  THEO   I heard about reducing collections in a talk about FP, but I don’t remember the details. Could you remind me how this works?

▪ This section deals with the implementation of a structural diff algorithm

▪ That’s the most challenging part of the reconciliation algorithm. We need to implement a structural diff algorithm for hash maps.

▪ In what sense is the diff structural?

    JOE   The structural diff algorithm looks at the structure of the hash maps and ignores the order of the fields.

▪ Basically, there are three kinds of diffs: field replacement, field addition, and field deletion.

▪ In order to make things not too complicated, for now, we’ll deal only with replacement and addition.

▪ I notice that the order of the maps matters a lot. What about nested fields?

    JOE   It’s the same idea, but the nesting makes it a bit more difficult to grasp.

▪ The version of the structural diff algorithm illustrated in this chapter does not deal with deletions. Dealing with deletions is definitely possible, but it requires a more complicated algorithm.

▪ We compare the elements of the arrays in order: if they are equal, the diff is null; if they differ, the diff has the value of the second array.

▪ Is it complicated to implement the structural diff algorithm?

    JOE   Definitely! It took a good dose of mental gymnastics to come up with these 30 lines of code.

▪ Calculating the diff between two versions of the state is efficient because two hash maps created via structural sharing from the same hash map have most of their nodes in common.

▪ Can you give me the information path of the single field in the structural diff between previous and next?

  THEO   It’s ["catalog", "booksByIsbn", "978-1779501127", "publicationYear"].

▪ That’s another benefit of immutable data. When the data is not mutated, it is safe to compare references.

▪ I think I understand why you called it optimistic concurrency control. It’s because we assume that conflicts don’t occur too often. Right?

▪ Optimistic concurrency control allows mutations to ask forgiveness instead of permission.

▪ Optimistic concurrency control is lock-free.

▪ Optimistic concurrency control with immutable data is super efficient.

▪ Before updating the state, we need to reconcile the conflicts between possible concurrent mutations.

▪ We reconcile between concurrent mutations in a way that is similar to how Git handles a merge between two branches: either a fast-forward or a three-way merge.

▪ The changes required to let our system manage concurrency are only in the commit phase

▪ The calculation phase does its calculation as if it were the only mutation running

▪ The commit phase is responsible for trying to reconcile concurrent mutations.

▪ The reconciliation algorithm is universal in the sense that it can be used in any system where the system data is represented as an immutable hash map.

▪ The implementation of the reconciliation algorithm is efficient, as it leverages the fact that subsequent versions of the system state are created via structural sharing.

▪ In a user-facing system, conflicting concurrent mutations are fairly rare.

▪ When we cannot safely reconcile between concurrent mutations, we abort the mutation and ask the user to try again.

▪ Calculating the structural diff between two versions of the state is efficient because two hash maps created via structural sharing from the same hash map have most of their nodes in common.

▪ When data is immutable, it is safe to compare by reference, which is fast. When the references are the same, it means that the data is the same.

▪ There are three kinds of structural differences between two nested hash maps: replacement, addition, and deletion.

▪ In a data-oriented system, our code deals mainly with data manipulation: most of our functions receive data and return data.

▪ The vast majority of the code base of a data-oriented system deals with data manipulation.

▪ It’s very cool to visualize my code as a tree, but I don’t see how it relates to unit tests.

    JOE   The tree of function calls guides us about the quality and the quantity of test cases we should write.

▪ The validity of the data depends on the context

▪ Why is it better to use a minimal version of the data in a test case?

    JOE   For a very simple reason—the smaller the data, the easier it is to manipulate.

▪ Functions that appear in a lower level in the tree of function calls tend to involve less complex data than functions that appear in a higher level in the tree

▪ The correlation between the depth of a function in the tree of function calls and the quality and quantity of the test cases

▪ Writing a unit test for the main function of a mutation requires more effort than for a query.

▪ Don’t forget to include negative test cases in your unit tests.

▪ Most of the code in a data-oriented system deals with data manipulation

▪ It’s straightforward to write unit tests for code that deals with data manipulation

▪ Functions that appear in a lower level in the tree of function calls tend to involve less complex data than functions that appear in a higher level in the tree.

▪ Functions that appear in a lower level in the tree of function calls usually need to be covered with more test cases than functions that appear in a higher level in the tree.

▪ Unit tests for mutations focus on the calculation phase of the mutation

▪ The smaller the data, the easier it is to manipulate

▪ We compare the output and the expected output of our functions with a generic function that recursively compares two pieces of data (e.g., _.isEqual).

▪ No, my boss Monica really wanted to close the deal. She feels that success with this project is strategically important for Albatross, so it’s worthwhile to accept some risk by giving what she calls an “optimistic” time estimation. I told her that it was really an unrealistic time estimation, but Monica insists that if we make smart decisions and bring in more developers, we can do it.

▪ I think that your concerns about DOP at scale totally make sense. However, it doesn’t mean that you should abandon DOP.

▪ Have you heard the story about the young woodcutter and the old man?

  THEO   No.

    JOE   It goes like this.

▪ A young woodcutter strained to saw down a tree. An old man who was watching nearby asked, “What are you doing?”

“Are you blind?” the woodcutter replied. “I’m cutting down this tree.”

The old man replied, “You look exhausted! Take a break. Sharpen your saw.”

The young woodcutter explained to the old man that he had been sawing for hours and did not have time to take a break.

The old man pushed back, “If you sharpen the saw, you would cut down the tree much faster.”

The woodcutter said, “I don’t have time to sharpen the saw. Don’t you see, I’m too busy!”

▪ The importance of validating data at system boundaries

▪ Validating data using the JSON Schema language

▪ Integrating data validation into an existing code base

▪ Getting detailed information about data validation failures

▪ In fact, data validation is not only possible but recommended when we follow data-oriented principles.

▪ Separate data schema from data representation.

▪ It’s true that DOP doesn’t force you to validate data, but it doesn’t prevent you from doing so. In DOP, the data schema is separate from the data representation.

▪ According to DOP, the most important data to validate is data that crosses the boundaries of the system.

▪ Which boundaries are you referring to?

    JOE   In the case of a web server, it would be the areas where the web server communicates with its clients and with its data sources.

▪ The boundaries of a system are defined as the areas where the system exchanges data.

▪ Let me see. The first one is the client boundary, then we have the database boundary, and finally, the web service boundary.

▪ It’s important to identify the boundaries of a system because, in DOP, we differentiate between two kinds of data validation: validation that occurs at the boundaries of the system and validation that occurs inside the system. Today, we’re going to focus on validation that occurs at the boundaries of the system.

▪ Why do we need data validation inside the system then?

    JOE   It has to do with making it easier to code your system as your code base grows.

▪ Data representation stands on its own, and the data schema stands on its own. You are free to validate that a piece of data conforms with a data schema as you will and when you will.

▪ In DOP, the data schema is separate from the data representation.

▪ in a schema language called JSON Schema.

▪ Information on the JSON Schema language can be found at https://json-schema.org. The schemas in this book use JSON Schema version 2020-12.

▪ Therefore, instead of allowing any string, we could have a list of allowed values.

  THEO   Like an enumeration value?

    JOE   Exactly! In fact, JSON Schema supports enumeration values with the enum keyword. Instead of {"type": "string"}
, you need to have {"enum": [...]}
and replace the dots with the supported fields.

▪ Data validation in DOP means checking whether a piece of data conforms to a schema.

▪ Libraries for JSON Schema validation

Language Library URL  
JavaScript Ajv https://github.com/ajv-validator/ajv  
Java        Snow https://github.com/ssilverman/snowy-json  
C#           　JSON.net Schema https://www.newtonsoft.com/jsonschema  
Python   　jschon https://github.com/marksparkza/jschon  
Ruby      JSONSchemer https://github.com/davishmcclurg/json_schemer

▪ The syntax of JSON Schema is much more verbose than the syntax for declaring the members in a class. Why is that so?

    JOE   For two reasons. First, because JSON Schema is language independent, it can be used in any programming language. As I told you, there are JSON Schema validators available in most programming languages.

▪ In a moment, we’ll talk about schema composition.

▪ Once again, I have to admit that JSON Schemas are more composable than class definitions.

▪ That’s a good opportunity for me to tell you about JSON Schema composition.

  THEO   What’s that?

    JOE   It’s a way to combine schemas, similarly to how we combine logical conditions with AND, OR, and NOT.

▪ DOP Principle #4 is to separate data schema and data representation

▪ The boundaries of a system are defined to be the areas where the system exchanges data

▪ Data validation in DOP means checking whether a piece of data conforms to a schema

▪ JSON Schemas are just maps and, as so, we are free to manipulate them like any other maps in our programs.

▪ Atoms as an alternative to locks

▪ The traditional way to manage concurrency in a multi-threaded environment involves lock mechanisms like mutexes. Lock mechanisms tend to increase the complexity of the system because it’s not trivial to make sure the system is free of deadlocks.

▪ In DOP, we leverage the fact that data is immutable, and we use a lock-free mechanism, called an atom, to manage concurrency. Atoms are simpler to manage than locks because they are lock-free.

▪ This chapter is mostly relevant to multi-threaded environments like Java, C#, Python, and Ruby. It is less relevant to single-threaded environments like JavaScript. The JavaScript code snippets in this chapter are written as though JavaScript were multi-threaded.

▪ Cloning data to avoid read locks doesn’t scale.

▪ Implementation of an atomic compare and set in various languages

Language Link  
Java            http://mng.bz/mx0W  
JavaScript Not relevant (single-threaded language)  
Ruby          http://mng.bz/5KG8  
Python       　https://github.com/maxcountryman/atomos  
C#               　http://mng.bz/6Zzp

▪ Are you familiar with the notion of in-memory cache?

  THEO   You mean memoization?

    JOE   Kind of.

▪ It’s quite common to represent an in-memory cache as a string map.

▪ When data is immutable, it is safe (and fast) to compare it by reference.

▪ I don’t know, but I am under the impression that mutexes are like phone calls, and atoms are like text messages.

▪ Managing concurrency with atoms is much simpler than managing concurrency with locks because we don’t have to deal with the risk of deadlocks.

▪ Cloning data to avoid read locks doesn’t scale.

▪ When data is immutable, reads are always safe.

▪ Atoms provide a way to manage concurrency without locks

▪ With atoms, deadlocks never happen

▪ We can manage composite data in a thread-safe way with atoms

▪ It’s quite common to represent an in-memory cache as a string map

▪ When data is immutable, it is safe (and fast) to compare by reference.

▪ Immutable collections are not the same as persistent data structures.

▪ It’s possible to manually ensure that our data isn’t mutated, but it’s cumbersome

▪ This insight allows us to create new versions of our collections using a shallow copy instead of a deep copy, and you claimed that it was efficient.

▪ At scale, naive structural sharing causes a performance hit, both in terms of memory and computation.

▪ Yes! For that, you’ll need to learn the real way to handle immutability. It’s called persistent data structures.

▪ Persistent data structures always preserve the previous version of themselves when they are modified.

▪ Persistent data structures address the two main limitations of naive structural sharing: safety and performance.

▪ In JavaScript, persistent data structures provide their own methods to access data, and none of those methods mutate data.

  THEO   Does that mean that we can’t use the dot notation to access fields?

    JOE   Correct. Fields of persistent data structures are accessed via a specific API.

▪ I understand how to use structural sharing at the level of the data structure for linked lists and prepend operations, but how would it work with operations like appending or modifying an element in a list?

    JOE   For that purpose, we need to be smarter and represent our list as a tree.

  THEO   How does that help?

▪ It helps because when a list is represented as a tree, most of the nodes in the tree can be shared between two versions of the list.

▪ Imagine that you take a list with 100,000 elements and split it into two lists of 50,000 elements each: elements 0 to 49,999 in list 1, and elements 50,000 to 99,999 in list 2. How many operations would you need to create a new version of the list where a single element—let’s say, element at index 75,100—is modified?

▪ In modern CPU architectures, the performance of updating a persistent list is dominated much more by the depth of the tree than by the number of nodes at each level of the tree.

▪ He feels a lot of respect for Phil Bagwell, who discovered how to manipulate persistent data structures efficiently, and for Rich Hickey, who created a programming language incorporating that discovery as a core feature and making it available to the world.

▪ Are persistent data structures available in all programming languages?

    JOE   A few programming languages like Clojure, Scala, and C# provide them as part of the language.

▪ In a language like JavaScript, it’s a bit more cumbersome to integrate persistent data structures

▪ For accessing a field in a map, Immutable.js provides two functions: get for direct fields and getIn for nested fields.

▪    JOE   Exactly! If the object passed to JSON.stringify() has a .toJSON() method, it’s called by JSON.stringify().

▪   THEO   When the number of elements in the collection is big enough, naive structural sharing has performance issues

▪ It’s possible to manually ensure that our data isn’t mutated, but it’s cumbersome

▪ At scale, naive structural sharing causes a performance hit, both in terms of memory and computation

▪ Naive structural sharing doesn’t prevent data structures from being accidentally mutated

▪ Immutable collections are not the same as persistent data structures

▪ Immutable collections don’t provide an efficient way to create new versions of the collections

▪ Persistent data structures protect data from mutation

▪ Persistent data structures provide an efficient way to create new versions of the collections

▪ Persistent data structures always preserve the previous version of themselves when they are modified

▪ Persistent data structures represent data internally in such a way that structural sharing scales well, both in terms of memory and computation

▪ When data is immutable, it is safe to share it.

▪ Internally, persistence uses a branching factor of 32.

▪ In practice, manipulation of persistent data structures is efficient even for collections with 10 billion entries!

▪ Due to modern architecture considerations, the performance of updating a persistent list is dominated much more by the depth of the tree than by the number of nodes at each level of the tree

▪ Persistent lists can be manipulated in near constant time.

▪ In most languages, third-party libraries provide an implementation of persistent data structures

▪ Paguro collections implement the read-only parts of Java collection interfaces

▪ Paguro collections can be passed to any methods that expect to receive a Java collection without mutating them.

▪ Traditionally in OOP, we use design patterns and complex layers of objects to structure access to the database

▪ In DOP, we prefer to represent data fetched from the database with generic data collections, namely, lists of maps, where fields in the maps correspond to database column values.

▪ The best way to manipulate data is to represent data as data

▪ Basic knowledge of relational database and SQL query syntax (like SELECT, AS, WHERE, and INNER JOIN) is assumed. This approach can be easily adapted to NoSQL databases.

▪ How do you think that we should represent data that comes from the database in DOP?

  THEO   As generic data collections, I guess.

    JOE   Exactly!

▪ In DOP, we always represent data with generic data collections.

▪ In DOP, we represent data from the database with generic data collections, and we manipulate it with generic functions

▪ In DOP, flexibility is increased as many parts of the system are free to manipulate data without dealing with concrete types

▪ In a dynamically-typed language like JavaScript, I understand that the types of the values in the list of maps returned by dbClient.query are determined at run time

▪ ►Note In this book, we avoid using the JavaScript dot notation to access a field in a hash map in order to illustrate how to apply DOP in languages that don’t support dot notation on hash maps.

▪ In DOP, fields are first-class citizens

▪ Now Theo understands what Joe meant when he told him “a cloud is cloud” when they were walking back from the park to the office. Instead of trapping data in the limits of our objects, DOP guides us to represent data as data.

▪ Inside our applications, we represent data fetched from the database, no matter if it is relational or nonrelational, as a generic data structure.

▪ In the case of a relational database, data is represented as a list of maps

▪ In DOP, field names are just strings. It allows us to write generic functions to manipulate list of maps representing data fetched from the database.

▪ No, quite often it’s JSON, for which we have parsers in all programming languages.

▪ Oh, I see. So, how do you manually parse a JSON string into a map?

    JOE   In JavaScript, we use JSON.parse. In Java, we use a third-party library like Gson (https://github.com/google/gson), maintained by Google.

▪ Classes are much less complex when we use them as a means to aggregate stateless functions that operate on similar domain entities

▪ Theo recalls Joe’s story about the young woodcutter and the old man. Theo was able to learn DOP and deliver the project on time! He’s pleased that he took the time “to sharpen his saw and commit to a deeper level of practice.”

▪ We build the insides of our systems like we build the outsides

▪ Components inside a program communicate via data that is represented as immutable data collections in the same way as components communicate via data over the wire

▪ Knowledge is never complete. As the great Socrates used to say, “The more I know, the more I realize I know nothing.” I’m confident you will be able to learn the missing parts by yourself and maybe even invent some.

▪ I remember that when Joe showed me how to validate data at system boundaries, I raised this concern about the development phase. Joe told me then that we validate data as it flows inside the system exactly like we validate data at system boundaries: we separate between data schema and data representation

▪ The main purpose of data validation at system boundaries is to prevent invalid data from getting into the system, whereas the main purpose of data validation inside the system is to make it easier to develop the system

▪ By making it easier to develop the system, do you mean to help the developers understand the expected shape of function arguments as in OOP?

▪ For records, we use maps where the names of the fields are known and the values can have different shapes. For indexes, we use maps where the names of the fields are unknown and the values have a common shape.

▪ We call the maps for records heterogeneous maps and the maps for indexes homogeneous maps.

▪ In DOP, records are represented as heterogeneous maps, whereas indexes are represented as homogeneous maps

▪ In JSON Schema, homogeneous string maps have type: object with no properties and additionalProperties associated to a schema.

▪ A tuple is an array where the size is fixed, and the elements can be of different shapes

▪ That’s similar to the way we validate data at system boundaries. The main difference is that the data validation for data that flows inside the system should run only at development time, and it should be disabled when the code runs in production.

▪   Because that data has been already validated up front at a system boundary. Validating it again on a function call is superfluous, and it would impact performance

▪ I see. It’s like assertions in Java. They are disabled in production code

▪ Data validation inside the system should be disabled in production

▪ For now, I am going to assume that we have a dev function that returns true when the code runs in the development environment and false when it runs in production

▪ I think we should treat data validation like we treat unit tests. We should validate function arguments only for functions for whom we would write unit tests.

▪ Treat data validation like unit tests.

▪ Do you think it would make sense to also validate the return value of functions?

  THEO   Absolutely

▪ What do you mean by advanced data validation?

  THEO   I mean going beyond static types.

▪ Take, for instance, the publication year of a book. It’s an integer, but what else could you say about this number?

  DAVE   It has to be positive. It would say it’s a positive integer.

  THEO   Come on, Dave! Be courageous, go beyond types.

  DAVE   I don’t know. I would say it’s a number that should be higher than 1900. I don’t think it makes sense to have a book that is published before 1900.

▪ I think have it! In DOP, data validation is executed at run time, while static type validation in OOP is executed at compile time. At compile time, we only have information about static types; at run time, we have the data itself. That’s why in DOP data validation, it’s possible to go beyond types.

▪ Of course, it’s also possible in traditional OOP to write custom run-time data validation. Here, though, we are comparing data schema with static types

▪ Can you write the regular expression for a valid UUID?

▪ We also realized that we don’t have to validate data for each and every function.

▪ There are tools that receive a JSON Schema as input and produce a diagram in a data model format.

▪ What is a data model format?

    JOE   It’s a format that allows you to define a data model in plain text. After that, you can generate an image from the text. My favorite data format is PlantUML.

▪ I have used JSON Schema Viewer and Malli.

▪ A unit test calls a function with some arguments and checks whether the function returns the expected value

▪ How do you generate random data that conforms to a schema?

    JOE   Using a tool like JSON Schema Faker.

▪ IDEs like IntelliJ and Visual Studio Code already support JSON Schema validation for JSON files

▪ Unlike data validation at system boundaries, data validation inside the system is supposed to run only at development time and should be disabled in production

▪ Data validation is executed at run time

▪ Data validation inside the system should be disabled in production

▪ Records are represented as heterogeneous maps, and indexes are represented as homogeneous maps

▪ When you define a complex data schema, it is advised to store nested schemas in variables to make the schemas easier to read

▪ We treat data validation like unit tests.

▪ Mimicking objects with multimethods (single dispatch)

▪ Implementing multimethod on several argument types (multiple dispatch)

▪ OOP is well-known for allowing different classes to be called with the same interface via a mechanism called polymorphism

▪ It may seem that the only way to have polymorphism in a program is with objects. In fact, in this chapter, we are going to see that it is possible to have polymorphism without objects, thanks to multimethods.

▪ Moreover, multimethods provide a more advanced polymorphism than OOP polymorphism because they support cases where the chosen implementation depends on several argument types (multiple dispatch) and even on the dynamic value of the arguments (dynamic dispatch).

▪ I see. And why do you think polymorphism is valuable?

  DAVE   Because it allows us to decouple an interface from its implementations.

▪ Anthropomorphism comes from the Greek ánthro–pos, which means human, and morphe–, which means form.

▪ Absolutely. Polymorphism comes from the Greek polús, which means many, and morphe–, which, again, means form.

▪ In OOP, I’d define an IAnimal interface with a greet method, and each animal class would implement greet in its own way

▪ Let me challenge you a bit. What is the fundamental difference between OOP polymorphism and a switch statement?

▪ Another drawback of your approach is that when you want to modify the implementation of greet for a specific animal, you have to change the code that deals with all the animals, while in my approach, you would change only a specific animal class.

  THEO   I agree, and I could also fix that by having a separate function for each animal, something like this.

▪ Now you got me. I admit that with a switch statement, I can’t add a new animal without modifying the original code, whereas in OOP, I can add a new class without having to modify the original code.

▪ Yeah, but you helped me to realize that the main benefit of polymorphism is that it makes the code easily extensible

▪ The main benefit of polymorphism is extensibility.

▪ Theo and Dave read some online material about multimethods. It doesn’t look too complicated

▪ He’s grateful for the experience, but he admits that country life can sometimes be hard without the conveniences of the city.

▪ But who said simple was easy?

▪ From what I read before lunch, it seems that multimethods are a software construct that provide polymorphism without the need for objects.

▪ Multimethods have two parts: a dispatch function and a set of methods that provide an implementation for each dispatched value

▪ The arguments of a multimethod are passed to the dispatch function and to the methods

▪ For that, we need a library. For instance, in JavaScript, the arrows/multimethod library provides an implementation of multimethods

▪ A multimethod dispatch function is responsible for three things: it defines the signature of the multimethod, it validates the arguments, and it emits a dispatch value.

▪ Does the method implementation have to be in the same module as the multimethod initialization?

  THEO   No, not at all! Method declarations are decoupled from multimethod initialization exactly like class definitions are decoupled from the interface definition. That’s what make multimethods extensible.

▪ Multimethods provides extensibility by decoupling between multimethod initialization and method implementations.

▪ In the context of multimethods, a method is a function that provides an implementation for a dispatch value

▪ Are the names of dispatch functions and methods important?

  THEO   According to what I read, not really, but I like to follow a simple naming convention: use the name of the multimethod (for example, greet) as a prefix for the dispatch function (for example, greetDispatch) and the methods

▪ Then I’d have the Dispatch suffix for the dispatch function and a specific suffix for each method (for example, greetDog, greetCat, and greetCow).

▪ Multimethods are called like regular functions.

▪ Now do you agree that multimethods with multiple dispatch offer a more powerful polymorphism that OOP polymorphism?

▪ Support for multimethods in different languages

Python has a library called multimethods (https://github.com/weissjeffm/multimethods), and Ruby has one called Ruby multimethods (https://github.com/psantacl/ruby-multimethods). Both seem to work quite like the JavaScript arrows/multimethod library.

▪ In Java, there is the Java Multimethod Framework (http://igm.univ-mlv.fr/~forax/works/jmmf/), and C# supports multimethods natively via the dynamic keyword.

▪ However, in both Java and C#, multimethods work only with static data types and not with generic data structures.

▪ The main benefit of polymorphism is extensibility.

▪ Multimethods make it possible to benefit from polymorphism when data is represented with generic maps.

▪ A multimethod is made of a dispatch function and multiple methods.

▪ The dispatch function of a multimethod emits a dispatch value

▪ Multimethods can mimic OOP class inheritance via single dispatch.

▪ In single dispatch, a multimethod receives a single map that contains a type field, and the dispatch function of the multimethod emits the value of the type field.

▪ In addition to single dispatch, multimethods provide two kinds of advanced polymorphisms: multiple dispatch and dynamic dispatch.

▪ Multiple dispatch is used when the behavior of the multimethod depends on multiple arguments.

▪ Dynamic dispatch is used when the behavior of the multimethod depends on run-time arguments

▪ The arguments of a multimethod are passed to the dispatch function and to the methods.

▪ A multimethod dispatch function is responsible for

Defining the signature.
Validating the arguments.
Emitting a dispatch value.

▪ Multimethods provides extensibility by decoupling between multimethod initialization and method implementations

▪ Multimethods are called like regular functions

▪ Multimethods support default implementations that are called when no method corresponds to the dispatch value

▪ In a multimethod that features multiple dispatch, the order of the elements in the array emitted by the dispatch function has to be consistent with the order of the elements in the wiring of the methods.

▪ When our business logic involves advanced data processing, the generic data manipulation functions provided by the language run time and by third-party libraries might not be sufficient.

▪ Separating business logic from the internal details of data manipulation makes the business logic code concise and easy to read for other developers.

▪ Could you pass me that thing on your desk that’s used for writing?

It takes Dave a few seconds to get that Theo has asked him to pass the pen on the desk. After he passes Theo the pen, he asks:

  DAVE   Why didn’t you simply ask for the pen?

  THEO   I wanted you to experience how it feels when we use descriptions instead of names to convey our intent.

▪ Maintain a clear separation between the code that deals with business logic and the implementation of the data manipulation.

▪ Separating business logic from data manipulation makes our code not only concise, but also easy to read because it conveys the intent in a clear manner.

▪ Pick the least generic utility function that solves your problem.

▪ But you can’t avoid state in real-life applications!

  THEO   Right, but we can minimize the number of modules that deal with state. In fact, that’s exactly what DOP has encouraged us to do: only the SystemState module deals with state, and all other modules deal with immutable data.

▪ I didn’t know that strings were considered valid JSON data. I thought only objects and arrays were valid.

  THEO   Both compound data types and primitive data types are valid JSON data.

▪ The essence of DOP is that it treats data as a first-class citizen

▪ As a consequence, we can reproduce any scenario that deals with data with the same simplicity as we reproduce a scenario that deals with numbers and strings.

▪ Reproducibility allows us to reproduce a scenario in a pristine environment

▪ Data-oriented programming (DOP) is a programming paradigm aimed at simplifying the design and implementation of software systems, where information is at the center in systems such as frontend or backend web applications and web services, for example

▪ Instead of designing information systems around software constructs that combine code and data (e.g., objects instantiated from classes), DOP encourages the separation of code from data.

▪ Moreover, DOP provides guidelines about how to represent and manipulate data.

▪ In DOP, data is treated as a first-class citizen

▪ The essence of DOP is that it treats data as a first-class citizen. It gives developers the ability to manipulate data inside a program with the same simplicity as they manipulate numbers or strings.

▪ Treating data as a first-class citizen is made possible by adhering to four core principles:

▪ Separating code (behavior) from data.

▪ Representing data with generic data structures.

▪ Treating data as immutable.

▪ Separating data schema from data representation.

▪ Object-oriented programming (OOP) languages such as Java, C#, C++, etc.

▪ Functional programming (FP) languages such as Clojure, OCaml, Haskell, etc.

▪ Languages that support both OOP and FP such as JavaScript, Python, Ruby, Scala, etc.

▪ Adherence to this principle in OOP means aggregating the code as methods of a static class

▪ Breaking this principle in FP means hiding state in the lexical scope of a function.

▪ Breaking Principle #1 in OOP happens when we write code that combines data and code together in an object

▪ Breaking this principle without classes in FP means hiding data in the lexical scope of a function.

▪ Careful separation of code from data benefits our programs in the following ways:

▪ Code can be reused in different contexts.

▪ Code can be tested in isolation.

▪ Imagine that besides the author entity, there is a user entity that has nothing to do with authors but has two of the same data fields as the author entity: firstName and lastName. The logic of calculating the full name is the same for authors and users—retrieving the values of two fields with the same names.

▪ Writing tests is easier when code is separated from data.

▪ The type of complexity I refer to is the one that makes systems hard to understand as defined in the paper, “Out of the Tar Pit,” by Ben Moseley and Peter Marks (http://mng.bz/enzq).

▪ Complex in the context of this book means hard to understand.

▪ Keep in mind that complexity and simplicity (like hard and easy) are not absolute but relative concepts

▪ The scope of a data entity or a code entity is smaller than the scope of an entity that combines code and data

▪ Some relations are data relations (association and composition), and some relations are code relations (inheritance and dependency).

▪ The left part is made only of data entities and data relations: association and composition.

▪ The right part is made only of code entities and code relations: dependency and inheritance.

▪ That is true, but in a sense, it is irrelevant. The point of Principle #1 is that a system made of entities that do not combine code and data tends to be simpler than a system made of entities that do combine code and data

▪ It has been said many times that simplicity is hard. According to the first principle of DOP, simplicity is easier to achieve when separating code and data.

▪ The price we pay in order to benefit from the separation between code and data is threefold:

There is no control on what code can access what data.

There is no packaging.

Our systems are made from more entities.

▪ In DOP, data stands on its own. It is transparent if you like, and as a consequence, it can be accessed by any piece of code.

When refactoring the shape of some data, every place in our code that accesses this kind of data must be known

▪ In DOP, the code that manipulates the data could be anywhere. For example, createAuthorData might be in one file and fullName in another file. This makes it difficult for developers to discover that the fullName function is available. In some situations, it could lead to wasted time and unnecessary code duplication.

▪ On one hand, when adhering to Principle #1, the entities of the system are simpler. On the other hand, there are more entities

▪ The most common generic data structures are maps (aka dictionaries) and arrays (or lists). But other generic data structures (e.g., sets, trees, and queues) can be used as well.

▪ In DOP, data is represented with generic data structures (like maps and arrays) instead of instantiating data via specific classes. In fact, most of the data entities that appear in a typical application can be represented with maps and arrays (or lists). But there exist other generic data structures (e.g., sets, lists, queues, etc.) that might be required in some use cases.

▪ An author is a data entity with a firstName, a lastName, and the number of books they have written

▪ In a language like JavaScript, we can also instantiate a map via a data literal, which is a bit more convenient.

▪ A flexible data model

▪ There is a famous quote by Alan Perlis that summarizes this benefit:

It is better to have 100 functions operate on one data structure than to have 10 functions operate on 10 data structures.

—Alan Perlis (“Epigrams on Programming,” 1982)

▪ Working with a flexible data model is particularly useful in applications where the shape of the data tends to be dynamic (e.g., web apps and web services).

▪ As with any programming principle, using this principle comes with its own set of trade-offs.

▪ The price paid for representing data with generic data structures is as follows:

There is a slight performance hit.

No data schema is required.

No compile-time check that the data is valid is necessary.

In some statically-typed languages, type casting is needed.

▪ When specific classes are used to instantiate data, retrieving the value of a class member is fast because the compiler knows how the data will look and can do many optimizations.

▪ With generic data structures, it is harder to optimize, so retrieving the value associated to a key in a map, for example, is a bit slower than retrieving the value of a class member.

▪ In most programming languages, this performance hit is not significant, but it is something to keep in mind.

▪ The existence of data schema at a class level is useful for developers and for IDEs because

Developers can easily discover the expected data shape.

IDEs provide features like field name autocompletion.

▪ When data is represented with generic data structures, the data schema is not part of the data representation

▪ When data is represented with generic data structures, data shape errors are caught only at run time.

▪ In some statically-typed languages, explicit type casting is needed.

▪ DOP uses generic data structures to represent data. This might cause a (small) performance hit and impose the need to manually document the shape of data because the compiler cannot validate it statically.

▪ Comparing object addresses is much faster than comparing all the fields

▪ Immutable data enables fast equality checks by comparing data by reference.

▪ As mentioned earlier, implementations of persistent data structures exist in most programming languages. But even the most efficient implementation is a bit slower than the in-place mutation of the data. In most applications, the performance hit and the additional memory consumption involved in using immutable data structures is not significant.

▪ With data separated from code and represented with generic and immutable data structures, now comes the question of how do we express the shape of the data?

▪ In DOP, the expected shape is expressed as a data schema that is kept separated from the data itself.

▪ DOP simplifies the design and implementation of information systems by treating data as a first-class citizen

▪ Data-oriented programming (DOP) has its origins in the 1950s with the invention of the programming language Lisp

▪ DOP is based on a set of best practices that can be found in both functional programming (FP) and object-oriented programming (OOP).

▪ However, this paradigm has only been applicable in production systems at scale since the 2010s with the implementation of efficient persistent data structures.

▪ With Lisp, John McCarthy had the ingenious idea to represent data as generic immutable lists and to invent a language that made it natural to create lists and to access any part of a list.

▪ That’s the reason why Lisp stands for LISt Processing.

▪ In a way, Lisp lists are the ancestors of JavaScript object literals. The idea that it makes sense to represent data with generic data structures (DOP Principle #2) definitely comes from Lisp.

▪ The main limitation of Lisp lists is that when we update a list, we need to create a new version by cloning it. This has a negative impact on performance both in terms of CPU and memory.

▪ In a short and easy-to-read paper, named “Values and Objects in Programming Languages,” Bruce MacLennan clarifies the distinction between values and objects.

▪ Values (for instance, numbers) are timeless abstractions for which the concepts of updating, sharing, and instantiation have no meaning.

▪ Objects (for instance, an employee object in a human resource software system) exist in time and, hence, can be created, destroyed, copied, shared, and updated.

▪ The meaning of the term object in this paper is not exactly the same as in the context of OOP.

▪ The author explains why it’s much simpler to write code that deals with values than to write code that deals with objects. This paper has been a source of inspiration for DOP as it encourages us to implement our systems in such a way that most of our code deals with values.

▪ In their paper, “Out of the Tar Pit,” Ben Moseley and Peter Marks claim that complexity is the single major difficulty in the development of large-scale software systems

▪ The main insight of the authors is that most of the complexity of software systems in not essential but accidental: the complexity doesn’t come from the problem we have to solve but from the software constructs we use to solve the problem.

▪ Rich Hickey likes to summarize Clojure’s core value with the phrase, “Just use maps!”

▪ Clojure has been the main source of inspiration for DOP. In a sense, this book is a formalization of the underlying principles of Clojure and how to apply them in other programming languages.

▪ The innovation of DOP is the combination of those principles into a cohesive whole. In this section, we put each of the four DOP principles into its broader scope.

▪ Separating code from data used to be the main point of contention between OOP and FP. Traditionally, in OOP we encapsulate data together with code in stateful objects, while in FP, we write stateless functions that receive data they manipulate as an explicit argument.

▪ This tension has been reduced over the years as it is possible in FP to write stateful functions with data encapsulated in their lexical scope (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures). Moreover, OOP languages like Java and C# have added support for anonymous functions (lambdas).

▪ One of the main innovations of JavaScript when it was released in December 1995 was the ease of creating and manipulating hash maps via object literals.

▪ Data immutability is considered a best practice as it makes the behavior of our program more predictable. For instance, in the book Effective Java (O’Reilly, 2017; http://mng.bz/5K81), Joshua Bloch mentions “minimize mutability” as one of Java best practices.

▪ There is a famous quote from Alan Kay, who is considered by many as the inventor of OOP, about the value of immutability:

The last thing you wanted any programmer to do is mess with internal state even if presented figuratively. Instead, the objects should be presented as sites of higher level behaviors more appropriate for use as dynamic components... . It is unfortunate that much of what is called "object-oriented programming" today is simply old style programming with fancier constructs. Many programs are loaded with “assignment-style” operations now done by more expensive attached procedures.

—Alan C. Kay (“The Early History of Smalltalk,” 1993)

▪ Unfortunately, until 2007 and the implementation of efficient persistent data structures in Clojure, immutability was not applicable for production applications at scale. As we mentioned in chapter 9, nowadays, efficient persistent data structures are available in most programming languages.

▪ There are only two hard things in Computer Science: cache invalidation and naming things.

—Phil Karlton

▪ As we have illustrated in this book, DOP is a paradigm that treats system data as a first-class citizen. Data is represented by generic immutable data structures like maps and vectors that are manipulated by general-purpose functions like map, filter, select, group, sort, and so forth.

▪ In this context, what’s important is the representation of data by the program.
