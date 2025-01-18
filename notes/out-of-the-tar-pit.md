Out of the Tar Pit (2006)

Ben Moseley & Peter Marks

───────────────

▪ Complexity is the single major difficulty in the successful development of large-scale software systems

▪ Following Brooks we distinguish accidental from essential difficulty, but disagree with his premise that most complexity remaining in contemporary systems is essential.

▪ We identify common causes of complexity and discuss general approaches which can be taken to eliminate them where they are accidental in nature

▪ The “software crisis” was first identified in 1968 [NR69] and in the intervening decades has deepened rather than abated. The biggest problem in the development and maintenance of large-scale software systems is complexity — large systems are hard to understand

▪ We believe that the major contributor to this complexity in many systems is the handling of state and the burden that this adds when trying to analyse and reason about the system.

▪ The classical ways to approach the difficulty of state include object-oriented programming which tightly couples state together with related behaviour, and functional programming which — in its pure form — eschews state and side-effects all together. These approaches each suffer from various (and differing) problems when applied to traditional large-scale systems.

▪ We argue that it is possible to take useful ideas from both and that — when combined with some ideas from the relational database world — this approach offers significant potential for simplifying the construction of large-scale software systems

▪ In the first half we focus on complexity. In section 2 we look at complexity in general and justify our assertion that it is at the root of the crisis, then we look at how we currently attempt to understand systems in section 3.

▪ In his classic paper — “No Silver Bullet” Brooks [Bro86] identified four properties of software systems which make building software hard: Complexity, Conformity, Changeability and Invisibility.

▪ Of these we believe that Complexity is the only significant one — the others can either be classified as forms of complexity, or be seen as problematic solely because of the complexity in the system.

▪ Complexity is the root cause of the vast majority of problems with software today. Unreliability, late delivery, lack of security — often even poor performance in large-scale systems can all be seen as deriving ultimately from unmanageable complexity

▪ The primary status of complexity as the major cause of these other problems comes simply from the fact that being able to understand a system is a prerequisite for avoiding all of them, and of course it is this which complexity destroys.

▪ As Dijkstra said [Dij97, EWD1243]

“…we have to keep it crisp, disentangled, and simple if we refuse to be crushed by the complexities of our own making…”

▪ …and the Economist devoted a whole article to software complexity [Eco04] — noting that by some estimates software problems cost the American economy $59 billion annually.

▪ Being able to think and reason about our systems (particularly the effects of changes to those systems) is of crucial importance.

▪ In his 1990 lecture Corbato said [Cor91]:

“The general problem with ambitious systems is complexity.”, “…it is important to emphasize the value of simplicity and elegance, for complexity has a way of compounding difficulties”

▪ This is the unfortunate truth:

Simplicity is Hard

▪ One final point is that the type of complexity we are discussing in this paper is that which makes large systems hard to understand. It is this that causes us to expend huge resources in creating and maintaining such systems.

▪ We argued above that the danger of complexity came from its impact on our attempts to understand a system.

▪ There are two widely-used approaches to understanding systems (or components of systems):

▪ Testing
This is attempting to understand a system from the outside — as a “black box”. Conclusions about the system are drawn on the basis of observations about how it behaves in certain specific situations.

▪ Informal Reasoning
This is attempting to understand the system by examining it from the inside. The hope is that by using the extra information available, a more accurate understanding can be gained.

▪ In any non-trivial system there is some complexity inherent in the problem that needs to be solved.

▪ Anyone who has ever telephoned a support desk for a software system and been told to “try it again”, or “reload the document”, or “restart the program”, or “reboot your computer” or “re-install the program” or even “re-install the operating system and then the program” has direct experience of the problems that state1 causes for writing reliable, understandable software.

▪ The reason these quotes will sound familiar to many people is that they are often suggested because they are often successful in resolving the problem. The reason that they are often successful in resolving the problem is that many systems have errors in their handling of state.

▪ “From the complexity comes the difficulty of enumerating, much less understanding, all the possible states of the program, and from that comes the unreliability”

▪ we agree with this, but believe that it is the presence of many possible states which gives rise to the complexity in the first place, and:

“computers… have very large numbers of states. This makes conceiving, describing, and testing them hard

