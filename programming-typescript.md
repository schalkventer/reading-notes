Programming TypeScript (2019)

Boris Cherny

───────────────

▪ Regardless of what programming languages you’ve used in the past, what unites all of us is our shared experience of tracking down exceptions, tracing through code line by line to figure out what went wrong and how we can fix it.

▪ You should keep your data structures immutable with spreads (...) most of the time

▪ JavaScript doesn’t expose pointers and references; instead it has value and reference types

▪ Values are immutable, and include things like strings, numbers, and booleans, while references point to often-mutable data structures like arrays, objects, and functions.

▪ When I use the word “value” in this book, I usually mean it loosely to refer to either a JavaScript value or a reference.

▪ This book largely presents how you should write TypeScript, and makes an argument for why you should try really hard not to make compromises. But in practice, how correct your code is is up to you and your team.

▪ If you’re not coming from JavaScript, here’s an example: if you have an object o, and you want to add a property k to it with the value 3, you can either mutate o directly—o.k = 3
—or you can apply your change to o, creating a new object as a result—let p = {...o, k: 3}

▪ Whatever your reasons are, what you’ve heard is true. TypeScript is the language that will power the next generation of web apps, mobile apps, NodeJS projects, and Internet of Things (IoT) devices. It will make your programs safer by checking for common mistakes, serve as documentation for yourself and future engineers, make refactoring painless, and make, like, half of your unit tests unnecessary (“What unit tests?”). TypeScript will double your productivity as a programmer, and it will land you a date with that cute barista across the street.

▪ What I am talking about, of course, is type safety.

▪ Here are a few examples of things that are invalid:

▪ Multiplying a number and a list

▪ Calling a function with a list of strings when it actually needs a list of objects

▪ Calling a method on an object when that method doesn’t actually exist on that object

▪ Importing a module that was recently moved

▪ Notice that instead of throwing exceptions when you try to do things that are obviously invalid, JavaScript tries to make the best of it and avoids exceptions whenever it can. Is JavaScript being helpful? Certainly. Does it make it easier for you to catch bugs quickly? Probably not.

▪ Don’t get me wrong: trying to fix our mistakes for us is a neat feature for a programming language to have (if only it worked for more than just programs!). But for JavaScript, this feature creates a disconnect between when you make a mistake in your code, and when you find out that you made a mistake in your code. Often, that means that the first time you hear about your mistake will be from someone else.

▪ So here’s a question: when exactly does JavaScript tell you that you made a mistake?

▪ Your program might get run when you test it in a browser, or when a user visits your website, or when you run a unit test. If you’re disciplined and write plenty of unit tests and end-to-end tests, smoke test your code before pushing it, and test it internally for a while before shipping it to users, you will hopefully find out about your error before your users do

▪ Even cooler than the fact that TypeScript gives you helpful error messages is when it gives them to you: TypeScript gives you error messages in your text editor, as you type.

▪ In addition to eliminating entire classes of type-related bugs, this will actually change the way you write code. You will find yourself sketching out a program at the type level before you fill it in at the value level;

▪ Depending on which statically typed language you use, “invalid” can mean a range of things, from programs that will crash when you run them to things that won’t crash but are clearly nonsensical.

▪ JavaScript compilers and runtimes tend to be smushed into a single program called an engine; as a programmer, this is what you’ll normally interact with. It’s how V8 (the engine powering NodeJS, Chrome, and Opera), SpiderMonkey (Firefox), JSCore (Safari), and Chakra (Edge) work, and it’s what gives JavaScript the appearance of being an interpreted language.

▪ There are generally two kinds of type systems: type systems in which you have to tell the compiler what type everything is with explicit syntax, and type systems that infer the types of things for you automatically. Both approaches have trade-offs.1

▪ Dynamic type binding means that JavaScript needs to actually run your program to know the types of things in it. JavaScript doesn’t know your types before running your program.

▪ TypeScript is a gradually typed language. That means that TypeScript works best when it knows the types of everything in your program at compile time, but it doesn’t have to know every type in order to compile your program.

▪ JavaScript is weakly typed, meaning if you do something invalid like add a number and an array (like we did in Chapter 1), it will apply a bunch of rules to figure out what you really meant so it can do the best it can with what you gave it.

▪ Let’s walk through the specific example of how JavaScript evaluates 3 + [1]
:

JavaScript notices that 3 is a number and [1] is an array.

Because we’re using +, it assumes we want to concatenate the two.

It implicitly converts 3 to a string, yielding "3".

It implicitly converts [1] to a string, yielding "1".

It concatenates the results, yielding "31".

▪ While JavaScript tries to be helpful by doing clever type conversions for you, TypeScript complains as soon as you do something invalid. When you run that same JavaScript code through TSC, you’ll get an error:

3 + [1]; // Error TS2365: Operator '+' cannot be applied to
// types '3' and 'number[]'.

▪ If you do something that doesn’t seem right, TypeScript complains, and if you’re explicit about your intentions, TypeScript gets out of your way. This behavior makes sense: who in their right mind would try to add a number and an array, expecting the result to be a string

▪ The kind of implicit conversion that JavaScript does can be a really hard-to-track-down source of errors, and is the bane of many JavaScript programmers. It makes it hard for individual engineers to get their jobs done, and it makes it even harder to scale code across a large team, since every engineer needs to understand the implicit assumptions your code makes.

▪ In short, if you must convert types, do it explicitly.

▪ In most places JavaScript doesn’t care what types you give it, and it instead tries to do its best to convert what you gave it to what it expects.

▪ TypeScript statically analyzes your code for errors like these, and shows them to you before you run it. If your code doesn’t compile, that’s a really good sign that you made a mistake and you should fix it before you try to run the code.

▪ With a good TypeScript extension for your preferred code editor, the error will show up as a red squiggly line under your code as you type it. This dramatically speeds up the feedback loop between writing code, realizing that you made a mistake, and updating the code to fix that mistake.

▪ When JavaScript throws exceptions or performs implicit type conversions, it does so at runtime.2 This means you have to actually run your program to get a useful signal back that you did something invalid. In the best case, that means as part of a unit test; in the worst case, it means an angry email from a user.

▪ That said, there are lots of errors that TypeScript can’t catch for you at compile time—things like stack overflows, broken network connections, and malformed user inputs—that will still result in runtime exceptions. What TypeScript does is make compile-time errors out of most errors that would have otherwise been runtime errors in a pure JavaScript world.

▪ Every TypeScript project should include a file called tsconfig.json in its root directory. This tsconfig.json is where TypeScript projects define things like which files should be compiled, which directory to compile them to, and which version of JavaScript to emit.

▪ include　Which folders should TSC look in to find your TypeScript files?

▪ lib         　Which APIs should TSC assume exist in the environment you’ll be running your code in? This includes things like ES5’s Function.prototype.bind, ES2015’s Object.assign, and the DOM’s document.querySelector.　

▪ module　Which module system should TSC compile your code to (CommonJS, SystemJS, ES2015, etc.)?

▪ outDir  Which folder should TSC put your generated JavaScript code in?　

▪ strict    Be as strict as possible when checking for invalid code. This option enforces that all of your code is properly typed. We’ll be using it for all of the examples in the book, and you should use it for your TypeScript project too.　

▪ target   　Which JavaScript version should TSC compile your code to (ES3, ES5, ES2015, ES2016, etc.)?　

▪ These are just a few of the available options—tsconfig.json supports dozens of options, and new ones are added all the time

▪ You won’t find yourself changing these much in practice, besides dialing in the module and target settings when switching to a new module bundler, adding "dom" to lib when writing TypeScript for the browser (you’ll learn more about this in Chapter 12), or adjusting your level of strictness when migrating your existing JavaScript code to TypeScript (see “Gradually Migrating from JavaScript to TypeScript”).

▪ Note that while using a tsconfig.json file to configure TSC is handy because it lets us check that configuration into source control, you can set most of TSC’s options from the command line too

▪ Install ts-node, and use it to compile and run your TypeScript with a single command

▪ Use a scaffolding tool like typescript-node-starter to quickly generate your folder structure for you.

▪ There are languages all over this spectrum: JavaScript, Python, and Ruby infer types at runtime; Haskell and OCaml infer and check missing types at compile time; Scala and TypeScript require some explicit types and infer and check the rest at compile time; and Java and C need explicit annotations for almost everything, which they check at compile time.

▪ To be sure, JavaScript surfaces syntax errors and a few select bugs (like multiple const declarations with the same name in the same scope) after it parses your program, but before it runs it. If you parse your JavaScript as part of your build process (e.g., with Babel), you can surface these errors at build time.

▪ Incrementally compiled languages can be quickly recompiled when you make a small change, rather than having to recompile your whole program (including the parts you didn’t touch).

▪ The boolean type is the set of all booleans (there are just two: true and false) and the operations you can perform on them (like ||, &&, and !).

▪ The number type is the set of all numbers and the operations you can perform on them (like +, -, *, /, %, ||, &&, and ?), including the methods you can call on them like .toFixed, .toPrecision, .toString, and so on.

▪ When you see that something is of type T, not only do you know that it’s a T, but you also know exactly what you can do with that T (and what you can’t). Remember, the whole point is to use the typechecker to stop you from doing invalid things. And the way the typechecker knows what’s valid and what’s not is by looking at the types you’re using and how you’re using them.

▪ any is the Godfather of types. It does anything for a price, but you don’t want to ask any for a favor unless you’re completely out of options

▪ In TypeScript everything needs to have a type at compile time, and any is the default type when you (the programmer) and TypeScript (the typechecker) can’t figure out what type something is. It’s a last resort type, and you should avoid it when possible.

▪ Why should you avoid it? Remember what a type is? (It’s a set of values and the things you can do with them.) any is the set of all values, and you can do anything with any. That means that if you have a value of type any you can add to it, multiply by it, call .pizza() on it—anything.

▪ By default, TypeScript is permissive, and won’t complain about values that it infers as any. To get TypeScript to complain about implicit anys, be sure to enable the noImplicitAny flag in your tsconfig.json.

▪ noImplicitAny is part of the strict family of TSC flags, so if you already enabled strict in your tsconfig.json (as we did in “tsconfig.json”), you’re good to go.

▪ If any is the Godfather, then unknown is Keanu Reeves as undercover FBI agent Johnny Utah in Point Break: laid back, fits right in with the bad guys, but deep down has a respect for the law and is on the side of the good guys

▪ For the few cases where you have a value whose type you really don’t know ahead of time, don’t use any, and instead reach for unknown

▪ Like any, it represents any value, but TypeScript won’t let you use an unknown type until you refine it by checking what it is (see “Refinement”).

▪ What operations does unknown support? You can compare unknown values (with ==, ===, ||, &&, and ?), negate them (with !), and refine them (like you can any other type) with JavaScript’s typeof and instanceof operators

▪ TypeScript will never infer something as unknown—you have to explicitly annotate it (a).

▪ You can compare values to values that are of type unknown (b).

▪ But, you can’t do things that assume an unknown value is of a specific type (c); you have to prove to TypeScript that the value really is of that type first (d).

▪ By using a value as a type, I essentially limited the possible values for e and f from all booleans to one specific boolean each. This feature is called type literals.

▪ TypeScript inferred a literal type for me because I used const instead of let or var. Because TypeScript knows that once a primitive is assigned with const its value will never change, it infers the most narrow type it can for that variable.

▪ Type literals make TypeScript unique in the language world and are something you should lord over your Java friends.

▪ number is the set of all numbers: integers, floats, positives, negatives, Infinity, NaN, and so on

▪ When working with long numbers, use numeric separators to make those numbers easier to read. You can use numeric separators in both type and value positions:

let oneMillion = 1_000_000 // Equivalent to 1000000
let twoMillion: 2_000_000 = 2_000_000

▪ bigint is a newcomer to JavaScript and TypeScript: it lets you work with large integers without running into rounding errors

▪ While the number type can only represent whole numbers up to 253, bigint can represent integers bigger than that too.