▪ These two similar problems — one intrinsic to testing, the other coming from state — combine together horribly. Each introduces a huge amount of uncertainty, and we are left with very little about which we can be certain if the system/component under scrutiny is of a stateful nature.

▪ One of the issues (that affects both testing and reasoning) is the exponential rate at which the number of possible states grows — for every single bit of state that we add we double the total number of possible states.

▪ Another issue — which is a particular problem for informal reasoning — is contamination.

▪ If the procedure in question (which is itself stateless) makes use of any other procedure which is stateful — even indirectly — then all bets are off, our procedure becomes contaminated and we can only understand it in the context of state.

▪ As has been said, the problem with state is that “when you let the nose of the camel into the tent, the rest of him tends to follow”.

▪ As a result of all the above reasons it is our belief that the single biggest remaining cause of complexity in most contemporary large systems is state, and the more we can do to limit and manage state, the better.

▪ Control is basically about the order in which things happen.

▪ The problem with control is that very often we do not want to have to be concerned with this.

▪ The difficulty is that when control is an implicit part of the language (as it almost always is), then every single piece of program must be understood in that context — even when (as is often the case) the programmer may wish to say nothing about this.

▪ When a programmer is forced (through use of a language with implicit control flow) to specify the control, he or she is being forced to specify an aspect of how the system should work rather than simply what is desired. Effectively they are being forced to over-specify the problem.

▪ This is because the person reading the code above must effectively duplicate the work of the hypothetical compiler — they must (by virtue of the definition of the language semantics) start with the assumption that the ordering specified is significant, and then by further inspection determine that it is not (in cases less trivial than the one above determining this can become very difficult).

▪ Having considered the impact of control on informal reasoning, we now look at a second control-related problem, concurrency, which affects testing as well.

▪ This cause is basically in many ways a secondary effect — much code is simply concerned with managing state or specifying control. Because of this we shall often not mention code volume explicitly. It is however worth brief independent attention for at least two reasons — firstly because it is the easiest form of complexity to measure, and secondly because it interacts badly with the other causes of complexity and this is important to consider.

▪ “Many of the classic problems of developing software products derive from this essential complexity and its nonlinear increase with size”

▪ Finally there are other causes, for example: duplicated code, code which is never actually used (“dead code”), unnecessary abstraction3, missed abstraction, poor modularity, poor documentation…

All of these other causes come down to the following three (inter-related) principles:

▪ Complexity breeds complexity

▪ There are a whole set of secondary causes of complexity. This covers all complexity introduced as a result of not being able to clearly understand a system.

▪ Duplication is a prime example of this — if (due to state, control or code volume) it is not clear that functionality already exists, or it is too complex to understand whether what exists does exactly what is required, there will be a strong tendency to duplicate. This is particularly true in the presence of time pressures.

▪ Simplicity is Hard
This was noted above — significant effort can be required to achieve simplicity. The first solution is often not the most simple, particularly if there is existing complexity, or time pressure. Simplicity can only be attained if it is recognised, sought and prized.

▪ In this case it means that we need to be very wary of any language that even permits state, regardless of how much it discourages its use (obvious examples are ML and Scheme).

▪ The bottom line is that the more powerful a language (i.e. the more that is possible within the language), the harder it is to understand systems constructed in it.

▪ The different classical approaches to managing complexity can perhaps best be understood by looking at how programming languages of each of the three major styles (imperative, functional, logic) approach the issue.

▪ Object-orientation — whilst being a very broadly applied term (encompassing everything from Java-style class-based to Self-style prototype-based languages, from single-dispatch to CLOS-style multiple dispatch languages, and from traditional passive objects to the active / actor styles) — is essentially an imperative approach to programming.

▪ In most forms of object-oriented programming (OOP) an object is seen as consisting of some state together with a set of procedures for accessing and manipulating that state.

▪ This is essentially similar to the (earlier) idea of an abstract data type (ADT) and is one of the primary strengths of the OOP approach when compared with less structured imperative styles.

▪ In the OOP context this is referred to as the idea of encapsulation, and it allows the programmer to enforce integrity constraints over an object’s state by regulating access to that state through the access procedures (“methods”).

▪ Another major problem4 is that encapsulation-based integrity constraint enforcement is strongly biased toward single-object constraints and it is awkward to enforce more complicated constraints involving multiple objects with this approach (for one thing it becomes unclear where such multiple-object constraints should reside).

▪ In OOP, each object is seen as being a uniquely identifiable entity regardless of its attributes. This is known as intensional identity (in contrast with extensional identity in which things are considered the same if their attributes are the same).

▪ Object identity does make sense when objects are used to provide a (mutable) stateful abstraction — because two distinct stateful objects can be mutated to contain different state even if their attributes (the contained state) happen initially to be the same.

▪ The bottom line is that all forms of OOP rely on state (contained within objects) and in general all behaviour is affected by this state. As a result of this, OOP suffers directly from the problems associated with state described above, and as such we believe that it does not provide an adequate foundation for avoiding complexity.

▪ One slight variation is that actor-style languages use the “message-passing” model of concurrency — they associate threads of control with individual objects and messages are passed between these. This can lead to easier informal reasoning in some cases, but the use of actor-style languages is not widespread.

▪ Conventional imperative and object-oriented programs suffer greatly from both state-derived and control-derived complexity.

▪ The untyped lambda calculus is known to be equivalent in power to the standard stateful abstraction of computation — the Turing machine.

▪ Modern functional programming languages are often classified as ‘pure’ — those such as Haskell [PJ+03] which shun state and side-effects completely, and ‘impure’ — those such as ML which, whilst advocating the avoidance of state and side-effects in general, do permit their use.

▪ The primary strength of functional programming is that by avoiding state (and side-effects) the entire system gains the property of referential transparency — which implies that when supplied with a given set of arguments a function will always return exactly the same result (speaking loosely we could say that it will always behave in the same way).

▪ As a result, even though the other weakness of testing remains (testing for one set of inputs says nothing at all about behaviour with another set of inputs), testing does become far more effective if a system has been developed in a functional style.

▪ By avoiding state functional programming also avoids all of the other state-related weaknesses discussed above, so — for example — informal reasoning also becomes much more effective.

▪ Functional languages do derive one slight benefit when it comes to control because they encourage a more abstract use of control using functionals (such as fold / map) rather than explicit looping.

▪ In most of this paper when we refer to “state” what we really mean is mutable state.

▪ Despite this, the fact is that we are using functional values to simulate state. There is in principle nothing to stop functional programs from passing a single extra parameter into and out of every single function in the entire system. If this extra parameter were a collection (compound value) of some kind then it could be used to simulate an arbitrarily large set of mutable variables.

▪ In effect this approach recreates a single pool of global variables — hence, even though referential transparency is maintained, ease of reasoning is lost (we still know that each function is dependent only upon its arguments, but one of them has become so large and contains irrelevant values that the benefit of this knowledge as an aid to understanding is almost nothing). This is however an extreme example and does not detract from the general power of the functional approach.

▪ It is worth noting in passing that — even though it would be no substitute for a guarantee of referential transparency — there is no reason why the functional style of programming cannot be adopted in stateful languages (i.e. imperative as well as impure functional ones). More generally, we would argue that — whatever the language being used — there are large benefits to be had from avoiding hidden, implicit, mutable state.

▪ It is sometimes argued (e.g. [vRH04]) that state is important because it permits a particular kind of modularity. This is certainly true. Working within a stateful framework it is possible to add state to any component without adjusting the components which invoke it. Working within a functional framework the same effect can only be achieved by adjusting every single component that invokes it to carry the additional information around (as with the getNextCounter function above).

▪ There is a fundamental trade-off between the two approaches. In the functional approach (when trying to achieve state-like results) you are forced to make changes to every part of the program that could be affected (adding the relevant extra parameter), in the stateful you are not.

▪ But what this means is that in a functional program you can always tell exactly what will control the outcome of a procedure (i.e. function) simply by looking at the arguments supplied where it is invoked. In a stateful program this property (again a consequence of referential transparency) is completely destroyed, you can never tell what will control the outcome, and potentially have to look at every single piece of code in the entire system to determine this information.

▪ The trade-off is between complexity (with the ability to take a shortcut when making some specific types of change) and simplicity (with huge improvements in both testing and reasoning).

▪ As with the discipline of (static) typing, it is trading a one-off up-front cost for continuing future gains and safety (“one-off” because each piece of code is written once but is read, reasoned about and tested on a continuing basis).