▪ The bigint type is the set of all BigInts, and supports things like addition (+), subtraction (-), multiplication (*), division (/), and comparison (

▪ let a = 1234n

▪ const b = 5678n

▪ The way Symbol('a') works in JavaScript is by creating a new symbol with the given name; that symbol is unique, and will not be equal (when compared with == or ===) to any other symbol (even if you create a second symbol with the same exact name!)

▪ symbols are inferred to be of type symbol but can be explicitly typed as unique symbol

▪ const e = Symbol('e') // typeof e

▪ TypeScript will infer its type as unique symbol
. It will show up as typeof yourVariableName, not unique symbol
, in your code editor.

▪ This is by design: JavaScript is generally structurally typed, so TypeScript favors that style of programming over a nominally typed style.

▪ Structural typing

A style of programming where you just care that an object has certain properties, and not what its name is (nominal typing). Also called duck typing in some languages (or, not judging a book by its cover).

▪ There are a few ways to use types to describe objects in TypeScript. The first is to declare a value as an object:

let a: object = {
b: 'x'
}

▪ In fact, object is a little narrower than any, but not by much. object doesn’t tell you a lot about the value it describes, just that the value is a JavaScript object (and that it’s not null).

▪ You can either let TypeScript infer your object’s shape for you, or explicitly describe it inside curly braces({}):

▪ Unlike the primitive types we’ve looked at so far—boolean, number, bigint, string, and symbol—declaring an object with const won’t hint to TypeScript to infer its type more narrowly. That’s because JavaScript objects are mutable, and for all TypeScript knows you might update their fields after you create them.

▪ Object literal syntax says, “Here is a thing that has this shape.” The thing might be an object literal, or it might be a class:

▪ describes the shape of an object, and both the object literal and the class instance from the last example satisfy that shape, so TypeScript lets us assign a Person to c.

▪ When you declare a variable in one place and initialize it later, TypeScript will make sure that your variable is definitely assigned a value by the time you use it:

▪ Can you tell TypeScript that something is optional, or that there might be more properties than you planned for? You bet:

▪ let a: {
b: number ￼
c?: string ￼
[key: number]: boolean ￼
}

▪ a might have any number of numeric properties that are booleans.

▪ Index Signatures

The [key: T]: U
syntax is called an index signature, and this is the way you tell TypeScript that the given object might contain more keys

▪ The way to read it is, “For this object, all keys of type T must have values of type U.”

▪ Index signatures let you safely add more keys to an object, in addition to any keys that you explicitly declared.

▪ There is one rule to keep in mind for index signatures: the index signature key’s type (T) must be assignable to either number or string.2

▪ Also note that you can use any word for the index signature key’s name—it doesn’t have to be key:

▪ You can also mark fields as read-only (that is, you can declare that a field can’t be modified after it’s assigned an initial value—kind of like const for object properties) with the readonly modifier:

▪ user.firstName =
'abbey with an e' // Error TS2540: Cannot assign to 'firstName' because it
// is a read-only property.

▪ Object literal notation has one special case: empty object types ({}). Every type—except null and undefined—is assignable to an empty object type, which can make it tricky to use. Try to avoid empty object types when possible:

▪ As a final note on objects, it’s worth mentioning one last way of typing something as an object: Object. This is pretty much the same as using {}, and is best avoided

▪ Object literal notation (like {a: string}
), also called a shape.

▪ Type aliases

Just like you can use variable declarations (let, const, and var) to declare a variable that aliases a value, you can declare a type alias that points to a type

▪ Age is but a number. It can also help make the definition of the Person shape easier to understand

▪ Aliases are never inferred by TypeScript, so you have to type them explicitly:

▪ Because Age is just an alias for number, that means it’s also assignable to number, so we can rewrite this as:

let age = 55

▪ Like JavaScript variable declarations (let, const, and var), you can’t declare a type twice:

▪ And like let and const, type aliases are block-scoped. Every block and every function has its own scope, and inner type alias declarations shadow outer ones:

▪ Type aliases are useful for DRYing up repeated complex types,4 and for making it clear what a variable is used for (some people prefer descriptive type names to descriptive variable names!).

▪ TypeScript gives us special type operators to describe unions and intersections of types: | for union and & for intersection.

▪ Like in JavaScript, TypeScript arrays are special kinds of objects that support things like concatenation, pushing, searching, and slicing

▪ TypeScript supports two syntaxes for arrays: T[] and Array

▪ They are identical both in meaning and in performance. This book uses T[] syntax for its terseness, but you should pick whichever style you like for your own code.

▪ The general rule of thumb is to keep arrays homogeneous. That is, don’t mix apples and oranges and numbers in a single array—try to design your programs so that every element of your array has the same type. The reason is that otherwise, you’re going to have to do more work to prove to TypeScript that what you’re doing is safe.

▪ when you initialize an empty array, TypeScript doesn’t know what type the array’s elements should be, so it gives you the benefit of the doubt and makes them any

▪ As you manipulate the array and add elements to it, TypeScript starts to piece together your array’s type. Once your array leaves the scope it was defined in (for example, if you declared it in a function, then returned it), TypeScript will assign it a final type that can’t be expanded anymore:

▪ Tuples are subtypes of array. They’re a special way to type arrays that have fixed lengths, where the values at each index have specific, known types

▪ Unlike most other types, tuples have to be explicitly typed when you declare them. That’s because the JavaScript syntax is the same for tuples and arrays (both use square brackets), and TypeScript already has rules for inferring array types from square brackets:

▪ Tuples support optional elements too. Just like in object types, ? means “optional”:

▪ Tuples also support rest elements, which you can use to type tuples with minimum lengths:

// A list of strings with at least 1 element
let friends: [string, ...string[]] = ['Sara', 'Tali', 'Chloe', 'Claire']

▪ Not only do tuple types safely encode heterogeneous lists, but they also capture the length of the list they type

▪ TypeScript comes with a readonly array type out of the box, which you can use to create immutable arrays. Read-only arrays are just like regular arrays, but you can’t update them in place

▪ To create a read-only array, use an explicit type annotation; to update a read-only array, use nonmutating methods like .concat and .slice instead of mutating ones like .push and .splice:

▪ let as: readonly number[] = [1, 2, 3] // readonly number[]

▪ Like Array, TypeScript comes with a couple of longer-form ways to declare read-only arrays and tuples:

▪ Which syntax you use—the terser readonly modifier, or the longer-form Readonly or ReadonlyArray utilities—is a matter of taste

▪ If you plan to make heavy use of immutable arrays, consider reaching for a more efficient implementation, like Lee Byron’s excellent immutable.

▪ JavaScript has two values to represent an absence of something: null and undefined. TypeScript supports both of these as values, and it also has types for them—any guess what they’re called? You got it, the types are called null and undefined too.

▪ They’re both special types, because in TypeScript the only thing of type undefined is the value undefined, and the only thing of type null is the value null.

▪ JavaScript programmers usually use the two interchangeably, though there is a subtle semantic difference worth mentioning: undefined means that something hasn’t been defined yet, and null means an absence of a value (like if you tried to compute a value, but ran into an error along the way). These are just conventions and TypeScript doesn’t hold you to them, but it can be a useful distinction to make.

▪ void is the return type of a function that doesn’t explicitly return anything (for example, console.log),

▪ never is the type of a function that never returns at all (like a function that throws an exception, or one that runs forever):

▪ returns undefined, but it doesn’t do so with an explicit return statement, so we say it returns void

▪ null has been called the “billion dollar mistake” by the guy that introduced it in the 1960s.

▪ The problem with null is it’s something that most languages’ type systems can’t express and don’t check for; so when a programmer tries to do something with a variable that they thought was defined but it actually turns out to be null at runtime, the code throws a runtime exception!

▪ But languages are coming around to encoding null in their type systems, and TypeScript is a great example of how to do it right. If the goal is to catch as many bugs as possible at compile time before your users encounter them, then being able to check for null in the type system is indispensable.

▪ There are two kinds of enums: enums that map from strings to strings, and enums that map from strings to numbers.

▪ enum Language {
English,
Spanish,
Russian
}

▪ By convention, enum names are uppercase and singular. Their keys are also uppercase.

▪ TypeScript will automatically infer a number as the value for each member of your enum, but you can also set values explicitly

▪ To retrieve a value from an enum, you access it with either dot or bracket notation—just like you would to get a value from a regular object:

▪ let myFirstLanguage = Language.Russian // Language
let mySecondLanguage = Language['English'] // Language

▪ Beware that when you do split your enum, TypeScript can only infer values for one of those declarations, so it’s good practice to explicitly assign a value to each enum member:

enum Language {
English = 0,
Spanish = 1
}

enum Language {
Russian = 2
}

▪ You can use computed values, and you don’t have to define all of them (TypeScript will do its best to infer what’s missing):

enum Language {
English = 100,
Spanish = 200 + 300,
Russian // TypeScript infers 501 (the next number after 500)
}

▪ TypeScript lets you access enums both by value and by key for convenience, but this can get unsafe quickly:

▪ You shouldn’t be able to get Color[6], but TypeScript doesn’t stop you! We can ask TypeScript to prevent this kind of unsafe access by opting into a safer subset of enum behavior with const enum
instead.

▪ const enum Language {
English,
Spanish,
Russian
}

▪ A const enum
doesn’t let you do reverse lookups, and so behaves a lot like a regular JavaScript object

▪ It also doesn’t generate any JavaScript code by default, and instead inlines the enum member’s value wherever it’s used (for example, TypeScript will replace every occurrence of Language.Spanish with its value, 1).

▪ All it takes is one pesky numeric value in your enum to make the whole enum unsafe.

▪ Because of all the pitfalls that come with using enums safely, I recommend you stay away from them—there are plenty of better ways to express yourself in TypeScript.

▪ And if a coworker insists on using enums and there’s nothing you can do to change their mind, be sure to ninja-merge a few TSLint rules while they’re out to warn about numeric values and non-const enums.

▪ const will infer more specific types, let and var more general ones.

▪ Most types have general and more specific counterparts, the latter subtypes of the former (see Table 3-3).

▪ When unknown is part of a union type, the result of the union will be unknown. You’ll read more about union types in “Union and intersection types”.

▪ Objects in JavaScript use strings for keys; arrays are special kinds of objects that use numerical keys.

▪ There’s one minor technical difference: {} lets you define whatever types you want for built-in methods on the Object prototype, like .toString and .hasOwnProperty (head over to MDN to learn more about prototypes), while Object enforces that the types you declare are assignable to those on Object’s prototype.

▪ The acronym DRY stands for “Don’t Repeat Yourself”—the idea that code shouldn’t be repetitive. It was introduced by Andrew Hunt and David Thomas in their book The Pragmatic Programmer: From Journeyman to Master (Addison-Wesley).

▪ The way to think about a bottom type is as a type that has no values. A bottom type corresponds to a mathematical proposition that’s always false.

▪ You are now ready for TypeScript’s pièce de résistance (or raison d’être, if you’re a functional programmer): functions.

▪ In JavaScript, functions are first-class objects. That means you can use them exactly like you would any other object: assign them to variables, pass them to other functions, return them from functions, assign them to objects and prototypes, write properties to them, read those properties back, and so on. There is a lot you can do with functions in JavaScript, and TypeScript models all of those things with its rich type system.

▪ The return type is inferred, but you can explicitly annotate it too if you want:

▪ The last example used named function syntax to declare the function, but JavaScript and TypeScript support at least five ways to do this:

▪ Besides function constructors (which you shouldn’t use unless you are being chased by bees because they are totally unsafe),1 all of these syntaxes are supported by TypeScript in a typesafe way, and they all follow the same rules around usually mandatory type annotations for parameters and optional annotations for return types.

▪ A parameter is a piece of data that a function needs to run, declared as part of a function declaration. Also called a formal parameter.

▪ An argument is a piece of data that you passed to a function when invoking it. Also called an actual parameter.

▪ Like in object and tuple types, you can use ? to mark parameters as optional

▪ When declaring your function’s parameters, required parameters have to come first, followed by optional parameters:

▪ Like in JavaScript, you can provide default values for optional parameters. Semantically it’s similar to making a parameter optional, in that callers no longer have to pass it in (a difference is that default parameters don’t have to be at the end of your list of parameters, while optional parameters do).

▪ Notice how when we give userId a default value, we remove its optional annotation, ?.

▪ You’ll find yourself using default parameters over optional parameters often.

▪ Sometimes, you might opt for a variadic function API—one that takes a variable number of arguments—instead of a fixed-arity API that takes a fixed number of arguments. Traditionally, that required using JavaScript’s magic arguments object.

▪ Because arguments is only array-like, and not a true array, you first have to convert it to an array before you can call the built-in .reduce on it:

▪ Rest parameters to the rescue! Instead of resorting to the unsafe arguments magic variable, we can instead use rest parameters to safely make our sum function accept any number of arguments

▪ In addition to invoking a function with parentheses (), JavaScript supports at least two other ways to call a function.

▪ add(10, 20) // evaluates to 30

▪ add.apply(null, [10, 20]) // evaluates to 30

▪ add.call(null, 10, 20) // evaluates to 30

▪ add.bind(null, 10, 20)() // evaluates to 30

▪ apply binds a value to this within your function (in this example, we bind this to null), and spreads its second argument over your function’s parameters

▪ call does the same, but applies its arguments in order instead of spreading.

▪ this-argument and a list of arguments to your function. The difference is that bind does not invoke your function; instead, it returns a new function that you can then invoke with (),

▪ To safely use .call, .apply, and .bind in your code, be sure to enable the strictBindCallApply option in your tsconfig.json (it’s automatically enabled if you already enabled strict mode).

▪ If you’re not coming from JavaScript, you may be surprised to learn that in JavaScript the this variable is defined for every function, not just for those functions that live as methods on classes

▪ this has a different value depending on how you called your function, which can make it notoriously fragile and hard to reason about.

▪ For this reason, a lot of teams ban this everywhere except in class methods—to do this for your codebase too, enable the no-invalid-this TSLint rule

▪ The general rule is that this will take the value of the thing to the left of the dot when invoking a method.

▪ let x = {
a() {
return this
}
}
x.a() // this is the object x in the body of a()

▪ But if at some point you reassign a before calling it, the result will change!

let a = x.a
a() // now, this is undefined in the body of a()

▪ Though exploring all of the semantics of this is beyond the scope of this book,2 this behavior—that this depends on the way you called a function, and not on the way that you declared it—can be surprising to say the least

▪ If your function uses this, be sure to declare your expected this type as your function’s first parameter (before any additional parameters), and TypeScript will enforce that this really is what you say it is at every call site. this isn’t treated like other parameters—it’s a reserved word when used as part of a function signature:


function fancyDate(this: Date) {

▪ fancyDate() // Error TS2684: The 'this' context of type 'void' is
// not assignable to method's 'this' of type 'Date'.

▪ We took a runtime error, and gave TypeScript enough information to warn about the error at compile time instead.

▪ To enforce that this types are always explicitly annotated in functions, enable the noImplicitThis setting in your tsconfig.json. strict mode includes noImplicitThis, so if you already have that enabled you’re good to go.

▪ Generator functions (generators for short) are a convenient way to, well, generate a bunch of values. They give the generator’s consumer fine control over the pace at which values are produced. Because they’re lazy—that is, they only compute the next value when a consumer asks for it—they can do things that can be hard to do otherwise, like generate infinite lists.

▪ The asterisk (*) before a function’s name makes that function a generator. Calling a generator returns an iterable iterator.

▪ We won’t delve deeper into generators in this book—they’re a big topic, and since this book is about TypeScript, I don’t want to get sidetracked with JavaScript features. The short of it is they’re a super cool JavaScript language feature that TypeScript supports too. To learn more about generators, head to their page on MDN.

▪ Iterators are the flip side to generators: while generators are a way to produce a stream of values, iterators are a way to consume those values. The terminology can get pretty confusing, so let’s start with a couple of definitions.

▪ Iterable

Any object that contains a property called Symbol.iterator, whose value is a function that returns an iterator.

▪ Iterator

Any object that defines a method called next, which returns an object with the properties value and done.

▪ When you create a generator (say, by calling createFibonacciGenerator), you get a value back that’s both an iterable and an iterator—an iterable iterator—because it defines both a Symbol.iterator property and a next method.

▪ You can manually define an iterator or an iterable by creating an object (or a class) that implements Symbol.iterator or next, respectively. For example, let’s define an iterator that returns the numbers 1 through 10:

▪ let numbers = {
*[Symbol.iterator]() {
for (let n = 1; n yield n
}
}
}

▪ The Function type, as you may have guessed, is not what you want to use most of the time. Like object describes all objects, Function is a catchall type for all functions, and doesn’t tell you anything about the specific function that it types.

▪ This is TypeScript’s syntax for a function’s type, or call signature (also called a type signature).

▪ You’ll notice it looks remarkably similar to an arrow function—this is intentional!

▪ Note

The parameter names a and b just serve as documentation, and don’t affect the assignability of a function with that type.

▪ Function call signatures only contain type-level code—that is, types only, no values. That means function call signatures can express parameter types, this types (see “Typing this”), return types, rest types, and optional types, and they cannot express default values (since a default value is a value, not a type).

▪ And because they have no body for TypeScript to infer from, call signatures require explicit return type annotations.

▪ People use the terms “type-level” and “value-level” a lot when talking about programming with static types, and it helps to have a common vocabulary.

Throughout this book, when I use the term type-level code, what I’m referring to is code that consists exclusively of types and type operators. Contrast that with value-level code, which is everything else.

▪ A rule of thumb is: if it’s valid JavaScript code, then it’s value-level; if it’s valid TypeScript but not valid JavaScript, then it’s type-level.4

▪ We declare a function expression log, and explicitly type it as type Log.

▪ We don’t need to annotate our parameters twice. Since message is already annotated as a string as part of the definition for Log, we don’t need to type it again here. Instead, we let TypeScript infer it for us from Log.

▪ Notice that the last example was the first example we’ve seen where we didn’t have to explicitly annotate our function parameter types. Because we already declared that log is of type Log, TypeScript is able to infer from context that message has to be of type string. This is a powerful feature of TypeScript’s type inference called contextual typing.

▪ TypeScript infers from context that n is a number—we declared that f’s argument index is a number in times’s signature, and TypeScript is smart enough to infer that n is that argument, so it must be a number.

Note that if we didn’t declare f inline, TypeScript wouldn’t have been able to infer its type:

▪ The function type syntax we used in the last section—type Fn = (...) => ...
—is a shorthand call signature. We can instead write it out more explicitly. Again taking the example of Log:

▪ // Shorthand call signature
type Log = (message: string, userId?: string) => void

▪ // Full call signature
type Log = {
(message: string, userId?: string): void
}

▪ The two are completely equivalent in every way, and differ only in syntax.

▪ But first, what does it even mean to overload a function?

▪ In most programming languages, once you declare a function that takes some set of parameters and yields some return type, you can call that function with exactly that set of parameters, and you will always get that same return type back. Not so in JavaScript. Because JavaScript is such a dynamic language, it’s a common pattern for there to be multiple ways to call a given function; not only that, but sometimes the output type will actually depend on the input type for an argument!

▪ TypeScript models this dynamism—overloaded function declarations, and a function’s output type depending on its input type—with its static type system. We might take this language feature for granted, but it’s a really advanced feature for a type system to have!

▪ You can use overloaded function signatures to design really expressive APIs. For example, let’s design an API to book a vacation—we’ll call it Reserve. Let’s start by sketching out its types (with a full type signature this time):

type Reserve = {
(from: Date, to: Date, destination: string): Reservation
}

▪ We might repurpose our API to support one-way trips too:

type Reserve = {
(from: Date, to: Date, destination: string): Reservation
(from: Date, destination: string): Reservation
}

▪ This is because of the way call signature overloading works in TypeScript. If you declare a set of overload signatures for a function f, from a caller’s point of view f’s type is the union of those overload signatures.

▪ Since reserve might be called in either of two ways, when you implement reserve you have to prove to TypeScript that you checked how it was called:6

▪ Overloaded call signatures are a natural way to model how createElement works. Think about how you might type createElement (try to answer this by yourself before you read on!).

The answer:

type CreateElement = {
(tag: 'a'): HTMLAnchorElement ￼
(tag: 'canvas'): HTMLCanvasElement
(tag: 'table'): HTMLTableElement
(tag: string): HTMLElement ￼
}

▪ We overload on the parameter’s type, matching on it with string literal types.

▪ We add a catchall case: if the user passed a custom tag name, or a cutting-edge experimental tag name that hasn’t made its way into TypeScript’s built-in type declarations yet, we return a generic HTMLElement

▪ Since TypeScript resolves overloads in the order they were declared,7 when you call createElement with a string that doesn’t have a specific overload defined (e.g., createElement('foo')), TypeScript will fall back to HTMLElement.

▪ But what if we want to overload a function declaration? As always, TypeScript has your back, with an equivalent syntax for function declarations. Let’s rewrite our createElement overloads:

function createElement(tag: 'a'): HTMLAnchorElement
function createElement(tag: 'canvas'): HTMLCanvasElement
function createElement(tag: 'table'): HTMLTableElement
function createElement(tag: string): HTMLElement {
// ...
}

▪ Full type signatures aren’t limited to overloading how you call a function. You can also use them to model properties on functions.

▪ Since JavaScript functions are just callable objects, you can assign properties to them to do things like:

function warnUser(warning) {
if (warnUser.wasCalled) {
return
}
warnUser.wasCalled = true
alert(warning)
}
warnUser.wasCalled = false

▪ That is, we show the user a warning, and we don’t show a warning more than once. Let’s use TypeScript to type warnUser’s full signature:

type WarnUser = {
(warning: string): void
wasCalled: boolean
}

▪ let warnUser: WarnUser = (warning: string) => {
if (warnUser.wasCalled) {
return
}
warnUser.wasCalled = true
alert(warning)
}
warnUser.wasCalled = false

▪ Concrete types are useful when you know precisely what type you’re expecting, and want to verify that type was actually passed. But sometimes, you don’t know what type to expect beforehand, and you don’t want to restrict your function’s behavior to a specific type!

▪ Generic type parameter

A placeholder type used to enforce a type-level constraint in multiple places. Also known as polymorphic type parameter.

▪ What we’ve done here is say: “This function filter uses a generic type parameter T; we don’t know what this type will be ahead of time, so TypeScript if you can infer what it is each time we call filter that would be swell.” TypeScript infers T from the type we pass in for array. Once TypeScript infers what T is for a given call to filter, it substitutes that type in for every T it sees. T is like a placeholder type, to be filled in by the typechecker from context;

▪ it parameterizes Filter’s type, which is why we call it a generic type parameter.

▪ Because it’s such a mouthful to say “generic type parameter” every time, people often shorten it to just “generic type,” or simply “generic.” I’ll use the terms interchangeably throughout this book.

▪ where you place the angle brackets scopes the generics (there are just a few places you can put them)

▪ TypeScript makes sure that within their scope, all instances of the generic type parameters are eventually bound to the same concrete types.

▪ Because of where the angle brackets are in this example, TypeScript will bind concrete types to our generic T when we call filter. And it will decide which concrete type to bind to T depending on what we called filter with. You can declare as many comma-separated generic type parameters as you want between a pair of angle brackets.

▪ T is just a type name, and we could have used any other name instead: A, Zebra, or l33t. By convention, people use uppercase single-letter names starting with the letter T and continuing to U, V, W, and so on depending on how many generics they need.

▪ If you’re declaring a lot of generics in a row or are using them in a complicated way, consider deviating from this convention and using more descriptive names like Value or WidgetType instead.

▪ Some people prefer to start at A instead of T. Different programming language communities prefer one or the other, depending on their heritage: functional language users prefer A, B, C, and so on because of their likeness to the Greek letters α, β, and γ that you might find in math proofs; object-oriented language users tend to use T for “Type.” TypeScript, though it supports both programming styles, uses the latter convention.

▪ Like a function’s parameter gets re-bound every time you call that function, so each call to filter gets its own binding for T:

type Filter = {
(array: T[], f: (item: T) => boolean): T[]
}

▪ The way to think about generics is as constraints. Just like annotating a function parameter as n: number
constrains the value of the parameter n to the type number, so using a generic T constrains the type of whatever type you bind to T to be the same type everywhere that T shows up.

▪ Generic types can also be used in type aliases, classes, and interfaces—we’ll use them copiously throughout this book. I’ll introduce them in context as we cover more topics.

▪ Use generics whenever you can. They will help keep your code general, reusable, and terse.

▪ The place where you declare a generic type doesn’t just scope the type, but also dictates when TypeScript will bind a concrete type to your generic.

▪ Because we declared as part of a call signature (right before the signature’s opening parenthesis, (), TypeScript will bind a concrete type to T when we actually call a function of type Filter.

▪ If we’d instead scoped T to the type alias Filter, TypeScript would have required us to bind a type explicitly when we used Filter:

▪ type Filter = {
(array: T[], f: (item: T) => boolean): T[]
}

let filter: Filter = (array, f) => // Error TS2314: Generic type 'Filter'
// ... // requires 1 type argument(s).

▪ Generally, TypeScript will bind concrete types to your generic when you use the generic: for functions, it’s when you call them; for classes, it’s when you instantiate them (more on that in “Polymorphism”); and for type aliases and interfaces (see “Interfaces”), it’s when you use or implement them.

▪ For each of TypeScript’s ways to declare a call signature, there’s a way to add a generic type to it:

▪ type Filter = { ￼
(array: T[], f: (item: T) => boolean): T[]
}
let filter: Filter = // ...

▪ type Filter = { ￼
(array: T[], f: (item: T) => boolean): T[]
}

▪ filter and map in the Standard Library

▪ filter uses the generic T that’s scoped to the entire Array interface. map uses T too, and adds a second generic U that’s scoped just to the map function

▪ That means TypeScript will bind a concrete type to T when you create an array, and every call to filter and map on that array will share that concrete type

▪ In most cases, TypeScript does a great job of inferring generic types for you. When you call the map function we wrote earlier, TypeScript infers that T is string and U is boolean:

▪ You can, however, explicitly annotate your generics too. Explicit annotations for generics are all-or-nothing; either annotate every required generic type, or none of them

▪ To fix this, we have to explicitly annotate Promises generic type parameter:

let promise = new Promise(resolve =>
resolve(45)
)
promise.then(result => // number
result * 4
)

▪ Note that this is the only valid place to declare a generic type in a type alias: right after the type alias’s name, before its assignment (=).

▪ You can use MyEvent to build another type—say, TimedEvent. When the generic T in TimedEvent is bound, TypeScript will also bind it to MyEvent:

type TimedEvent = {
event: MyEvent
from: Date
to: Date
}

▪ T has an upper bound of TreeNode. That is, T can be either a TreeNode, or a subtype of TreeNode

▪ If we had typed T as just T (leaving off extends TreeNode
), then mapNode would have thrown a compile-time error, because you can’t safely read node.value on an unbounded node of type T (what if a user passes in a number?).

▪ As a convenience for when we don’t know the specific element type that MyEvent will be bound to beforehand, we can add a default for MyEvent’s generic:


type MyEvent = {
target: T
type: string
}

▪ We can also use this opportunity to apply what we learned in the last few sections and add a bound to T, to make sure that T is an HTML element:


type MyEvent = {
target: T
type: string
}

▪ Note that like optional parameters in functions, generic types with defaults have to appear after generic types without defaults:

▪ Type-Driven Development

▪ When you write in TypeScript, you will often find yourself “leading with the types.” This, of course, refers to type-driven development.

▪ A style of programming where you sketch out type signatures first, and fill in values later.

▪ When you write a TypeScript program, start by defining your functions’ type signatures—in other words, lead with the types—filling in the implementations later

▪ By sketching out your program out at the type level first, you make sure that everything makes sense at a high level before you get down to your implementations.

▪ If you enter that last example into your code editor, you’ll see that its type is Function. What is this Function type? It’s an object that is callable (you know, by putting () after it) and has all the prototype methods from Function.prototype. But its parameters and return type are untyped, so you can call the function with any arguments you want, and TypeScript will stand idly by, watching you do something that by all means should be illegal in whatever town you live in.

▪ For a deep dive into this, check out Kyle Simpson’s You Don’t Know JS series from O’Reilly.

▪ The exceptions to this rule of thumb are enums and namespaces. Enums generate both a type and a value, and namespaces exist just at the value level.

▪ Mostly—TypeScript hoists literal overloads above nonliteral ones, before resolving them in order. You might not want to depend on this feature, though, since it can make your overloads hard to understand for other engineers who aren’t familiar with this behavior.

▪ If you’re like most programmers coming from an object-oriented programming language, classes are your bread and butter. Classes are how you organize and think about your code, and they serve as your primary unit of encapsulation

▪ You’ll be pleased to learn that TypeScript classes borrow heavily from C#, and support things like visibility modifiers, property initializers, polymorphism, decorators, and interfaces. But because TypeScript classes compile down to regular JavaScript classes, you can also express JavaScript idioms like mixins in a typesafe way.

▪ Some of TypeScript’s class features, like property initializers and decorators, are supported by JavaScript classes too,1 and so generate runtime code. Other features, like visibility modifiers, interfaces, and generics, are TypeScript-only features that just exist at compile time, and don’t generate any code when you compile your application to JavaScript.

▪ In this chapter I’ll guide you through an extended example of how we work with classes in TypeScript, so that you can gain some intuition not only for TypeScript’s object-oriented language features, but for how and why we use them

▪ Try to follow along, entering the code in your code editor as we go.

▪ We’re going to build a chess engine. Our engine will model a game of chess and provide an API for two players to take turns making moves

▪ There are six types of pieces:

// ...
class King extends Piece {}
class Queen extends Piece {}
class Bishop extends Piece {}
class Knight extends Piece {}
class Rook extends Piece {}
class Pawn extends Piece {}

▪ Standard algebraic notation in chess: A–H (the x-axis) are called “files” and 1–8 (the inverted y-axis) “ranks”

▪ class Position {
constructor(
private file: File, ￼
private rank: Rank
) {}
}

▪ Since there are relatively few colors, ranks, and files, we can manually enumerate their possible values as type literals. This will let us squeeze out some extra safety by constraining these types’ domains from all strings and all numbers to a handful of very specific strings and numbers.

▪ The private access modifier in the constructor automatically assigns the parameter to this (this.file and so on), and sets its visibility to private, meaning that code within a Piece instance can read and write to it, but code outside of a Piece instance can’t.

▪ Different instances of Piece can access each other’s private members; instances of any other class—even a subclass of Piece—can’t.

▪ We declare the instance variable position as protected. Like private, protected assigns the property to this, but unlike private, protected makes the property visible both to instances of Piece and to instances of any subclass of Piece

▪ We didn’t assign position a value when declaring it, so we have to assign a value to it in Piece’s constructor function. If we hadn’t assigned it a value in the constructor, TypeScript would have told us that the variable is not definitely assigned, i.e., we said it’s of type T, but it’s actually T | undefined
because it’s not assigned a value in a property initializer or in the constructor—so we would need to update its signature to indicate that it’s not necessarily a Position, but it might also be undefined

▪ TypeScript supports three access modifiers for properties and methods on a class:

▪ public

Accessible from anywhere. This is the default access level.

▪ protected

Accessible from instances of this class and its subclasses.

▪ private

Accessible from instances of this class only.

▪ Using access modifiers, you can design classes that don’t expose too much information about their implementations, and instead expose well-defined APIs for others to use.

▪ abstract class Piece {
constructor(
// ...

▪ The abstract keyword means that you can’t instantiate the class directly

▪ Our Piece class now:

Tells its subclasses that they have to implement a method called canMoveTo that is compatible with the given signature

▪ Declare classes with the class keyword. Extend them with the extends keyword.

▪ Classes can be either concrete or abstract. Abstract classes can have abstract methods and abstract properties.

▪ Methods can be private, protected, or, by default, public. They can be instance methods or static methods.

▪ Classes can have instance properties, which can also be private, protected, or, by default, public. You can declare them in constructor parameters or as property initializers.

▪ You can mark instance properties as readonly when declaring them.

▪ Like JavaScript, TypeScript supports super calls

▪ If your child class overrides a method defined on its parent class (say, if Queen and Piece both implement the take method), the child instance can make a super call to call its parent’s version of the method (e.g., super.take

▪ There are two kinds of super calls:

▪ Method calls, like super.take.

▪ Constructor calls, which have the special form super() and can only be called from a constructor function.

▪ If your child class has a constructor function, you must call super() from the child’s constructor to correctly wire up the class (don’t worry, TypeScript will warn you if you forget; it’s like a cool futuristic robot elephant in that way).

▪ Note that you can only access a parent class’s methods, and not its properties, with super.

▪ Instead, you can use this as a return type annotation to let TypeScript do the work for you:


class Set {
has(value: number): boolean {
// ...
}
add(value: number): this {
// ...
}
}

▪ This is a really convenient feature for working with chained APIs, like we do in “Builder Pattern”.

▪ When you use classes, you will often find yourself using them with interfaces.

▪ Like type aliases, interfaces are a way to name a type so you don’t have to define it inline

▪ Type aliases and interfaces are mostly two syntaxes for the same thing (like function expressions and function declarations), but there are a few small differences.

▪ Everywhere you used your Sushi type alias, you can also use your Sushi interface. Both declarations define shapes, and those shapes are assignable to one another (in fact, they’re identical!).

▪ Interfaces don’t have to extend other interfaces. In fact, an interface can extend any shape: an object type, a class, or another interface.

▪ What are the differences between types and interfaces? There are three, and they’re subtle

▪ The first is that type aliases are more general, in that their righthand side can be any type, including a type expression (a type, and maybe some type operators like & or |); for an interface, the righthand side must be a shape

▪ The second difference is that when you extend an interface, TypeScript will make sure that the interface you’re extending is assignable to your extension. For example:

interface A {
good(x: number): string
bad(x: number): string
}

interface B extends A {
good(x: string | number): string
bad(x: string): string // Error TS2430: Interface 'B' incorrectly extends
} // interface 'A'. Type 'number' is not assignable
// to type 'string'.

▪ This is not the case when you use intersection types: if you turn the interfaces from the last example into type aliases and the extends into an intersection (&), TypeScript will do its best to combine your extension with the type it’s extending, resulting in an overloaded signature for bad instead of a compile-time error (try it in your code editor!).

▪ When you’re modeling inheritance for object types, the assignability check that TypeScript does for interfaces can be a helpful tool to catch errors.

▪ The third difference is that multiple interfaces with the same name in the same scope are automatically merged; multiple type aliases with the same name in the same scope will throw a compile-time error. This is a feature called declaration merging.

▪ Declaration merging is TypeScript’s way of automatically combining multiple declarations that share the same name. It came up when we introduced enums (“Enums”), and it also comes up when working with other features like namespace declarations (see “Namespaces”).

▪ For example, if you declare two identically named User interfaces, then TypeScript will automatically combine them for you into a single interface:

// User has a single field, name
interface User {
name: string
}

// User now has two fields, name and age
interface User {
age: number
}

let a: User = {
name: 'Ashley',
age: 30
}

▪ Note that the two interfaces can’t conflict; if one types property as a T and the other types it as a U, and T and U aren’t identical, then you’ll get an error:

interface User {
age: string
}

interface User {
age: number

▪ And if your interface declares generics (skip ahead to “Polymorphism” to learn more), those generics have to be declared the exact same way for two interfaces to be mergeable—down to the generic’s name!

▪ When you declare a class, you can use the implements keyword to say that it satisfies a particular interface.

▪ Like other explicit type annotations, this is a convenient way to add a type-level constraint that your class is implemented correctly as closely as possible to the implementation itself, so that the error from an incorrect implementation doesn’t show up downstream where it’s less clear why it was thrown.

▪ It’s also a familiar way to implement common design patterns like adapters, factories, and strategies (see the end of this chapter for some examples).

▪ interface Animal {
eat(food: string): void
sleep(hours: number): void
}

class Cat implements Animal {
eat(food: string) {
console.info('Ate some', food, '. Mmm!')
}
sleep(hours: number) {
console.info('Slept for', hours, 'hours')
}
}

Cat has to implement every method that Animal declares, and can implement more methods and properties on top if it wants.

▪ Interfaces can declare instance properties, but they can’t declare visibility modifiers (private, protected, and public) and they can’t use the static keyword.

▪ You can also mark instance properties as readonly, just like we did for object types in Objects (in Chapter 3):

▪ You’re not limited to implementing just one interface—you can implement as many as you want:

▪ class Cat implements Animal, Feline {

▪ Implementing Interfaces Versus Extending Abstract Classes

▪ Implementing an interface is really similar to extending an abstract class. The difference is that interfaces are more general and lightweight, and abstract classes are more special-purpose and feature-rich.

▪ An interface is a way to model a shape. At the value level, that means an object, array, function, class, or class instance

▪ Interfaces do not emit JavaScript code, and only exist at compile time.

▪ An abstract class can only model, well, a class.

▪ It emits runtime code that is, you guessed it, a JavaScript class.

▪ Abstract classes can have constructors, provide default implementations, and set access modifiers for properties and methods. Interfaces can’t do any of those things.

▪ Which one you use depends on your use case. When an implementation is shared among multiple classes, use an abstract class. When you need a lightweight way to say “this class is a T,” use an interface.

▪ Like every other type in TypeScript, TypeScript compares classes by their structure, not by their name. A class is compatible with any other type that shares its shape, including a regular old object that defines the same properties or methods as the class. This is important to keep in mind for those of you coming from C#, Java, Scala, and most other languages where classes are typed nominally. It means that if you have a function that takes a Zebra and you give it a Poodle, TypeScript might not mind:

class Zebra {
trot() {
// ...
}
}

class Poodle {
trot() {
// ...
}
}

▪ function ambleAround(animal: Zebra) {
animal.trot()
}

let zebra = new Zebra
let poodle = new Poodle

ambleAround(zebra) // OK
ambleAround(poodle) // OK

▪ As the phylogeneticists among you know, a zebra is no poodle—but TypeScript doesn’t mind! As long as Poodle is assignable to Zebra, TypeScript is OK with it because from our function’s point of view, the two are interchangeable; all that matters is that they implement .trot

▪ If you were using almost any other language that types classes nominally, this code would have raised an error; but TypeScript is structurally typed through and through, so this code is perfectly acceptable.

▪ The exception to this rule is classes with private or protected fields: when checking whether or not a shape is assignable to a class, if the class has any private or protected fields and the shape is not an instance of that class or a subclass of that class, then the shape is not assignable to the class:

▪ Classes Declare Both Values and Types

▪ Most things that you can express in TypeScript are either values or types:

▪ This contextual term resolution is really nice, and lets us do cool things like implement companion types (see “Companion Object Pattern”).

▪ Classes and enums are special. They are unique because they generate both a type in the type namespace and a value in the value namespace:

▪ When we work with classes, we need a way to say “this variable should be an instance of this class” and the same goes for enums (“this variable should be a member of this enum”). Because classes and enums generate types at the type level we’re able to express this “is-a” relationship easily.2

▪ We also need a way to represent a class at runtime, so that we can instantiate it with new, call static methods on it, do metaprogramming with it, and operate on it with instanceof—so a class needs to generate a value too.

▪ We use the typeof keyword (a type operator provided by TypeScript, which is like JavaScript’s value-level typeof but for types).

▪ That new() bit is called a constructor signature, and is TypeScript’s way of saying that a given type can be instantiated with the new operator.

▪ Because TypeScript is structurally typed, that’s the best we can do to describe what a class is: a class is anything that can be new-ed.

▪ interface StringDatabaseConstructor {
new(state?: State): StringDatabase
from(state: State): StringDatabase
}

▪ So, not only does a class declaration generate terms at the value and type levels, but it generates two terms at the type level: one representing an instance of the class; one representing the class constructor itself (reachable with the typeof type operator).

▪ Like functions and types, classes and interfaces have rich support for generic type parameters, including defaults and bounds. You can scope a generic to your whole class or interface, or to a specific method:

▪ Note that you cannot declare generic types in a constructor. Instead, move the declaration up to your class declaration.

▪ Static methods do not have access to their class’s generics

▪ You can bind generics to interfaces too:

▪ And like with functions, you can bind concrete types to generics explicitly, or let TypeScript infer the types for you:

▪ JavaScript and TypeScript don’t have trait or mixin keywords, but it’s straightforward to implement them ourselves

▪ Both are ways to simulate multiple inheritance (classes that extend more than one other class)

▪ and do role-oriented programming, a style of programming where you don’t say things like “this thing is a Shape" but instead describe properties of a thing, like “it can be measured” or “it has four sides.” Instead of “is-a” relationships, you describe “can” and “has-a” relationships.

▪ Mixins are a pattern that allows us to mix behaviors and properties into a class.

▪ By convention, mixins:

Can have state (i.e., instance properties)

Can only provide concrete methods (not abstract ones)

Can have constructors, which are called in the same order as their classes were mixed in

▪ TypeScript doesn’t have a built-in concept of mixins, but it’s easy to implement them ourselves

▪ For example, let’s design a debugging library for TypeScript classes. We’ll call it EZDebug. The library works by letting you log out information about whatever classes use the library, so that you can inspect them at runtime.

▪ We’ll model it with a mixin, which we’ll call withEZDebug. A mixin is just a function that takes a class constructor and returns a class constructor, so our mixin might look like this:

type ClassConstructor = new(...args: any[]) => {} ￼

▪ function withEZDebug(Class: C) {

▪ We start by declaring a type ClassConstructor, which represents any constructor

▪ Since TypeScript is completely structurally typed, we say that a constructor is anything that can be new-ed

▪ We don’t know what types of parameters the constructor might have, so we say it takes any number of arguments of any type.

▪ We let TypeScript infer withEZDebug’s return type, which is the intersection of C and our new anonymous class.

▪ Since a mixin is a function that takes a constructor and returns a constructor, we return an anonymous class constructor.

▪ Finally, since this anonymous class extends another class, to wire everything up correctly we need to remember to call Class’s constructor too.

▪ type ClassConstructor = new(...args: any[]) => {}

▪ function withEZDebug(Class: C) {
return class extends Class {
debug() {
let Name = Class.constructor.name
let value = this.getDebugValue()
return Name + '(' + JSON.stringify(value) + ')'
}
}
}

▪ The answer is that instead of accepting any old class, we use a generic type to make sure the class passed into withEZDebug defines a .getDebugValue method:

▪ function withEZDebug getDebugValue(): object ￼
}>>(Class: C) {
// ...
}

▪ let User = withEZDebug(HardToDebugUser)
let user = new User(3, 'Emma', 'Gluzman')
user.debug() // evaluates to 'User({"id": 3, "name": "Emma Gluzman"})'

▪ Cool, right? You can apply as many mixins to a class as you want to yield a class with richer and richer behavior, all in a typesafe way. Mixins help encapsulate behavior, and are an expressive way to specify reusable behaviors.4

▪ Decorators are an experimental TypeScript feature that gives us a clean syntax for metaprogramming with classes, class methods, properties, and method parameters. They’re just a syntax for calling a function on the thing you’re decorating.

▪ Because they’re still experimental—meaning they may change in a backward-incompatible way, or may even be entirely removed in future TypeScript releases—decorators are hidden behind a TSC flag. If you’re OK with that, and want to play around with the feature, set "experimentalDecorators": true
in your tsconfig.json and read on.

▪ To get a sense for how decorators work, let’s start with an example:

@serializable
class APIPayload {
getValue(): Payload {
// ...
}
}

▪ The @serializable class decorator wraps our APIPayload class, and optionally returns a new class that replaces it

▪ Without decorators, you might implement the same thing with:

let APIPayload = serializable(class APIPayload {
getValue(): Payload {
// ...
}
})

▪ For each type of decorator, TypeScript requires that you have a function in scope with the given name and the required signature for that type of decorator (see Table 5-1).

▪ TypeScript doesn’t come with any built-in decorators: whatever decorators you use, you have to implement yourself (or install from NPM). The implementation for each kind of decorator—for classes, methods, properties, and function parameters—is a regular function that satisfies a specific signature, depending on what it’s decorating.

▪ Remember, new() is how we structurally type a class constructor in TypeScript.

▪ And for a class constructor that can be extended (with extends), TypeScript requires that we type its arguments with an any spread: new(...any[]).

▪ @serializable can decorate any class whose instances implement the method .getValue, which returns a Payload.

▪ Class decorators are functions that take a single argument—the class

▪ TypeScript assumes that a decorator doesn’t change the shape of the thing it’s decorating—meaning that you didn’t add or remove methods and properties.

▪ It checks at compile time that the class you returned is assignable to the class you passed in, but at the time of writing, TypeScript does not keep track of extensions you make in your decorators.

▪ Though TypeScript doesn’t support the final keyword for classes or methods, it’s easy to simulate it for classes

▪ If you haven’t worked much with object-oriented languages before, final is the keyword some languages use to mark a class as nonextensible, or a method as nonoverridable.

▪ class MessageQueue {
private constructor(private messages: string[]) {}
}

When a constructor is marked private, you can’t new the class or extend it:

▪ As well as preventing you from extending the class—which is what we want—private constructors also prevent you from directly instantiating it

▪ But for final classes we do want the ability to instantiate a class, just not to extend it. How do we keep the first restriction but get rid of the second? Easy:


class MessageQueue {
private constructor(private messages: string[]) {}
static create(messages: string[]) {
return new MessageQueue(messages)
}
}

▪ MessageQueue.create([])

▪ type Shoe = {
purpose: string
}

class BalletFlat implements Shoe {
purpose = 'dancing'
}

class Boot implements Shoe {
purpose = 'woodcutting'
}

class Sneaker implements Shoe {
purpose = 'walking'
}

▪ Note that this example uses a type, but we could have just as well used an interface instead.

▪ Now, let’s make a shoe factory:

let Shoe = {
create(type: 'balletFlat' | 'boot' | 'sneaker'): Shoe { ￼
switch (type) { ￼
case 'balletFlat': return new BalletFlat
case 'boot': return new Boot
case 'sneaker': return new Sneaker
}
}
}

▪ Using a union type for type helps make .create as typesafe as possible, preventing consumers from passing in an invalid type at compile time.

▪ Switching on type makes it easy for TypeScript to enforce that we’ve handled every type of Shoe.

▪ Voilà! We have a factory pattern. Note that we could have gone further and indicated in Shoe.create’s type signature that passing in 'boot' will give a Boot, 'sneaker' will give a Sneaker, and so on, but that would break the abstraction that the factory pattern gives us (that the consumer shouldn’t know what concrete class they’ll get back, just that the class satisfies a particular interface).

▪ The builder pattern is a way to separate the construction of an object from the way that object is actually implemented

▪ If you’ve used JQuery, or ES6 data structures like Map and Set, this style of API should look familiar

▪ new RequestBuilder()
.setURL('/users')
.setMethod('get')
.setData({firstName: 'Anna'})
.send()

▪ We’ve now explored TypeScript classes from all sides: how to declare classes; how to inherit from classes and implement interfaces; how to mark classes as abstract so they can’t be instantiated; how to put a field or method on a class with static and on an instance without it; how to control access to a field or method with the private, protected, and public visibility modifiers; and how to mark a field as nonwritable using the readonly modifier

▪ We’ve covered how to safely use this and super, explored what it means for classes to be both values and types at the same time, and talked about the differences between type aliases and interfaces, the basics of declaration merging, and using generic types in classes.

▪ Finally, we covered a few more advanced patterns for working with classes: mixins, decorators, and simulating final classes

▪ And to cap the chapter off, we went through and derived a couple of common patterns for working with classes.

▪ Because TypeScript is structurally typed, of course, the relationship for classes is more of a “looks-like”—any object that implements the same shape as your class will be assignable to the type of your class.

▪ A handful of languages—Scala, PHP, Kotlin, and Rust, to name a few—implement a pared-down version of mixins, called traits. Traits are like mixins, but don’t have constructors and don’t support instance properties. This makes it easier to wire them up and prevent collisions between multiple traits accessing state that is shared between them and the base class.

▪ TypeScript has a world-class type system that supports powerful type-level programming features that might make even the crotchetiest Haskell programmer jealous

▪ We need such an expressive and unusual type system because JavaScript is so dynamic. Modeling things like prototypes, dynamically bound this, function overloads, and always-changing objects requires a rich type system and a utility belt of type operators that would make Batman do a double-take.

▪ If you have two types A and B, and B is a subtype of A, then you can safely use a B anywhere an A is required

▪ Array is a subtype of Object.

▪ Tuple is a subtype of Array.

▪ Everything is a subtype of any.

▪ never is a subtype of everything.

▪ If you have a class Bird that extends Animal, then Bird is a subtype of Animal.

▪ From the definition I just gave for subtype, that means:

Anywhere you need an Object you can also use an Array.

Anywhere you need an Array you can also use a Tuple.

Anywhere you need an any you can also use an Object.

You can use a never anywhere.

Anywhere you need an Animal you can also use a Bird.

▪ As you might have guessed, a supertype is the opposite of a subtype.

▪ Supertype

If you have two types A and B, and B is a supertype of A, then you can safely use an A anywhere a B is required

▪ This is just the opposite of how subtypes work, and nothing more.

▪ For simple types like number, string, and so on, you can just look them up in the flowchart in Figure 3-1

▪ Subtyping rules for types that contain other types (i.e., things with type parameters like Array, shapes with fields like {a: number}
, or functions like (a: A) => B
) are harder to reason about, and the answers aren’t as clear-cut. In fact, subtyping rules for these kinds of complex types are a big point of disagreement among programming languages—almost no two languages are alike!

▪ To make the following rules easier to read, I’m going to introduce a few pieces of syntax that let us talk about types a little more precisely and tersely

▪ This syntax is not valid TypeScript; it’s just a way for you and me to share a common language when we talk about types.

▪ You might represent it with a pair of types that look something like this:

// An existing user that we got from the server
type ExistingUser = {
id: number
name: string
}

// A new user that hasn't been saved to the server yet
type NewUser = {
name: string
}

▪ In general, TypeScript is not designed to be perfectly safe; instead, its type system tries to strike a balance between catching real mistakes and being easy to use, without you needing to get a degree in programming language theory to understand why something is an error.

▪ TypeScript’s behavior is as follows: if you expect a shape, you can also pass a type with property types that are 
▪ When talking about types, we say that TypeScript shapes (objects and classes) are covariant in their property types. That is, for an object A to be assignable to an object B, each of its properties must be 
▪ Invariance

You want exactly a T.

▪ Covariance

You want a 
▪ Contravariance

You want a >:T.

▪ Bivariance

You’re OK with either :T.

▪ In TypeScript, every complex type is covariant in its members—objects, classes, arrays, and function return types—with one exception: function parameter types, which are contravariant.

▪ Not all languages make this same design decision. In some languages objects are invariant in their property types, because as we saw, covariant property types can lead to unsafe behavior

▪ Some languages—like Scala, Kotlin, and Flow—even have explicit syntax for programmers to specify variance for their own data types.

▪ When designing TypeScript, its authors opted for a balance between ease of use and safety. When you make objects invariant in their property types, even though it’s safer, it can make a type system tedious to use

▪ A function A is a subtype of function B if A has the same or lower arity (number of parameters) than B and:

A’s this type either isn’t specified, or is >: B
’s this type.

Each of A’s parameters is >: its corresponding parameter in B.

A’s return type is ’s return type.

▪ We say that functions are covariant in their return types, which is a fancy way of saying that for a function to be a subtype of another function, its return type has to be 
▪ This means functions are contravariant in their parameter and this types. That is, for a function to be a subtype of another function, each of its parameters and its this type must be >: its corresponding parameter in the other function.

▪ For legacy reasons, functions in TypeScript are actually covariant in their parameter and this types by default. To opt into the safer, contravariant behavior we just explored, be sure to enable the {"strictFunctionTypes": true}
flag in your tsconfig.json.

▪ Subtype and supertype relations are core concepts in any statically typed language. They’re also important to understanding how assignability works (as a reminder, assignability refers to TypeScript’s rules for whether or not you can use a type A where another type B is required).

▪ When TypeScript wants to answer the question “Is type A assignable to type B?” it follows a few simple rules.

▪ A .

A is any.

▪ Type widening is key to understanding how TypeScript’s type inference works

▪ In general, TypeScript will be lenient when inferring your types, and will err on the side of inferring a more general type rather than the most specific type possible. This makes your life as a programmer easier, and means less time spent quelling the typechecker’s complaints.

▪ When you declare a variable in a way that allows it to be mutated later (e.g., with let or var), its type is widened from its literal value to the base type that literal belongs to:

▪ You can use an explicit type annotation to prevent your type from being widened:

▪ When you reassign a nonwidened type using let or var, TypeScript widens it for you. To tell TypeScript to keep it narrow, add an explicit type annotation to your original declaration:

▪ const a = 'x' // 'x'
let b = a // string

const c: 'x' = 'x' // 'x'
let d = c // 'x'

▪ Variables initialized to null or undefined are widened to any:

let a = null // any

▪ But when a variable initialized to null or undefined leaves the scope it was declared in, TypeScript assigns it a definite type:


function x() {
let a = null // any
a = 3 // any
a = 'b' // any
return a
}

x() // string

▪ TypeScript comes with a special const type that you can use to opt out of type widening a declaration at a time

▪ const opts your type out of widening and recursively marks its members as readonly, even for deeply nested data structures:

let d = [1, {x: 2}] // (number | {x: number})[]
let e = [1, {x: 2}] as const // readonly [1, {readonly x: 2}]

▪ Use as const
when you want TypeScript to infer your type as narrowly as possible.

▪ Object literal may only specify known properties,
// but 'tierr' does not exist in type 'Options'.
// Did you mean to write 'tier'?

This is a common bug when working with JavaScript, so it’s really helpful that TypeScript helps us catch it. But if object types are covariant in their members, how is it that TypeScript catches this?

▪ TypeScript was able to catch this due to its excess property checking, which works like this: when you try to assign a fresh object literal type T to another type U, and T has properties that aren’t present in U, TypeScript reports an error.

▪ A fresh object literal type is the type TypeScript infers from an object literal

▪ If that object literal either uses a type assertion (see “Type Assertions”) or is assigned to a variable, then the fresh object literal type is widened to a regular object type, and its freshness disappears.

▪ new API({ ￼
baseURL: 'https://api.mysite.com',
badTier: 'prod'
} as Options)

▪ Don’t worry—you don’t need to memorize these rules. They are TypeScript’s internal heuristics for catching the most bugs possible in a practical way, so as not to be a burden on you, the programmer.

▪ TypeScript performs flow-based type inference, which is a kind of symbolic execution where the typechecker uses control flow statements like if, ?, ||, and switch, as well as type queries like typeof, instanceof, and in, to refine types as it goes, just like a programmer reading through the code would.1 It’s an incredibly convenient feature for a typechecker to have, but is another one of those things that remarkably few languages support.2

▪ TypeScript is smart enough to know that doing a loose equality check against null will return true for both null and undefined in JavaScript. It knows that if this check passes then we will return, and if we didn’t return that means the check didn’t pass, so from then on width’s type is number | string
(it can’t be null or undefined anymore). We say that the type was refined from number | string | null | undefined
to number | string

▪ A typeof check queries a value at runtime to see what its type is. TypeScript takes advantage of typeof at compile time too: in the if branch where the check passes, TypeScript knows that width is a number; otherwise (since that branch returns) width must be a string—it’s the only type left.

▪ TypeScript does a superb job of taking what’s going through your mind as you read and write code, and crystallizing it in the form of typechecking and inference rules.

▪ Inside the if block, TypeScript knows that event.value has to be a string (because of the typeof check), which implies that after the if block event.value has to be a tuple of [number, number]
(because of the return in the if block).

▪ While the refinement worked for event.value, it didn’t carry over to event.target. Why?

▪ When handle takes a parameter of type UserEvent, that doesn’t mean we have to pass a UserTextEvent or UserMouseEvent—in fact, we could pass an argument of type UserMouseEvent | UserTextEvent
. And since members of a union might overlap, TypeScript needs a more reliable way to know when we’re in one case of a union type versus another case.

▪ The way to do this is to use a literal type to tag each case of your union type.

▪ A good tag is:

On the same place in each case of your union type. That means the same object field if it’s a union of object types, or the same index if it’s a union of tuple types. In practice, tagged unions usually use object types.

▪ Typed as a literal type (a literal string, number, boolean, etc.). You can mix and match different types of literals, but it’s good practice to stick to a single type; typically, that’s a string literal type.

▪ Not generic. Tags should not take any generic type arguments.

▪ Mutually exclusive (i.e., unique within the union type).

▪ type UserTextEvent = {type: 'TextEvent', value: string, target: HTMLInputElement}
type UserMouseEvent = {type: 'MouseEvent', value: [number, number],
target: HTMLElement}

type UserEvent = UserTextEvent | UserMouseEvent

function handle(event: UserEvent) {
if (event.type === 'TextEvent') {
event.value // string
event.target // HTMLInputElement
// ...
return
}
event.value // [number, number]
event.target // HTMLElement
}

▪ Now when we refine event based on the value of its tagged field (event.type), TypeScript knows that in the if branch event has to be a UserTextEvent, and after the if branch it has to be a UserMouseEvent. Since the tag is unique per union type, TypeScript knows that the two are mutually exclusive.

▪ Use tagged unions when writing a function that has to handle the different cases of a union type. For example, they’re invaluable when working with Flux actions, Redux reducers, or React’s useReducer.

▪ Totality

▪ A programmer puts two glasses on her bedside table before going to sleep: a full one, in case she gets thirsty, and an empty one, in case she doesn’t. 

Anonymous

▪ Totality, also called exhaustiveness checking, is what allows the typechecker to make sure you’ve covered all your cases. It comes to us from Haskell, OCaml, and other languages that are based around pattern matching.

▪ Error TS2366: Function lacks ending return statement and
return type does not include 'undefined'.

▪ To ask TypeScript to check that all of your functions’ code paths return a value (and throw the preceding warning if you missed a spot), enable the noImplicitReturns flag in your tsconfig.json

▪ Whether you enable this flag or not is up to you: some people prefer a code style with fewer explicit returns, and some people are fine with a few extra returns in the name of better type safety and more bugs caught by the typechecker.

▪ Maybe a client’s continued voicemails about that missed deadline have you jittery, and you forgot to handle numbers under 100 in your business-critical isBig function. Again, never fear—TypeScript is watching out for you:

Error TS7030: Not all code paths return a value

▪ Remember union (|) and intersection (&), the two type operators I introduced in “Union and intersection types”? It turns out they’re not the only type operators TypeScript gives you! Let’s run through a few more type operators that come in handy for working with shapes

▪ Instead, you can key in to your type:

▪ type FriendList = APIResponse['user']['friendList']

▪ You can key in to any shape (object, class constructor, or class instance), and any array.

▪ For example, to get the type of an individual friend:

type Friend = FriendList['friends'][number]

▪ number is a way to key in to an array type; for tuples, use 0, 1, or another number literal type to represent the index you want to key in to.

▪ The syntax for keying in is intentionally similar to how you look up fields in regular JavaScript objects—just as you might look up a value in an object, so you can look up a type in a shape

▪ Note that you have to use bracket notation, not dot notation, to look up property types when keying in.

▪ Use keyof to get all of an object’s keys as a union of string literal types

▪ type ResponseKeys = keyof APIResponse // 'user'

▪ type UserKeys = keyof APIResponse['user'] // 'userId' | 'friendList'

▪ In JavaScript, objects and arrays can have both string and symbol keys. And by convention, we usually use number keys for arrays, which are coerced to strings at runtime.

▪ This behavior is correct, but can make working with keyof wordy, as you may have to prove to TypeScript that the particular key you’re manipulating is a string, and not a number or a symbol.

▪ To opt into TypeScript’s legacy behavior—where keys must be strings—enable the keyofStringsOnly tsconfig.json flag.

▪ The Record Type

▪ TypeScript’s built-in Record type is a way to describe an object as a map from something to something

▪ Record gives you one extra degree of freedom compared to regular object index signatures: with a regular index signature you can constrain the types of an object’s values, but the key can only be a regular string, number, or symbol; with Record, you can also constrain the types of an object’s keys to subtypes of string and number

▪ Mapped Types

▪ TypeScript gives us a second, more powerful way to declare a safer nextDay type: mapped types.

▪ Let’s use mapped types to say that nextDay is an object with a key for each Weekday, whose value is a Day:

let nextDay: {[K in Weekday]: Day} = {
Mon: 'Tue'
}

▪ Mapped types are a language feature unique to TypeScript. Like literal types, they’re a utility feature that just makes sense for the challenge that is statically typing JavaScript.

▪ As the name implies, it’s a way to map over an object’s key and value types. In fact, TypeScript uses mapped types to implement its built-in Record type we used earlier:

type Record = {
[P in K]: T
}

▪ Mapped types give you more power than a mere Record because in addition to letting you give types to an object’s keys and values, when you combine them with keyed-in types, they let you put constraints on which value type corresponds to which key name

▪ type Account = {
id: number
isEmployee: boolean
notes: string[]
}

// Make all fields optional
type OptionalAccount = {
[K in keyof Account]?: Account[K] ￼
}

▪ // Make all fields nullable
type NullableAccount = {
[K in keyof Account]: Account[K] | null ￼
}

▪ We can mark fields as optional (?) or readonly, and we can also unmark them. With the minus (–) operator—a special type operator only available with mapped types—we can undo ? and readonly, making fields required and writable again, respectively. Here we create a new object type Account2, equivalent to our Account type, by mapping over ReadonlyAccount and removing the readonly modifier with the minus (–) operator.

▪ Minus (–) has a corresponding plus (+) type operator. You will probably never use this operator directly, because it’s implied: within a mapped type, readonly is equivalent to +readonly, and ? is equivalent to +?. + is just there for completeness

▪ The mapped types we derived in the last section are so useful that TypeScript ships with many of them built in:

▪ Record

An object with keys of type Keys and values of type Values

▪ Partial

Marks every field in Object as optional

▪ Required

Marks every field in Object as nonoptional

▪ Readonly

Marks every field in Object as read-only

▪ Pick

Returns a subtype of Object, with just the given Keys

▪ Companion Object Pattern

▪ The companion object pattern comes to us from Scala, and is a way to pair together objects and classes that share the same name

▪ In TypeScript, there’s a similar pattern that’s similarly useful—we’ll also call it the companion object pattern—that we can use to pair together a type and an object.

▪ Remember that in TypeScript, types and values live in separate namespaces; you’ll read a little more about this in “Declaration Merging”. That means in the same scope, you can have the same name (in this example, Currency) bound to both a type and a value.

▪ This pattern has a few nice properties. It lets you group type and value information that’s semantically part of a single name (like Currency) together.

▪ It also lets consumers import both at once:

import {Currency} from './Currency'

▪ let amountDue: Currency = { ￼
unit: 'JPY',
value: 83733.10
}

let otherAmountDue = Currency.from(330, 'EUR')

▪ Use the companion object pattern when a type and an object are semantically related, with the object providing utility methods that operate on the type

▪ When you declare a tuple in TypeScript, TypeScript will be lenient about inferring that tuple’s type. It will infer the most general possible type based on what you gave it, ignoring the length of your tuple and which position holds which type:

let a = [1, true] // (number | boolean)[]

▪ But sometimes you want inference that’s stricter, that would treat a as a fixed-length tuple and not as an array. You could, of course, use a type assertion to cast your tuple to a tuple type (more on this in “Type Assertions”). Or, you could use an as const
assertion (“The const type”) to infer the tuple’s type as narrowly as possible, marking it as read-only.

▪ What if you want to type your tuple as a tuple, but avoid a type assertion, and avoid the narrow inference and read-only modifier that as const
gives you?

▪ To do that, you can take advantage of the way TypeScript infers types for rest parameters (jump back to “Using bounded polymorphism to model arity” for more about that):

▪ function tuple< ￼
T extends unknown[] ￼
>(
...ts: T ￼
): T { ￼
return ts ￼
}

let a = tuple(1, true) // [number, boolean]

▪ The thing about type refinement is it’s only powerful enough to refine the type of a variable in the scope you’re in. As soon as you leave that scope, the refinement doesn’t carry over to whatever new scope you’re in

▪ In our isString implementation, we refined the input parameter’s type to string using typeof, but because type refinement doesn’t carry over to new scopes, it got lost—all TypeScript knows is that isString returned a boolean.

▪ What we can do is tell the typechecker that not only does isString return a boolean, but whenever that boolean is true, the argument we passed to isString is a string. To do that, we use something called a user-defined type guard:

▪ Type guards are a built-in TypeScript feature, and are what lets you refine types with typeof and instanceof

▪ But sometimes, you need the ability to declare type guards yourself—that’s what the is operator is for. When you have a function that refines its parameters’ types and returns a boolean, you can use a user-defined type guard to make sure that refinement is flowed whenever you use that function.

▪ User-defined type guards are limited to a single parameter, but they aren’t limited to simple types:

▪ type LegacyDialog = // ...
type Dialog = // ...

function isLegacyDialog(
dialog: LegacyDialog | Dialog
): dialog is LegacyDialog {
// ...
}

▪ You won’t use user-defined type guards often, but when you do, they’re awesome for writing clean, reusable code. Without them, you’d have to inline all your typeof and instanceof type guards instead of building functions like isLegacyDialog and isString to perform those same checks in a better-encapsulated, more readable way.

▪ Conditional types might be the single most unique feature in all of TypeScript.

▪ At a high level, conditional types let you say, “Declare a type T that depends on types U and V; if U , then assign T to A, and otherwise, assign T to B.”

▪ We declare a new conditional type IsString that takes a generic type T.

▪ The “condition” part of this conditional type is T extends string
; that is, “Is T a subtype of string?”

▪ If T is a subtype of string, we resolve to the type true.


￼

Otherwise, we resolve to the type false.

▪ Note how the syntax looks just like a regular value-level ternary expression, but at the type level. And like regular ternary expressions, you can nest them too.

▪ Conditional types aren’t limited to type aliases. You can use them almost anywhere you can use a type: in type aliases, interfaces, classes, parameter types, and generic defaults in functions and methods.

▪ While you can express simple conditions like the examples we just looked at in a variety of ways in TypeScript—with conditional types, overloaded function signatures, and mapped types—conditional types let you do more

▪ (string | number) extends T ? A : B
(string extends T ? A : B) | (number extends T ? A : B)

▪ (string | number | boolean) extends T ? A : B
(string extends T ? A : B) | (number extends T ? A : B) | (boolean extends T ? A : B)

▪ Let’s say we have a function that takes some variable of type T, and lifts it to an array of type T[].

▪ Note that the conditional doesn’t actually do anything here because both its branches resolve to the same type T[]; it’s just here to tell TypeScript to distribute T over the tuple type.) Take a look:


type ToArray2 = T extends unknown ? T[] : T[]
type A = ToArray2 // number[]

▪ When you use a conditional type, TypeScript will distribute union types over the conditional’s branches. It’s like taking the conditional type and mapping (er, distributing) it over each element in the union.

▪ Let’s build Without
, which computes the types that are in T but not in U.

type Without = T extends U ? never : T

▪ type A = Without
boolean | number | string,
boolean
> // number | string

▪ Start with the inputs:

type A = Without

▪ Distribute the condition over the union:

type A = Without
| Without
| Without

▪ As a refresher, so far we’ve seen just one way to declare generic type parameters: using angle brackets (). Conditional types have their own syntax for declaring generic types inline: the infer keyword.

▪ type ElementType = T extends unknown[] ? T[number] : T
type A = ElementType // number

▪ Now, let’s rewrite it using infer:

type ElementType2 = T extends (infer U)[] ? U : T
type B = ElementType2 // number

▪ Notice how the infer clause declares a new type variable, U—TypeScript will infer the type of U from context, based on what T you passed to ElementType2

▪ it puts the burden of computing U on the caller, when we wanted ElementUgly to compute the type itself.

▪ Honestly, this was a bit of a silly example because we already have the keying-in operator ([]) to look up the type of an array’s elements. What about a more complicated example?

▪ type SecondArg = F extends (a: any, b: infer B) => any ? B : never

▪ // Get the type of Array.slice
type F = typeof Array['prototype']['slice']

▪ type A = SecondArg // number | undefined

▪ So, [].slice’s second argument is a number | undefined
. And we know this at compile time—try doing that in Java

▪ Conditional types let you express some really powerful operations at the type level. That’s why TypeScript ships with a few globally available conditional types out of the box:

▪ Exclude

Like our Without type from before, computes those types in T that are not in U:

▪ NonNullable

Computes a version of T that excludes null and undefined:

▪ ReturnType

Computes a function’s return type (note that this doesn’t work as you’d expect for generic and overloaded functions):

▪ InstanceType

Computes the instance type of a class constructor:

▪ Sometimes you don’t have time to type something perfectly, and you just want TypeScript to trust that what you’re doing is safe

▪ Maybe a type declaration for a third party module you’re using is wrong

▪ maybe you’re getting data from an API and you haven’t regenerated type declarations with Apollo yet

▪ Luckily, TypeScript knows that we’re only human, and gives us a few escape hatches for when we just want to do something and don’t have time to prove to TypeScript that it’s safe

▪ In case it’s not obvious, you should use the following TypeScript features as little as possible. If you find yourself relying on them, you might be doing something wrong.

▪ If you have a type B and A , then you can assert to the typechecker that B is actually an A or a C.

▪ Notably, you can only assert that a type is a supertype or a subtype of itself—you can’t, for example, assert that a number is a string, because those types aren’t related

▪ TypeScript gives us two syntaxes for type assertions:

▪ // Assert that input is a string
formatInput(input as string)

▪ // This is equivalent to
formatInput(input)

▪ We use a type assertion (as) to tell TypeScript that input is a string, not a string | number
as the types would have us believe.

▪ The legacy syntax for type assertions uses angle brackets. The two syntaxes are functionally equivalent.

▪ Prefer as syntax for type assertions over angle bracket (
▪ Use TSLint’s no-angle-bracket-type-assertion rule to automatically enforce this for your codebase.

▪ Sometimes, two types might not be sufficiently related, so you can’t assert that one is the other. To get around this, simply assert as any (remember from “Assignability” that any is assignable to anything), then spend a few minutes in the corner thinking about what you’ve done:

▪ Clearly, type assertions are unsafe, and you should avoid using them when possible.

▪ We remove the dialog from the DOM on the next turn of the event loop, so that any other code that depends on dialog has a chance to finish running.

▪ Because we’re inside the arrow function, we’re now in a new scope. TypeScript doesn’t know if some code mutated dialog between ￼ and ￼, so it invalidates the refinement we made in

▪ On top of that, while we know that if dialog.id is defined then an element with that ID definitely exists in the DOM (because we designed our framework that way), all TypeScript knows is that calling document.getElementById returns an HTMLElement | null
. We know it’ll always be a nonnullable HTMLElement, but TypeScript doesn’t know that—it only knows about the types we gave it.

▪ One way to fix this is to add a bunch of if (_ === null)
checks everywhere. While that’s the right way to do it if you’re unsure if something is null or not, TypeScript comes with special syntax for when you’re sure it’s not null | undefined
:

▪ dialog.id!

▪ element.parentNode!

▪ When you find yourself using nonnull assertions a lot, it’s often a sign that you should refactor your code

▪ For example, we could get rid of an assertion by splitting Dialog into a union of two types:

type VisibleDialog = {id: string}
type DestroyedDialog = {}
type Dialog = VisibleDialog | DestroyedDialog

▪ After we check that dialog has an id property defined—implying that it’s a VisibleDialog—even inside the arrow function TypeScript knows that the reference to dialog hasn’t changed: the dialog inside the arrow function is the same dialog outside the function, so the refinement carries over instead of being invalidated like it was in the last example.

▪ We can use a definite assignment assertion to tell TypeScript that userId will definitely be assigned by the time we read it (notice the exclamation mark):


let userId!: string
fetchUser()

userId.toUpperCase() // OK

▪ As with type assertions and nonnull assertions, if you find yourself using definite assignment assertions often, you might be doing something wrong.

▪ By this point in the book, if I were to shake you awake at three in the morning and yell “IS TYPESCRIPT’S TYPE SYSTEM STRUCTURAL OR NOMINAL?!” you’d yell back “OF COURSE IT’S STRUCTURAL!

▪ Laws aside, the reality is that sometimes nominal types really are useful

▪ For example, let’s say you have a few ID types in your application, representing unique ways of addressing the different types of objects in your system:

type CompanyID = string
type OrderID = string
type UserID = string
type ID = CompanyID | OrderID | UserID

▪ This is where nominal types come in handy.5 While TypeScript doesn’t support nominal types out of the box, we can simulate them with a technique called type branding.

▪ Type branding takes a little work to set up, and using it in TypeScript is not as smooth an experience as it is in languages that have built-in support for nominal type aliases. That said, branded types can make your program significantly safer.

▪ Depending on your application and the size of your engineering team (the larger your team, the more likely this technique will come in handy for preventing mistakes), you may not need to do this.

▪ Start by creating a synthetic type brand for each of your nominal types:


type CompanyID = string & {readonly brand: unique symbol}
type OrderID = string & {readonly brand: unique symbol}
type UserID = string & {readonly brand: unique symbol}
type ID = CompanyID | OrderID | UserID

▪ An intersection of string and {readonly brand: unique symbol}
is, of course, gibberish. I chose it because it’s impossible to naturally construct that type, and the only way to create a value of that type is with an assertion.

▪ That’s the crucial property of branded types: they make it hard to accidentally use a wrong type in their place. I used unique symbol
as the “brand” because it’s one of two truly nominal kinds of types in TypeScript (the other is enum); I took an intersection of that brand with string so that we can assert that a given string is a given branded type.

▪ We now need a way to create values of type CompanyID, OrderID, and UserID. To do that, we’ll use the companion object pattern (introduced in “Companion Object Pattern”). We’ll make a constructor for each branded type, using a type assertion to construct a value of each of our gibberish types:

▪ function CompanyID(id: string) {
return id as CompanyID
}

▪ What’s nice about this approach is how little runtime overhead it has: just one function call per ID construction, which will probably be inlined by your JavaScript VM anyway.

▪ When building JavaScript applications, tradition holds that it’s unsafe to extend prototypes for built-in types. This rule of thumb goes back to before the days of jQuery, when wise JavaScript mages built libraries like MooTools that extended and overwrote built-in prototype methods directly. But when too many mages augmented prototypes at once, conflicts arose. And without static type systems, you’d only find out about these conflicts from angry users at runtime.

▪ If you’re not coming from JavaScript, you may be surprised to learn that in JavaScript, you can modify any built-in method (like [].push, 'abc'.toUpperCase, or Object.assign) at runtime. Because it’s such a dynamic language, JavaScript gives you direct access to prototypes for every built-in object—Array.prototype, Function.prototype, Object.prototype, and so on.

▪ While back in the day extending these prototypes was unsafe, if your code is covered by a static type system like TypeScript, then you can now do it safely.6

▪ For example, we’ll add a zip method to the Array prototype

▪ // Tell TypeScript about .zip
interface Array { ￼
zip(list: U[]): [T, U][]
}

▪ // Implement .zip
Array.prototype.zip = function(
this: T[], ￼
list: U[]
): [T, U][] {
return this.map((v, k) =>
tuple(v, list[k]) ￼
)
}

▪ We start by telling TypeScript that we’re adding zip to Array. We take advantage of interface merging (“Declaration Merging”) to augment the global Array interface, adding our own zip method to the already globally defined interface.

▪ Since our file doesn’t have any explicit imports or exports—meaning it’s in script mode, as described in “Module Mode Versus Script Mode”—we were able to augment the global Array interface directly by declaring an interface with the exact same name as the existing Array interface, and letting TypeScript take care of merging the two for us.

▪ If our file were in module mode (which might be the case if, for example, we needed to import something for our zip implementation), we’d have to wrap our global extension in a declare global
type declaration (see “Type Declarations”):

▪ declare global {
interface Array {
zip(list: U[]): [T, U][]
}
}

▪ global is a special namespace containing all the globally defined values (anything that you can use in a module-mode file without importing it first; see Chapter 10) that lets you augment names in the global scope from a file in module mode.

▪ We then implement the zip method on Array’s prototype. We use a this type so that TypeScript correctly infers the T type of the array we’re calling .zip on.

▪ Notice that when we declare interface Array
we augment the global Array namespace for our whole TypeScript project—meaning even if we don’t import zip.ts from our file, TypeScript will think that [].zip is available

▪ But in order to augment Array.prototype, we have to be sure that whatever file uses zip loads zip.ts first, in order to install the zip method on Array.prototype. How do we make sure that any file that uses zip loads zip.ts first?

Easy: we update our tsconfig.json to explicitly exclude zip.ts from our project, so that consumers have to explicitly import it first:

{
*exclude*: [
"./zip.ts"
]
}

▪ Now we can use zip as we please, with total safety:

import './zip'

[1, 2, 3]
.map(n => n * 2) // number[]
.zip(['a', 'b', 'c']) // [number, string][]

▪ In this chapter we covered the most advanced features of TypeScript’s type system: from the ins and outs of variance to flow-based type inference, refinement, type widening, totality, and mapped and conditional types.

▪ We then derived a few advanced patterns for working with types: type branding to simulate nominal types, taking advantage of the distributive property of conditional types to operate on types at the type level, and safely extending prototypes.

▪ If you didn’t understand or don’t remember everything, that’s OK—come back to this chapter later, and use it as a reference when you’re struggling with how to express something more safely.

▪ Symbolic execution is a form of program analysis where you use a special program called a symbolic evaluator to run your program the same way a runtime would, but without assigning definite values to variables; instead, each variable is modelled as a symbol whose value gets constrained as the program runs. Symbolic execution lets you say things like “this variable is never used,” or “this function never returns,” or “in the positive branch of the if statement on line 102, variable x is guaranteed not to be null.”

▪ Flow-based type inference is supported by a handful of languages, including TypeScript, Flow, Kotlin, and Ceylon. It’s a way to refine types within a block of code, and is an alternative to C/Java-style explicit type annotations and Haskell/OCaml/Scala-style pattern matching.

▪ The idea is to take a symbolic execution engine and embed it right in the typechecker, in order to give feedback to the typechecker and reason through a program in a way that is closer to how a human programmer might do it.

▪ JavaScript has seven falsy values: null, undefined, NaN, 0, -0, "", and of course, false. Everything else is truthy.

▪ DefinitelyTyped is the open source repository for type declarations for third-party JavaScript. To learn more, jump ahead to “JavaScript That Has Type Declarations on DefinitelyTyped”.

▪ 5 In some languages, these are also called opaque types

▪ There are other reasons why you might want to avoid extending the prototype, like code portability, making your dependency graphs more explicit, or improving performance by only loading those methods that you actually use. However, safety is no longer one of those reasons.

▪ TypeScript does everything it can to move runtime exceptions to compile time: from the rich type system it provides to the powerful static and symbolic analyses it performs, it works hard so you don’t have to

▪ Unfortunately, regardless of what language you write in, sometimes runtime exceptions do sneak through. TypeScript is really good about preventing them, but even it can’t prevent things like network and filesystem failures, errors parsing user input, stack overflows, and out of memory errors. What it does do—thanks to its lush type system—is give you lots of ways to deal with the runtime errors that end up making it through.

▪ In this chapter I’ll walk you through the most common patterns for representing and handling errors in TypeScript:

Returning null

Throwing exceptions

Returning exceptions

The Option type

▪ Which mechanism you use is up to you, and depends on your application

▪ Returning null is the most lightweight way to handle errors in a typesafe way. Valid user input results in a Date, invalid user input in a null, and the type system checks for us that we handled both.

▪ However, we lose some information doing it this way parse doesn’t tell us why exactly the operation failed, which stinks for whatever engineer has to comb through our logs to debug this

▪ as well as the user who gets a pop up saying that there was an “Error parsing date for some reason” rather than a specific, actionable error like “Enter a date in the form YYYY/MM/DD.”

▪ Returning null is also difficult to compose: having to check for null after every operation can become verbose as you start to nest and chain operations.

▪ Let’s throw an exception instead of returning null, so that we can handle specific failure modes and have some metadata about the failure so we can debug it more easily.

▪ RangeError('Enter a date in the form YYYY/MM/DD')

▪ Now when we consume this code, we need to be careful to catch the exception so that we can handle it gracefully without crashing our whole application:

▪ We probably want to be careful to rethrow other exceptions, so we don’t silently swallow every possible error:

▪ We might want to subclass the error for something more specific, so that when another engineer changes parse or ask to throw other RangeErrors, we can differentiate between our error and the one they added:

▪ Looking good. We can now do more than just signal that something failed: we can use a custom error to indicate why it failed

▪ We can also effectively chain and nest operations by wrapping any number of operations in a single try/catch (we don’t have to check each operation for failure, like we did when returning null).

▪ But in practice, an engineer probably wouldn’t wrap this code in a try/catch and check for exceptions at all, because engineers are lazy (at least, I am), and the type system isn’t telling them that they missed a case and should handle it.

▪ How else can we indicate to consumers that they should handle both the success and the error cases?

▪ TypeScript isn’t Java, and doesn’t support throws clauses.1 But we can achieve something similar with union types:

▪ Now a consumer is forced to handle all three cases—InvalidDateFormatError, DateIsInTheFutureError, and successful parse—or they’ll get a TypeError at compile time:

▪ Communicate to consumers which specific exceptions might be thrown.

Force consumers to handle (or rethrow) each of the exceptions.

A lazy consumer can avoid handling each error individually. But they have to do so explicitly:

▪ A downside is that chaining and nesting error-giving operations can quickly get verbose. If a function returns T | Error1
, then any function that consumes that function has two options:

Explicitly handle Error1.

Handle T (the success case) and pass Error1 through to its consumers to handle. If you do this enough, the list of possible errors that a consumer has to handle grows quickly:

▪ This approach is verbose, but gives us excellent safety.

▪ You can also describe exceptions using special-purpose data types. This approach has some downsides compared to returning unions of values and errors (notably, interoperability with code that doesn’t use these data types), but it does give you the ability to chain operations over possibly errored computations.

▪ Three of the most popular options (heh!) are the Try, Option,2 and Either types.

▪ In this chapter, we’ll just cover the Option type;3 the other two are similar in spirit.

▪ Note that the Try, Option, and Either data types don’t come built into JavaScript environments the same way that Array, Error, Map, or Promise are. If you want to use these types, you’ll have to find implementations on NPM, or write them yourself.

▪ The Option type comes to us from languages like Haskell, OCaml, Scala, and Rust

▪ The idea is that instead of returning a value, you return a container that may or may not have a value in it.

▪ The container has a few methods defined on it, which lets you chain operations even though there may not actually be a value inside.

▪ The container can be pretty much any data structure, so long as it can hold a value. For example, you could use an array as the container:

▪ As you may have noticed, a downside of Option is that, much like our original null-returning approach, it doesn’t tell the consumer why the error happened; it just signals that something went wrong.

▪ Where Option really shines is when you need to do multiple operations in a row, each of which might fail.

For example, before we assumed that prompt always succeeds, and parse might fail. But what if prompt can fail too? That might happen if the user cancelled out of the birthday prompt—that’s an error and we shouldn’t continue our computation. We can model that with… another Option!

▪ Yikes—that didn’t work. Since we mapped an array of Dates (Date[]) to an array of arrays of Dates (Date[][]), we need to flatten it back to an array of Dates before we can keep going:

▪ flatten(ask()
.map(parse))
.map(date => date.toISOString())
.forEach(date => console.info('Date is', date))

▪ ask()
.flatMap(parse)
.flatMap(date => new Some(date.toISOString()))
.flatMap(date => new Some('Date is ' + date))
.getOrElse('Error parsing date for some reason')

▪ Option is an interface that’s implemented by two classes: Some and None (see Figure 7-1). They are the two kinds of Options. Some is an Option that contains a value of type T, and None is an Option without a value, which represents a failure.

▪ Option is both a type and a function.

▪ Its type is an interface that simply serves as the supertype of Some and None.

▪ Its function is the way to create a new value of type Option.

▪ interface Option {}

▪ class Some implements Option { ￼
constructor(private value: T) {}
}

▪ class None implements Option {} ￼

▪ Option is an interface that we’ll share between Some and None.

▪ Some represents a successful operation that resulted in a value. Like the array we used before, Some is a container for that value.

▪ None represents an operation that failed, and does not contain a value

▪ Option is [T] | []

▪ Some is [T].

▪ None is [].

▪ What can you do with an Option? For our bare-bones implementation, we’ll define just two operations:

▪ flatMap

A way to chain operations on a possibly empty Option

▪ getOrElse

A way to retrieve a value from an Option

▪ interface Option {
flatMap(f: (value: T) => Option): Option
getOrElse(value: T): T
}
class Some extends Option {
constructor(private value: T) {}
}
class None extends Option {}

▪ flatMap takes a function f that takes a value of type T (the type of the value the Option contains) and returns an Option of U. flatMap calls f with the Option’s value, and returns a new Option.

▪ getOrElse takes a default value of the same type T as the value that the Option contains, and returns either that default value (if the Option is an empty None) or the Option’s value (if the Option is a Some).

▪ Since a None represents a failed computation, calling flatMap on it always returns a None: once a computation fails, we can’t recover from that failure (at least not with our particular Option implementation).

▪ Calling getOrElse on a None always returns the value we passed into getOrElse.

▪ That is, we know that mapping over a None always results in a None, and mapping over a Some results in either a Some or a None, depending on what calling f returns. We’ll exploit this and use overloaded signatures to give flatMap more specific types:

▪ If a user passes in null or undefined, we’ll give them back a None; otherwise, we’ll return a Some. Once again, we’ll overload the signature to do that:

▪ That’s it. We’ve derived a fully working, minimal Option type that lets us safely perform operations over maybe-null values. We use it like this:

let result = Option(6) // Some
.flatMap(n => Option(n * 3)) // Some
.flatMap(n => new None) // None
.getOrElse(7) // 7

▪ Options are a powerful way to work with series of operations that may or may not succeed

▪ They give you excellent type safety, and signal to consumers via the type system that a given operation might fail.

▪ However, Options aren’t without their downsides. They signal failure with a None, so you don’t get more details about what failed and why. They also don’t interoperate with code that doesn’t use Options (you’ll have to explicitly wrap those APIs to return Options).

▪ Still, what you did there was pretty neat. The overloads you added let you do something that you can’t express in most languages, even those that rely on the Option type for working with nullable values.

▪ By restricting Option to just Some or None where possible via overloaded call signatures, you made your code a whole lot safer, and a whole lot of Haskell programmers very jealous.

▪ In this chapter we covered the different ways to signal and recover from errors in TypeScript: returning null, throwing exceptions, returning exceptions, and the Option type.

▪ You now have an arsenal of approaches for safely working with things that might fail.

▪ Whether you want to simply signal that something failed (null, Option), or give more information about why it failed (throwing and returning exceptions).

▪ Whether you want to force consumers to explicitly handle every possible exception (returning exceptions), or write less error-handling boilerplate (throwing exceptions).

▪ Also called the Maybe type

▪ Google “try type” or “either type” for more information on those types.

▪ But the really interesting programs—the building blocks of real-world applications that make network requests, interact with databases and filesystems, respond to user interaction, offload CPU-intensive work to separate threads—all make use of asynchronous APIs like callbacks, promises, and streams.

▪ These asynchronous tasks are where JavaScript really shines and sets itself apart from other mainstream multithreaded languages like Java and C++. Popular JavaScript engines like V8 and SpiderMonkey do with one thread what traditionally required many threads, by being clever and multiplexing tasks over a single thread while other tasks are idling.

▪ This event loop is the standard threading model for JavaScript engines, and the one that we’ll assume you’re using.

▪ This event-looped concurrency model is how JavaScript avoids all the common footguns endemic to multithreaded programming, along with the overhead of synchronized data types, mutexes, semaphores, and all the other bits of multithreading jargon.

▪ And when you do run JavaScript over multiple threads, it’s rare to use shared memory; the typical pattern is to use message passing and to serialize data when sending it between threads.

▪ It’s a design reminiscent of Erlang, actor systems, and other purely functional concurrency models, and is what makes multithreaded programming in JavaScript foolproof.

▪ That said, asynchronous programming does make programs harder to reason about, because you can no longer mentally trace through a program line by line; you have to know when to pause and move execution elsewhere, and when to resume again.

▪ TypeScript gives us the tools to reason about asynchronous programs: types let us trace through asynchronous work, and built-in support for async/await let us apply familiar synchronous thinking to asynchronous programs.

▪ But before we get to working with asynchronous programs, let’s talk a bit more about how asynchronicity actually works in modern JavaScript engines—how is it that we can suspend and resume execution on what seems to be a single thread?

▪ Let’s start with an example. We’ll set a couple of timers, one that fires after one millisecond, and the other after two:

setTimeout(() => console.info('A'), 1)
setTimeout(() => console.info('B'), 2)
console.info('C')

Now, what will get logged to the console? Is it A, B, C?

▪ If you haven’t worked with JavaScript or TypeScript before, this behavior might seem mysterious and unintuitive. In reality, it’s pretty straightforward; it just doesn’t follow the same concurrency model as a sleep would in C, or scheduling work in another thread would in Java.

▪ At a high level, the JavaScript VM simulates concurrency like this (see Figure 8-1):

▪ The main JavaScript thread calls into native asynchronous APIs like XMLHTTPRequest (for AJAX requests), setTimeout (for sleeping), readFile (for reading a file from disk), and so on. These APIs are provided by the JavaScript platform—you can’t create them yourself.1

▪ Once you call into a native asynchronous API, control returns to the main thread and execution continues as if the API was never called.

▪ Once the asynchronous operation is done, the platform puts a task in its event queue. Each thread has its own queue, used for relaying the results of asynchronous operations back to the main thread. A task includes some metainformation about the call, and a reference to a callback function from the main thread.

▪ Whenever the main thread’s call stack is emptied, the platform will check its event queue for pending tasks.

▪ If there’s a task waiting, the platform runs it; that triggers a function call, and control returns to that main thread function.

▪ When the call stack resulting from that function call is once again empty, the platform again checks the event queue for tasks that are ready to go.

▪ This loop repeats until both the call stack and the event queue are empty, and all asynchronous native API calls have completed.

▪ The basic unit of the asynchronous JavaScript program is the callback

▪ A callback is a plain old function that you pass as an argument to another function.

▪ As in a synchronous program, that other function invokes your function when it’s done doing whatever it does (making a network request, etc.). Callbacks invoked by asynchronous code are just functions, and there’s no giveaway in their type signatures that they are invoked asynchronously.

▪ For NodeJS native APIs like fs.readFile (used to asynchronously read the contents of a file from disk) and dns.resolveCname (used to asynchronously resolve CNAME records), the convention for callbacks is that the first parameter is an error or null, and the second parameter is a result or null.

▪ Notice that there’s nothing special about either readFile’s type or callback’s type: both are regular JavaScript functions. Looking at the signature, there’s no indication that readFile is asynchronous and that control will be passed to the next line right after readFile is called (not waiting for its result).

▪ To run the following example yourself, be sure to first install type declarations for NodeJS:

npm install @types/node --save-dev

▪ Unless you’re a TypeScript or JavaScript engineer and are familiar with how NodeJS’s built-in APIs work, and know that they’re asynchronous and you can’t rely on the order in which API calls appear in your code to dictate in which order filesystem operations actually happen, you wouldn’t know that we just introduced a subtle bug where the first readFile call may or may not return the access log with our new line appended, depending on how busy the filesystem is at the time this code runs.

▪ callbacks are also difficult to sequence—which can lead to what some people call “callback pyramids”:

▪ When sequencing operations, you usually want to continue down the chain when an operation succeeds, bailing out as soon as you hit an error

▪ With callbacks, you have to do this manually; when you start accounting for synchronous errors too (e.g., the NodeJS convention is to throw when you give it a badly typed argument, rather than calling your provided callback with an Error object), properly sequencing callbacks can get error-prone.

▪ This is a limitation of plain old callbacks. Without more sophisticated abstractions for operating on asynchronous tasks, working with multiple callbacks that depend on each other in some way can get messy fast.

▪ While callbacks are great for modeling simple tasks, they quickly get hairy as you try to do things with lots of asynchronous tasks.

▪ Luckily, we’re not the first programmers to run into these limitations. In this section we’ll develop the concept of promises, which are a way to abstract over asynchronous work so that we can compose it, sequence it, and so on.

▪ Even if you’ve worked with promises or futures before, this will be a helpful exercise to understand how they work.

▪ Notice how there’s no callback pyramid here—we’ve effectively linearized what we want to do into a single, easy-to-understand chain of asynchronous tasks.

▪ When one succeeds, the next one runs; if it fails, we skip to the catch clause.

▪ Let’s design a Promise API that lets us do this.

Promise starts from humble beginnings:

class Promise {
}

▪ A new Promise
takes a function we call an executor, which the Promise implementation will call with two arguments, a resolve function and a reject function:

▪ type Executor = (
resolve: Function,
reject: Function
) => void

▪ class Promise {
constructor(f: Executor) {}
}

▪ type Executor = (
resolve: (result: T) => void,
reject: (error: E) => void
) => void
// ...

▪ class Promise {
constructor(f: Executor) {}

▪ then and catch are two ways to sequence Promises: then maps a successful result of a Promise to a new Promise,

▪ catch recovers from a rejection by mapping an error to a new Promise.

▪ We also have to handle the case of Promises that throw actual exceptions (as in, throw Error('foo')
). When we implement then and catch, we’ll do this by wrapping code in try/catches and rejecting in the catch clause.

▪ Because TypeScript has no choice but to inherit JavaScript’s behavior, and in JavaScript when you throw you can throw anything—a string, a function, an array, a Promise, and not necessarily an Error—we can’t assume that a rejection will be a subtype of Error.

▪ type Executor = (
resolve: (result: T) => void,
reject: (error: unknown) => void
) => void

▪ class Promise {
constructor(f: Executor) {}

▪ then(g: (result: T) => Promise): Promise {
// ...

▪ catch(g: (error: unknown) => Promise): Promise {
// ...
}
}

▪ We now have a fully baked Promise interface.

▪ Promises are a really powerful abstraction for working with asynchronous code. They’re such a popular pattern that they even have their own JavaScript (and therefore, TypeScript) syntax: async and await.

▪ This syntax lets you interact with asynchronous operations the same way you do with synchronous ones.

▪ Think of await as language-level syntax sugar for .then

▪ When you await a Promise, you have to do so in an async block

▪ And instead of .catch, you can wrap your await in a regular try/catch block.

▪ we didn’t cover finally in the previous section, but it behaves the way you think it would, firing after both then and catch have a chance to fire

▪ While promises are fantastic for modeling, sequencing, and composing future values, what if you have multiple values, which will become available at multiple points in the future? This is less exotic than it sounds—think bits of a file being read from the filesystem, pixels of a video streaming over the internet from the Netflix server to your laptop

▪ While these things may sound pretty different on the surface, you can look at them all as asynchronous streams; they are all lists of things where each thing comes in at some point in the future.

▪ There are a few ways to model this, the most common being with an event emitter (like NodeJS’s EventEmitter) or with a reactive programming library like RxJS.3

▪ The difference between the two is like the difference between callbacks and promises: events are quick and lightweight, while reactive programming libraries are more powerful, and give you the ability to compose and sequence streams of events.

▪ To learn more about reactive programming, head over to the documentation for your favorite reactive programming library—for example, RxJS, MostJS, or xstream.

▪ At a high level, event emitters offer APIs that support emitting events on a channel and listening for events on that channel

▪ interface Emitter {

// Send an event
emit(channel: string, value: unknown): void

// Do something when an event is sent
on(channel: string, f: (value: unknown) => void): void

}

▪ Event emitters are a popular design pattern in JavaScript. You might have encountered them when using DOM events, JQuery events, or NodeJS’s EventEmitter module.

▪ Macros that generate methods to emit events and listen on each channel are a common workaround to this problem, but in TypeScript, you can express this naturally and safely using the type system.

▪ import Redis from 'redis'

// Create a new instance of a Redis client
let client = redis.createClient()

// Listen for a few events emitted by the client
client.on('ready', () => console.info('Client is ready'))
client.on('error', e => console.error('An error occurred!', e))
client.on('reconnecting', params => console.info('Reconnecting...', params))

▪ As programmers using the Redis library, we want to know what types of arguments to expect in our callbacks when we use the on API.

▪ If we were the authors of this library, the simplest way to achieve safety would be with an overloaded type:

type RedisClient = {
on(event: 'ready', f: () => void): void
on(event: 'error', f: (e: Error) => void): void
on(event: 'reconnecting',
f: (params: {attempt: number, delay: number}) => void): void
}

▪ This works pretty well, but it’s a bit wordy. Let’s express it in terms of a mapped type (see “Mapped Types”), pulling out the event definitions into their own type, Events:

▪ type Events = { ￼
ready: void
error: Error
reconnecting: {attempt: number, delay: number}
}

▪ type RedisClient = { ￼
on(
event: E,
f: (arg: Events[E]) => void
): void
}

▪ We start by defining a single object type that enumerates every event the Redis client might emit, along with the arguments for that event.

▪ We can then use this type to make the Node–Redis library safer, by typing both of its methods—emit and on—as safely as possible:

// ...
type RedisClient = {
on(
event: E,
f: (arg: Events[E]) => void
): void
emit(
event: E,
arg: Events[E]
): void
}

▪ This pattern of pulling out event names and arguments into a shape and mapping over that shape to generate listeners and emitters is common in real-world TypeScript code

▪ It’s also terse, and very safe. When an emitter is typed this way you can’t misspell a key, mistype an argument, or forget to pass in an argument.

▪ It also serves as documentation for engineers using your code, as their code editors will suggest to them the possible events they might listen on and the types of parameters in those events’ callbacks.

▪ Using mapped types to build typesafe event emitters is a popular pattern. For example, it’s how DOM events are typed in TypeScript’s standard library.

▪ WindowEventMap is a mapping from event name to event type, which the .addEventListener and .removeEventListener APIs map over to produce better, more specific event types than the default Event type:

▪ But sometimes, when doing CPU-intensive tasks, you might opt for true parallelism: the ability to split out work across multiple threads, in order to do it faster or to keep your main thread idle and responsive.

▪ In this section, we’ll explore a few patterns for writing safe, parallel programs in the browser and on the server

▪ while asynchronous APIs like Promise and setTimeout run code concurrently, Workers give you the ability to run code in parallel, on another CPU thread.

▪ Web Workers can send network requests, write to the filesystem, and so on, with a few minor restrictions.

▪ Because Web Workers are a browser-provided API, its designers put a lot of emphasis on safety—not type safety like we know and love, but memory safety

▪ Anyone that’s written C, C++, Objective C, or multithreaded Java or Scala knows the pitfalls of concurrently manipulating shared memory.

▪ When you have multiple threads reading from and writing to the same piece of memory, it’s really easy to run into all sorts of concurrency issues like nondeterminism, deadlocks, and so on.

▪ Because browser code must be particularly safe, and minimize the chances of crashing the browser and causing a poor user experience, the primary way to communicate between the main thread and Web Workers, and between Web Workers and other Web Workers, is with message passing.

▪ To follow along with the examples in this section, be sure to tell TSC that you’re planning to run this code in a browser by enabling the dom lib in your tsconfig.json:

▪ And for the code that you’re running in a Web Worker, use the webworker lib:


{
"compilerOptions": {
"lib": ["webworker", "es2015"]
}
}

▪ If you’re using a single tsconfig.json for both your Web Worker script and your main thread, enable both at once

▪ The message passing API works like this. You first spawn a web worker from a thread:

// MainThread.ts
let worker = new Worker('WorkerScript.js')

▪ let worker = new Worker('WorkerScript.js')

worker.postMessage('some data')

▪ You can pass almost any kind of data to another thread with the postMessage API.4

▪ The main thread will clone the data you pass before handing it off to the worker thread.

▪ On the Web Worker side, you listen to incoming events with the globally available onmessage API:

// WorkerScript.ts
onmessage = e => {
console.log(e.data) // Logs out 'some data'
}

▪ This API is a lot like the event emitter API we looked at in “Event Emitters”. It’s a simple way to pass messages around, but without types, we don’t know that we’ve correctly handled all the possible types of messages that might be sent.

▪ // MainThread.ts
type Message = string
type ThreadID = number
type UserID = number
type Participants = UserID[]

▪ type Commands = {
sendMessageToThread: [ThreadID, Message]
createThread: [Participants]
addUserToThread: [ThreadID, UserID]
removeUserFromThread: [ThreadID, UserID]
}

▪ type Events = {
receivedMessage: [ThreadID, UserID, Message]
createdThread: [ThreadID, Participants]
addedUserToThread: [ThreadID, UserID]
removedUserFromThread: [ThreadID, UserID]
}

▪ How could we apply these types to the Web Worker messaging API? The simplest way might be to define a union of all possible message types, then switch on the Message type. But this can get pretty tedious. For our Command type, it might look something like this:

▪ // WorkerScript.ts
type Command = ￼
| {type: 'sendMessageToThread', data: [ThreadID, Message]} ￼
| {type: 'createThread', data: [Participants]}
| {type: 'addUserToThread', data: [ThreadID, UserID]}
| {type: 'removeUserFromThread', data: [ThreadID, UserID]}

▪ function processCommandFromMainThread( ￼
command: Command
) {
switch (command.type) { ￼
case 'sendMessageToThread':
let [threadID, message] = command.data
console.log(message)
// ...
}
}

▪ We define a union of all possible commands that the main thread might send to a worker thread, along with the arguments for each command.

▪ This is just a regular union type. When defining long union types, leading with pipes (|) can make those types easier to read.

▪ Since the Command type is a discriminated union type (see [[discriminated unions]]), we use a switch to exhaustively handle every possible type of message the main thread might send our way.

▪ Let’s abstract Web Workers’ snowflake API behind a familiar EventEmitter-based API. That way we can cut down on the verbosity of our incoming and outgoing message types.

▪ We’ll start by constructing a typesafe wrapper for NodeJS’s EventEmitter API (which is available for the browser under the events package on NPM):

▪ emit takes a channel plus arguments corresponding to the list of parameters we defined in the Events type.

▪ Similarly, on takes a channel and a listener. listener takes a variable number of arguments corresponding to the list of parameters we defined in the Events type.

▪ On the flip side, we can also use an EventEmitter-based API to send commands back from the main thread to the worker thread. Note that if you use this pattern in your own code, you might consider using a more full-featured emitter (like Paolo Fragomeni’s excellent EventEmitter2) that supports wildcard listeners, so you don’t have to manually add a listener for each type of event:

▪ This is a common pattern in TypeScript: even if something is unsafe, you can usually wrap it in a typesafe API

▪ We can’t easily pass functions between threads, but we can define functions in a worker thread and send arguments to them, then send results back

▪ type Protocol = { ￼
[command: string]: {
in: unknown[]
out: unknown
}
}

▪ Anytime you need to communicate between two processes—whether on the same machine or between multiple computers on a network—typesafe protocols are a great tool to make that communication safe.

▪ While this section helped develop some intuition for what problems protocols solve, for a real-world application you’ll likely want to reach for an existing tool like Swagger, gRPC, Thrift, or GraphQL—for an overview, head over to “Typesafe APIs”.

▪ Typesafe parallelism in NodeJS works the same way as it does for Web Worker threads in the browser (see “Typesafe protocols”). While the message-passing layer itself is unsafe, it’s easy to build a typesafe API over it.

▪ // MainThread.ts
import {fork} from 'child_process'

let child = fork('./ChildThread.js') ￼

child.on('message', data => ￼
console.info('Child process sent a message', data)
)

child.send({type: 'syn', data: [3]}) ￼

▪ We use NodeJS’s fork API to spawn a new child process.

▪ In this chapter we started with the basics of JavaScript’s event loop, and continued on to a discussion of the building blocks of asynchronous code in JavaScript and how to safely express them in TypeScript: callbacks, promises, async/await, and event emitters.

▪ We then covered multithreading, exploring passing messages between threads (in the browser and on the server) and building full protocols for communicating between threads.

▪ For simple asynchronous tasks, callbacks are as straightforward as it gets.

▪ For more complex tasks that need to be sequenced and parallelized, promises and async/await are your friend.

▪ When a promise doesn’t cut it (e.g., if you’re firing an event multiple times), reach for event emitters or a reactive streams library like RxJS.

▪ To extend these techniques to multiple threads, use event emitters, typesafe protocols, or typesafe APIs (see “Typesafe APIs”).

▪ Eagle-eyed readers will notice how similar this API is to the flatMap API we developed in “The Option Type”. That similarity is no accident! Both Promise and Option are inspired by the Monad design pattern popularized by the functional programming language Haskell.

▪ Observables are the basic building block of reactive programming’s approach to doing things to values over time. There’s an in-progress proposal to standardize Observables in the Observable proposal.

▪ Look forward to a deeper dive into Observables in a future edition of this book, once the proposal is more broadly adopted by JavaScript engines.

▪ Except for functions, errors, DOM nodes, property descriptors, getters and setters, and prototype methods and properties. For more information, head over to the HTML5 specification.

▪ You can also use the Transferable API to pass certain types of data (like ArrayBuffer) between threads by reference. In this section we won’t be using Transferable to explicitly transfer object ownership across threads, but that’s an implementation detail. If you use Transferable for your use case, the approach is identical from a type safety point of view.

▪ This implementation is naive because it spawns a new worker every time we issue a command; in the real world, you probably want to have a pooling mechanism that keeps a warm pool of workers around, and recycles freed workers.

▪ While you could build every part of your application yourself from the ground up—the networking and database layers on the server, a user interface framework and state management solution on the frontend—you probably shouldn’t.

▪ It’s hard to get the details right, and luckily for us, lots of these hard problems on the frontend and backend have already been solved by other engineers. By taking advantage of existing tools, libraries, and frameworks to build things both on the frontend and the backend, we can iterate quickly and on stable ground when building our own applications.

▪ TypeScript is a natural fit for the world of frontend applications. With its rich support for JSX and its ability to safely model mutability, TypeScript lends structure and safety to your application and makes it easier to write correct, maintainable code in the fast-paced environment that is frontend development.

▪ all of the built-in DOM APIs are typesafe. To use them from TypeScript, just include their type declarations in your project’s tsconfig.json:

{
"compilerOptions": {
"lib": ["dom", "es2015"]
}
}

▪ That will tell TypeScript to include lib.dom.d.ts—its built-in browser and DOM type declarations—when typechecking your code.

▪ The lib tsconfig.json option just tells TypeScript to include a set of specific type declarations when processing the code in your project; it won’t emit any extra code, or generate any JavaScript that will exist at runtime.

▪ It won’t, for example, make the DOM magically work in a NodeJS environment (your code will compile, but it will fail at runtime)—it’s on you to make sure that your type declarations match up to what your JavaScript environment actually supports at runtime.

▪ With DOM type declarations enabled, you’ll be able to safely consume DOM and browser APIs to do things like:

▪ While for simple frontend applications these low-level DOM APIs are enough and will give you what you need to do safe, type-guided programming for the browser, most real-world frontend applications use a framework to abstract away how DOM rendering and rerendering, data binding, and events work. The following sections will give some pointers on how to effectively use TypeScript with a few of the most popular browser frameworks.

▪ React is among the most popular frontend frameworks today, and is a great choice when it comes to type safety.

▪ The reason React is so safe is because React components—the basic building blocks of React applications—are both defined and consumed in TypeScript. This property is hard to find among frontend frameworks, and means that both component definitions and consumers are typechecked.

▪ You can use types to say things like “this component takes a user ID and a color” or “this component can only have list items as children.” These constraints are then enforced by TypeScript, verifying that your components do what they say they do.

▪ This safety around component definitions and consumers—the view layer of a frontend application—is killer

▪ The view is traditionally the place where typos, missed attributes, mistyped parameters, and improperly nested elements cause programmers to collectively spend thousands of hours tearing their hair out and indignantly refreshing their browsers.

▪ When using React, you define your views using a special DSL called JavaScript XML (JSX) that you embed straight into your JavaScript code. It sort of looks like HTML in your JavaScript.

▪ You then run your JavaScript through a JSX compiler that rewrites that funky JSX syntax into regular JavaScript function calls.

▪ The process looks something like this. Say you’re building a menu app for your friend’s restaurant, and you list out a few items on the brunch menu with the following JSX:


Homemade granola with yogurt


Fantastic french toast with fruit


Tortilla Española with salad




After running that code through a JSX compiler like Babel’s transform-react-jsx plugin, you’ll get the following output:


React.createElement(
'ul',
{'class': 'list'},
React.createElement(
'li',
null,
'Homemade granola with yogurt'
),
React.createElement(
'li',
null,
'Fantastic French toast with fruit'
),
React.createElement(
'li',
null,
'Tortilla Española with salad'
)
);

▪ Because JSX compiles to a call to React.createElement, be sure to import the React library into each file where you use JSX so that you have a variable named React in scope:

import React from 'react'

▪ Also note that I’ve set {"esModuleInterop": true}
in my tsconfig.json to support importing React without a wildcard (*) import. If you’re following along, either enable esModuleInterop in your own tsconfig.json, or use a wildcard import instead:

▪ import * as React from 'react'

▪ The nice thing about JSX is you can write what looks a lot like normal HTML, then compile it automatically to a JavaScript engine–friendly format. As an engineer you only use a familiar, high-level, declarative DSL, and you don’t have to deal with the implementation details.

▪ You don’t need JSX to work with React (you can write that compiled code directly and it’ll work fine), and you can use JSX without React (the specific function call that JSX tags compile to—React.createElement in the previous example—is configurable), but the combination of React with JSX is magical, and makes writing views really fun, and really, really safe.

▪ Files that contain JSX use the file extension .jsx. And TypeScript files that contain JSX use the .tsx extension. TSX is to JSX what TypeScript is to JavaScript—a compile-time safety and assistance layer to help you be more productive and produce code with fewer mistakes.

▪ To enable TSX support for your project, add the following line to your tsconfig.json:


{
"compilerOptions": {
"jsx": "react"
}
}

▪ The jsx directive has three modes at the time of writing:

▪ react

Compile JSX to a .js file using the JSX pragma (by default, React.createElement).

▪ react-native

Preserve JSX without compiling it, but do emit a file with a .js extension.

▪ preserve

Typecheck JSX but don’t compile it away, and emit a file with a .jsx extension.

▪ Under the hood, TypeScript exposes a few hooks for typing TSX in a pluggable way. These are special types on the global.JSX namespace that TypeScript looks at as the source of truth for TSX types throughout your program.

▪ If you’re just using React, you don’t need to go that low-level; but if you’re building your own TypeScript library that uses TSX (and doesn’t use React)—or if you’re curious how the React type declarations do it—head over to Appendix G.

▪ We use React’s useState hook to declare local state for a function component. useState is one of a handful of hooks available in React, which you can combine to create your own custom hooks

▪ React lets us declare two kinds of components: function components and class components. Both kinds of components take some properties and render some TSX. From a consumer’s point of view, they are identical.

▪ Props is always an object type, and is named Props by convention. For our FancyButton component, isDisabled is optional, while the rest of our props are required.

▪ React has its own set of wrapper types for DOM events. When using React events, be sure to use React’s event types rather than regular DOM event types.

▪ A function component is just a regular function that has up to one parameter (the props object) and returns a React-renderable type

▪ React is permissive and can render a wide range of types: TSX, strings, numbers, booleans, null, and undefined.

▪ Note that because we passed the initial value false to useState, TypeScript was able to infer that the piece of state is a boolean; if we’d instead used a type that TypeScript wasn’t able to infer—for example, an array—we would have bound the type explicitly (e.g., with useState;([])).

▪ We use TSX syntax to create an instance of FancyButton. The 
syntax is almost identical to calling FancyButton, but it lets React manage the lifecycle of FancyButton for us.

▪ JSX is well formed. Tags are closed and properly nested, and tag names aren’t misspelled.

▪ When we instantiate a 
we pass all required—plus any optional—props to FancyButton (size, text, and onClick), and that the props are all correctly typed.

▪ We don’t pass any extraneous props to FancyButton, just the ones that are required.

▪ To declare a class component, we extend the React.Component base class.

▪ TSX supports fragments using the special syntax. A fragment is a nameless TSX element that wraps other TSX, and is a way to avoid rendering extra DOM elements in places where you need to return a single TSX element.

▪ For example, a React component’s render method needs to return a single TSX element; to do that, we could have wrapped our code with a 

or any other element, but that would have incurred unnecessary overhead during rendering.

▪ We define signUp using an arrow function, to make sure that this in the function doesn’t get re-bound.

▪ Notice how we mix and match value-based (FancyButton, SignupForm) and intrinsic (section, h2) components in this example.

▪ We didn’t use React’s PropTypes feature, which is a way to declare and check props’ types at runtime. Since TypeScript is already checking types for us at compile time, we don’t need to do it again.

▪ Angular is a more fully featured frontend framework than React, and comes with support not just for rendering views but also for sending and managing network requests, routing, and dependency injection.

▪ It’s built from the ground up to work with TypeScript (in fact, the framework itself is written in TypeScript!).

▪ Central to the way Angular works is the Ahead-of-Time (AoT) compiler built into Angular CLI, Angular’s command-line utility, that grabs the type information you gave it with your TypeScript annotations and uses that information to compile your code down to regular JavaScript

▪ Instead of calling TypeScript directly, Angular applies a whole bunch of optimizations and transformations to your code before ultimately delegating to TypeScript and compiling it down to JavaScript

▪ To initialize a new Angular project, start by globally installing Angular CLI using NPM:

npm install @angular/cli --global

▪ Then, use Angular CLI to initialize a new Angular application:

ng new my-angular-app

▪ Follow the prompts, and Angular CLI will set up a bare-bones Angular application for you.

▪ Angular components are like React components, and include a way to describe a component’s DOM structure, styling, and controller.

▪ With Angular, you generate component boilerplate with Angular CLI, then fill in the details by hand. An Angular component consists of a few different files:

A template, which describes the DOM a component renders

A set of CSS styles

A component class, which is a TypeScript class that dictates your components’ business logic

▪ @Component({
selector: 'simple-message',
styleUrls: ['./simple-message.component.css'],
templateUrl: './simple-message.component.html'
})

▪ export class SimpleMessageComponent implements OnInit {

▪ Angular’s lifecycle hooks are available as TypeScript interfaces—just declare which ones you implement (ngOnChanges, ngOnInit, etc.).

▪ TypeScript then enforces that you implement methods that comply with the lifecycle hooks you want. In this example we implemented the OnInit interface, which requires that we implement the ngOnInit method.

▪ Angular makes heavy use of TypeScript decorators (see “Decorators”) to declare metadata related to your Angular components, services, and modules.

▪ To enable typechecking for your Angular templates (you should!), be sure to enable fullTemplateTypeCheck in your tsconfig.json:

{
"angularCompilerOptions": {
"fullTemplateTypeCheck": true
}
}

▪ Note that angularCompilerOptions isn’t specifying options for TSC. Rather, it defines compiler flags specific to Angular’s AoT compiler.

▪ Angular comes with a built-in dependency injector (DI), which is a way for the framework to take care of instantiating services and passing them in as arguments to components and services that depend on them.

▪ constructor(
private messageService: MessageService
) {}

▪ ngOnInit() {
this.messageService.getMessage().

▪ Angular’s AoT compiler looks at the parameters that your component’s constructor takes, plucks out their types (e.g., MessageService), and searches the relevant dependency injector’s dependency map for a dependency of that specific type

▪ import {Injectable} from '@angular/core'
import {HttpClient} from '@angular/common/http'

▪ Regardless of which frontend and backend frameworks you decide to use, you’ll want a way to safely communicate across machines—from client to server, server to client, server to server, and client to client.

▪ There are a few competing tools and standards in this space. But before we explore what they are and how they work, let’s think about how we might build our own solution, and what benefits and drawbacks it might have (we are engineers, after all).

▪ The problem we want to solve is this: though our clients and servers might be 100% typesafe—bastions of safety—at some point they’ll need to talk to each other over untyped network protocols like HTTP, TCP, or some other socket-based protocols.

▪ A good starting point could be a typesafe protocol like the one we developed in “Typesafe protocols”.

▪ You could build corresponding post and put functions to write back to your REST API, and add a type for each entity your server supports. On the backend, you’d then implement a corresponding set of handlers for each type of entity, reading from your database to return to the client whatever entity it asked for.

▪ But what happens if your server isn’t written in TypeScript, or if you aren’t able to share your Request type between the client and server (leading to the two getting out of sync over time), or if you don’t use REST (maybe you use GraphQL instead)? Or what if you have other clients to support, like Swift clients on iOS or Java clients on Android?

▪ That’s where typed, code-generated APIs come in. They come in a lot of flavors, each with libraries available in a bunch of languages (including TypeScript)—for example:

▪ Swagger for RESTful APIs

▪ Apollo and Relay for GraphQL

▪ gRPC and Apache Thrift for RPC

▪ These tools rely on a common source of truth for both server and clients—data models for Swagger, GraphQL schemas for Apollo, Protocol Buffers for gRPC—which are then compiled into language-specific bindings for whatever language you might be using (in our case, that’s TypeScript).

▪ This code generation is what prevents your client and server (or multiple clients) from getting out of sync with each other; since every platform shares a common schema, you won’t run into the case where you updated your iOS app to support a field, but forgot to press Merge on your pull request to add server support for it.

▪ When you build an application that interacts with a database, you might start with raw SQL or API calls, which are inherently untyped:

▪ // PostgreSQL, using node-postgres
let client = new Client

▪ let res = await client.query(
'SELECT name FROM users where id = $1',
[739311]
) // any

▪ db.collection('users')
.find({id: 739311})
.toArray((err, user) =>
// user is any
)

▪ However, raw SQL APIs are still fairly low-level, and it’s still easy to use the wrong type, or forget a type and accidentally end up with anys.

▪ That’s where object-relational mappers (ORMs) come in. ORMs generate code from your database schema, giving you high-level APIs to express queries, updates, deletions, and so on.

▪ In statically typed languages, these APIs are typesafe, so you don’t have to worry about typing things correctly and manually binding generic type parameters.

▪ When accessing your database from TypeScript, consider using an ORM.

▪ At the time of writing, Umed Khudoiberdiev’s excellent TypeORM is the most complete ORM for TypeScript, and supports MySQL, PostgreSQL, Microsoft SQL Server, Oracle, and even MongoDB.

▪ Using TypeORM, your query to get a user’s first name might look like this:

let user = await UserRepository
.findOne({id: 739311}) // User | undefined

▪ Always use an ORM when working with databases—it’s more convenient

▪ In this chapter we’ve covered a lot: directly manipulating the DOM; using React and Angular

▪ adding type safety to your APIs with tools like Swagger, gRPC, and GraphQL; and using TypeORM to safely interact with your database.

▪ JavaScript frameworks change at a rapid pace, and by the time you read this, the specific APIs and frameworks described here may be on their way to becoming museum exhibits

▪ Use your newfound intuition for what problems typesafe frameworks solve to identify places where you can take advantage of someone else’s work to make your code safer, more abstract, and more modular.

▪ The big idea to take away from this chapter isn’t what the best framework to use in the year 2019 is, but what sorts of problems can be better solved with frameworks.

▪ With the combination of typesafe UI code, a typed API layer, and a typesafe backend, you can eliminate entire classes of bugs from your application, and sleep better at night as a result.

▪ When you write a program, you can express encapsulation at several levels. At the lowest level, functions encapsulate behaviors, and data structures like objects and lists encapsulate data. You might then group functions and data into classes, or keep them separate as namespaced utilities with a separate database or store for your data. A single class or a set of utilities per file is typical.

▪ Going up, you might group a few classes or utilities into a package, which you publish to NPM.

▪ When we talk about modules, it’s important to make a distinction between how the compiler (TSC) resolves modules, how your build system (Webpack, Gulp, etc.) resolves modules, and how modules are actually loaded into your application at runtime (
tags, SystemJS, etc.).

▪ The different ways to namespace and modularize your code

▪ The different ways to import and export code

▪ Scaling these approaches as your codebase grows

▪ In the beginning (in 1995), JavaScript didn’t support any sort of module system. Without modules, everything was declared in a global namespace, which made it really hard to build and scale applications.

▪ You could quickly run out of variable names, and run into collisions between variable names;

▪ without exposing explicit APIs for each module, it’s hard to know which parts of a module you’re supposed to use, and which parts are private implementation details.

▪ To help solve these problems, people simulated modules with either objects or Immediately Invoked Function Expressions (IIFEs), which they assigned to the global window, making them available to other modules in their application (and in other applications hosted on the same web page)

▪ Because loading and running JavaScript blocks the browser’s UI, as a web application grows and includes more and more lines of code, the user’s browser gets slower and slower. For this reason, clever programmers started dynamically loading JavaScript after the page loaded, rather than loading it all in one shot

▪ Nearly 10 years after JavaScript was first released, Dojo (Alex Russell, 2004), YUI (Thomas Sha, 2005), and LABjs (Kyle Simpson, 2009) shipped module loaders—ways to lazily (and often asynchronously) load JavaScript code after the initial page load has happened.

▪ Lazy and asynchronous module loading meant three things:

▪ Modules needed to be well encapsulated. Otherwise, a page might be broken while dependencies are streaming in.

▪ Dependencies between modules needed to be explicit. Otherwise, we don’t know which modules need to be loaded and in what order.

▪ Every module needed a unique identifier within the app. Otherwise, there’s no reliable way to specify what modules need to be loaded.

▪ Loading a module with LABjs looked like this:

$LAB
 .script('/emailBaseModule.js').wait()
 .script('/emailListModule.js')
 .script('/emailComposerModule.js')

▪ Around the same time, NodeJS (Ryan Dahl, 2009) was being developed, and its creators took a lesson from JavaScript’s growing pains and from other languages and decided to build a module system right into the platform.

▪ Like any good module system, it needed to satisfy the same three criteria as LABjs and YUI’s loaders. NodeJS did that with the CommonJS module standard, which looked like this:

// emailBaseModule.js
var emailList = require('emailListModule')

▪ In the meantime, on the web the AMD module standard (James Burke, 2008)—pushed by Dojo and RequireJS—was taking off.

▪ It supported an equivalent set of functionality, and came with its own build system for bundling up JavaScript code:

define('emailBaseModule',
 ['require', 'exports', 'emailListModule', 'emailComposerModule'],
 function(require, exports, emailListModule, emailComposerModule) {
 exports.renderBase = function() {
 // ...
 }
 }
)

▪ A few years after that, Browserify came out (James Halliday, 2011), giving frontend engineers the ability to use CommonJS on the frontend, too. CommonJS became the de facto standard for module bundling and import/export syntax.

▪ There were a few problems with the CommonJS way of doing things. Among them, require calls are necessarily synchronous, and the CommonJS module resolution algorithm is not ideal for use on the web.

▪ On top of that, code that uses it isn’t statically analyzable in some cases (as a TypeScript programmer, this should perk your ears up), because module.exports can appear anywhere (even in dead code branches that are never actually reached) and require calls can appear anywhere and contain arbitrary strings and expressions, making it impossible to statically link a JavaScript program, and verify that all referenced files really exist and export what they say they export.

▪ Against this backdrop, ES2015—the sixth edition of the ECMAScript language—introduced a new standard for imports and exports that had a clean syntax and was statically analyzable. It looks like this:

// emailBaseModule.js
import emailList from 'emailListModule'

▪ This is the standard we use in JavaScript and TypeScript code today. However, at the time of writing the standard isn’t yet natively supported in every JavaScript runtime, so we have to compile it down to a format that is supported (CommonJS for NodeJS environments, globals or a module-loadable format for browser environments).

▪ Unless you’re being chased by wolves, you should use ES2015 imports and exports in your TypeScript code, rather than using CommonJS, global, or namespaced modules

▪ And because types and values live in separate namespaces, it’s perfectly fine to export two things—one at the value level and one at the type level—that share the same name. Like for any other code, TypeScript will infer whether you meant the type or the value when you actually use it:

▪ As your application gets bigger, its time to initial render will get worse and worse. This is especially a problem for frontend applications where the network can be a bottleneck, but it also applies to backend applications that take more time to start up as you import more code at the top level—code that needs to be loaded from the filesystem, parsed, compiled, and evaluated, all while blocking other code from running.

▪ On the frontend, one way to deal with this problem (besides writing less code!) is with code splitting: chunking your code up into a bunch of generated JavaScript files, instead of shipping everything in a single large file. With splitting you get the benefit of loading multiple chunks in parallel, which eases the toll of large network requests (see Figure 10-1).

▪ A further optimization is to lazy-load chunks of code when they’re actually needed. Really large frontend applications—like those at Facebook and Google—use this type of optimization as a matter of course. Without it, clients might be loading gigabytes of JavaScript code on the initial page load, which could take minutes or hours (not to mention that people would probably stop using those services once they received their mobile bills).

▪ LABjs and its siblings introduced the concept of lazy-loading code when you actually need it, and the concept was formalized in dynamic imports. It looks like this:

let locale = await import('locale_us-en')

▪ You can use import either as a statement to statically pull in code (as we’ve used it up to this point), or as a function that returns a Promise for your module (as we did in this example).

▪ While you can pass an arbitrary expression that evaluates to a string to import, you lose type safety when you do.

▪ To safely use dynamic imports, be sure to either:

▪ Pass a string literal directly to import, without assigning the string to a variable first.

▪ Pass an expression to import and manually annotate the module’s signature.

▪ If using the second option, a common pattern is to statically import the module, but use it only in a type position, so that TypeScript compiles away the static import (to learn more, see “The types Directive”).

▪ We imported locale from ./locales/locale-us, but we only used it for its type, which we retrieved with typeof locale

▪ We needed to do that because TypeScript couldn’t statically look up the type of import(path), because path is a computed variable and not a static string. Because we never used locale as a value, and instead just scavenged it for its type, TypeScript compiled away the static import

▪ TypeScript supports dynamic imports in esnext module mode only. To use dynamic imports, set {"module": "esnext"}
in your tsconfig.json’s compilerOptions.

▪ By default, CommonJS default exports don’t interoperate with ES2015 default imports; to use a default export, you have to use a wildcard import:

import * as fs from 'fs'
fs.readFile('some/file.txt')

▪ To interoperate more smoothly, set {"esModuleInterop": true}
in your tsconfig.json’s compilerOptions.

▪ As I mentioned at the top of the chapter, even though this code compiles, that doesn’t mean it’ll work at runtime. Whichever module standard you use—import/export, CommonJS, AMD, UMD, or browser globals—your module bundler and module loader have to be aware of that format so they can package up and split your code correctly at compile time, and load your code correctly at runtime.

▪ TypeScript parses each of your TypeScript files in one of two modes: module mode or script mode

▪ It decides which mode to use based on a single heuristic: does your file have any imports or exports? If so, it uses module mode; otherwise, it uses script mode.

▪ In script mode, any top-level variables you declare will be available to other files in your project without an explicit import, and you can safely consume global exports from third-party UMD modules without explicitly importing them first.

▪ A couple of use cases for script mode are:

▪ To quickly prototype browser code that you plan to compile to no module system at all ({"module": "none"}
in your tsconfig.json) and include as raw <script />
tags in your HTML file.

▪ To create type declarations (see “Type Declarations”)

▪ You’ll almost always want to stick to module mode, which TypeScript will choose for you automatically as you write real-world code that imports other code and exports things for other files to use.

▪ TypeScript gives us another way to encapsulate code: the namespace keyword. Namespaces will feel familiar to a lot of Java, C#, C++, PHP, and Python programmers.

▪ If you’re coming from a language with namespaces, note that although namespaces are supported by TypeScript, they’re not the preferred way to encapsulate code; if you’re not sure whether to use namespaces or modules, choose modules.

▪ A namespace must have a name (like Network), and it can export functions, variables, types, interfaces, or other namespaces. Any code in a namespace block that’s not explicitly exported is private to the block.

▪ Like interfaces, namespaces can be augmented, making it convenient to split them across files. TypeScript will recursively merge identically named namespaces for us:

▪ If you end up with long namespace hierarchies, you can use aliases to shorten them for convenience

▪ Note that despite the similar syntax, destructuring (like you do when importing ES2015 modules) is not supported for aliases:

▪ Collisions between identically named exports are not allowed:

▪ Unlike imports and exports, namespaces don’t respect your tsconfig.json’s module setting, and always compile to global variables.

▪ Flowers is declared within an IIFE—a function that calls itself immediately—to create a closure and prevent variables that weren’t explicitly exported from leaking out of the Flowers module.

▪ Prefer regular modules (the import and export kind) over namespaces as a way to more closely stick to JavaScript standards and make your dependencies more explicit.

▪ Explicit dependencies have lots of benefits for readability, enforcing module isolation (because namespaces are automatically merged, but modules are not), and static analysis, which matters for big frontend projects where stripping out dead code and splitting your compiled code into multiple files is crucial for performance.

▪ So far we’ve touched on three types of merging that TypeScript does for us:

▪ Merging values and types, so that the same name can refer to either a value or a type depending how we use it (see “Companion Object Pattern”)

▪ Merging multiple namespaces into one

▪ Merging multiple interfaces into one (see “Declaration Merging”)

▪ This means that if, for example, you declare a value and a type alias in the same scope, TypeScript will allow it, and infer which one you meant—the type or the value—from whether you use the name in a value or a type position

▪ Eagle-eyed readers may notice the moduleResolution flag available in their tsconfig.json. This flag controls the algorithm TypeScript uses to resolve module names in your application. The flag supports two modes:

▪ node: Always use this mode. It resolves modules using the same algorithm that NodeJS uses. Modules prefixed with a ., /, or ~ (like ./my/file) are resolved from the local filesystem, either relative to the current file, or using an absolute path (relative to your / directory, or whatever your tsconfig.json’s baseUrl is set to), depending on the prefix you use. TypeScript loads module paths that don’t have a prefix from your node modules folder, the same as NodeJS.

▪ TypeScript builds on NodeJS’s resolution strategy in two ways:

▪ In addition to the main field in a package’s package.json that NodeJS looks at to find the default importable file in a directory, TypeScript also looks at the TypeScript-specific types property (more on that in “Type Lookup for JavaScript”).

▪ When importing a file with an unspecified extension, TypeScript first looks for a file with that name and a .ts extension, followed by .tsx, .d.ts, and finally .js.

▪ classic: You should never use this mode. In this mode, relative paths are resolved like in node mode, but for unprefixed names, TypeScript will look for a file with the given name in the current folder, then walk up the directory tree a folder at a time until it finds a matching file. This is really surprising behavior for anyone coming from the NodeJS or JavaScript world, and does not interoperate well with other build tools.

▪ In this chapter we covered TypeScript’s module system, starting with a brief history of JavaScript module systems, ES2015 modules and safely lazy-loading code with dynamic imports, interoperating with CommonJS and AMD modules, and module mode versus script mode

▪ We then covered namespaces, namespace merging, and how TypeScript’s declaration merging works.

▪ Most of us are in this boat: though once in a while you’ll have the leeway to start a greenfield project in TypeScript, most of the time it will start as a little island of safety, embedded in a larger, less safe codebase

▪ Either way, you will probably start with an island of TypeScript in a type-less sea.

▪ So far in this book I’ve been teaching you to write TypeScript the right way. This chapter is about writing TypeScript the practical way, in real codebases that are in the process of migrating away from untyped languages, that use third-party JavaScript libraries, that at times sacrifice type safety for a quick hot patch to unbreak prod.

▪ Using type declarations

▪ Gradually migrating from JavaScript to TypeScript

▪ Using third-party JavaScript and TypeScript

▪ A type declaration is a file with the extension .d.ts. Along with JSDoc annotations (see “Step 2b: Add JSDoc Annotations (Optional)”), it’s a way to attach TypeScript types to JavaScript code that would otherwise be untyped.

▪ Type declarations have a similar syntax to regular TypeScript, with a few differences:

▪ Type declarations can only contain types, and can’t contain values. That means no function, class, object, or variable implementations, and no default values for parameters.

▪ While type declarations can’t define values, they can declare that there exists a value defined somewhere in your JavaScript. We use the special declare keyword for this.

▪ Type declarations only declare types for things that are visible to consumers. We don’t include things like types that aren’t exported, or types for local variables inside of function bodies.

▪ Let’s jump into an example, and take a look at a piece of TypeScript (.ts) code and its equivalent type declaration (.d.ts).

▪ Notice the declare keyword before class. We can’t actually define a class in a type declaration, but we can declare that we defined a class in the .d.ts file’s corresponding JavaScript file

▪ Think of declare like an affirmation: “I swear that my JavaScript exports a class of this type.”

▪ Notice how Observable.d.ts is just Observable.ts, minus the implementations. In other words, it’s just the types from Observable.ts.

▪ Think about it: if the authors of RxJS wanted to package in typing information on NPM for their TypeScript-wielding users (RxJS can be used in both TypeScript and JavaScript applications), they would have two options: package both source TypeScript files (for TypeScript users) and compiled JavaScript files (for JavaScript users), or ship compiled JavaScript files along with type declarations for TypeScript users

▪ The latter reduces the file size, and makes it unambiguous what the correct import to use is. It also helps keep compile times for your application fast, since your TSC instance doesn’t have to recompile RxJS every time you compile your own app (in fact, it’s the reason the optimization strategy we introduce in “Project References” works!).

▪ Type declaration files have a few uses:

▪ When someone else uses your compiled TypeScript from their TypeScript application, their TSC instance will look for .d.ts files corresponding to your generated JavaScript files. This tells TypeScript what the types are for your project.

▪ Code editors with TypeScript support (like VSCode) will read these .d.ts files to give your users helpful type hints as they type, even if they don’t use TypeScript.

▪ They speed up compile times significantly by avoiding unnecessarily re-compiling your TypeScript code.

▪ A type declaration is a way to tell TypeScript, “There exists this thing that’s defined in JavaScript, and I’m going to describe it to you.”

▪ When we talk about type declarations, we often call them ambient in order to differentiate them from regular declarations that contain values;

▪ for example, an ambient variable declaration uses the declare keyword to declare that a variable is defined somewhere in JavaScript, while a regular nonambient variable declaration is a normal let or const declaration that declares a variable without using the declare keyword.

▪ You can use type declarations for a few things:

▪ To tell TypeScript about a global variable that’s defined in JavaScript somewhere. For example, if you polyfilled the Promise global or defined process.env in a browser environment, you might use an ambient variable declaration to give TypeScript a heads-up.

▪ To define a type that’s globally available everywhere in your project, so to use it you don’t have to import it first (we call this an ambient type declaration).

▪ To tell TypeScript about a third-party module that you installed with NPM (an ambient module declaration).

▪ A type declaration, regardless of what you’re using it for, has to live in a script-mode .ts or .d.ts file (recall our earlier discussion of script mode in “Module Mode Versus Script Mode”)

▪ By convention, we give our file a .d.ts extension if it has a corresponding .js file; otherwise, we use a .ts extension.

▪ It doesn’t matter what you call the file—for example, I like to stick to a single top-level types.ts until it gets unwieldy—and a single type declaration file can contain as many type declarations as you want.

▪ Finally, while top-level values in a type declaration file need the declare keyword (declare let
, declare function
, declare class
, and so on), top-level types and interfaces do not.

▪ An ambient variable declaration is a way to tell TypeScript about a global variable that can be used in any .ts or .d.ts file in your project without explicitly importing it first.

▪ So you create a new file, polyfills.ts, and define a global process.env:

process = {
 env: {
 NODE_ENV: 'production'
 }
}

Of course, TypeScript then comes to the rescue, throwing a red squiggly at you to try to save you from the mistake you’re clearly making by augmenting the window global:

Error TS2304: Cannot find name 'process'.

▪ But in this case, TypeScript is being overprotective. You really do want to augment window, and you want to do it safely.

▪ declare let process: {
 env: {
 NODE_ENV: 'development' | 'production'
 }
}

▪ You’re declaring to TypeScript that there’s a global object process that has a single property env, that has a property NODE_ENV. Once you tell TypeScript about that, the red squiggly disappears and you can safely define your process global.

▪ TypeScript comes with a set of type declarations for describing the JavaScript standard library that includes built-in JavaScript types, like Array and Promise, and methods on built-in types, like ''.toUpperCase. It also includes global objects like window and document (in a browser environment), and onmessage (in a Web Worker environment).

▪ You can pull in TypeScript’s built-in type declarations using your tsconfig.json’s lib field.

▪ Ambient type declarations follow the same rules as ambient variable declarations: the declaration has to live in a script-mode .ts or .d.ts file, and it’ll be available globally to the other files in your project without an explicit import

▪ For example, let’s declare a global utility type ToArray<T> that lifts T to an array, if it isn’t an array already.

▪ We can define this type in any script-mode file in our project—for this example, let’s define it in a top-level types.ts file:

type ToArray<T> = T extends unknown[] ? T : T[]

▪ We can now use this type from any project file, without an explicit import:

▪ Consider using ambient type declarations to model data types that are used throughout your application. For example, you might use them to make the UserID type we developed in “Simulating Nominal Types” globally available:

type UserID = string & {readonly brand: unique symbol}

▪ Now, you can use UserID anywhere in your application without having to explicitly import it first.

▪ When you consume a JavaScript module and want to quickly declare some types for it so you can use it safely—without having to contribute the type declarations back to the JavaScript module’s GitHub repository or DefinitelyTyped first—ambient module declarations are the tool to use.

▪ An ambient module declaration is a regular type declaration, surrounded by a special declare module
syntax:

declare module 'module-name' {
 export type MyType = number
 export type MyDefaultType = {a: string}
 export let myExport: MyType
 let myDefaultExport: MyDefaultType
 export default myDefaultExport
}

▪ A module name ('module-name' in this example) corresponds to an exact import path. When you import that path, your ambient module declaration tells TypeScript what’s available:

import ModuleName from 'module-name'
ModuleName.a // string

▪ If you have a nested module, make sure you include the whole import path in its declaration:

declare module '@most/core' {
 // Type declaration
}

▪ If you just want to quickly tell TypeScript “I’m importing this module—I’ll type it later, just assume it’s an any for now,” keep the header but omit the actual declaration:

// Declare a module that can be imported, where each of its imports are any
declare module 'unsafe-module-name'

▪ Now if you consume this module, it’s less safe:

import {x} from 'unsafe-module-name'
x // any

▪ Module declarations support wildcard imports, so you can give a type to any import path that matches the given pattern. Use a wildcard (*) to match an import path:1

// Type JSON files imported with Webpack's json-loader
declare module 'json!*' {
 let value: object
 export default value
}

▪ // Type CSS files imported with Webpack's style-loader
declare module '*.css' {
 let css: CSSRuleList
 export default css
}

▪ Now, you can load JSON and CSS files:

import a from 'json!myFile'
a // object

import b from './widget.css'
b // CSSRuleList

▪ For the last two examples to work, you’ll need to configure your build system to load .json and .css files. You can declare to TypeScript that these path patterns are safe to import, but TypeScript won’t be able to build them by itself.

▪ TypeScript was designed with JavaScript interoperability in mind, not as an afterthought. So while it’s not painless, migrating to TypeScript is a good experience, letting you convert your codebase over a file at a time, opting into stricter levels of safety as you migrate, showing your boss and your coworkers just how impactful statically typing your code can be, one commit at a time.

▪ Any bugs that could be caught at compile time are, and TypeScript’s rich autocompletion halves the time it takes to write each line of code.

▪ You might have to take a few baby steps to get there:

▪ When working on a codebase that combines TypeScript and JavaScript, start by letting TSC compile JavaScript files alongside your TypeScript. In your tsconfig.json:

{
 "compilerOptions": {
 "allowJs": true
}

▪ With allowJs set to true, TypeScript won’t typecheck your existing JavaScript code, but it will transpile it (to ES3, ES5, or whatever target is set to in your tsconfig.json) using the module system you asked for (in your tsconfig.json’s module field).

▪ Enable this in your tsconfig.json:


{
 "compilerOptions": {
 "allowJs": true,
 "checkJs": true
}

▪ Now, whenever TypeScript compiles a JavaScript file it’ll do its best to infer types and typecheck as it goes, like it does for regular TypeScript code.

▪ If your codebase is big and flipping on checkJs reports too many type errors at once, turn it off, and instead enable checking for a JavaScript file at a time by adding the // @ts-check
directive (a regular comment at the top of the file).

▪ Or, if a few big files are throwing the bulk of your errors and you don’t want to fix them just yet, keep checkJs on and add the // @ts-nocheck
directive to just those files.

▪ Because TypeScript can’t infer everything (e.g., function parameter types), it will infer a lot of types in your JavaScript code as any. If you have strict mode enabled in your tsconfig.json (you should!), you may want to temporarily allow implicit anys while you migrate.

▪ In your tsconfig.json, add:


{
 "compilerOptions": {
 "allowJs": true,
 "checkJs": true,
 "noImplicitAny": false
}

▪ When TypeScript runs over JavaScript code, it uses a more lenient inference algorithm than it does for TypeScript code.

▪ All function parameters are optional.

▪ The types of properties on functions and classes are inferred from usage (rather than having to be declared up front):

▪ Until you get a chance to convert that file to TypeScript, you can use a JSDoc annotation to type your new function.

▪ You’ve probably seen JSDoc before; it’s those funny-looking comments above some JavaScript and TypeScript code with @-annotations like @param, @returns, and so on.

▪ TypeScript understands JSDoc, and uses it as input to its typechecker the same way that it uses explicit type annotations in TypeScript code.

▪ Head over to the TypeScript Wiki to learn more about supported JSDoc annotations.

▪ As soon as you rename a file in your code editor, you’ll see your friends the red squigglies appear (the TypeError, not the kids’ TV show), uncovering type errors, missed cases, forgotten null checks, and misspelled variable names.

▪ Because TypeScript is a gradually typed language, it’s built from the ground up to interoperate with untyped JavaScript code as safely as possible. Regardless of whether you’re interoperating strictly typed TypeScript with untyped JavaScript or strictly typed TypeScript with loosely typed TypeScript, TypeScript will do its best to make sure that you’re doing it as safely as possible, and that on the strictly typed island that you’ve so carefully built, everything is as safe as it can be.

▪ Finally, you can disable TSC’s JavaScript interoperability flags, enforcing that all of your code is written in strictly typed TypeScript:


{
 "compilerOptions": {
 "allowJs": false,
 "checkJs": false
}

▪ When you import a JavaScript file from a TypeScript file, TypeScript follows an algorithm that looks like this to look up type declarations for your JavaScript code (remember that “file” and “module” are interchangeable when we talk about TypeScript):4

▪ Look for a sibling .d.ts file with the same name as your .js file. If it exists, use it as the type declaration for the .js file.

▪ Otherwise, if allowJs and checkJs are true, infer the .js file’s types (informed by any JSDoc annotations in the .js file).

▪ Otherwise, treat the whole module as an any.

▪ When importing a third-party JavaScript module—that is, an NPM package that you installed to node modules—TypeScript uses a slightly different algorithm:

▪ Look for a local type declaration for the module. If it exists, use it.

▪ For example, say your app’s folder structure looks like this:

my-app/
├──node_modules/
│ └──foo/
├──src/
│ ├──index.ts
│ └──types.d.ts

And types.d.ts looks like this:

// types.d.ts
declare module 'foo' {
 let bar: {}
 export default bar
}

If you then import foo, TypeScript will use the ambient module declaration in types.d.ts as the source of types for foo:

// index.ts
import bar from 'foo'

▪ Otherwise, look at the module’s package.json. If it defines a field called types or typings, use the .d.ts file that field points to as the source of type declarations for the module.

▪ Otherwise, traverse out a directory at a time, and look for a node modules/@types directory that has type declarations for the module.

▪ Otherwise, proceed to steps 1–3 of the local type lookup algorithm.

▪ By default, TypeScript looks in node modules/@types in your project’s folder and containing folders (../node modules/@types and so on) for third-party type declarations. Most of the time, you want to leave this behavior as is.

▪ To override this default behavior for global type declarations, configure typeRoots in your tsconfig.json with an array of folders to look in for type declarations. For example, you can tell TypeScript to look for type declarations in the typings folder as well as node modules/@types:

{
 "compilerOptions": {
 "typeRoots" : ["./typings", "./node modules/@types"]
 }
}

▪ For even more granular control, use the types option in your tsconfig.json to specify which packages you want TypeScript to look up types for. For example, the following config ignores all third-party type declarations except the ones for React:

{
 "compilerOptions": {
 "types" : ["react"]
 }
}

▪ When you npm install
third-party JavaScript code into your project, there are three possible scenarios:

▪ The code you installed comes with type declarations out of the box.

▪ The code you installed doesn’t come with type declarations, but declarations are available on DefinitelyTyped.

▪ The code you installed doesn’t come with type declarations, and declarations are not available on DefinitelyTyped.

▪ You know that a package comes with type declarations out of the box if you import it with {"noImplicitAny": true}
and TypeScript doesn’t throw a red squiggly at you.

▪ Unless the code you’re installing was actually compiled from TypeScript, you always run the risk that the type declarations it comes with don’t match up to the code those declarations describe. When type declarations come packaged with source code the risk of this happening is pretty low (especially for popular packages), but it’s something to be aware of.

▪ Even if the third-party code you’re importing doesn’t come with type declarations, declarations for it are probably available on DefinitelyTyped, TypeScript’s community-maintained, centralized repository for ambient module declarations for open source projects.

▪ To check if the package you installed has type declarations available on DefinitelyTyped, either search on TypeSearch or just try installing the declarations

▪ All DefinitelyTyped type declarations are published to NPM under the @types scope, so you can just npm install
from that scope:

▪ npm install lodash --save # Install Lodash
npm install @types/lodash --save-dev # Install type declarations for Lodash

▪ Most of the time, you’ll want to use npm install
’s --save-dev flag to add your installed type declarations to your package.json’s devDependencies field.

▪ Whitelist the specific import by adding a // @ts-ignore
directive above your untyped import. TypeScript will let you use the untyped module, but the module and all of its contents will be typed as any:

// @ts-ignore
import Unsafe from 'untyped-module'

▪ Whitelist all usages of this module by creating an empty type declaration file and stubbing out the module. For example, if you installed the rarely used package nearby-ferret-alerter, you could make a new type declaration (e.g., types.d.ts) and add to it the ambient type declaration:

// types.d.ts
declare module 'nearby-ferret-alerter'

▪ Now, fill in the type declaration. For example, the result might look like this:

// types.d.ts
declare module 'nearby-ferret-alerter' {
 export default function alert(loudness: 'soft' | 'loud'): Promise<void>
 export function getFerretCount(): Promise<number>
}

▪ If you got as far as the third option and now have a local type declaration for your module, consider contributing it back to NPM so the next person that needs type declarations for the awesome nearby-ferret-alerter package can use it too. To do this you can either submit a pull request to the nearby-ferret-alerter Git repository and contribute the type declarations directly, or, if the maintainers of that repository don’t want to be on the hook for maintaining TypeScript type declarations, contribute your declarations to DefinitelyTyped instead.

▪ Automatically generating type declarations for untyped JavaScript is an active area of research. Check out dts-gen for a way to automatically generate type declaration scaffolding for any third-party JavaScript module.

▪ Ways to use JavaScript from TypeScript

▪ Import untyped JavaScript　{"allowJs": true}
Poor　

▪ Import and check JavaScript　{"allowJs": true, "checkJs": true}
OK　

▪ Import and check JSDoc-annotated JavaScript　{"allowJs": true, "checkJs": true, "strict": true}
Excellent　

▪ Import JavaScript with type declarations　{"allowJs": false, "strict": true}
Excellent　

▪ Import TypeScript　{"allowJs": false, "strict": true}
Excellent　

▪ Interoperating with JavaScript can be one of the trickiest aspects of TypeScript

▪ Wildcard matching with * follows the same rules as regular glob pattern matching.

▪ DefinitelyTyped is the open source repository for JavaScript type declarations

▪ If you’ve deployed and run a JavaScript application in production, then you know how to run a TypeScript application too—once you compile it to JavaScript, the two aren’t so different

▪ This chapter is about productionizing and building TypeScript applications, but there isn’t much here that’s unique to TypeScript apps—it mostly applies to JavaScript applications too.

▪ I suggest keeping your source TypeScript code in a top-level src/ folder, and compiling it to a top-level dist/ folder. This folder structure is a popular convention, and splitting your source code and generated code into two top-level folders can make your life easier down the line, when you’re integrating with other tooling.

▪ It also makes it easier to exclude generated artifacts from source control.

▪ Try to stick to this convention when you can:

my-app/
├──dist/
│ ├──index.d.ts
│ ├──index.js
│ └──services/
│ ├──foo.d.ts
│ ├──foo.js
│ ├──bar.d.ts
│ └──bar.js
├──src/
│ ├──index.ts
│ └──services/
│ ├──foo.ts
│ └──bar.ts

▪ When you compile a TypeScript program to JavaScript, there are a few different artifacts that TSC can generate for you (Table 12-1).

▪ The second type of artifact—source maps—is special files that link each piece of your generated JavaScript back to the specific line and column of the TypeScript file that it was generated from

▪ The third artifact—type declarations—lets other TypeScript projects take advantage of your generated types.

▪ JavaScript can be an unusual language to work with: not only does it have a quickly evolving specification with a yearly release cycle, but, as a programmer, you can’t always control which JavaScript version the platform you’re running your program on implements.

▪ On top of that, many JavaScript programs are isomorphic, meaning you can run them on either the server or the client.

▪ If you run your backend JavaScript program on a server that you control, then you can control exactly which JavaScript version it will run on.

▪ If you then release your backend JavaScript program as an open source project, you don’t know which JavaScript version will be supported by your consumers’ JavaScript platforms.

▪ The best you can do in a NodeJS environment is declare a range of supported NodeJS versions, but in a browser environment you’re out of luck.

▪ If you run your JavaScript in a browser, you have no idea which browser people will use to run it—the latest Chrome, Firefox, or Edge that supports most modern JavaScript features, a slightly outdated version of one of those browsers that’s missing some bleeding-edge functionality, an antiquated browser like Internet Explorer 8, or an embedded browser like the one that runs on the PlayStation 4 in your garage.

▪ The best you can do is define a minimum set of features that people’s browsers need to support to run your application, ship polyfills for as many of those features as you can, and try to detect when users are on really old browsers that your app won’t run on and show them a message saying that they need to upgrade.

▪ If you release an isomorphic JavaScript library (e.g., a logging library that runs on both browser and server), then you have to support both a minimum NodeJS version and a swath of browser JavaScript engines and versions.

▪ Not every JavaScript environment supports every JavaScript feature out of the box, but you should still try to write code in the latest language version.

▪ There are two ways to do this:

▪ Transpile (i.e., automatically convert) applications from the latest version of JavaScript to the oldest JavaScript version that a platform you target supports. We do this for language features like for..of loops and async/await, which can be automatically converted to for loops and .then calls, respectively.

▪ Polyfill (i.e., provide implementations for) any modern features that are missing in the JavaScript runtime you’re running on. We do this for features provided by the JavaScript standard library (like Promise, Map, and Set) and for prototype methods (like Array.prototype.includes and Function.prototype.bind).

▪ TSC has built-in support for transpiling your code to older JavaScript versions, but it will not automatically polyfill your code.

▪ target sets the JavaScript version you want to transpile to: es5, es2015, etc.

▪ module sets the module system you want to target: es2015 modules, commonjs modules, systemjs modules, etc.

▪ lib tells TypeScript which JavaScript features are available in the environments you’re targeting: es5 features, es2015 features, the dom, etc. It doesn’t actually implement these features—that’s what polyfills are for—but it does tell TypeScript that the features are available (either natively or via a polyfill).

▪ In the past, there was a new revision of the JavaScript language released every few years, with an incrementing language version (ES1, ES3, ES5, ES6). As of 2015, the JavaScript language now has a yearly release cycle, with each language version named after the year it’s released in (ES2015, ES2016, and so on).

▪ Some JavaScript features, however, get TypeScript support before they’re actually slated for a specific JavaScript version; we refer to these features as “ESNext” (as in, the next revision).

▪ es3 for ECMAScript 3

es5 for ECMAScript 5 (this is a good default if you’re not sure what to use)

es6 or es2015 for ECMAScript 2015

▪ es2016 for ECMAScript 2016

es2017 for ECMAScript 2017

es2018 for ECMAScript 2018

▪ esnext for whatever the most recent ECMAScript revision is

▪ As I mentioned, there’s one hitch with transpiling your code to older JavaScript versions: while most language features can be safely transpiled (let to var, class to function), you still need to polyfill functionality yourself if your target environment doesn’t support a newer library feature.

▪ Some examples are utilities like Promise and Reflect, and data structures like Map, Set, and Symbol.

▪ When targeting a bleeding-edge environment like the latest Chrome, Firefox, or Edge, you usually won’t need any polyfills; but if you’re targeting browsers a few versions back—or most NodeJS environments—you will need to polyfill missing features.

▪ Thankfully, you won’t need to write polyfills yourself. Instead, you can install them from a popular polyfill library like core-js, or add polyfills to your code automatically by running your typechecked TypeScript code through Babel with @babel/polyfill.

▪ If you plan to run your application in a browser, be careful not to bloat the size of your JavaScript bundle by including every single polyfill regardless of whether or not the browser you’re running your code in actually needs it—your target platform probably already supports some of the features you’re polyfilling.

▪ Instead, use a service like Polyfill.io to load just those polyfills that your user’s browser needs.

▪ Once you’ve added polyfills to your code, it’s time to tell TSC that your environment is guaranteed to support the features you polyfilled—enter your tsconfig.json’s lib field. For example, you could use this configuration if you’ve polyfilled all ES2015 features plus ES2016’s Array.prototype.includes:

{
 "compilerOptions": {
 "lib": ["es2015", "es2016.array.includes"]
 }
}

▪ If you’re running your code in the browser, also enable DOM type declarations for things like window, document, and all the other APIs you get when running your JavaScript in the browser:


{
 "compilerOptions": {
 "lib": ["es2015", "es2016.array.include", "dom"]
 }
}

▪ For a full list of supported libs run tsc --help

▪ Source maps are a way to link your transpiled code back to the source code it was generated from. Most developer tools (like Chrome DevTools), error reporting and logging frameworks, and build tools know about source maps