▪ Still, the fact remains that such arguments have been insufficient to result in widespread adoption of functional programming. We must therefore conclude that the main weakness of functional programming is the flip side of its main strength — namely that problems arise when (as is often the case) the system to be built must maintain state of some kind.

▪ Again, despite their huge strengths, monads have as yet been insufficient to give rise to widespread adoption of functional techniques.

▪ Together with functional programming, logic programming is considered to be a declarative style of programming because the emphasis is on specifying what needs to be done rather than exactly how to do it.

▪ The seminal “logic programming” language was Prolog. Prolog is best seen as a pure logical core (pure Prolog) with various extra-logical5 extensions.

▪ It is for this reason that Prolog falls short of the ideals of logic programming. Specifically it is necessary to be concerned with the operational interpretation of the program whilst writing the axioms.

▪ Other languages such as Oz (which has its roots in logic programming but has been extended to become “multi-paradigm”) provide mutable state in a traditional way — similar to the way it is provided by impure functional languages.

▪ Brooks defined difficulties of “essence” as those inherent in the nature of software and classified the rest as “accidents”

▪ We shall basically use the terms in the same sense — but prefer to start by considering the complexity of the problem itself before software has even entered the picture.

▪ Hence we define the following two types of complexity:

Essential Complexity
is inherent in, and the essence of, the problem (as seen by the users).
Accidental Complexity
is all the rest — complexity with which the development team would not have to deal in the ideal world (e.g. complexity arising from performance issues and from suboptimal language and infrastructure).

▪ Note that the definition of essential is deliberately more strict than common usage. Specifically when we use the term essential we will mean strictly essential to the users’ problem (as opposed to — perhaps — essential to some specific, implemented, system, or even — essential to software in general). For example — according to the terminology we shall use in this paper — bits, bytes, transistors, electricity and computers themselves are not in any way essential (because they have nothing to do with the users’ problem).

▪ In order to justify these two definitions we start by considering the role of a software development team — namely to produce (using some given language and infrastructure) and maintain a software system which serves the purposes of its users

▪ The complexity in which we are interested is the complexity involved in this task, and it is this which we seek to classify as accidental or essential. We hence see essential complexity as “the complexity with which the team will have to be concerned, even in the ideal world”.

▪ Note that the “have to” part of this observation is critical — if there is any possible way that the team could produce a system that the users will consider correct without having to be concerned with a given type of complexity then that complexity is not essential.

▪ Given that in the real world not all possible ways are practical, the implication is that any real development will need to contend with some accidental complexity. The definition does not seek to deny this — merely to identify its secondary nature.

▪ Ultimately (as we shall see below in section 7) our definition is equivalent to saying that what is essential to the team is what the users have to be concerned with. This is because in the ideal world we would be using language and infrastructure which would let us express the users’ problem directly without having to express anything else — and this is how we arrive at the definitions given above.

▪ Brooks asserts [Bro86] (and others such as Booch agree [Boo91]) that “The complexity of software is an essential property, not an accidental one”. This would suggest that the majority (at least) of the complexity that we find in contemporary large systems is of the essential type.

▪ When it comes to accidental and essential complexity we firmly believe that the former exists and that the goal of software engineering must be both to eliminate as much of it as possible, and to assist with the latter.

▪ Given that our main recommendations revolve around trying to avoid as much accidental complexity as possible, we now need to look at which bits of the complexity must be considered accidental and which essential.

▪ Our next observation is that because we ultimately need something to happen — i.e. we are going to need to have our system processed mechanically (on a computer) — we are going to need formality. We are going to need to derive formal requirements from the informal ones.

▪ So, taken together, this means that even in the ideal world we have:

Informal requirements → Formal requirements

▪ It is interesting to note that effectively what we have just described is in fact the very essence of declarative programming — i.e. that you need only specify what you require, not how it must be achieved.

▪ All data will either be provided directly to the system (input) or derived.

▪ Data of this kind can always be re-derived (from the input data — i.e. from the essential state) whenever required. As a result we do not need to store it in the ideal world (we just re-derive it when it is required) and it is clearly accidental state.

▪ even in the ideal world we are going to have some essential state — as we have just established

▪ The obvious implication of the above is that there are large amounts of accidental state in typical systems. In fact, it is our belief that the vast majority of state (as encountered in typical contemporary systems) simply isn’t needed (in this ideal world).

▪ Because of this, and the huge complexity which state can cause, the ideal world removes all non-essential state.

▪ As already noted, our vision of an ideal world is similar in many ways to the vision of declarative programming that lies behind functional and logic programming.

▪ One possible situation of this kind is for derived data which is dependent upon both a whole series of user inputs over time, and its own previous values. In such cases it can be advantageous10 to maintain the accidental state even in the ideal world.

▪ An example of this would be the derived data representing the position state of a computer-controlled opponent in an interactive game — it is at all times derivable by a function of both all prior user movements and the initial starting positions,11 but this is not the way it is most naturally expressed.

▪ Performance
making use of accidental state and control can be required for efficiency — as we saw in the second problem of section 7.2.1.

▪ Ease of Expression
making use of accidental state can be the most natural way to express logic in some cases — as we saw in section 7.2.2.

▪ Of the two, we believe that performance will be the most common.

▪ Our recommendations for dealing with complexity (as exemplified by both state and control) can be summed up as:

Avoid
Separate

▪ Specifically the overriding aim must be to avoid state and control where they are not absolutely and truly essential.

▪ The recommendation of avoidance is however tempered by the acknowledegment that there will sometimes be complexity that either is truly essential (section 7.1.1) or, whilst not truly essential, is useful from a practical point of view ( section 7.2.3). Such complexity must be separated out from the rest of the system — and this gives us our second recommendation.

▪ There is nothing particularly profound in these recommendations, but they are worth stating because they are emphatically not the way most software is developed today.

▪ Indeed, as we shall see (in section 7.3.2), from the point of view of the logic of the system, we can effectively forget that the accidental state even exists. More specific examples of this approach are given in the second half of this paper.

▪ This problem (see section 7.2.2) fundamentally arises when derived (i.e. accidental) state offers the most natural way to express parts of the logic of the system.

▪ Instead what we recommend is that, in cases where it really is the only natural thing to do, we should pretend that the accidental state is really essential state for the purposes of the separation discussed below

▪ One implication of this overall structure is that the system (essential + accidental but useful) should still function completely correctly if the “accidental but useful” bits are removed (leaving only the two essential components) — albeit possibly unacceptably slowly.

▪ The differing nature of what is specified by each of the components leads naturally to certain relationships between them, to restrictions on the ways in which they can or cannot refer to each other. These restrictions are absolute, and because of this provide a huge aid to understanding the different components of the system independently.

▪ Essential State
This can be seen as the foundation of the system. The specification of the required state is completely self-contained — it can make no reference to either of the other parts which must be specified. One implication of this is that changes to the essential state specification itself may require changes in both the other specifications, but changes in either of the other specifications may never require changes to the specification of essential state.

▪ Essential Logic
This is in some ways the “heart” of the system — it expresses what is sometimes termed the “business” logic

▪ This logic expresses — in terms of the state — what must be true. It does not say anything about how, when, or why the state might change dynamically — indeed it wouldn’t make sense for the logic to be able to change the state in any way.
Changes to the essential state specification may require changes to the logic specification, and changes to the logic specification may require changes to the specification for accidental state and control. The logic specification will make no reference to any part of the accidental specification. Changes in the accidental specification can hence never require any change to the essential logic.

▪ Accidental State and Control
This (by virtue of its accidental nature) is conceptually the least important part of the system. Changes to it can never affect the other specifications (because neither of them make any reference to any part of it), but changes to either of the others may require changes here.

▪ This first part of the paper has done two main things. It has given arguments for the overriding danger of complexity, and it has given some hope that much of the complexity may be avoided or controlled.

▪ The key difference between what we are advocating and existing approaches (as embodied by the various styles of programming language) is a high level separation into three components — each specified in a different language14

▪ Doing this separation when building a system may not be easy, but we believe that for any large system it will be significantly less difficult than dealing with the complexity that arises otherwise.

▪ It is hard to overstate the dangers of complexity. If it is not controlled it spreads. The only way to escape this risk is to place the goals of avoid and separate at the top of the design objectives for a system.

▪ It is not sufficient simply to pay heed to these two objectives — it is crucial that they be the overriding consideration. This is because complexity breeds complexity and one or two early “compromises” can spell complexity disaster in the long run.

▪ It is worth noting in particular the risks of “designing for performance”. The dangers of “premature optimisation” are as real as ever — there can be no comparison between the difficulty of improving the performance of a slow system designed for simplicity and that of removing complexity from a complex system which was designed to be fast (and quite possibly isn’t even that because of myriad inefficiencies hiding within its complexity).

▪ The relational model [Cod70] has — despite its origins — nothing intrinsically to do with databases. Rather it is an elegant approach to structuring data, a means for manipulating such data, and a mechanism for maintaining integrity and consistency of state. These features are applicable to state and data in any context.

▪ In addition to these three broad areas [Cod79, section 2.1], [Dat04, p109], a fourth strength of the relational model is its insistence on a clear separation between the logical and physical layers of the system.

▪ We see the relational model as having the following four aspects:

▪ Structure
the use of relations as the means for representing all data

▪ Manipulation
a means to specify derived data

▪ Integrity
a means to specify certain inviolable restrictions on the data

▪ Data Independence
a clear separation is enforced between the logical data and its physical representation

▪ As a final comment, it is widely recognised that SQL (of any version) — despite its widespread use — is not an accurate reflection of the relational model [Cod90, p371, Serious flaws in SQL], [Dat04, p xxiv] so the reader is warned against equating the two.

▪ As mentioned above, relations provide the sole means for structuring data in the relational model

▪ A relation is best seen as a homogeneous set of records, each record itself consisting of a heterogeneous set of uniquely named attributes (this is slightly different from the general mathematical definition of a relation as a set of tuples whose components are identified by position rather than name).

▪ Implications of this definition include the fact that — by virtue of being a set — a relation can contain no duplicates, and it has no ordering

▪ Both of these restrictions are in contrast with the common usage of the word table which can obviously contain duplicate rows (and column names), and — by virtue of being a visual entity on a page — inevitably has both an ordering of its rows and of its columns.

▪ Base Relations
are those which are stored directly
Derived Relations
(also known as Views) are those which are defined in terms of other relations (base or derived) — see section 8.2

▪ The idea of structuring data using relations is appealing because no subjective, up-front decisions need to be made about the access paths that will later be used to query and process the data.

▪ The two main data structuring approaches which preceded the relational model (the network and hierarchical models) were both access path dependent in this way.

▪ For example, in the hierarchical model a subjective choice would be forced early on as to whether departments would form the top level (with each department “containing” its employees) or the other way round (with employees “containing” their departments). The choice made would impact all future use of the data.

▪ If the first alternative was selected, then users of the data would find it easy to retrieve all employees within a given department (following the access path), but they would find it harder to retrieve the department of a given employee (and would have to use some other technique corresponding to a search of all departments).

▪ The network model alleviated the problem to some degree by allowing multiple access paths between data instances (so the choice could be made to provide both an access path from department to employee and an access path from employee to department). The problem of course is that it is impossible to predict in advance what all the future required access paths will be, and because of this there will always be a disparity between:

▪ Primary retrieval requirements
which were foreseen, and can be satisfied simply by following the provided access paths
Secondary retrieval requirements
which were either unforeseen, or at least not specially supported, and hence can only be satisfied by some alternative mechanism such as search

▪ The ability of the relational model to avoid access paths completely was one of the primary reasons for its success over the network and hierarchical models.

▪ It is also interesting to consider briefly what is involved when taking an object-oriented (OOP) approach to our example. We can choose between the following options:

Give Employee objects a reference to their Department
Give Department objects a set (or array) of references to their Employees
Both of the above

▪ If we choose the third option, then we at best expose ourselves to extra work in maintaining the redundant references, and at worst expose ourselves to bugs.

▪ There are disturbing similarities between the data structuring approaches of OOP and XML on the one hand and the network and hierarchical models on the other.

▪ A final advantage of using relations for the structure — in contrast with approaches such as Chen’s ER-modelling [Che76] — is that no distinction is made between entities and relationships. (Using such a distinction can be problematic because whether something is an entity or a relationship can be a very subjective question).

▪ Codd introduced two different mechanisms for expressing the manipulation aspects of the relational model — the relational calculus and the relational algebra. They are formally equivalent (in that expressions in each can be converted into equivalent expressions in the other), and we shall only consider the algebra.

▪ One significant benefit of this manipulation language (aside from its simplicity) is that it has the property of closure — that all operands and results are of the same kind (relations) — hence the operations can be nested in arbitrary ways (indeed this property is inherent in any single-sorted algebra).

▪ The approach of functional relational programming (FRP16) derives its name from the fact that the essential components of the system (the logic and the essential state) are based upon functional programming and the relational model (see Figure 2).

▪ Essential State
A Relational definition of the stateful components of the system

▪ Essential Logic
Derived-relation definitions, integrity constraints and (pure) functions

▪ Accidental State and Control
A declarative specification of a set of performance optimizations for the system

▪ Other
A specification of the required interfaces to the outside world (user and system interfaces)

▪ In contrast with the object-oriented approach, FRP emphasises a clear separation of state and behaviour19.

▪ This component consists solely of a specification of the essential state for the system in terms of base relvars20

▪ Specifically it is the names and types of the base relvars that are specified here, not their actual contents. The contents of the relvars (i.e. the relations themselves) will of course be crucial when the system is used, but here we are discussing only the static structure of the system.

▪ In accordance with section 7.1.1, FRP strongly encourages that data be treated as essential state only21 when it has been input directly by a user22.

▪ In addition to the relational algebra, the definitions can make use of an arbitrary set of pure user-defined functions which make up the functional part of the essential logic.

▪ What is true is that more normalized designs do impose implicit restrictions, and this can reduce the number of (explicit) integrity constraints that must be specified.

▪ This component fundamentally consists of a series of isolated (in the sense that they cannot refer to each other in any way) performance “hints”. These hints — which should be declarative in nature — are intended to provide guidance to the infrastructure responsible for running the FRP system.

▪ An example of the first kind of state-related hint might be a simple directive that a particular derived-relvar should actually be stored (rather than continually recalculated), so that it is always quickly available.

▪ Specifically, all input must be converted into relational assignments (which replace the old relvar values in the essential state with new ones), and all output (and side-effects) must be driven from changes to the values of relvars (primarily derived relvars).

▪ The exact nature of this task is likely to be highly application-dependent, but we can say that there will probably be a requirement for a series of feeder (or input) and observer (or output) components. These may well be defined, at least partially, in a traditional, imperative way if custom interfacing is required.

▪ Feeders are components which convert input into relational assignments — i.e. cause changes to the essential state. In order to be able to cause these state changes, feeders will need to specify them in some form of state manipulation language provided by the infrastructure.

▪ The infrastructure which eventually runs the FRP system will ensure that the command respects the integrity constraints23 — either by rejecting non-conformant commands, or possibly in some cases by modifying them to ensure conformance.

▪ The infrastructure which runs the system will ensure that the observer is invoked (with the new relation value) whenever it changes. In this way observers act both as what are sometimes called live-queries and also as triggers.

▪ In several places above we have referred to the “infrastructure which runs the FRP system”. The FRP system is the specification — comprising of the four components above, the infrastructure is what is needed to execute this specification (by interpretation, compilation or some mixture).

▪ It does not have to be a functional language, but the infrastructure must only allow it to be used in a functional way

▪ The minimum requirement on the infrastructure from observers is for it to be able to supply the new value of a relvar whenever it changes.

▪ Practical extensions that could be useful are the ability to provide deltas, throttling and coalescing capabilities (if the observers are viewed as live query-handlers, then these extensions represent potential query meta-data).

▪ Finally, the ability to access arbitrary historical relvar values would obviously be a useful extension in some scenarios.

▪ Finally, it is of course perfectly possible to develop an FRP infrastructure in any general purpose language — be it object-oriented, functional or logic.

▪ FRP follows the guidelines of avoid and separate as recommended in section 7 and hence gains all the benefits which derive from that.

▪ The architecture is explicitly designed to avoid useless accidental state, and to avoid even the possibility of an FRP system ever getting into a “bad state”.

▪ Specifically derived state is not normally stored (is not treated as essential state). In normal circumstances26 hybrid feeders/observers never feed back in the exact same data which they observed — they only ever feed in some externally generated input or response.

▪ When it comes to separation, the architecture clearly exhibits both the logic / state split and the accidental / essential split recommended in section 7.

▪ An example of what this means is that you do not have to think about any accidental state when concentrating on the logic of your system.

▪ In fact, you do not really have to think about the essential state as being state either — from the point of view of the logic, the essential state is seen as constant.

▪ Furthermore, the functional component (of the logic) has no access to any state at all (even the essential state) — it is totally referentially transparent, can only access what is supplied in the function arguments, and hence offers hugely better prospects for testing (as mentioned earlier in section 4.1.1).

▪ Additionally, there are major advantages gained from adopting a relational representation of data — specifically, there is no introduction of subjective bias into the data, no concern with data access paths. This is in contrast with approaches such as OOP or XML (as we saw in section 8.1.2).

▪ FRP also avoids any explicit parallelism in the essential components but provides for the possibility of separated accidental control should that be required.

▪ By data abstraction we basically mean the creation of compound data types and the use of the corresponding compound values (whose internal contents are hidden).

▪ We believe that in many cases, un-needed data abstraction actually represents another common (and serious) cause of complexity.

▪ Subjectivity
Firstly the grouping of data items together into larger compound data abstractions is an inherently subjective business (Ungar and Smith discuss this problem in the context of Self in [SU96]). Groupings which make sense for one purpose will inevitably differ from those most natural for other uses, yet the presence of pre-existing data abstractions all too easily leads to inappropriate reuse.

▪ Data Hiding
Secondly, large and heavily structured data abstractions can seriously erode the benefits of referential transparency (section 5.2.1) in exactly the manner of the extreme example discussed in section 5.2.3. This problem occurs both because data abstractions will often cause un-needed, irrelevant data to be supplied to a function, and because the data which does get used (and hence influences the result of a function) is hidden at the function call site. This hidden and excessive data leads to problems for testing as well as informal reasoning in ways very similar to state (see section 4.1).

▪ FRP also offers benefits in the area of data hiding, simply by discouraging it. Specifically, FRP offers no support for nested relations or for creating product types (as we shall see in section 9.3).

▪ Once the system is deployed, the FRP infrastructure will reject any state modification attempts which would violate any of these integrity constraints.

▪ This hint instructs the infrastructure to denormalize the Room and Floor relations into a single shared storage structure. (Note that because we are able to express this as part of the accidental state and control we have not been forced to compromise the essential parts of our system which still treat Room and Floor separately).

▪ FRP draws some influence from the ideas of [DD00]. In contrast with this work however, FRP is aimed at general purpose, large-scale application programming.

▪ There are also some similarities to Backus’ Applicative State Transition systems [Bac78], and to the Aldat project at McGill [Mer85] which investigated general purpose applications of relational algebra.

▪ We have argued that complexity causes more problems in large software systems than anything else. We have also argued that it can be tamed — but only through a concerted effort to avoid it where possible, and to separate it where not.

▪ Specifically we have argued that a system can usefully be separated into three main parts: the essential state, the essential logic, and the accidental state and control.

▪ We believe that taking these principles and applying them to the top level of a system design — effectively using different specialised languages for the different components — can offer more in terms simplicity than can the unstructured adoption of any single general language (be it imperative, logic or functional).

▪ In cases (such as existing large systems) where this separation cannot be directly applied we believe the focus should be on avoiding state, avoiding explicit control where possible, and striving at all costs to get rid of code.

▪ So, what is the way out of the tar pit? What is the silver bullet? … it may not be FRP, but we believe there can be no doubt that it is simplicity.

▪ By “state” we mean mutable state specifically — i.e. excluding things like (immutable) single-assignment variables which are provided by logic programming languages for example

▪ There is some limited similarity between our goal of “Separate” and the goal of separation of concerns as promoted by proponents of Aspect Oriented Programming — but as we shall see in section 7.3.2, exactly what is meant by separation is critical.

▪ Not to be confused with functional reactive programming [EH97] which does in fact have some similarities to this approach, but has no intrinsic focus on relations or the relational model

▪ Other systems connected electronically are considered equivalent to users inputting data for these purposes.

▪ Frederick P. Brooks, Jr. No silver bullet: Essence and accidents of software engineering.

▪ Mythical Man-Month: Essays on Software Engineering,

▪ P. P. Chen. “The Entity-Relationship Model”.

▪ Edsger W. Dijkstra. The humble programmer. 
