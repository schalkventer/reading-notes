Eloquent JavaScript, 3rd Edition: A Modern Introduction to Programming (2018)

 Marijn Haverbeke

---

▪ This is a book about instructing computers. Computers are about as common as screwdrivers today, but they are quite a bit more complex, and making them do what you want them to do isn’t always easy.

▪ If the task you have for your computer is a common, well-understood one, such as showing you your email or acting like a calculator, you can open the appropriate application and get to work. But for unique or open-ended tasks, there probably is no application.

▪ That is where programming may come in. Programming is the act of constructing a program—a set of precise instructions telling a computer what to do. Because computers are dumb, pedantic beasts, programming is fundamentally tedious and frustrating.

▪ Fortunately, if you can get over that fact, and maybe even enjoy the rigor of thinking in terms that dumb machines can deal with, programming can be rewarding. It allows you to do things in seconds that would take forever by hand. It is a way to make your computer tool do things that it couldn’t do before. And it provides a wonderful exercise in abstract thinking.

▪ Most programming is done with programming languages. A programming language is an artificially constructed language used to instruct computers.

▪ It is interesting that the most effective way we’ve found to communicate with a computer borrows so heavily from the way we communicate with each other. Like human languages, computer languages allow words and phrases to be combined in new ways, making it possible to express ever new concepts.

▪ At one point language-based interfaces, such as the BASIC and DOS prompts of the 1980s and 1990s, were the main method of interacting with computers. They have largely been replaced with visual interfaces, which are easier to learn but offer less freedom

▪ One such language, JavaScript, is built into every modern web browser and is thus available on almost every device.

▪ Programming, it turns out, is hard. The fundamental rules are simple and clear, but programs built on top of these rules tend to become complex enough to introduce their own rules and complexity. You’re building your own maze, in a way, and you might just get lost in it.

▪ Much of this material will then be combined in ways that require you to make additional connections.

▪ A program is many things. It is a piece of text typed by a programmer, it is the directing force that makes the computer do what it does, it is data in the computer’s memory, yet it controls the actions performed on this same memory

▪ Analogies that try to compare programs to objects we are familiar with tend to fall short. A superficially fitting one is that of a machine—lots of separate parts tend to be involved, and to make the whole thing tick, we have to consider the ways in which these parts interconnect and contribute to the operation of the whole.

▪ Computers themselves can do only stupidly straightforward things. The reason they are so useful is that they do these things at an incredibly high speed. A program can ingeniously combine an enormous number of these simple actions to do very complicated things.

▪ A program is a building of thought. It is costless to build, it is weightless, and it grows easily under our typing hands.

But without care, a program’s size and complexity will grow out of control, confusing even the person who created it.

▪ Keeping programs under control is the main problem of programming.

▪ The art of programming is the skill of controlling complexity.

▪ The field of programming is young and still developing rapidly, and it is varied enough to have room for wildly different approaches.

▪ There are many terrible mistakes to make in program design, and you should go ahead and make them so that you understand them. A sense of what a good program looks like is developed in practice, not learned from a list of rules.

▪ 00110001 00000000 00000000
00110001 00000001 00000001
00110011 00000001 00000010
01010001 00001011 00000010
00100010 00000010 00001000
01000011 00000001 00000000
01000001 00000001 00000001
00010000 00000010 00000000
01100010 00000000 00000000

▪ That is a program to add the numbers from 1 to 10 together and print out the result: 1 + 2 + ... + 10 = 55

▪ To program early computers, it was necessary to set large arrays of switches in the right position or punch holes in strips of cardboard and feed them to the computer.

▪ Each line of the previous program contains a single instruction. It could be written in English like this:

▪ Store the number 0 in memory location 0.

Store the number 1 in memory location 1.

Store the value of memory location 1 in memory location 2.

Subtract the number 11 from the value in memory location 2.

If the value in memory location 2 is the number 0, continue with instruction 9.

Add the value of memory location 1 to memory location 0.

Add the number 1 to the value of memory location 1.

Continue with instruction 3.

Output the value of memory location 0.

▪ Here is the same program in JavaScript:

let total = 0, count = 1;
while (count total += count;
count += 1;
}
console.log(total);
// → 55

▪ Finally, here is what the program could look like if we happened to have the convenient operations range and sum available, which respectively create a collection of numbers within a range and compute the sum of a collection of numbers:

console.log(sum(range(1, 10)));
// → 55

▪ A good programming language helps the programmer by allowing them to talk about the actions that the computer has to perform on a higher level.

▪ It helps omit details, provides convenient building blocks (such as while and console.log), allows you to define your own building blocks (such as sum and range), and makes those blocks easy to compose.

▪ JavaScript was introduced in 1995 as a way to add programs to web pages in the Netscape Navigator browser.

▪ It has made modern web applications possible—applications with which you can interact directly without doing a page reload for every action.

▪ It is important to note that JavaScript has almost nothing to do with the programming language named Java. The similar name was inspired by marketing considerations rather than good judgment. When JavaScript was being introduced, the Java language was being heavily marketed and was gaining popularity. Someone thought it was a good idea to try to ride along on this success. Now we are stuck with the name.

▪ After its adoption outside of Netscape, a standard document was written to describe the way the JavaScript language should work so that the various pieces of software that claimed to support JavaScript were actually talking about the same language. This is called the ECMAScript standard, after the Ecma International organization that did the standardization.

▪ In practice, the terms ECMAScript and JavaScript can be used interchangeably—they are two names for the same language.

▪ There are those who will say terrible things about JavaScript. Many of these things are true

▪ JavaScript is ridiculously liberal in what it allows. The idea behind this design was that it would make programming in JavaScript easier for beginners. In actuality, it mostly makes finding problems in your programs harder because the system will not point them out to you.

▪ This flexibility also has its advantages, though. It leaves space for a lot of techniques that are impossible in more rigid languages, and as you will see (for example in Chapter 10), it can be used to overcome some of JavaScript’s shortcomings

▪ After learning the language properly and working with it for a while, I have learned to actually like JavaScript.

▪ ECMAScript version 3 was the widely supported version in the time of JavaScript’s ascent to dominance, roughly between 2000 and 2010

▪ During this time, work was underway on an ambitious version 4, which planned a number of radical improvements and extensions to the language. Changing a living, widely used language in such a radical way turned out to be politically difficult, and work on the version 4 was abandoned in 2008, leading to a much less ambitious version 5, which made only some uncontroversial improvements, coming out in 2009.

▪ Then in 2015 version 6 came out, a major update that included some of the ideas planned for version 4. Since then we’ve had new, small updates every year.

▪ Web browsers are not the only platforms on which JavaScript is used. Some databases, such as MongoDB and CouchDB, use JavaScript as their scripting and query language. Several platforms for desktop and server programming, most notably the Node.js project (the subject of Chapter 20), provide an environment for programming JavaScript outside of the browser.

▪ Code is the text that makes up programs

▪ I believe reading code and writing code are indispensable parts of learning to program. Try to not just glance over the examples—read them attentively and understand them. This may be slow and confusing at first, but I promise that you’ll quickly get the hang of it.

▪ The language part of the book starts with four chapters that introduce the basic structure of the JavaScript language. They introduce control structures (such as the while word you saw in this introduction), functions (writing your own building blocks), and data structures.

▪ Next, Chapters 5 and 6 introduce techniques to use functions and objects to write more abstract code and keep complexity under control.

▪ Inside the computer’s world, there is only data. You can read data, modify data, create new data—but that which isn’t data cannot be mentioned

▪ Bits are any kind of two-valued things, usually described as zeros and ones. Inside the computer, they take forms such as a high or low electrical charge, a strong or weak signal, or a shiny or dull spot on the surface of a CD. Any piece of discrete information can be reduced to a sequence of zeros and ones and thus represented in bits.

▪ Here are the bits that make up the number 13, with the weights of the digits shown below them:

0 0 0 0 1 1 0 1
128 64 32 16 8 4 2 1

▪ So that’s the binary number 00001101. Its non-zero digits stand for 8, 4, and 1, and add up to 13.

▪ A typical modern computer has more than 30 billion bits in its volatile data storage (working memory). Nonvolatile storage (the hard disk or equivalent) tends to have yet a few orders of magnitude more.

▪ To be able to work with such quantities of bits without getting lost, we must separate them into chunks that represent pieces of information. In a JavaScript environment, those chunks are called values

▪ Values of the number type are, unsurprisingly, numeric values. In a JavaScript program, they are written as follows:

13

▪ JavaScript uses a fixed number of bits, 64 of them, to store a single number value. There are only so many patterns you can make with 64 bits, which means that the number of different numbers that can be represented is limited.

▪ Those bits also store negative numbers, so one bit indicates the sign of the number. A bigger issue is that nonwhole numbers must also be represented. To do this, some of the bits are used to store the position of the decimal point.

▪ The actual maximum whole number that can be stored is more in the range of 9 quadrillion (15 zeros)—which is still pleasantly huge.

▪ For very big or very small numbers, you may also use scientific notation by adding an e (for exponent), followed by the exponent of the number.

2.998e8

▪ Calculations with whole numbers (also called integers) smaller than the aforementioned 9 quadrillion are guaranteed to always be precise

▪ Unfortunately, calculations with fractional numbers are generally not. Just as π (pi) cannot be precisely expressed by a finite number of decimal digits, many numbers lose some precision when only 64 bits are available to store them.

▪ This is a shame, but it causes practical problems only in specific situations. The important thing is to be aware of it and treat fractional digital numbers as approximations, not as precise values.

▪ Arithmetic operations such as addition or multiplication take two number values and produce a new number from them.

▪ The + and * symbols are called operators

▪ As you might have guessed, the multiplication happens first. But as in mathematics, you can change this by wrapping the addition in parentheses.

(100 + 4) * 11

▪ When operators appear together without parentheses, the order in which they are applied is determined by the precedence of the operators

▪ The % symbol is used to represent the remainder operation. X % Y
is the remainder of dividing X by Y.

▪ There are three special values in JavaScript that are considered numbers but don’t behave like normal numbers

▪ The first two are Infinity and -Infinity, which represent the positive and negative infinities.

▪ NaN stands for “not a number”, even though it is a value of the number type. You’ll get this result when you, for example, try to calculate 0 / 0
(zero divided by zero), Infinity - Infinity
, or any number of other numeric operations that don’t yield a meaningful result.

▪ The next basic data type is the string. Strings are used to represent text. They are written by enclosing their content in quotes

▪ You can use single quotes, double quotes, or backticks to mark strings, as long as the quotes at the start and the end of the string match

▪ When an n character occurs after a backslash, it is interpreted as a newline. Similarly, a t after a backslash means a tab character.

▪ Strings, too, have to be modeled as a series of bits to be able to exist inside the computer. The way JavaScript does this is based on the Unicode standard. This standard assigns a number to virtually every character you would ever need, including characters from Greek, Arabic, Japanese, Armenian, and so on. If we have a number for every character, a string can be described by a sequence of numbers.

▪ Operators that use two values are called binary operators, while those that take one are called unary operators.

▪ The minus operator can be used both as a binary operator and as a unary operator.

▪ Strings can be compared in the same way.

console.log("Aardvark" < "Zoroaster")
// → true

▪ The way strings are ordered is roughly alphabetic but not really what you’d expect to see in a dictionary: uppercase letters are always “less” than lowercase ones, so "Z" < "a"
, and nonalphabetic characters (!, -, and so on) are also included in the ordering. When comparing strings, JavaScript goes over the characters from left to right, comparing the Unicode codes one by one.

▪ There is only one value in JavaScript that is not equal to itself, and that is NaN (“not a number”).

▪ NaN is supposed to denote the result of a nonsensical computation, and as such, it isn’t equal to the result of any other nonsensical computations.

▪ operators we have seen so far, || has the lowest precedence, then comes &&, then the comparison operators (>, ==, and so on), and then the rest.

▪ The last logical operator I will discuss is not unary, not binary, but ternary, operating on three values. It is written with a question mark and a colon

▪ This one is called the conditional operator (or sometimes just the ternary operator since it is the only such operator in the language

▪ There are two special values, written null and undefined, that are used to denote the absence of a meaningful value. They are themselves values, but they carry no information

▪ Many operations in the language that don’t produce a meaningful value (you’ll see some later) yield undefined simply because they have to yield some value

▪ The difference in meaning between undefined and null is an accident of JavaScript’s design, and it doesn’t matter most of the time. In cases where you actually have to concern yourself with these values, I recommend treating them as mostly interchangeable.

▪ In the Introduction, I mentioned that JavaScript goes out of its way to accept almost any program you give it, even programs that do odd things.

▪ When an operator is applied to the “wrong” type of value, JavaScript will quietly convert that value to the type it needs, using a set of rules that often aren’t what you want or expect. This is called type coercion.

▪ When something that doesn’t map to a number in an obvious way (such as "five" or undefined) is converted to a number, you get the value NaN

▪ Further arithmetic operations on NaN keep producing NaN, so if you find yourself getting one of those in an unexpected place, look for accidental type conversions.

▪ But when the types differ, JavaScript uses a complicated and confusing set of rules to determine what to do. In most cases, it just tries to convert one of the values to the other value’s type.

▪ Expressions like 0 == false
and "" == false
are also true because of automatic type conversion

▪ The same goes for false && X
, which is false and will ignore X. This is called short-circuit evaluation.

▪ In this chapter, we will start to do things that can actually be called programming. We will expand our command of the JavaScript language beyond the nouns and sentence fragments we’ve seen so far, to the point where we can express meaningful prose

▪ A fragment of code that produces a value is called an expression

▪ Every value that is written literally (such as 22 or "psychoanalysis") is an expression. An expression between parentheses is also an expression, as is a binary operator applied to two expressions or a unary operator applied to one.

▪ This shows part of the beauty of a language-based interface. Expressions can contain other expressions in a way similar to how subsentences in human languages are nested—a subsentence can contain its own subsentences, and so on. This allows us to build expressions that describe arbitrarily complex computations.

▪ If an expression corresponds to a sentence fragment, a JavaScript statement corresponds to a full sentence. A program is a list of statements.

▪ The simplest kind of statement is an expression with a semicolon after it. This is a program:

1;
!false;

▪ It is a useless program, though

▪ A statement stands on its own, so it amounts to something only if it affects the world

▪ These changes are called side effects. The statements in the previous example just produce the values 1 and true and then immediately throw them away. This leaves no impression on the world at all. When you run this program, nothing observable happens.

▪ In some cases, JavaScript allows you to omit the semicolon at the end of a statement. In other cases, it has to be there, or the next line will be treated as part of the same statement. The rules for when it can be safely omitted are somewhat complex and error-prone. So in this book, every statement that needs a semicolon will always get one

▪ To catch and hold values, JavaScript provides a thing called a binding, or variable:

let caught = 5 * 5;

▪ After a binding has been defined, its name can be used as an expression. The value of such an expression is the value the binding currently holds.

▪ You should imagine bindings as tentacles, rather than boxes. They do not contain values; they grasp them—two bindings can refer to the same value

▪ A single let statement may define multiple bindings. The definitions must be separated by commas.

let one = 1, two = 2;

▪ Binding names can be any word. Digits can be part of binding names—catch22 is a valid name, for example—but the name must not start with a digit. A binding name may include dollar signs ($) or underscores (_) but no other punctuation or special characters.

▪ Words with a special meaning, such as let, are keywords, and they may not be used as binding names

▪ There are also a number of words that are “reserved for use” in future versions of JavaScript, which also can’t be used as binding names.

▪ The full list of keywords and reserved words is rather long.

▪ Don’t worry about memorizing this list. When creating a binding produces an unexpected syntax error, see whether you’re trying to define a reserved word.

▪ The collection of bindings and their values that exist at a given time is called the environment

▪ When a program starts up, this environment is not empty. It always contains bindings that are part of the language standard, and most of the time, it also has bindings that provide ways to interact with the surrounding system

▪ Executing a function is called invoking, calling, or applying it. You can call a function by putting parentheses after an expression that produces a function value.

▪ The values between the parentheses are given to the program inside the function. In the example, the prompt function uses the string that we give it as the text to show in the dialog box.

▪ Values given to functions are called arguments.

▪ The prompt function isn’t used much in modern web programming, mostly because you have no control over the way the resulting dialog looks, but can be helpful in toy programs and experiments.

▪ Showing a dialog box or writing text to the screen is a side effect. A lot of functions are useful because of the side effects they produce

▪ Functions may also produce values, in which case they don’t need to have a side effect to be useful. For example, the function Math.max takes any amount of number arguments and gives back the greatest.

▪ When a function produces a value, it is said to return that value. Anything that produces a value is an expression in JavaScript, which means function calls can be used within larger expressions

▪ Not all programs are straight roads. We may, for example, want to create a branching road, where the program takes the proper branch based on the situation at hand. This is called conditional execution

▪ Conditional execution is created with the if keyword in JavaScript. In the simple case, we want some code to be executed if, and only if, a certain condition holds

▪ let theNumber = Number(prompt("Pick a number"));
if (!Number.isNaN(theNumber)) {
console.log("Your number is the square root of " +
theNumber * theNumber);
}

▪ The Number.isNaN function is a standard JavaScript function that returns true only if the argument it is given is NaN

▪ The Number function happens to return NaN when you give it a string that doesn’t represent a valid number

▪ The braces can be used to group any number of statements into a single statement, called a block.

▪ You often won’t just have code that executes when a condition holds true, but also code that handles the other case

▪ In the examples, I’ve been adding spaces in front of statements that are part of some larger statement. These spaces are not required—the computer will accept the program just fine without them. In fact, even the line breaks in programs are optional

▪ In code where new blocks are opened inside other blocks, it can become hard to see where one block ends and another begins. With proper indentation, the visual shape of a program corresponds to the shape of the blocks inside it.

▪ I like to use two spaces for every open block, but tastes differ—some people use four spaces, and some people use tab characters. The important thing is that each new block adds the same amount of space.

▪ Because this pattern is so common, JavaScript and similar languages provide a slightly shorter and more comprehensive form, the for loop.

▪ Having the looping condition produce false is not the only way a loop can finish. There is a special statement called break that has the effect of immediately jumping out of the enclosing loop.

▪ If you were to remove that break statement or you accidentally write an end condition that always produces true, your program would get stuck in an infinite loop. A program stuck in an infinite loop will never finish running, which is usually a bad thing.

▪ The continue keyword is similar to break, in that it influences the progress of a loop. When continue is encountered in a loop body, control jumps out of the body and continues with the loop’s next iteration.

▪ JavaScript provides a shortcut for this.

counter += 1;

Similar shortcuts work for many other operators, such as result *= 2
to double result or counter -= 1
to count downward.

▪ There is a construct called switch that is intended to express such a “dispatch” in a more direct way

▪ Unfortunately, the syntax JavaScript uses for this (which it inherited from the C/Java line of programming languages) is somewhat awkward—a chain of if statements may look better

▪ In some cases, such as the "sunny" case in the example, this can be used to share some code between cases (it recommends going outside for both sunny and cloudy weather). But be careful—it is easy to forget such a break, which will cause the program to execute code you do not want executed.

▪ Binding names may not contain spaces, yet it is often helpful to use multiple words to clearly describe what the binding represents

▪ The standard JavaScript functions, and most JavaScript programmers, follow the bottom style—they capitalize every word except the first. It is not hard to get used to little things like that, and code with mixed naming styles can be jarring to read, so we follow this convention.

▪ In a few cases, such as the Number function, the first letter of a binding is also capitalized. This was done to mark this function as a constructor

▪ A comment is a piece of text that is part of a program but is completely ignored by the computer

▪ You now know that a program is built out of statements, which themselves sometimes contain more statements. Statements tend to contain expressions, which themselves can be built out of smaller expressions.

▪ Putting statements after one another gives you a program that is executed from top to bottom. You can introduce disturbances in the flow of control by using conditional (if, else, and switch) and looping (while, do, and for) statements.

▪ Bindings can be used to file pieces of data under a name, and they are useful for tracking state in your program

▪ The environment is the set of bindings that are defined.

▪ JavaScript systems always put a number of useful standard bindings into your environment.

▪ Functions are special values that encapsulate a piece of program. You can invoke them by writing functionName(argument1, argument2)

▪ Such a function call is an expression and may produce a value.

▪ FizzBuzz

Write a program that uses console.log to print all the numbers from 1 to 100, with two exceptions. For numbers divisible by 3, print "Fizz" instead of the number, and for numbers divisible by 5 (and not 3), print "Buzz" instead.

When you have that working, modify your program to print "FizzBuzz" for numbers that are divisible by both 3 and 5 (and still print "Fizz" or "Buzz" for numbers divisible by only one of those).

▪ Functions are the bread and butter of JavaScript programming. The concept of wrapping a piece of program in a value has many uses. It gives us a way to structure larger programs, to reduce repetition, to associate names with subprograms, and to isolate these subprograms from each other.

▪ Typical adult English speakers have some 20,000 words in their vocabulary. Few programming languages come with 20,000 commands built in. And the vocabulary that is available tends to be more precisely defined, and thus less flexible, than in human language. Therefore, we usually have to introduce new concepts to avoid repeating ourselves too much.

▪ Some functions produce a value, such as power and square, and some don’t, such as makeNoise, whose only result is a side effect. A return statement determines the value the function returns

▪ A return keyword without an expression after it will cause the function to return undefined. Functions that don’t have a return statement at all, such as makeNoise, similarly return undefined.

▪ Parameters to a function behave like regular bindings, but their initial values are given by the caller of the function, not the code in the function itself.

▪ Every time the function is called, new instances of these bindings are created. This provides some isolation between functions—each function call acts in its own little world (its local environment) and can often be understood without knowing a lot about what’s going on in the global environment.

▪ JavaScript distinguishes not just global and local bindings. Blocks and functions can be created inside other blocks and functions, producing multiple degrees of locality.

▪ This approach to binding visibility is called lexical scoping.

▪ A function value can do all the things that other values can do—you can use it in arbitrary expressions, not just call it. It is possible to store a function value in a new binding, pass it as an argument to a function, and so on. Similarly, a binding that holds a function is still just a regular binding and can, if not constant, be assigned a new value, like so:

▪ When the function keyword is used at the start of a statement, it works differently.

▪ This is a function declaration.

▪ The preceding code works, even though the function is defined below the code that uses it. Function declarations are not part of the regular top-to-bottom flow of control. They are conceptually moved to the top of their scope and can be used by all the code in that scope.

▪ This is sometimes useful because it offers the freedom to order code in a way that seems meaningful, without worrying about having to define all functions before they are used.

▪ When there is only one parameter name, you can omit the parentheses around the parameter list.

▪ If the body is a single expression, rather than a block in braces, that expression will be returned from the function.

▪ When an arrow function has no parameters at all, its parameter list is just an empty set of parentheses.

▪ Arrow functions were added in 2015, mostly to make it possible to write small function expressions in a less verbose way.

▪ Because a function has to jump back to the place that called it when it returns, the computer must remember the context from which the call happened

▪ The place where the computer stores this context is the call stack.

▪ Every time a function is called, the current context is stored on top of this stack. When a function returns, it removes the top context from the stack and uses that context to continue execution.

▪ Storing this stack requires space in the computer’s memory. When the stack grows too big, the computer will fail with a message like “out of stack space” or “too much recursion”.

▪ We defined square with only one parameter. Yet when we call it with three, the language doesn’t complain. It ignores the extra arguments and computes the square of the first one.

▪ JavaScript is extremely broad-minded about the number of arguments you pass to a function. If you pass too many, the extra ones are ignored. If you pass too few, the missing parameters get assigned the value undefined.

▪ The downside of this is that it is possible—likely, even—that you’ll accidentally pass the wrong number of arguments to functions. And no one will tell you about it.

▪ The upside is that this behavior can be used to allow a function to be called with different numbers of arguments. For example, this minus function tries to imitate the - operator by acting on either one or two arguments:

function minus(a, b) {
if (b === undefined) return -a;
else return a - b;
}

console.log(minus(10));
// → -10
console.log(minus(10, 5));
// → 5

▪ If you write an = operator after a parameter, followed by an expression, the value of that expression will replace the argument when it is not given.

▪ For example, this version of power makes its second argument optional. If you don’t provide it or pass the value undefined, it will default to two, and the function will behave like square.

▪ The ability to treat functions as values, combined with the fact that local bindings are re-created every time a function is called, brings up an interesting question. What happens to local bindings when the function call that created them is no longer active?

▪ This feature—being able to reference a specific instance of a local binding in an enclosing scope—is called closure. A function that references bindings from local scopes around it is called a closure. This behavior not only frees you from having to worry about lifetimes of bindings but also makes it possible to use function values in some creative ways.

▪ With a slight change, we can turn the previous example into a way to create functions that multiply by an arbitrary amount.

function multiplier(factor) {
return number => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// → 10

▪ The explicit local binding from the wrapValue example isn’t really needed since a parameter is itself a local binding.

▪ Thinking about programs like this takes some practice. A good mental model is to think of function values as containing both the code in their body and the environment in which they are created. When called, the function body sees the environment in which it was created, not the environment in which it is called.

▪ In the example, multiplier is called and creates an environment in which its factor parameter is bound to 2. The function value it returns, which is stored in twice, remembers this environment. So when that is called, it multiplies its argument by 2.

▪ A function that calls itself is called recursive. Recursion allows some functions to be written in a different style. Take, for example, this alternative implementation of power:

function power(base, exponent) {
if (exponent == 0) {
return 1;
} else {
return base * power(base, exponent - 1);
}
}

console.log(power(2, 3));
// → 8

▪ This is rather close to the way mathematicians define exponentiation and arguably describes the concept more clearly than the looping variant. The function calls itself multiple times with ever smaller exponents to achieve the repeated multiplication.

▪ But this implementation has one problem: in typical JavaScript implementations, it’s about three times slower than the looping version. Running through a simple loop is generally cheaper than calling a function multiple times.

▪ The dilemma of speed versus elegance is an interesting one. You can see it as a kind of continuum between human-friendliness and machine-friendliness. Almost any program can be made faster by making it bigger and more convoluted. The programmer has to decide on an appropriate balance.

▪ In the case of the power function, the inelegant (looping) version is still fairly simple and easy to read. It doesn’t make much sense to replace it with the recursive version. Often, though, a program deals with such complex concepts that giving up some efficiency in order to make the program more straightforward is helpful.

▪ Worrying about efficiency can be a distraction. It’s yet another factor that complicates program design, and when you’re doing something that’s already difficult, that extra thing to worry about can be paralyzing.

▪ Therefore, always start by writing something that’s correct and easy to understand. If you’re worried that it’s too slow—which it usually isn’t since most code simply isn’t executed often enough to take any significant amount of time—you can measure afterward and improve it if necessary.

▪ Recursion is not always just an inefficient alternative to looping. Some problems really are easier to solve with recursion than with loops. Most often these are problems that require exploring or processing several “branches”, each of which might branch out again into even more branches.

▪ The indentation indicates the depth of the call stack.

▪ The first is that you find yourself writing similar code multiple times. You’d prefer not to do that. Having more code means more space for mistakes to hide and more material to read for people trying to understand the program. So you take the repeated functionality, find a good name for it, and put it into a function.

▪ The second way is that you find you need some functionality that you haven’t written yet and that sounds like it deserves its own function. You’ll start by naming the function, and then you’ll write its body. You might even start writing code that uses the function before you actually define the function itself.

▪ How difficult it is to find a good name for a function is a good indication of how clear a concept it is that you’re trying to wrap

▪ It works! But that name, printZeroPaddedWithLabel, is a little awkward. It conflates three things—printing, zero-padding, and adding a label—into a single function.

Instead of lifting out the repeated part of our program wholesale, let’s try to pick out a single concept.

▪ A function with a nice, obvious name like zeroPad makes it easier for someone who reads the code to figure out what it does

▪ How smart and versatile should our function be? We could write anything, from a terribly simple function that can only pad a number to be three characters wide to a complicated generalized number-formatting system that handles fractional numbers, negative numbers, alignment of decimal dots, padding with different characters, and so on.

▪ A useful principle is to not add cleverness unless you are absolutely sure you’re going to need it. It can be tempting to write general “frameworks” for every bit of functionality you come across. Resist that urge. You won’t get any real work done—you’ll just be writing code that you never use.

▪ Functions can be roughly divided into those that are called for their side effects and those that are called for their return value. (Though it is definitely also possible to both have side effects and return a value.)

▪ A pure function is a specific kind of value-producing function that not only has no side effects but also doesn’t rely on side effects from other code—for example, it doesn’t read global bindings whose value might change

▪ A pure function has the pleasant property that, when called with the same arguments, it always produces the same value (and doesn’t do anything else). A call to such a function can be substituted by its return value without changing the meaning of the code

▪ When you are not sure that a pure function is working correctly, you can test it by simply calling it and know that if it works in that context, it will work in any context. Nonpure functions tend to require more scaffolding to test.

▪ Still, there’s no need to feel bad when writing functions that are not pure or to wage a holy war to purge them from your code. Side effects are often useful. There’d be no way to write a pure version of console.log, for example, and console.log is good to have.

▪ Some operations are also easier to express in an efficient way when we use side effects, so computing speed can be a reason to avoid purity.

▪ You can get the Nth character, or letter, from a string by writing "string"[N]. The returned value will be a string containing only one character (for example, "b"). The first character has position 0, which causes the last one to be found at position string.length - 1
. In other words, a two-character string has length 2, and its characters have positions 0 and 1.

▪ Write a function countBs that takes a string as its only argument and returns a number that indicates how many uppercase “B” characters there are in the string.

▪ On two occasions I have been asked, ‘Pray, Mr. Babbage, if you put into the machine wrong figures, will the right answers come out?’ [...] I am not able rightly to apprehend the kind of confusion of ideas that could provoke such a question.

Charles Babbage, Passages from the Life of a Philosopher (1864)

▪ Numbers, Booleans, and strings are the atoms that data structures are built from. Many types of information require more than one atom, though. Objects allow us to group values—including other objects—to build more complex structures.

▪ The programs we have built so far have been limited by the fact that they were operating only on simple data types. This chapter will introduce basic data structures. By the end of it, you’ll know enough to start writing useful programs.

▪ Fortunately, JavaScript provides a data type specifically for storing sequences of values. It is called an array and is written as a list of values between square brackets, separated by commas.

▪ Zero-based counting has a long tradition in technology and in certain ways makes a lot of sense, but it takes some getting used to. Think of the index as the amount of items to skip, counting from the start of the array.

▪ Almost all JavaScript values have properties. The exceptions are null and undefined. If you try to access a property on one of these nonvalues, you get an error.

null.length;
// → TypeError: null has no properties

▪ When using a dot, the word after the dot is the literal name of the property. When using square brackets, the expression between the brackets is evaluated to get the property name.

▪ Whereas value.x fetches the property of value named “x”, value[x] tries to evaluate the expression x and uses the result, converted to a string, as the property name.

▪ They can be any string, but the dot notation works only with names that look like valid binding names. So if you want to access a property named 2 or John Doe, you must use square brackets: value[2] or value["John Doe"]

▪ The elements in an array are stored as the array’s properties, using numbers as property names. Because you can’t use the dot notation with numbers and usually want to use a binding that holds the index anyway, you have to use the bracket notation to get at them.

▪ This property name is a valid binding name, and we know its name in advance, so to find the length of an array, you typically write array.length because that’s easier to write than array["length"].

▪ Interestingly, even though the call to toUpperCase does not pass any arguments, the function somehow has access to the string "Doh", the value whose property we called. How this works is described in Chapter 6.

▪ Properties that contain functions are generally called methods of the value they belong to, as in “toUpperCase is a method of a string”.

▪ These somewhat silly names are the traditional terms for operations on a stack. A stack, in programming, is a data structure that allows you to push values into it and pop them out again in the opposite order so that the thing that was added last is removed first

▪ When an object is written over multiple lines, indenting it like in the example helps with readability

▪ Properties whose names aren’t valid binding names or valid numbers have to be quoted.

▪ This means that braces have two meanings in JavaScript. At the start of a statement, they start a block of statements. In any other position, they describe an object

▪ It is possible to assign a value to a property expression with the = operator. This will replace the property’s value if it already existed or create a new property on the object if it didn’t.

▪ The binary in operator, when applied to a string and an object, tells you whether that object has a property with that name

▪ The difference between setting a property to undefined and actually deleting it is that, in the first case, the object still has the property (it just doesn’t have a very interesting value), whereas in the second case the property is no longer present and in will return false.

▪ To find out what properties an object has, you can use the Object.keys function. You give it an object, and it returns an array of strings—the object’s property names.

▪ There’s an Object.assign function that copies all properties from one object into another.

▪ Arrays, then, are just a kind of object specialized for storing sequences of things.

▪ The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all immutable—it is impossible to change values of those types. You can combine them and derive new values from them, but when you take a specific string value, that value will always remain the same.

▪ Comparing different objects will return false, even if they have identical properties.

▪ There is no “deep” comparison operation built into JavaScript, which compares objects by contents, but it is possible to write it yourself (which is one of the exercises at the end of this chapter).

▪ Note that the object added to the journal looks a little odd. Instead of declaring properties like events: events
, it just gives a property name. This is shorthand that means the same thing—if a property name in brace notation isn’t followed by a value, its value is taken from the binding with the same name

▪ Arrays have an includes method that checks whether a given value exists in the array. The function uses that to determine whether the event name it is interested in is part of the event list for a given day.

▪ This kind of loop is common in classical JavaScript—going over arrays one element at a time is something that comes up a lot, and to do that you’d run a counter over the length of the array and pick out each element in turn.

▪ By going over all the events and adding those that aren’t already in there to the events array, the function collects every type of event.

▪ To search for a specific value, arrays provide an indexOf method. The method searches through the array from the start to the end and returns the index at which the requested value was found—or -1 if it wasn’t found. To search from the end instead of the start, there’s a similar method called lastIndexOf.

▪ Both indexOf and lastIndexOf take an optional second argument that indicates where to start searching.

▪ Another fundamental array method is slice, which takes start and end indices and returns an array that has only the elements between them. The start index is inclusive, the end index exclusive.

▪ When the end index is not given, slice will take all of the elements after the start index. You can also omit the start index to copy the entire array.

▪ The concat method can be used to glue arrays together to create a new array, similar to what the + operator does for strings.

▪ Values of type string, number, and Boolean are not objects, and though the language doesn’t complain if you try to set new properties on them, it doesn’t actually store those properties. As mentioned earlier, such values are immutable and cannot be changed.

▪ One difference is that a string’s indexOf can search for a string containing more than one character, whereas the corresponding array method looks only for a single element.

▪ When such a function is called, the rest parameter is bound to an array containing all further arguments. If there are other parameters before it, their values aren’t part of that array.

▪ This “spreads” out the array into the function call, passing its elements as separate arguments. It is possible to include an array like that along with other arguments, as in max(9, ...numbers, 2)

▪ Square bracket array notation similarly allows the triple-dot operator to spread another array into the new array.

▪ As we’ve seen, Math is a grab bag of number-related utility functions, such as Math.max (maximum), Math.min (minimum), and Math.sqrt (square root).

▪ The Math object is used as a container to group a bunch of related functionality. There is only one Math object, and it is almost never useful as a value. Rather, it provides a namespace so that all these functions and values do not have to be global bindings.

▪ If you need to do trigonometry, Math can help. It contains cos (cosine), sin (sine), and tan (tangent), as well as their inverse functions, acos, asin, and atan, respectively. The number π (pi)—or at least the closest approximation that fits in a JavaScript number—is available as Math.PI.

▪ There is an old programming tradition of writing the names of constant values in all caps.

▪ Though computers are deterministic machines—they always react the same way if given the same input—it is possible to have them produce numbers that appear random. To do that, the machine keeps some hidden value, and whenever you ask for a new random number, it performs complicated computations on this hidden value to create a new value. It stores a new value and returns some number derived from it. That way, it can produce ever new, hard-to-predict numbers in a way that seems random.

▪ Note that if you try to destructure null or undefined, you get an error, much as you would if you directly try to access a property of those values.

▪ Because properties only grasp their value, rather than contain it, objects and arrays are stored in the computer’s memory as sequences of bits holding the addresses—the place in memory—of their contents. So an array with another array inside of it consists of (at least) one memory region for the inner array, and another for the outer array, containing (among other things) a binary number that represents the position of the inner array.

▪ If you want to save data in a file for later or send it to another computer over the network, you have to somehow convert these tangles of memory addresses to a description that can be stored or sent

▪ What we can do is serialize the data. That means it is converted into a flat description. A popular serialization format is called JSON (pronounced “Jason”), which stands for JavaScript Object Notation. It is widely used as a data storage and communication format on the Web, even in languages other than JavaScript.

▪ JSON looks similar to JavaScript’s way of writing arrays and objects, with a few restrictions. All property names have to be surrounded by double quotes, and only simple data expressions are allowed—no function calls, bindings, or anything that involves actual computation. Comments are not allowed in JSON.

▪ JavaScript gives us the functions JSON.stringify and JSON.parse to convert data to and from this format. The first takes a JavaScript value and returns a JSON-encoded string. The second takes such a string and converts it to the value it encodes.

▪ Objects and arrays (which are a specific kind of object) provide ways to group several values into a single value

▪ There are some named properties in arrays, such as length and a number of methods. Methods are functions that live in properties and (usually) act on the value they are a property of.

▪ You can iterate over arrays using a special kind of for loop—for (let element of array)

▪ Thinking back to the notes about side effects and pure functions in the previous chapter, which variant do you expect to be useful in more situations? Which one runs faster?

▪ A common data structure is the list (not to be confused with array). A list is a nested set of objects, with the first object holding a reference to the second, the second to the third, and so on.

let list = {
value: 1,
rest: {
value: 2,
rest: {
value: 3,
rest: null
}
}
};

▪ But you have to take one silly exception into account: because of a historical accident, typeof null
also produces "object".

▪ A large program is a costly program, and not just because of the time it takes to build. Size almost always involves complexity, and complexity confuses programmers. Confused programmers, in turn, introduce mistakes (bugs) into programs. A large program then provides a lot of space for these bugs to hide, making them hard to find

▪ Abstraction

▪ In the context of programming, these kinds of vocabularies are usually called abstractions. Abstractions hide details and give us the ability to talk about problems at a higher (or more abstract) level.

▪ As an analogy, compare these two recipes for pea soup. The first one goes like this:

▪ Put 1 cup of dried peas per person into a container. Add water until the peas are well covered. Leave the peas in water for at least 12 hours. Take the peas out of the water and put them in a cooking pan. Add 4 cups of water per person. Cover the pan and keep the peas simmering for two hours. Take half an onion per person. Cut it into pieces with a knife. Add it to the peas. Take a stalk of celery per person. Cut it into pieces with a knife. Add it to the peas. Take a carrot per person. Cut it into pieces. With a knife! Add it to the peas. Cook for 10 more minutes.

▪ Per person: 1 cup dried split peas, half a chopped onion, a stalk of celery, and a carrot.

Soak peas for 12 hours. Simmer for 2 hours in 4 cups of water (per person). Chop and add vegetables. Cook for 10 more minutes.

▪ The second is shorter and easier to interpret. But you do need to understand a few more cooking-related words such as soak, simmer, chop, and, I guess, vegetable.

▪ It is a useful skill, in programming, to notice when you are working at too low a level of abstraction.

▪ Plain functions, as we’ve seen them so far, are a good way to build abstractions. But sometimes they fall short.

▪ We don’t have to pass a predefined function to repeat. Often, it is easier to create a function value on the spot instead.

▪ let labels = [];
repeat(5, i => {
labels.push(`Unit ${i + 1}`);
});
console.log(labels);

▪ In cases like this example, where the body is a single small expression, you could also omit the braces and write the loop on a single line.

▪ Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions

▪ Higher-order functions allow us to abstract over actions, not just values. They come in several forms. For example, we can have functions that create new functions.

▪ There is a built-in array method, forEach, that provides something like a for/of loop as a higher-order function.

▪ One area where higher-order functions shine is data processing

▪ Note how the filter function, rather than deleting elements from the existing array, builds up a new array with only the elements that pass the test. This function is pure. It does not modify the array it is given

▪ The map method transforms an array by applying a function to all of its elements and building a new array from the returned values

▪ Another common thing to do with arrays is to compute a single value from them. Our recurring example, summing a collection of numbers, is an instance of this.

▪ The higher-order operation that represents this pattern is called reduce (sometimes also called fold).

▪ The parameters to reduce are, apart from the array, a combining function and a start value.

▪ The standard array method reduce, which of course corresponds to this function, has an added convenience. If your array contains at least one element, you are allowed to leave off the start argument. The method will take the first element of the array as its start value and start reducing at the second element.

▪ Higher-order functions start to shine when you need to compose operations. As an example, let’s write code that finds the average year of origin for living and dead scripts in the data set.

▪ You can see it as a pipeline: we start with all scripts, filter out the living (or dead) ones, take the years from those, average them, and round the result.

You could definitely also write this computation as one big loop.

▪ In terms of what the computer is actually doing, these two approaches are also quite different. The first will build up new arrays when running filter and map, whereas the second computes only some numbers, doing less work. You can usually afford the readable approach, but if you’re processing huge arrays, and doing so many times, the less abstract style might be worth the extra speed.

▪ The some method is another higher-order function. It takes a test function and tells you whether that function returns true for any of the elements in the array.

▪ In Chapter 1 I mentioned that JavaScript strings are encoded as a sequence of 16-bit numbers. These are called code units. A Unicode character code was initially supposed to fit within such a unit (which gives you a little over 65,000 characters). When it became clear that wasn’t going to be enough, many people balked at the need to use more memory per character. To address these concerns, UTF-16, the format used by JavaScript strings, was invented. It describes most common characters using a single 16-bit code unit but uses a pair of two such units for others.

▪ UTF-16 is generally considered a bad idea today. It seems almost intentionally designed to invite mistakes. It’s easy to write programs that pretend code units and characters are the same thing. And if your language doesn’t use two-unit characters, that will appear to work just fine. But as soon as someone tries to use such a program with some less common Chinese characters, it breaks. Fortunately, with the advent of emoji, everybody has started using two-unit characters, and the burden of dealing with such problems is more fairly distributed.

▪ Unfortunately, obvious operations on JavaScript strings, such as getting their length through the length property and accessing their content using square brackets, deal only with code units.

▪ // Two emoji characters, horse and shoe
let horseShoe = "🐴👟";
console.log(horseShoe.length);
// → 4
console.log(horseShoe[0]);
// → (Invalid half-character)
console.log(horseShoe.charCodeAt(0));
// → 55357 (Code of the half-character)
console.log(horseShoe.codePointAt(0));
// → 128052 (Actual code for horse emoji)

▪ In the previous chapter, I mentioned that a for/of loop can also be used on strings. Like codePointAt, this type of loop was introduced at a time where people were acutely aware of the problems with UTF-16. When you use it to loop over a string, it gives you real characters, not code units.

▪ The filter method returns a new array containing only the elements that pass the predicate function.

▪ Implement every as a function that takes an array and a predicate function as parameters

▪ An abstract data type is realized by writing a special kind of program […] which defines the type in terms of the operations which can be performed on it.

Barbara Liskov, Programming with Abstract Data Types

▪ Chapter 4 introduced JavaScript’s objects. In programming culture, we have a thing called object-oriented programming, a set of techniques that use objects (and related concepts) as the central principle of program organization.

▪ Though no one really agrees on its precise definition, object-oriented programming has shaped the design of many programming languages, including JavaScript

▪ The core idea in object-oriented programming is to divide programs into smaller pieces and make each piece responsible for managing its own state

▪ Different pieces of such a program interact with each other through interfaces, limited sets of functions or bindings that provide useful functionality at a more abstract level, hiding their precise implementation.

▪ Such program pieces are modeled using objects. Their interface consists of a specific set of methods and properties. Properties that are part of the interface are called public. The others, which outside code should not be touching, are called private.

▪ Many languages provide a way to distinguish public and private properties and prevent outside code from accessing the private ones altogether. JavaScript, once again taking the minimalist approach, does not—not yet at least. There is work underway to add this to the language.

▪ Separating interface from implementation is a great idea. It is usually called encapsulation.

▪ Usually a method needs to do something with the object it was called on. When a function is called as a method—looked up as a property and immediately called, as in object.method()—the binding called this in its body automatically points at the object that it was called on.

▪ You can think of this as an extra parameter that is passed in a different way. If you want to pass it explicitly, you can use a function’s call method, which takes the this value as its first argument and treats further arguments as normal parameters.

▪ Since each function has its own this binding, whose value depends on the way it is called, you cannot refer to the this of the wrapping scope in a regular function defined with the function keyword.

▪ Arrow functions are different—they do not bind their own this but can see the this binding of the scope around them

▪ Thus, you can do something like the following code, which references this from inside a local function:

function normalize() {
console.log(this.coords.map(n => n / this.length));
}
normalize.call({coords: [0, 2, 3], length: 5});
// → [0, 0.4, 0.6]

▪ If I had written the argument to map using the function keyword, the code wouldn’t work.

▪ In addition to their set of properties, most objects also have a prototype. A prototype is another object that is used as a fallback source of properties

▪ When an object gets a request for a property that it does not have, its prototype will be searched for the property, then the prototype’s prototype, and so on.

▪ So who is the prototype of that empty object? It is the great ancestral prototype, the entity behind almost all objects, Object.prototype.

▪ console.log(Object.getPrototypeOf({}) ==
Object.prototype);
// → true

▪ console.log(Object.getPrototypeOf(Object.prototype));
// → null

▪ As you guess, Object.getPrototypeOf returns the prototype of an object.

▪ The prototype relations of JavaScript objects form a tree-shaped structure, and at the root of this structure sits Object.prototype. It provides a few methods that show up in all objects, such as toString, which converts an object to a string representation

▪ Many objects don’t directly have Object.prototype as their prototype but instead have another object that provides a different set of default properties. Functions derive from Function.prototype, and arrays derive from Array.prototype.

▪ Such a prototype object will itself have a prototype, often Object.prototype, so that it still indirectly provides methods like toString.

▪ You can use Object.create to create an object with a specific prototype.

▪ The “proto” rabbit acts as a container for the properties that are shared by all rabbits. An individual rabbit object, like the killer rabbit, contains properties that apply only to itself—in this case its type—and derives shared properties from its prototype

▪ Classes

▪ JavaScript’s prototype system can be interpreted as a somewhat informal take on an object-oriented concept called classes

▪ Such an object is called an instance of the class.

▪ So to create an instance of a given class, you have to make an object that derives from the proper prototype, but you also have to make sure it, itself, has the properties that instances of this class are supposed to have. This is what a constructor function does.

▪ JavaScript provides a way to make defining this type of function easier. If you put the keyword new in front of a function call, the function is treated as a constructor

▪ function Rabbit(type) {
this.type = type;
}
Rabbit.prototype.speak = function(line) {
console.log(`The ${this.type} rabbit says '${line}'`);
};

let weirdRabbit = new Rabbit("weird");

▪ Constructors (all functions, in fact) automatically get a property named prototype, which by default holds a plain, empty object that derives from Object.prototype. You can overwrite it with a new object if you want. Or you can add properties to the existing object, as the example does.

▪ By convention, the names of constructors are capitalized so that they can easily be distinguished from other functions

▪ It is important to understand the distinction between the way a prototype is associated with a constructor (through its prototype property) and the way objects have a prototype (which can be found with Object.getPrototypeOf). The actual prototype of a constructor is Function.prototype since constructors are functions. Its prototype property holds the prototype used for instances created through it.

▪ So JavaScript classes are constructor functions with a prototype property. That is how they work, and until 2015, that was how you had to write them. These days, we have a less awkward notation

▪ The class keyword starts a class declaration, which allows us to define a constructor and a set of methods all in a single place. Any number of methods may be written inside the declaration’s braces.

▪ The one named constructor is treated specially. It provides the actual constructor function, which will be bound to the name Rabbit. The others are packaged into that constructor’s prototype. Thus, the earlier class declaration is equivalent to the constructor definition from the previous section. It just looks nicer.

▪ When you add a property to an object, whether it is present in the prototype or not, the property is added to the object itself. If there was already a property with the same name in the prototype, this property will no longer affect the object, as it is now hidden behind the object’s own property.

▪ As the rabbit teeth example shows, overriding can be used to express exceptional properties in instances of a more generic class of objects, while letting the nonexceptional objects take a standard value from their prototype.

▪ Calling toString on an array gives a result similar to calling .join(",") on it—it puts commas between the values in the array. Directly calling Object.prototype.toString with an array produces a different string. That function doesn’t know about arrays, so it simply puts the word object and the name of the type between square brackets.

▪ A map (noun) is a data structure that associates values (the keys) with other values. For example, you might want to map names to ages. It is possible to use objects for this.

▪ Here, the object’s property names are the people’s names, and the property values are their ages. But we certainly didn’t list anybody named toString in our map. Yet, because plain objects derive from Object.prototype, it looks like the property is there.

▪ As such, using plain objects as maps is dangerous. There are several possible ways to avoid this problem. First, it is possible to create objects with no prototype. If you pass null to Object.create, the resulting object will not derive from Object.prototype and can safely be used as a map.

▪ Object property names must be strings. If you need a map whose keys can’t easily be converted to strings—such as objects—you cannot use an object as your map.

▪ Fortunately, JavaScript comes with a class called Map that is written for this exact purpose. It stores a mapping and allows any type of keys.

▪ The methods set, get, and has are part of the interface of the Map object. Writing a data structure that can quickly update and search a large set of values isn’t easy, but we don’t have to worry about that. Someone else did it for us, and we can go through this simple interface to use their work.

▪ If you do have a plain object that you need to treat as a map for some reason, it is useful to know that Object.keys returns only an object’s own keys, not those in the prototype

▪ As an alternative to the in operator, you can use the hasOwnProperty method, which ignores the object’s prototype.

▪ I mentioned that some of the standard prototypes define their own version of toString so they can create a string that contains more useful information than "[object Object]"

▪ This is a simple instance of a powerful idea. When a piece of code is written to work with objects that have a certain interface—in this case, a toString method—any kind of object that happens to support this interface can be plugged into the code, and it will just work.

▪ This technique is called polymorphism. Polymorphic code can work with values of different shapes, as long as they support the interface it expects.

▪ This is another case of polymorphism—such loops expect the data structure to expose a specific interface, which arrays and strings do. And we can also add this interface to our own objects! But before we can do that, we need to know what symbols are.

▪ It is possible for multiple interfaces to use the same property name for different things. For example, I could define an interface in which the toString method is supposed to convert the object into a piece of yarn. It would not be possible for an object to conform to both that interface and the standard use of toString.

▪ When I claimed that property names are strings, that wasn’t entirely accurate. They usually are, but they can also be symbols. Symbols are values created with the Symbol function. Unlike strings, newly created symbols are unique—you cannot create the same symbol twice.

▪ The string you pass to Symbol is included when you convert it to a string and can make it easier to recognize a symbol when, for example, showing it in the console. But it has no meaning beyond that—multiple symbols may have the same name.

▪ Being both unique and usable as property names makes symbols suitable for defining interfaces that can peacefully live alongside other properties, no matter what their names are.

▪ const toStringSymbol = Symbol("toString");
Array.prototype[toStringSymbol] = function() {
return `${this.length} cm of blue yarn`;
};

▪ The object given to a for/of loop is expected to be iterable. This means it has a method named with the Symbol.iterator symbol (a symbol value defined by the language, stored as a property of the Symbol function).

▪ When called, that method should return an object that provides a second interface, iterator. This is the actual thing that iterates. It has a next method that returns the next result. That result should be an object with a value property that provides the next value, if there is one, and a done property, which should be true when there are no more results and false otherwise.

▪ Note that the next, value, and done property names are plain strings, not symbols. Only Symbol.iterator, which is likely to be added to a lot of different objects, is an actual symbol.

▪ Let’s implement an iterable data structure. We’ll build a matrix class, acting as a two-dimensional array.

▪ The constructor function takes a width, a height, and an optional element function that will be used to fill in the initial values. There are get and set methods to retrieve and update elements in the matrix.

▪ The next method starts by checking whether the bottom of the matrix has been reached. If it hasn’t, it first creates the object holding the current value and then updates its position, moving to the next row if necessary.

▪ Matrix.prototype[Symbol.iterator] = function() {

▪ We can now loop over a matrix with for/of.

let matrix = new Matrix(2, 2, (x, y) => `value ${x},${y}`);
for (let {x, y, value} of matrix) {
console.log(x, y, value);
}

▪ Interfaces often consist mostly of methods, but it is also okay to include properties that hold non-function values. For example, Map objects have a size property that tells you how many keys are stored in them.

▪ Such methods are called getters, and they are defined by writing get in front of the method name in an object expression or class declaration.

▪ Whenever someone reads from this object’s size property, the associated method is called. You can do a similar thing when a property is written to, using a setter.

▪ The Temperature class allows you to read and write the temperature in either degrees Celsius or degrees Fahrenheit, but internally it stores only Celsius and automatically converts to and from Celsius in the fahrenheit getter and setter.

▪ Sometimes you want to attach some properties directly to your constructor function, rather than to the prototype. Such methods won’t have access to a class instance but can, for example, be used to provide additional ways to create instances.

▪ Inside a class declaration, methods that have static written before their name are stored on the constructor.

▪ So the Temperature class allows you to write Temperature.fromFahrenheit(100) to create a temperature using degrees Fahrenheit.

▪ In object-oriented programming terms, this is called inheritance. The new class inherits properties and behavior from the old class

▪ The use of the word extends indicates that this class shouldn’t be directly based on the default Object prototype but on some other class. This is called the superclass. The derived class is the subclass.

▪ To initialize a SymmetricMatrix instance, the constructor calls its superclass’s constructor through the super keyword.

▪ The set method again uses super but this time not to call the constructor but to call a specific method from the superclass’s set of methods.

▪ We are redefining set but do want to use the original behavior. Because this.set refers to the new set method, calling that wouldn’t work. Inside class methods, super provides a way to call methods as they were defined in the superclass.

▪ Inheritance allows us to build slightly different data types from existing data types with relatively little work. It is a fundamental part of the object-oriented tradition, alongside encapsulation and polymorphism. But while the latter two are now generally regarded as wonderful ideas, inheritance is more controversial.

▪ Whereas encapsulation and polymorphism can be used to separate pieces of code from each other, reducing the tangledness of the overall program, inheritance fundamentally ties classes together, creating more tangle. When inheriting from a class, you usually have to know more about how it works than when simply using it.

▪ Inheritance can be a useful tool, and I use it now and then in my own programs, but it shouldn’t be the first tool you reach for, and you probably shouldn’t actively go looking for opportunities to construct class hierarchies (family trees of classes).

▪ It is occasionally useful to know whether an object was derived from a specific class. For this, JavaScript provides a binary operator called instanceof.

▪ The operator will see through inherited types, so a SymmetricMatrix is an instance of Matrix. The operator can also be applied to standard constructors like Array. Almost every object is an instance of Object.

▪ Constructors, which are functions whose names usually start with a capital letter, can be used with the new operator to create new objects.

▪ The new object’s prototype will be the object found in the prototype property of the constructor

▪ ou can make good use of this by putting the properties that all values of a given type share into their prototype. There’s a class notation that provides a clear way to define a constructor and its prototype.

▪ You can define getters and setters to secretly call methods every time an object’s property is accessed. Static methods are methods stored in a class’s constructor, rather than its prototype.

▪ The instanceof operator can, given an object and a constructor, tell you whether that object is an instance of that constructor.

▪ One useful thing to do with objects is to specify an interface for them and tell everybody that they are supposed to talk to your object only through that interface. The rest of the details that make up your object are now encapsulated, hidden behind the interface.

▪ More than one type may implement the same interface. Code written to use an interface automatically knows how to work with any number of different objects that provide the interface. This is called polymorphism.

▪ When implementing multiple classes that differ in only some details, it can be helpful to write the new classes as subclasses of an existing class, inheriting part of its behavior.

▪ The standard JavaScript environment provides another data structure called Set. Like an instance of Map, a set holds a collection of values. Unlike Map, it does not associate other values with those—it just tracks which values are part of the set. A value can be part of a set only once—adding it again doesn’t have any effect.

▪ Earlier in the chapter I mentioned that an object’s hasOwnProperty can be used as a more robust alternative to the in operator when you want to ignore the prototype’s properties

▪ [...] the question of whether Machines Can Think [...] is about as relevant as the question of whether Submarines Can Swim.

Edsger Dijkstra, The Threats to Computing Science

▪ The network of roads in the village forms a graph. A graph is a collection of points (places in the village) with lines between them (roads). This graph will be the world that our robot moves through.

▪ If you’re thinking in terms of object-oriented programming, your first impulse might be to start defining objects for the various elements in the world: a class for the robot, one for a parcel, maybe one for places. These could then hold properties that describe their current state, such as the pile of parcels at a location, which we could change when updating the world.

This is wrong.

▪ The fact that something sounds like an object does not automatically mean that it should be an object in your program. Reflexively writing classes for every concept in your application tends to leave you with a collection of interconnected objects that each have their own internal, changing state. Such programs are often hard to understand and thus easy to break.

▪ Instead, let’s condense the village’s state down to the minimal set of values that define it. There’s the robot’s current location and the collection of undelivered parcels, each of which has a current location and a destination address. That’s it.

And while we’re at it, let’s make it so that we don’t change this state when the robot moves but rather compute a new state for the situation after the move.

▪ Parcel objects aren’t changed when they are moved but re-created. The move method gives us a new village state but leaves the old one entirely intact.

▪ Data structures that don’t change are called immutable or persistent. They behave a lot like strings and numbers in that they are who they are and stay that way, rather than containing different things at different times.

▪ In JavaScript, just about everything can be changed, so working with values that are supposed to be persistent requires some restraint.

▪ There is a function called Object.freeze that changes an object so that writing to its properties is ignored. You could use that to make sure your objects aren’t changed, if you want to be careful. Freezing does require the computer to do some extra work, and having updates ignored is just about as likely to confuse someone as having them do the wrong thing. So I usually prefer to just tell people that a given object shouldn’t be messed with and hope they remember it.

▪ Why am I going out of my way to not change objects when the language is obviously expecting me to?

Because it helps me understand my programs. This is about complexity management again. When the objects in my system are fixed, stable things, I can consider operations on them in isolation—moving to Alice’s house from a given start state always produces the same new state. When objects change over time, that adds a whole new dimension of complexity to this kind of reasoning.

▪ For a small system like the one we are building in this chapter, we could handle that bit of extra complexity

▪ But the most important limit on what kind of systems we can build is how much we can understand

▪ Anything that makes your code easier to understand makes it possible to build a more ambitious system.

▪ Unfortunately, although understanding a system built on persistent data structures is easier, designing one, especially when your programming language isn’t helping, can be a little harder. We’ll look for opportunities to use persistent data structures in this book, but we’ll also be using changeable ones.

▪ A delivery robot looks at the world and decides in which direction it wants to move. As such, we could say that a robot is a function that takes a VillageState object and returns the name of a nearby place.

▪ Because we want robots to be able to remember things, so that they can make and execute plans, we also pass them their memory and allow them to return a new memory

▪ Remember that Math.random() returns a number between zero and one—but always below one. Multiplying such a number by the length of an array and then applying Math.floor to it gives us a random index for the array.

▪ The problem of finding a route through a graph is a typical search problem. We can tell whether a given solution (a route) is a valid solution, but we can’t directly compute the solution the way we could for 2 + 2. Instead, we have to keep creating potential solutions until we find one that works.

▪ Most data structures provided in a standard JavaScript environment aren’t very well suited for persistent use. Arrays have slice and concat methods, which allow us to easily create new arrays without damaging the old one. But Set, for example, has no methods for creating a new set with an item added or removed.

▪ Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.

Brian Kernighan and P.J. Plauger, The Elements of Programming Style

▪ Flaws in computer programs are usually called bugs. It makes programmers feel good to imagine them as little things that just happen to crawl into our work. In reality, of course, we put them there ourselves.

▪ Many mistakes could be pointed out to us automatically by the computer, if it knew enough about what we’re trying to do. But here JavaScript’s looseness is a hindrance. Its concept of bindings and properties is vague enough that it will rarely catch typos before actually running the program. And even then, it allows you to do some clearly nonsensical things without complaint, such as computing true * "monkey"
.

▪ There are some things that JavaScript does complain about. Writing a program that does not follow the language’s grammar will immediately make the computer complain

▪ Other things, such as calling something that’s not a function or looking up a property on an undefined value, will cause an error to be reported when the program tries to perform the action.

▪ But often, your nonsense computation will merely produce NaN (not a number) or an undefined value, while the program happily continues, convinced that it’s doing something meaningful. The mistake will manifest itself only later, after the bogus value has traveled through several functions. It might not trigger an error at all but silently cause the program’s output to be wrong. Finding the source of such problems can be difficult.

▪ The process of finding mistakes—bugs—in programs is called debugging.

▪ JavaScript can be made a little stricter by enabling strict mode. This is done by putting the string "use strict"
at the top of a file or a function body.

▪ Normally, when you forget to put let in front of your binding, as with counter in the example, JavaScript quietly creates a global binding and uses that. In strict mode, an error is reported instead. This is very helpful.

▪ It should be noted, though, that this doesn’t work when the binding in question already exists as a global binding. In that case, the loop will still quietly overwrite the value of the binding.

▪ Another change in strict mode is that the this binding holds the value undefined in functions that are not called as methods. When making such a call outside of strict mode, this refers to the global scope object, which is an object whose properties are the global bindings. So if you accidentally call a method or constructor incorrectly in strict mode, JavaScript will produce an error as soon as it tries to read something from this, rather than happily writing to the global scope.

▪ For example, consider the following code, which calls a constructor function without the new keyword so that its this will not refer to a newly constructed object:

▪ We are immediately told that something is wrong. This is helpful.

▪ Fortunately, constructors created with the class notation will always complain if they are called without new, making this less of a problem even in non-strict mode.

▪ Strict mode does a few more things. It disallows giving a function multiple parameters with the same name and removes certain problematic language features entirely (such as the with statement, which is so wrong it is not further discussed in this book).

▪ In short, putting "use strict"
at the top of your program rarely hurts and might help you spot a problem.

▪ Some languages want to know the types of all your bindings and expressions before even running a program. They will tell you right away when a type is used in an inconsistent way. JavaScript considers types only when actually running the program, and even there often tries to implicitly convert values to the type it expects, so it’s not much help.

▪ A lot of mistakes come from being confused about the kind of value that goes into or comes out of a function. If you have that information written down, you’re less likely to get confused.

▪ When the types of a program are known, it is possible for the computer to check them for you, pointing out mistakes before the program is run

▪ There are several JavaScript dialects that add types to the language and check them. The most popular one is called TypeScript. If you are interested in adding more rigor to your programs, I recommend you give it a try.

▪ In this book, we’ll continue using raw, dangerous, untyped JavaScript code.

▪ Doing this by hand, again and again, is a really bad idea. Not only is it annoying, it also tends to be ineffective since it takes too much time to exhaustively test everything every time you make a change.

▪ Writing tests is a bit more work than testing manually, but once you’ve done it, you gain a kind of superpower: it takes you only a few seconds to verify that your program still behaves properly in all the situations you wrote tests for. When you break something, you’ll immediately notice, rather than randomly running into it at some later time.

▪ function test(label, body) {
if (!body()) console.log(`Failed: ${label}`);
}

test("convert Latin text to uppercase", () => {
return "hello".toUpperCase() == "HELLO";
});
test("convert Greek text to uppercase", () => {
return "Χαίρετε".toUpperCase() == "ΧΑΊΡΕΤΕ";
});
test("don't convert case-less characters", () => {
return "مرحبا".toUpperCase() == "مرحبا";
});

Writing tests like this tends to produce rather repetitive, awkward code.

▪ Fortunately, there exist pieces of software that help you build and run collections of tests (test suites) by providing a language (in the form of functions and methods) suited to expressing tests and by outputting informative information when a test fails. These are usually called test runners.

▪ Some code is easier to test than other code. Generally, the more external objects that the code interacts with, the harder it is to set up the context in which to test it. The style of programming shown in the previous chapter, which uses self-contained persistent values rather than changing objects, tends to be easy to test.

▪ Sometimes it is obvious. The error message will point at a specific line of your program, and if you look at the error description and that line of code, you can often see the problem.

▪ We know that our program is malfunctioning, and we want to find out why.

This is where you must resist the urge to start making random changes to the code to see whether that makes it better. Instead, think. Analyze what is happening and come up with a theory of why it might be happening. Then, make additional observations to test this theory—or, if you don’t yet have a theory, make additional observations to help you come up with one.

▪ Putting a few strategic console.log calls into the program is a good way to get additional information about what the program is doing.

▪ An alternative to using console.log to peek into the program’s behavior is to use the debugger capabilities of your browser

▪ Browsers come with the ability to set a breakpoint on a specific line of your code. When the execution of the program reaches a line with a breakpoint, it is paused, and you can inspect the values of bindings at that point. I won’t go into details, as debuggers differ from browser to browser, but look in your browser’s developer tools or search the Web for more information.

▪ Another way to set a breakpoint is to include a debugger statement (consisting of simply that keyword) in your program. If the developer tools of your browser are active, the program will pause whenever it reaches such a statement.

▪ Not all problems can be prevented by the programmer, unfortunately. If your program communicates with the outside world in any way, it is possible to get malformed input, to become overloaded with work, or to have the network fail.

▪ Sometimes the right thing to do is take the bad input in stride and continue running. In other cases, it is better to report to the user what went wrong and then give up. But in either situation, the program has to actively do something in response to the problem.

▪ When a function cannot proceed normally, what we would like to do is just stop what we are doing and immediately jump to a place that knows how to handle the problem. This is what exception handling does.

▪ Exceptions are a mechanism that makes it possible for code that runs into a problem to raise (or throw) an exception. An exception can be any value.

▪ Raising one somewhat resembles a super-charged return from a function: it jumps out of not just the current function but also its callers, all the way down to the first call that started the current execution. This is called unwinding the stack. You may remember the stack of function calls that was mentioned in Chapter 3.

▪ If exceptions always zoomed right down to the bottom of the stack, they would not be of much use. They’d just provide a novel way to blow up your program

▪ Their power lies in the fact that you can set “obstacles” along the stack to catch the exception as it is zooming down. Once you’ve caught an exception, you can do something with it to address the problem and then continue to run the program.

▪ The throw keyword is used to raise an exception. Catching one is done by wrapping a piece of code in a try block, followed by the keyword catch

▪ When the code in the try block causes an exception to be raised, the catch block is evaluated, with the name in parentheses bound to the exception value

▪ After the catch block finishes—or if the try block finishes without problems—the program proceeds beneath the entire try/catch statement.

▪ In this case, we used the Error constructor to create our exception value. This is a standard JavaScript constructor that creates an object with a message property. In most JavaScript environments, instances of this constructor also gather information about the call stack that existed when the exception was created, a so-called stack trace

▪ This information is stored in the stack property and can be helpful when trying to debug a problem: it tells us the function where the problem occurred and which functions made the failing call.

▪ Note that the look function completely ignores the possibility that promptDirection might go wrong. This is the big advantage of exceptions: error-handling code is necessary only at the point where the error occurs and at the point where it is handled. The functions in between can forget all about it.

▪ Every action that might cause an exception, which is pretty much every function call and property access, might cause control to suddenly leave your code.

▪ But transfer first removes the money from the account and then calls getAccount before it adds it to another account. If it is broken off by an exception at that point, it’ll just make the money disappear.

▪ But often problems like this occur in more subtle ways. Even functions that don’t look like they will throw an exception might do so in exceptional circumstances or when they contain a programmer mistake.

▪ One way to address this is to use fewer side effects. Again, a programming style that computes new values instead of changing existing data helps. If a piece of code stops running in the middle of creating a new value, no one ever sees the half-finished value, and there is no problem.

▪ So there is another feature that try statements have. They may be followed by a finally block either instead of or in addition to a catch block. A finally block says “no matter what happens, run this code after trying to run the code in the try block.”

▪ Note that even though the finally code is run when an exception is thrown in the try block, it does not interfere with the exception. After the finally block runs, the stack continues unwinding.

▪ Writing programs that operate reliably even when exceptions pop up in unexpected places is hard. Many people simply don’t bother, and because exceptions are typically reserved for exceptional circumstances, the problem may occur so rarely that it is never even noticed. Whether that is a good thing or a really bad thing depends on how much damage the software will do when it fails.

▪ When an exception makes it all the way to the bottom of the stack without being caught, it gets handled by the environment. What this means differs between environments. In browsers, a description of the error typically gets written to the JavaScript console (reachable through the browser’s Tools or Developer menu). Node.js, the browserless JavaScript environment we will discuss in Chapter 20, is more careful about data corruption. It aborts the whole process when an unhandled exception occurs.

▪ For programmer mistakes, just letting the error go through is often the best you can do. An unhandled exception is a reasonable way to signal a broken program, and the JavaScript console will, on modern browsers, provide you with some information about which function calls were on the stack when the problem occurred.

▪ For problems that are expected to happen during routine use, crashing with an unhandled exception is a terrible strategy.

▪ Invalid uses of the language, such as referencing a nonexistent binding, looking up a property on null, or calling something that’s not a function, will also result in exceptions being raised. Such exceptions can also be caught.

▪ When a catch body is entered, all we know is that something in our try body caused an exception. But we don’t know what did or which exception it caused.

▪ JavaScript (in a rather glaring omission) doesn’t provide direct support for selectively catching exceptions: either you catch them all or you don’t catch any. This makes it tempting to assume that the exception you get is the one you were thinking about when you wrote the catch block.

But it might not be. Some other assumption might be violated, or you might have introduced a bug that is causing an exception.

▪ As a general rule, don’t blanket-catch exceptions unless it is for the purpose of “routing” them somewhere—for example, over the network to tell another system that our program crashed. And even then, think carefully about how you might be hiding information.

▪ We could compare its message property against the error message we happen to expect. But that’s a shaky way to write code—we’d be using information that’s intended for human consumption (the message) to make a programmatic decision. As soon as someone changes (or translates) the message, the code will stop working.

▪ Rather, let’s define a new type of error and use instanceof to identify it.

class InputError extends Error {}

▪ It doesn’t define its own constructor, which means that it inherits the Error constructor

▪ Assertions are checks inside a program that verify that something is the way it is supposed to be. They are used not to handle situations that can come up in normal operation but to find programmer mistakes.

▪ Now, instead of silently returning undefined (which you get when reading an array property that does not exist), this will loudly blow up your program as soon as you misuse it. This makes it less likely for such mistakes to go unnoticed and easier to find their cause when they occur.

▪ I do not recommend trying to write assertions for every possible kind of bad input. That’d be a lot of work and would lead to very noisy code. You’ll want to reserve them for mistakes that are easy to make (or that you find yourself making).

▪ Mistakes and bad input are facts of life. An important part of programming is finding, diagnosing, and fixing bugs

▪ Problems can become easier to notice if you have an automated test suite or add assertions to your programs.

▪ Throwing an exception causes the call stack to be unwound until the next enclosing try/catch block or until the bottom of the stack. The exception value will be given to the catch block that catches it, which should verify that it is actually the expected kind of exception and then do something with it.

▪ To help address the unpredictable control flow caused by exceptions, finally blocks can be used to ensure that a piece of code always runs when a block finishes.

▪ Some people, when confronted with a problem, think ‘I know, I’ll use regular expressions.’ Now they have two problems.

Jamie Zawinski

▪ Programming tools and techniques survive and spread in a chaotic, evolutionary way. It’s not always the pretty or brilliant ones that win but rather the ones that function well enough within the right niche or that happen to be integrated with another successful piece of technology.

▪ Regular expressions are a way to describe patterns in string data. They form a small, separate language that is part of JavaScript and many other languages and systems.

▪ Regular expressions are both terribly awkward and extremely useful

▪ Their syntax is cryptic, and the programming interface JavaScript provides for them is clumsy. But they are a powerful tool for inspecting and processing strings.

▪ Properly understanding regular expressions will make you a more effective programmer.

▪ A regular expression is a type of object. It can be either constructed with the RegExp constructor or written as a literal value by enclosing a pattern in forward slash (/) characters.

let re1 = new RegExp("abc");
let re2 = /abc/;

▪ When using the RegExp constructor, the pattern is written as a normal string, so the usual rules apply for backslashes.

The second notation, where the pattern appears between slash characters, treats backslashes somewhat differently.

▪ First, since a forward slash ends the pattern, we need to put a backslash before any forward slash that we want to be part of the pattern.

▪ In addition, backslashes that aren’t part of special character codes (like \n) will be preserved, rather than ignored as they are in strings, and change the meaning of the pattern. Some characters, such as question marks and plus signs, have special meanings in regular expressions and must be preceded by a backslash if they are meant to represent the character itself.

▪ Regular expression objects have a number of methods. The simplest one is test. If you pass it a string, it will return a Boolean telling you whether the string contains a match of the pattern in the expression

▪ If abc occurs anywhere in the string we are testing against (not just at the start), test will return true.

▪ Finding out whether a string contains abc could just as well be done with a call to indexOf. Regular expressions allow us to express more complicated patterns.

▪ Say we want to match any number. In a regular expression, putting a set of characters between square brackets makes that part of the expression match any of the characters between the brackets.

▪ console.log(/[0123456789]/.test("in 1992"));
// → true

▪ console.log(/[0-9]/.test("in 1992"));
// → true

▪ Within square brackets, a hyphen (-) between two characters can be used to indicate a range of characters, where the ordering is determined by the character’s Unicode number. Characters 0 to 9 sit right next to each other in this ordering (codes 48 to 57), so [0-9] covers all of them and matches any digit.

▪ A number of common character groups have their own built-in shortcuts. Digits are one of them: \d means the same thing as [0-9].

▪ \d  Any digit character

▪ \w An alphanumeric character (“word character”)

▪ \s  Any whitespace character (space, tab, newline, and similar)

▪ \D A character that is not a digit

▪ \W　A nonalphanumeric character

▪ \S  A nonwhitespace character

▪ .    Any character except for newline

▪ So you could match a date and time format like 01-30-2003 15:20 with the following expression:

let dateTime = /\d\d-\d\d-\d\d\d\d \d\d:\d\d/;

▪ These backslash codes can also be used inside square brackets. For example, [\d.] means any digit or a period character. But the period itself, between square brackets, loses its special meaning. The same goes for other special characters, such as +.

▪ To invert a set of characters—that is, to express that you want to match any character except the ones in the set—you can write a caret (^) character after the opening bracket.

let notBinary = /[^01]/;
console.log(notBinary.test("1100100010100110"));
// → false
console.log(notBinary.test("1100100010200110"));
// → true

▪ When you put a plus sign (+) after something in a regular expression, it indicates that the element may be repeated more than once. Thus, /\d+/ matches one or more digit characters.

▪ The star (*) has a similar meaning but also allows the pattern to match zero times

▪ A question mark makes a part of a pattern optional, meaning it may occur zero times or one time

▪ In the following example, the u character is allowed to occur, but the pattern also matches when it is missing.

let neighbor = /neighbou?r/;

▪ To indicate that a pattern should occur a precise number of times, use braces. Putting {4} after an element, for example, requires it to occur exactly four times

▪ It is also possible to specify a range this way: {2,4} means the element must occur at least twice and at most four times.

▪ Here is another version of the date and time pattern that allows both single- and double-digit days, months, and hours. It is also slightly easier to decipher.

let dateTime = /\d{1,2}-\d{1,2}-\d{4} \d{1,2}:\d{2}/;
console.log(dateTime.test("1-30-2003 8:45"));
// → true

▪ You can also specify open-ended ranges when using braces by omitting the number after the comma. So, {5,} means five or more times.

▪ To use an operator like * or + on more than one element at a time, you have to use parentheses

▪ A part of a regular expression that is enclosed in parentheses counts as a single element as far as the operators following it are concerned.

▪ The i at the end of the expression in the example makes this regular expression case insensitive, allowing it to match the uppercase B in the input string, even though the pattern is itself all lowercase.

▪ The test method is the absolute simplest way to match a regular expression. It tells you only whether it matched and nothing else. Regular expressions also have an exec (execute) method that will return null if no match was found and return an object with information about the match otherwise.

▪ An object returned from exec has an index property that tells us where in the string the successful match begins. Other than that, the object looks like (and in fact is) an array of strings, whose first element is the string that was matched.

▪ String values have a match method that behaves similarly.

console.log("one two 100".match(/\d+/));
// → ["100"]

▪ When the regular expression contains subexpressions grouped with parentheses, the text that matched those groups will also show up in the array

▪ The whole match is always the first element. The next element is the part matched by the first group (the one whose opening parenthesis comes first in the expression), then the second group, and so on.

▪ When a group does not end up being matched at all (for example, when followed by a question mark), its position in the output array will hold undefined

▪ Similarly, when a group is matched multiple times, only the last match ends up in the array

▪ JavaScript has a standard class for representing dates—or, rather, points in time

▪ If you simply create a date object using new, you get the current date and time.

▪ new Date(2009, 11, 9, 12, 59, 59, 999));
// → Wed Dec 09 2009 12:59:59 GMT+0100 (CET)

▪ JavaScript uses a convention where month numbers start at zero (so December is 11), yet day numbers start at one. This is confusing and silly. Be careful.

▪ The last four arguments (hours, minutes, seconds, and milliseconds) are optional and taken to be zero when not given.

▪ Timestamps are stored as the number of milliseconds since the start of 1970, in the UTC time zone. This follows a convention set by “Unix time”, which was invented around that time. You can use negative numbers for times before 1970. The getTime method on a date object returns this number. It is big, as you can imagine.

▪ If you give the Date constructor a single argument, that argument is treated as such a millisecond count.

▪ You can get the current millisecond count by creating a new Date object and calling getTime on it or by calling the Date.now function.

▪ Date objects provide methods such as getFullYear, getMonth, getDate, getHours, getMinutes, and getSeconds to extract their components

▪ Besides getFullYear there’s also getYear, which gives you the year minus 1900 (98 or 119) and is mostly useless

▪ let [_, month, day, year] =
/(\d{1,2})-(\d{1,2})-(\d{4})/.exec(string);

▪ The _ (underscore) binding is ignored and used only to skip the full match element in the array returned by exec

▪ If we want to enforce that the match must span the whole string, we can add the markers ^ and $. The caret matches the start of the input string, whereas the dollar sign matches the end. So, /^\d+$/ matches a string consisting entirely of one or more digits, /^!/ matches any string that starts with an exclamation mark, and /x^/ does not match any string (there cannot be an x before the start of the string).

▪ If, on the other hand, we just want to make sure the date starts and ends on a word boundary, we can use the marker \b. A word boundary can be the start or end of the string or any point in the string that has a word character (as in \w) on one side and a nonword character on the other.

console.log(/cat/.test("concatenate"));
// → true
console.log(/\bcat\b/.test("concatenate"));
// → false

▪ Note that a boundary marker doesn’t match an actual character. It just enforces that the regular expression matches only when a certain condition holds at the place where it appears in the pattern.

▪ The pipe character (|) denotes a choice between the pattern to its left and the pattern to its right. So I can say this:

let animalCount = /\b\d+ (pig|cow|chicken)s?\b/;
console.log(animalCount.test("15 pigs"));

▪ Parentheses can be used to limit the part of the pattern that the pipe operator applies to, and you can put multiple such operators next to each other to express a choice between more than two alternatives.

▪ The matcher stops as soon as it finds a full match. This means that if multiple branches could potentially match a string, only the first one (ordered by where the branches appear in the regular expression) is used.

▪ When a g option (for global) is added to the regular expression, all matches in the string will be replaced, not just the first.

▪ It would have been sensible if the choice between replacing one match or all matches was made through an additional argument to replace or by providing a different method, replaceAll. But for some unfortunate reason, the choice relies on a property of the regular expression instead.

▪ If we want to swap these names and remove the comma to get a Firstname Lastname
format, we can use the following code:

console.log(
"Liskov, Barbara\nMcCarthy, John\nWadler, Philip"
.replace(/(\w+), (\w+)/g, "$2 $1"));
// → Barbara Liskov
// John McCarthy
// Philip Wadler

▪ The $1 and $2 in the replacement string refer to the parenthesized groups in the pattern. $1 is replaced by the text that matched against the first group, $2 by the second, and so on, up to $9. The whole match can be referred to with $&.

▪ It is possible to pass a function—rather than a string—as the second argument to replace. For each replacement, the function will be called with the matched groups (as well as the whole match) as arguments, and its return value will be inserted into the new string.

▪ let s = "the cia and fbi";
console.log(s.replace(/\b(fbi|cia)\b/g,
str => str.toUpperCase()));
// → the CIA and FBI

▪ Here’s a more interesting one:

let stock = "1 lemon, 2 cabbages, and 101 eggs";
function minusOne(match, amount, unit) {
amount = Number(amount) - 1;
if (amount == 1) { // only one left, remove the 's'
unit = unit.slice(0, unit.length - 1);
} else if (amount == 0) {
amount = "no";
}
return amount + " " + unit;
}
console.log(stock.replace(/(\d+) (\w+)/g, minusOne));
// → no lemon, 1 cabbage, and 100 eggs

▪ Because of this behavior, we say the repetition operators (+, *, ?, and {}) are greedy, meaning they match as much as they can and backtrack from there. If you put a question mark after them (+?, *?, ??, {}?), they become nongreedy and start by matching as little as possible, matching more only when the remaining pattern does not fit the smaller match.

▪ A lot of bugs in regular expression programs can be traced to unintentionally using a greedy operator where a nongreedy one would work better. When using a repetition operator, consider the nongreedy variant first.

▪ There are cases where you might not know the exact pattern you need to match against when you are writing your code. Say you want to look for the user’s name in a piece of text and enclose it in underscore characters to make it stand out.

▪ But you can build up a string and use the RegExp constructor on that.

▪ When creating the \b boundary markers, we have to use two backslashes because we are writing them in a normal string, not a slash-enclosed regular expression

▪ The second argument to the RegExp constructor contains the options for the regular expression—in this case, "gi" for global and case insensitive.

▪ let name = "dea+hl[]rd";
let text = "This dea+hl[]rd guy is super annoying.";
let escaped = name.replace(/[\\[.+*?(){|^$]/g, "\\$&");
let regexp = new RegExp("\\b" + escaped + "\\b", "gi");
console.log(text.replace(regexp, "_$&_"));
// → This _dea+hl[]rd_ guy is super annoying.

▪ The indexOf method on strings cannot be called with a regular expression. But there is another method, search, that does expect a regular expression. Like indexOf, it returns the first index on which the expression was found, or -1 when it wasn’t found.

▪ Unfortunately, there is no way to indicate that the match should start at a given offset (like we can with the second argument to indexOf), which would often be useful.

▪ Again, a less confusing solution would have been to just allow an extra argument to be passed to exec, but confusion is an essential feature of JavaScript’s regular expression interface.

▪ let pattern = /y/g;
pattern.lastIndex = 3;
let match = pattern.exec("xyzzy");
console.log(match.index);
// → 4
console.log(pattern.lastIndex);
// → 5

▪ If the match was successful, the call to exec automatically updates the lastIndex property to point after the match. If no match was found, lastIndex is set back to zero, which is also the value it has in a newly constructed regular expression object.

▪ The difference between the global and the sticky options is that, when sticky is enabled, the match will succeed only if it starts directly at lastIndex, whereas with global, it will search ahead for a position where a match can start.

▪ When using a shared regular expression value for multiple exec calls, these automatic updates to the lastIndex property can cause problems. Your regular expression might be accidentally starting at an index that was left over from a previous call.

▪ let digit = /\d/g;
console.log(digit.exec("here it is: 1"));
// → ["1"]
console.log(digit.exec("and now: 1"));
// → null

▪ Another interesting effect of the global option is that it changes the way the match method on strings works. When called with a global expression, instead of returning an array similar to that returned by exec, match will find all matches of the pattern in the string and return an array containing the matched strings.

▪ So be cautious with global regular expressions. The cases where they are necessary—calls to replace and places where you want to explicitly use lastIndex—are typically the only places where you want to use them.

▪ let input = "A string with 3 numbers in it... 42 and 88.";
let number = /\b\d+\b/g;
let match;
while (match = number.exec(input)) {
console.log("Found", match[0], "at", match.index);
}

▪ This makes use of the fact that the value of an assignment expression (=) is the assigned value

▪ Some operating systems, however, use not just a newline character to separate lines but a carriage return character followed by a newline ("\r\n").

▪ Given that the split method also allows a regular expression as its argument, we can use a regular expression like /\r?\n/ to split in a way that allows both "\n" and "\r\n" between lines.

▪ The pattern if (match = string.match(...))
is similar to the trick of using an assignment as the condition for while. You often aren’t sure that your call to match will succeed, so you can access the resulting object only inside an if statement that tests for this.

▪ Because of JavaScript’s initial simplistic implementation and the fact that this simplistic approach was later set in stone as standard behavior, JavaScript’s regular expressions are rather dumb about characters that do not appear in the English language

▪ For example, as far as JavaScript’s regular expressions are concerned, a “word character” is only one of the 26 characters in the Latin alphabet (uppercase or lowercase), decimal digits, and, for some reason, the underscore character. Things like é or β, which most definitely are word characters, will not match \w (and will match uppercase \W, the nonword category).

▪ By a strange historical accident, \s (whitespace) does not have this problem and matches all characters that the Unicode standard considers whitespace, including things like the nonbreaking space and the Mongolian vowel separator.

▪ as discussed in Chapter 5, not actual characters. This means characters that are composed of two code units behave strangely.

console.log(/🍎{3}/.test("🍎🍎🍎"));
// → false
console.log(//.test(""));
// → false
console.log(//u.test(""));
// → true

▪ The problem is that the 🍎 in the first line is treated as two code units, and the {3} part is applied only to the second one. Similarly, the dot matches a single code unit, not the two that make up the rose emoji.

▪ You must add a u option (for Unicode) to your regular expression to make it treat such characters properly

▪ Though this was only just standardized and is, at the time of writing, not widely supported yet, it is possible to use \p in a regular expression (that must have the Unicode option enabled) to match all characters to which the Unicode standard assigns a given property.

▪ console.log(/\p{Script=Greek}/u.test("α"));
// → true

▪ console.log(/\p{Script=Arabic}/u.test("α"));
// → false

▪ Unicode defines a number of useful properties, though finding the one that you need may not always be trivial. You can use the \p{Property=Value} notation to match any character that has the given value for that property.

▪ If the property name is left off, as in \p{Name}, the name is assumed to be either a binary property such as Alphabetic or a category such as Number.

▪ /abc/     　A sequence of characters

▪ /[abc]/  Any character from a set of characters

▪ /[^abc]/　Any character not in a set of characters

▪ /[0-9]/   　Any character in a range of characters

▪ /x+/       　One or more occurrences of the pattern x

▪ /x+?/     　One or more occurrences, nongreedy

▪ /x*/       　Zero or more occurrences

▪ /x?/       　Zero or one occurrence

▪ /x{2,4}/ Two to four occurrences

▪ /(abc)/  A group

▪ /a|b|c/ Any one of several patterns

▪ /\d/        Any digit character

▪ /\w/       　An alphanumeric character (“word character”)

▪ /\s/        Any whitespace character

▪ /./          Any character except newlines

▪ /\b/        A word boundary

▪ /^/         　Start of input

▪ /$/         　End of input

▪ A regular expression has a method test to test whether a given string matches it

▪ It also has a method exec that, when a match is found, returns an array containing all matched groups. Such an array has an index property that indicates where the match started.

▪ Strings have a match method to match them against a regular expression

▪ a search method to search for one, returning only the starting position of the match

▪ Their replace method can replace matches of a pattern with a replacement string or function.

▪ Regular expressions can have options, which are written after the closing slash

▪ The i option makes the match case insensitive

▪ The g option makes the expression global, which, among other things, causes the replace method to replace all instances instead of just the first

▪ The y option makes it sticky, which means that it will not search ahead and skip part of the string when looking for a match

▪ The u option turns on Unicode mode, which fixes a number of problems around the handling of characters that take up two code units.

▪ Regular expressions are a sharp tool with an awkward handle. They simplify some tasks tremendously but can quickly become unmanageable when applied to complex problems.

▪ Part of knowing how to use them is resisting the urge to try to shoehorn things that they cannot cleanly express into them.

▪ Sometimes it helps to enter your expression into an online tool like https://debuggex.com to see whether its visualization corresponds to what you intended and to experiment with the way it responds to various input strings.

▪ Code golf is a term used for the game of trying to express a particular program in as few characters as possible

▪ Quoting style

Imagine you have written a story and used single quotation marks throughout to mark pieces of dialogue. Now you want to replace all the dialogue quotes with double quotes, while keeping the single quotes used in contractions like aren’t.

▪ Write code that is easy to delete, not easy to extend.

Tef, Programming is Terrible

▪ A typical real program grows organically. New pieces of functionality are added as new needs come up. Structuring—and preserving structure—is additional work. It’s work that will pay off only in the future, the next time someone works on the program. So it is tempting to neglect it and allow the parts of the program to become deeply entangled.

▪ First, understanding such a system is hard. If everything can touch everything else, it is difficult to look at any given piece in isolation. You are forced to build up a holistic understanding of the entire thing.

▪ Second, if you want to use any of the functionality from such a program in another situation, rewriting it may be easier than trying to disentangle it from its context.

▪ The phrase “big ball of mud” is often used for such large, structureless programs. Everything sticks together, and when you try to pick out a piece, the whole thing comes apart, and your hands get dirty.

▪ Modules are an attempt to avoid these problems. A module is a piece of program that specifies which other pieces it relies on and which functionality it provides for other modules to use (its interface).

▪ Module interfaces have a lot in common with object interfaces, as we saw them in Chapter 6. They make part of the module available to the outside world and keep the rest private. By restricting the ways in which modules interact with each other, the system becomes more like LEGO, where pieces interact through well-defined connectors, and less like mud, where everything mixes with everything.

▪ The relations between modules are called dependencies. When a module needs a piece from another module, it is said to depend on that module.

▪ When this fact is clearly specified in the module itself, it can be used to figure out which other modules need to be present to be able to use a given module and to automatically load dependencies.

▪ Just putting your JavaScript code into different files does not satisfy these requirements. The files still share the same global namespace. They can, intentionally or accidentally, interfere with each other’s bindings. And the dependency structure remains unclear

▪ Designing a fitting module structure for a program can be difficult. In the phase where you are still exploring the problem, trying different things to see what works, you might want to not worry about it too much since it can be a big distraction. Once you have something that feels solid, that’s a good time to take a step back and organize it.

▪ One of the advantages of building a program out of separate pieces, and being actually able to run those pieces on their own, is that you might be able to apply the same piece in different programs.

▪ But how do you set this up? Say I want to use the parseINI function from Chapter 9 in another program. If it is clear what the function depends on (in this case, nothing), I can just copy all the necessary code into my new project and use it. But then, if I find a mistake in that code, I’ll probably fix it in whichever program I’m working with at the time and forget to also fix it in the other program.

▪ Once you start duplicating code, you’ll quickly find yourself wasting time and energy moving copies around and keeping them up-to-date.

▪ That’s where packages come in. A package is a chunk of code that can be distributed (copied and installed). It may contain one or more modules and has information about which other packages it depends on. A package also usually comes with documentation explaining what it does so that people who didn’t write it might still be able to use it.

▪ Working in this way requires infrastructure. We need a place to store and find packages and a convenient way to install and upgrade them. In the JavaScript world, this infrastructure is provided by NPM (https://npmjs.org).

▪ NPM is two things: an online service where one can download (and upload) packages and a program (bundled with Node.js) that helps you install and manage them.

▪ At the time of writing, there are more than half a million different packages available on NPM. A large portion of those are rubbish, I should mention, but almost every useful, publicly available package can be found on there. For example, an INI file parser, similar to the one we built in Chapter 9, is available under the package name ini.

▪ Having quality packages available for download is extremely valuable. It means that we can often avoid reinventing a program that 100 people have written before and get a solid, well-tested implementation at the press of a few keys.

▪ Software is cheap to copy, so once someone has written it, distributing it to other people is an efficient process. But writing it in the first place is work, and responding to people who have found problems in the code, or who want to propose new features, is even more work.

▪ Most code on NPM is licensed this way. Some licenses require you to also publish code that you build on top of the package under the same license. Others are less demanding, just requiring that you keep the license with the code as you distribute it. The JavaScript community mostly uses the latter type of license. When using other people’s packages, make sure you are aware of their license.

▪ Until 2015, the JavaScript language had no built-in module system. Yet people had been building large systems in JavaScript for more than a decade, and they needed modules.

▪ So they designed their own module systems on top of the language. You can use JavaScript functions to create local scopes and objects to represent module interfaces.

▪ This style of modules provides isolation, to a certain degree, but it does not declare dependencies. Instead, it just puts its interface into the global scope and expects its dependencies, if any, to do the same. For a long time this was the main approach used in web programming, but it is mostly obsolete now.

▪ A less scary way of interpreting data as code is to use the Function constructor. It takes two arguments: a string containing a comma-separated list of argument names and a string containing the function body. It wraps the code in a function value so that it gets its own scope and won’t do odd things with other scopes.

▪ CommonJS

The most widely used approach to bolted-on JavaScript modules is called CommonJS modules. Node.js uses it and is the system used by most packages on NPM.

▪ The main concept in CommonJS modules is a function called require. When you call this with the module name of a dependency, it makes sure the module is loaded and returns its interface.

▪ Because the loader wraps the module code in a function, modules automatically get their own local scope. All they have to do is call require to access their dependencies and put their interface in the object bound to exports.

▪ Destructuring is very convenient when creating bindings for imported interfaces.

▪ To avoid loading the same module multiple times, require keeps a store (cache) of already loaded modules. When called, it first checks if the requested module has been loaded and, if not, loads it. This involves reading the module’s code, wrapping it in a function, and calling it.

▪ When it starts with "./" or "../", it is generally interpreted as relative to the current module’s filename. So "./format-date" would be the file named format-date.js in the same directory.

▪ When the name isn’t relative, Node.js will look for an installed package by that name. In the example code in this chapter, we’ll interpret such names as referring to NPM packages

▪ CommonJS modules work quite well and, in combination with NPM, have allowed the JavaScript community to start sharing code on a large scale.

▪ But they remain a bit of a duct-tape hack. The notation is slightly awkward—the things you add to exports are not available in the local scope, for example. And because require is a normal function call taking any kind of argument, not just a string literal, it can be hard to determine the dependencies of a module without running its code.

▪ This is why the JavaScript standard from 2015 introduces its own, different module system. It is usually called ES modules, where ES stands for ECMAScript

▪ For one thing, the notation is now integrated into the language. Instead of calling a function to access a dependency, you use a special import keyword.

▪ An ES module’s interface is not a single value but a set of named bindings

▪ When there is a binding named default, it is treated as the module’s main exported value

▪ If you import a module like ordinal in the example, without braces around the binding name, you get its default binding. Such modules can still export other bindings under different names alongside their default export.

▪ To create a default export, you write export default
before an expression, a function declaration, or a class declaration.

export default ["Winter", "Spring", "Summer", "Autumn"];

▪ It is possible to rename imported bindings using the word as.

import {days as dayNames} from "date-names";

▪ Another important difference is that ES module imports happen before a module’s script starts running. That means import declarations may not appear inside functions or blocks, and the names of dependencies must be quoted strings, not arbitrary expressions.

▪ Many projects are written using ES modules and then automatically converted to some other format when published. We are in a transitional period in which two different module systems are used side by side, and it is useful to be able to read and write code in either of them.

▪ In fact, many JavaScript projects aren’t even, technically, written in JavaScript. There are extensions, such as the type checking dialect mentioned in Chapter 8, that are widely used. People also often start using planned extensions to the language long before they have been added to the platforms that actually run JavaScript.

▪ To make this possible, they compile their code, translating it from their chosen JavaScript dialect to plain old JavaScript—or even to a past version of JavaScript—so that old browsers can run it.

▪ Including a modular program that consists of 200 different files in a web page produces its own problems. If fetching a single file over the network takes 50 milliseconds, loading the whole program takes 10 seconds, or maybe half that if you can load several files simultaneously.

▪ Because fetching a single big file tends to be faster than fetching a lot of tiny ones, web programmers have started using tools that roll their programs (which they painstakingly split into modules) back into a single big file before they publish it to the Web. Such tools are called bundlers.

▪ And we can go further. Apart from the number of files, the size of the files also determines how fast they can be transferred over the network. Thus, the JavaScript community has invented minifiers. These are tools that take a JavaScript program and make it smaller by automatically removing comments and whitespace, renaming bindings, and replacing pieces of code with equivalent code that take up less space.

▪ So it is not uncommon for the code that you find in an NPM package or that runs on a web page to have gone through multiple stages of transformation—converted from modern JavaScript to historic JavaScript, from ES module format to CommonJS, bundled, and minified.

▪ We won’t go into the details of these tools in this book since they tend to be boring and change rapidly. Just be aware that the JavaScript code you run is often not the code as it was written.

▪ Structuring programs is one of the subtler aspects of programming. Any nontrivial piece of functionality can be modeled in various ways.

▪ Good program design is subjective—there are trade-offs involved and matters of taste. The best way to learn the value of well-structured design is to read or work on a lot of programs and notice what works and what doesn’t.

▪ Don’t assume that a painful mess is “just the way it is”. You can improve the structure of almost everything by putting more thought into it.

▪ If you are designing something that is intended to be used by multiple people—or even by yourself, in three months when you no longer remember the specifics of what you did—it is helpful if your interface is simple and predictable.

▪ That may mean following existing conventions. A good example is the ini package. This module imitates the standard JSON object by providing parse and stringify (to write an INI file) functions, and, like JSON, converts between strings and plain objects. So the interface is small and familiar, and after you’ve worked with it once, you’re likely to remember how to use it.

▪ Even if there’s no standard function or widely used package to imitate, you can keep your modules predictable by using simple data structures and doing a single, focused thing

▪ This points to another helpful aspect of module design—the ease with which something can be composed with other code. Focused modules that compute values are applicable in a wider range of programs than bigger modules that perform complicated actions with side effects.

▪ Relatedly, stateful objects are sometimes useful or even necessary, but if something can be done with a function, use a function. Several of the INI file readers on NPM provide an interface style that requires you to first create an object, then load the file into your object, and finally use specialized methods to get at the results. This type of thing is common in the object-oriented tradition, and it’s terrible. Instead of making a single function call and moving on, you have to perform the ritual of moving your object through various states. And because the data is now wrapped in a specialized object type, all code that interacts with it has to know about that type, creating unnecessary interdependencies.

▪ Often defining new data structures can’t be avoided—only a few basic ones are provided by the language standard, and many types of data have to be more complex than an array or a map. But when an array suffices, use an array.

▪ An example of a slightly more complex data structure is the graph from Chapter 7. There is no single obvious way to represent a graph in JavaScript. In that chapter, we used an object whose properties hold arrays of strings—the other nodes reachable from that node.

▪ This can be a barrier to composition—when various packages are using different data structures to describe similar things, combining them is difficult. Therefore, if you want to design for composability, find out what data structures other people are using and, when possible, follow their example.

▪ Modules provide structure to bigger programs by separating the code into pieces with clear interfaces and dependencies

▪ The interface is the part of the module that’s visible from other modules, and the dependencies are the other modules that it makes use of.

▪ Because JavaScript historically did not provide a module system, the CommonJS system was built on top of it. Then at some point it did get a built-in system, which now coexists uneasily with the CommonJS system

▪ A package is a chunk of code that can be distributed on its own. NPM is a repository of JavaScript packages. You can download all kinds of useful (and useless) packages from it.

▪ A circular dependency is a situation where module A depends on B, and B also, directly or indirectly, depends on A. Many module systems simply forbid this because whichever order you choose for loading such modules, you cannot make sure that each module’s dependencies have been loaded before it runs.

▪ CommonJS modules allow a limited form of cyclic dependencies. As long as the modules do not replace their default exports object and don’t access each other’s interface until after they finish loading, cyclic dependencies are okay.

▪ The central part of a computer, the part that carries out the individual steps that make up our programs, is called the processor. The programs we have seen so far are things that will keep the processor busy until they have finished their work. The speed at which something like a loop that manipulates numbers can be executed depends pretty much entirely on the speed of the processor.

▪ But many programs interact with things outside of the processor. For example, they may communicate over a computer network or request data from the hard disk—which is a lot slower than getting it from memory.

▪ In a synchronous programming model, things happen one at a time. When you call a function that performs a long-running action, it returns only when the action has finished and it can return the result.

▪ An asynchronous model allows multiple things to happen at the same time. When you start an action, your program continues to run. When the action finishes, the program is informed and gets access to the result (for example, the data read from disk).

▪ Another way to describe the difference is that waiting for actions to finish is implicit in the synchronous model, while it is explicit, under our control, in the asynchronous one.

▪ Asynchronicity cuts both ways. It makes expressing programs that do not fit the straight-line model of control easier, but it can also make expressing programs that do follow a straight line more awkward.

▪ Both of the important JavaScript programming platforms—browsers and Node.js—make operations that might take a while asynchronous, rather than relying on threads. Since programming with threads is notoriously hard (understanding what a program does is much more difficult when it’s doing multiple things at once), this is generally considered a good thing.

▪ One approach to asynchronous programming is to make functions that perform a slow action take an extra argument, a callback function. The action is started, and when it finishes, the callback function is called with the result.

▪ As an example, the setTimeout function, available both in Node.js and in browsers, waits a given number of milliseconds (a second is a thousand milliseconds) and then calls a function.

setTimeout(() => console.log("Tick"), 500);

▪ Performing multiple asynchronous actions in a row using callbacks means that you have to keep passing new functions to handle the continuation of the computation after the actions.

▪ This style of programming is workable, but the indentation level increases with each asynchronous action because you end up in another function. Doing more complicated things, such as running multiple actions at the same time, can get a little awkward.

▪ If we had used the handler’s return value as the response value, that would mean that a request handler can’t itself perform asynchronous actions. A function doing asynchronous work typically returns before the work is done, having arranged for a callback to be called when it completes. So we need some asynchronous mechanism—in this case, another callback function—to signal when a response is available.

▪ In a way, asynchronicity is contagious. Any function that calls a function that works asynchronously must itself be asynchronous, using a callback or similar mechanism to deliver its result.

▪ Calling a callback is somewhat more involved and error-prone than simply returning a value, so needing to structure large parts of your program that way is not great.

▪ Working with abstract concepts is often easier when those concepts can be represented by values. In the case of asynchronous actions, you could, instead of arranging for a function to be called at some point in the future, return an object that represents this future event.

▪ This is what the standard class Promise is for. A promise is an asynchronous action that may complete at some point and produce a value. It is able to notify anyone who is interested when its value is available.

▪ The easiest way to create a promise is by calling Promise.resolve. This function ensures that the value you give it is wrapped in a promise. If it’s already a promise, it is simply returned—otherwise, you get a new promise that immediately finishes with your value as its result.

▪ let fifteen = Promise.resolve(15);
fifteen.then(value => console.log(`Got ${value}`));
// → Got 15

▪ To get the result of a promise, you can use its then method. This registers a callback function to be called when the promise resolves and produces a value

▪ You can add multiple callbacks to a single promise,

▪ they will be called, even if you add them after the promise has already resolved (finished).

▪ A normal value is simply there. A promised value is a value that might already be there or might appear at some point in the future. Computations defined in terms of promises act on such wrapped values and are executed asynchronously as the values become available.

▪ To create a promise, you can use Promise as a constructor. It has a somewhat odd interface—the constructor expects a function as argument, which it immediately calls, passing it a function that it can use to resolve the promise. It works this way, instead of for example with a resolve method, so that only the code that created the promise can resolve it.

▪ This is the main advantage of promises—they simplify the use of asynchronous functions. Instead of having to pass around callbacks, promise-based functions look similar to regular ones: they take input as arguments and return their output. The only difference is that the output may not be available yet.

▪ One of the most pressing problems with the callback style of asynchronous programming is that it makes it extremely difficult to make sure failures are properly reported to the callbacks

▪ A widely used convention is that the first argument to the callback is used to indicate that the action failed, and the second contains the value produced by the action when it was successful. Such callback functions must always check whether they received an exception and make sure that any problems they cause, including exceptions thrown by functions they call, are caught and given to the right function.

▪ Promises make this easier. They can be either resolved (the action finished successfully) or rejected (it failed).

▪ So if any element in a chain of asynchronous actions fails, the outcome of the whole chain is marked as rejected, and no success handlers are called beyond the point where it failed.

▪ Much like resolving a promise provides a value, rejecting one also provides one, usually called the reason of the rejection

▪ When an exception in a handler function causes the rejection, the exception value is used as the reason

▪ There’s a Promise.reject function that creates a new, immediately rejected promise.

▪ To explicitly handle such rejections, promises have a catch method that registers a handler to be called when the promise is rejected, similar to how then handlers handle normal resolution

▪ If a catch handler throws an error, the new promise is also rejected.

▪ As a shorthand, then also accepts a rejection handler as a second argument, so you can install both types of handlers in a single method call.

▪ A function passed to the Promise constructor receives a second argument, alongside the resolve function, which it can use to reject the new promise.

▪ The chains of promise values created by calls to then and catch can be seen as a pipeline through which asynchronous values or failures move

▪ Much like an uncaught exception is handled by the environment, JavaScript environments can detect when a promise rejection isn’t handled and will report this as an error.

▪ Because promises can be resolved (or rejected) only once, this will work. The first time resolve or reject is called determines the outcome of the promise, and further calls caused by a request coming back after another request finished are ignored.

▪ To build an asynchronous loop, for the retries, we need to use a recursive function—a regular loop doesn’t allow us to stop and wait for an asynchronous action

▪ Promise.resolve is used to convert the value returned by handler to a promise if it isn’t already.

▪ This nicely illustrates the difficulty of properly handling errors with raw callbacks—it is easy to forget to properly route exceptions like that, and if you don’t do it, failures won’t get reported to the right callback. Promises make this mostly automatic and thus less error-prone.

▪ When working with collections of promises running at the same time, the Promise.all function can be useful. It returns a promise that waits for all of the promises in the array to resolve and then resolves to an array of the values that these promises produced (in the same order as the original array). If any promise is rejected, the result of Promise.all is itself rejected.

▪ When a neighbor isn’t available, we don’t want the entire combined promise to fail since then we still wouldn’t know anything. So the function that is mapped over the set of neighbors to turn them into request promises attaches handlers that make successful requests produce true and rejected ones produce false.

▪ This style of network communication is called flooding—it floods the network with a piece of information until all nodes have it.

▪ Comparing the JSON strings is a crude but effective way to compare their content.

▪ A distinguishing property of computer networks is that they aren’t reliable—abstractions built on top of them can help, but you can’t abstract away network failure. So network programming is typically very much about anticipating and dealing with failures.

▪ Because connections is a Map, Object.keys doesn’t work on it. It has a keys method, but that returns an iterator rather than an array. An iterator (or iterable value) can be converted to an array with the Array.from function.

▪ And the thing the code actually does is completely linear—it always waits for the previous action to complete before starting the next one. In a synchronous programming model, it’d be simpler to express.

▪ The good news is that JavaScript allows you to write pseudo-synchronous code to describe asynchronous computation

▪ An async function is a function that implicitly returns a promise and that can, in its body, await other promises in a way that looks synchronous.

▪ An async function is marked by the word async before the function keyword. Methods can also be made async by writing async before their name. When such a function or method is called, it returns a promise. As soon as the body returns something, that promise is resolved. If it throws an exception, the promise is rejected.

▪ Inside an async function, the word await can be put in front of an expression to wait for a promise to resolve and only then continue the execution of the function.

▪ Such a function no longer, like a regular JavaScript function, runs from start to completion in one go. Instead, it can be frozen at any point that has an await, and can be resumed at a later time.

▪ For non-trivial asynchronous code, this notation is usually more convenient than directly using promises. Even if you need to do something that doesn’t fit the synchronous model, such as perform multiple actions at the same time, it is easy to combine await with the direct use of promises.

▪ This ability of functions to be paused and then resumed again is not exclusive to async functions. JavaScript also has a feature called generator functions. These are similar, but without the promises.

▪ There’s no longer a need to create an object to hold the iteration state—generators automatically save their local state every time they yield.

▪ Such yield expressions may occur only directly in the generator function itself and not in an inner function you define inside of it.

▪ The state a generator saves, when yielding, is only its local environment and the position where it yielded.

▪ Asynchronous programs are executed piece by piece. Each piece may start some actions and schedule code to be executed when the action finishes or fails. In between these pieces, the program sits idle, waiting for the next action

▪ So callbacks are not directly called by the code that scheduled them

▪ If I call setTimeout from within a function, that function will have returned by the time the callback function is called. And when the callback returns, control does not go back to the function that scheduled it.

▪ Asynchronous behavior happens on its own empty function call stack. This is one of the reasons that, without promises, managing exceptions across asynchronous code is hard

▪ Promises always resolve or reject as a new event. Even if a promise is already resolved, waiting for it will cause your callback to run after the current script finishes, rather than right away

▪ When your program runs synchronously, in a single go, there are no state changes happening except those that the program itself makes. For asynchronous programs this is different—they may have gaps in their execution during which other code can run.

▪ But it is seriously broken. It’ll always return only a single line of output, listing the nest that was slowest to respond.

Can you work out why?

The problem lies in the += operator, which takes the current value of list at the time where the statement starts executing and then, when the await finishes, sets the list binding to be that value plus the added string.

▪ This could have easily been avoided by returning the lines from the mapped promises and calling join on the result of Promise.all, instead of building up the list by changing a binding. As usual, computing new values is less error-prone than changing existing values.

▪ Mistakes like this are easy to make, especially when using await, and you should be aware of where the gaps in your code occur. An advantage of JavaScript’s explicit asynchronicity (whether through callbacks, promises, or await) is that spotting these gaps is relatively easy

▪ Asynchronous programming makes it possible to express waiting for long-running actions without freezing the program during these actions

▪ JavaScript environments typically implement this style of programming using callbacks, functions that are called when the actions complete. An event loop schedules such callbacks to be called when appropriate, one after the other, so that their execution does not overlap.

▪ Programming asynchronously is made easier by promises, objects that represent actions that might complete in the future

▪ async functions, which allow you to write an asynchronous program as if it were synchronous.

▪ The evaluator, which determines the meaning of expressions in a programming language, is just another program.

Hal Abelson and Gerald Sussman, Structure and Interpretation of Computer Programs

▪ Building your own programming language is surprisingly easy (as long as you do not aim too high) and very enlightening.

▪ The most immediately visible part of a programming language is its syntax, or notation

▪ A parser is a program that reads a piece of text and produces a data structure that reflects the structure of the program contained in that text. If the text does not form a valid program, the parser should point out the error.

▪ The data structure that the parser will use to describe a program consists of expression objects, each of which has a type property indicating the kind of expression it is and other properties to describe its content.

▪ Expressions of type "value" represent literal strings or numbers. Their value property contains the string or number value that they represent. Expressions of type "word" are used for identifiers (names). Such objects have a name property that holds the identifier’s name as a string. Finally, "apply" expressions represent applications.

▪ The >(x, 5)
part of the previous program would be represented like this:

{
type: "apply",
operator: {type: "word", name: ">"},
args: [
{type: "word", name: "x"},
{type: "value", value: 5}
]
}

▪ Such a data structure is called a syntax tree. If you imagine the objects as dots and the links between them as lines between those dots, it has a treelike shape

▪ The fact that expressions contain other expressions, which in turn might contain more expressions, is similar to the way tree branches split and split again.

▪ Fortunately, this problem can be solved very well by writing a parser function that is recursive in a way that reflects the recursive nature of the language

▪ What can we do with the syntax tree for a program? Run it, of course! And that is what the evaluator does. You give it a syntax tree and a scope object that associates names with values, and it will evaluate the expression that the tree represents and return the value that this produces.

▪ The specialForms object is used to define special syntax in Egg. It associates words with functions that evaluate such forms. It is currently empty. Let’s add if.

▪ This is the program we’ve seen several times before, which computes the sum of the numbers 1 to 10, expressed in Egg. It is clearly uglier than the equivalent JavaScript program—but not bad for a language implemented in less than 150 lines of code.

▪ What we have built is an interpreter. During evaluation, it acts directly on the representation of the program produced by the parser.

▪ Compilation is the process of adding another step between the parsing and the running of a program, which transforms the program into something that can be evaluated more efficiently by doing as much work as possible in advance

▪ Traditionally, compilation involves converting the program to machine code, the raw format that a computer’s processor can execute. But any process that converts a program to a different representation can be thought of as compilation.

▪ If you compare the implementation of Egg, built on top of JavaScript, with the amount of work and complexity required to build a programming language directly on the raw functionality provided by a machine, the difference is huge. Regardless, this example ideally gave you an impression of the way programming languages work.

▪ Though the toy language in this chapter doesn’t do anything that couldn’t be done better in JavaScript, there are situations where writing small languages helps get real work done.

▪ Or imagine you are building a giant robotic dinosaur and need to program its behavior. JavaScript might not be the most effective way to do this. You might instead opt for a language that looks like this:

behavior walk
perform when
destination ahead
actions
move left-foot
move right-foot

behavior attack
perform when
Godzilla in-view
actions
fire laser-eyes
launch arm-rockets

▪ This is what is usually called a domain-specific language, a language tailored to express a narrow domain of knowledge. Such a language can be more expressive than a general-purpose language because it is designed to describe exactly the things that need to be described in its domain, and nothing else.

▪ The dream behind the Web is of a common information space in which we communicate by sharing information. Its universality is essential: the fact that a hypertext link can point to anything, be it personal, local or global, be it draft or highly polished.

Tim Berners-Lee, The World Wide Web: A very short personal history

▪ Without web browsers, there would be no JavaScript. Or even if there were, no one would ever have paid any attention to it.

▪ Web technology has been decentralized from the start, not just technically but also in the way it evolved. Various browser vendors have added new functionality in ad hoc and sometimes poorly thought-out ways, which then, sometimes, ended up being adopted by others—and finally set down as in standards.

▪ This is both a blessing and a curse. On the one hand, it is empowering to not have a central party control a system but have it be improved by various parties working in loose collaboration (or occasionally open hostility). On the other hand, the haphazard way in which the Web was developed means that the resulting system is not exactly a shining example of internal consistency. Some parts of it are downright confusing and poorly conceived.

▪ A network protocol describes a style of communication over a network. There are protocols for sending email, for fetching email, for sharing files, and even for controlling computers that happen to be infected by malicious software.

▪ For example, the Hypertext Transfer Protocol (HTTP) is a protocol for retrieving named resources (chunks of information, such as web pages or pictures). It specifies that the side making the request should start with a line like this, naming the resource and the version of the protocol that it is trying to use:

GET /index.html HTTP/1.1

▪ Most protocols are built on top of other protocols

▪ HTTP treats the network as a streamlike device into which you can put bits and have them arrive at the correct destination in the correct order.

▪ The Transmission Control Protocol (TCP) is a protocol that addresses this problem. All Internet-connected devices “speak” it, and most communication on the Internet is built on top of it.

▪ A TCP connection works as follows: one computer must be waiting, or listening, for other computers to start talking to it. To be able to listen for different kinds of communication at the same time on a single machine, each listener has a number (called a port) associated with it.

▪ Most protocols specify which port should be used by default. For example, when we want to send an email using the SMTP protocol, the machine through which we send it is expected to be listening on port 25.

▪ If the target machine can be reached and is listening on that port, the connection is successfully created. The listening computer is called the server, and the connecting computer is called the client.

▪ Such a connection acts as a two-way pipe through which bits can flow—the machines on both ends can put data into it.

▪ This is a convenient model. You could say that TCP provides an abstraction of the network.

▪ The World Wide Web (not to be confused with the Internet as a whole) is a set of protocols and formats that allow us to visit web pages in a browser

▪ The “Web” part in the name refers to the fact that such pages can easily link to each other, thus connecting into a huge mesh that users can move through.

▪ To become part of the Web, all you need to do is connect a machine to the Internet and have it listen on port 80 with the HTTP protocol so that other computers can ask it for documents

▪ Each document on the Web is named by a Uniform Resource Locator (URL),

▪ The first part tells us that this URL uses the HTTP protocol (as opposed to, for example, encrypted HTTP, which would be https://)

▪ Then comes the part that identifies which server we are requesting the document from.

▪ Last is a path string that identifies the specific document (or resource) we are interested in.

▪ Machines connected to the Internet get an IP address, which is a number that can be used to send messages to that machine, and looks something like 149.210.142.219 or 2001:4860:4860::8888.

▪ But lists of more or less random numbers are hard to remember and awkward to type, so you can instead register a domain name for a specific address or set of addresses. I registered eloquentjavascript.net to point at the IP address of a machine I control and can thus use that domain name to serve web pages.

▪ If you type this URL into your browser’s address bar, the browser will try to retrieve and display the document at that URL. First, your browser has to find out what address eloquentjavascript.net refers to. Then, using the HTTP protocol, it will make a connection to the server at that address and ask for the resource /13_browser.html. If all goes well, the server sends back a document, which your browser then displays on your screen.

▪ HTML, which stands for Hypertext Markup Language, is the document format used for web pages. An HTML document contains text, as well as tags that give structure to the text, describing things such as links, paragraphs, and headings.

▪ The document starts with 
, which tells the browser to interpret the page as modern HTML, as opposed to various dialects that were in use in the past.

▪ HTML documents have a head and a body. The head contains information about the document, and the body contains the document itself

▪ Some opening tags, such as the one for the link (), contain extra information in the form of name="value" pairs. These are called attributes. In this case, the destination of the link is indicated with href="http://eloquentjavascript.net", where href stands for “hypertext reference”.

▪ Some kinds of tags do not enclose anything and thus do not need to be closed. The metadata tag 
is an example of this.

▪ To be able to include angle brackets in the text of a document, even though they have a special meaning in HTML, yet another form of special notation has to be introduced. A plain opening angle bracket is written as < (“less than”), and a closing bracket is written as > (“greater than”)

▪ In HTML, an ampersand (&) character followed by a name or character code and a semicolon (;) is called an entity and will be replaced by the character it encodes.

▪ Inside attribute values, which are wrapped in double quotes, " can be used to insert an actual quote character.

▪ HTML is parsed in a remarkably error-tolerant way. When tags that should be there are missing, the browser reconstructs them. The way in which this is done has been standardized, and you can rely on all modern browsers to do it in the same way.

▪ The , , and tags are gone completely. The browser knows that and belong in the head and that 

means the body has started. Furthermore, I am no longer explicitly closing the paragraphs since opening a new paragraph or ending the document will close them implicitly. The quotes around the attribute values are also gone.

▪ Such a script will run as soon as its tag is encountered while the browser reads the HTML<br><br>▪ This page will pop up a dialog when opened—the alert function resembles prompt, in that it pops up a little window, but only shows a message without asking for input.<br><br>▪ Including large programs directly in HTML documents is often impractical. The <script> tag can be given an src attribute to fetch a script file (a text file containing a JavaScript program) from a URL.<br><br>▪ A script tag must always be closed with , even if it refers to a script file and doesn’t contain any code. If you forget this, the rest of the page will be interpreted as part of the script.

▪ You can load ES modules (see Chapter 10) in the browser by giving your script tag a type="module" attribute

▪ Some attributes can also contain a JavaScript program. The tag shown next (which shows up as a button) has an onclick attribute. The attribute’s value will be run whenever the button is clicked.

▪ DO NOT PRESS

▪ Note that I had to use single quotes for the string in the onclick attribute because double quotes are already used to quote the whole attribute. I could also have used ".

▪ Yet the attraction of the Web is that you can browse it without necessarily trusting all the pages you visit. This is why browsers severely limit the things a JavaScript program may do: it can’t look at the files on your computer or modify anything not related to the web page it was embedded in.

▪ Isolating a programming environment in this way is called sandboxing, the idea being that the program is harmlessly playing in a sandbox. But you should imagine this particular kind of sandbox as having a cage of thick steel bars over it so that the programs playing in it can’t actually get out.

▪ The hard part of sandboxing is allowing the programs enough room to be useful yet at the same time restricting them from doing anything dangerous. Lots of useful functionality, such as communicating with other servers or reading the content of the copy-paste clipboard, can also be used to do problematic, privacy-invading things.

▪ Every now and then, someone comes up with a new way to circumvent the limitations of a browser and do something harmful, ranging from leaking minor private information to taking over the whole machine that the browser runs on. The browser developers respond by fixing the hole, and all is well again—until the next problem is discovered, and hopefully publicized, rather than secretly exploited by some government agency or mafia.

▪ In the early stages of the Web, a browser called Mosaic dominated the market. After a few years, the balance shifted to Netscape, which was then, in turn, largely supplanted by Microsoft’s Internet Explorer. At any point where a single browser was dominant, that browser’s vendor would feel entitled to unilaterally invent new features for the Web. Since most users used the most popular browser, websites would simply start using those features—never mind the other browsers.

▪ This was the dark age of compatibility, often called the browser wars. Web developers were left with not one unified Web but two or three incompatible platforms. To make things worse, the browsers in use around 2003 were all full of bugs, and of course the bugs were different for each browser. Life was hard for people writing web pages.

▪ If you are starting to learn web development today, consider yourself lucky. The latest versions of the major browsers behave quite uniformly and have relatively few bugs.

▪ Too bad! Same old story! Once you’ve finished building your house you notice you’ve accidentally learned something that you really should have known—before you started.

Friedrich Nietzsche, Beyond Good and Evil

▪ The browser builds up a model of the document’s structure and uses this model to draw the page on the screen.

▪ This representation of the document is one of the toys that a JavaScript program has available in its sandbox.

▪ It is a data structure that you can read or modify. It acts as a live data structure: when it’s modified, the page on the screen is updated to reflect the changes.

▪ You can imagine an HTML document as a nested set of boxes. Tags such as 

and enclose other tags, which in turn contain other tags or text

▪ The data structure the browser uses to represent the document follows this shape. For each box, there is an object, which we can interact with to find out things such as what HTML tag it represents and which boxes and text it contains. This representation is called the Document Object Model, or DOM for short.

▪ Each node may refer to other nodes, children, which in turn may have their own children. This shape is typical of nested structures where elements can contain subelements that are similar to themselves.

▪ We call a data structure a tree when it has a branching structure, has no cycles (a node may not contain itself, directly or indirectly), and has a single, well-defined root. In the case of the DOM, document.documentElement serves as the root.

▪ Trees come up a lot in computer science. In addition to representing recursive structures such as HTML documents or programs, they are often used to maintain sorted sets of data because elements can usually be found or inserted more efficiently in a tree than in a flat array.

▪ Each DOM node object has a nodeType property, which contains a code (number) that identifies the type of node

▪ Elements have code 1, which is also defined as the constant property Node.ELEMENT_NODE. Text nodes, representing a section of text in the document, get code 3 (Node.TEXT_NODE). Comments have code 8 (Node.COMMENT_NODE).

▪ Later in this chapter, we’ll see that other parts of the DOM interface also feel cumbersome and alien. The reason for this is that the DOM wasn’t designed for just JavaScript. Rather, it tries to be a language-neutral interface that can be used in other systems as well—not just for HTML but also for XML, which is a generic data format with an HTML-like syntax.

▪ This is unfortunate. Standards are often useful. But in this case, the advantage (cross-language consistency) isn’t all that compelling. Having an interface that is properly integrated with the language you are using will save you more time than having a familiar interface across languages.

▪ As an example of this poor integration, consider the childNodes property that element nodes in the DOM have. This property holds an array-like object, with a length property and properties labeled by numbers to access the child nodes. But it is an instance of the NodeList type, not a real array, so it does not have methods such as slice and map.

▪ Then there are issues that are simply poor design. For example, there is no way to create a new node and immediately add children or attributes to it. Instead, you have to first create it and then add the children and attributes one by one, using side effects. Code that interacts heavily with the DOM tends to get long, repetitive, and ugly.

▪ But these flaws aren’t fatal. Since JavaScript allows us to create our own abstractions, it is possible to design improved ways to express the operations you are performing. Many libraries intended for browser programming come with such tools.

▪ every node has a parentNode property that points to the node it is part of, if any. Likewise, every element node (node type 1) has a childNodes property that points to an array-like object holding its children.

▪ In theory, you could move anywhere in the tree using just these parent and child links. But JavaScript also gives you access to a number of additional convenience links. The firstChild and lastChild properties point to the first and last child elements or have the value null for nodes without children.

▪ Similarly, previousSibling and nextSibling point to adjacent nodes, which are nodes with the same parent that appear immediately before or after the node itself. For a first child, previousSibling will be null, and for a last child, nextSibling will be null.

▪ There’s also the children property, which is like childNodes but contains only element (type 1) children, not other types of child nodes. This can be useful when you aren’t interested in text nodes.

▪ When dealing with a nested data structure like this one, recursive functions are often useful

▪ Navigating these links among parents, children, and siblings is often useful. But if we want to find a specific node in the document, reaching it by starting at document.body and following a fixed path of properties is a bad idea.

▪ Doing so bakes assumptions into our program about the precise structure of the document—a structure you might want to change later

▪ Another complicating factor is that text nodes are created even for the whitespace between nodes. The example document’s tag does not have just three children (

and two 

elements) but actually has seven: those three, plus the spaces before, after, and between them.

▪ All element nodes have a getElementsByTagName method, which collects all elements with the given tag name that are descendants (direct or indirect children) of that node and returns them as an array-like object.

▪ To find a specific single node, you can give it an id attribute and use document.getElementById instead.

▪ A third, similar method is getElementsByClassName, which, like getElementsByTagName, searches through the contents of an element node and retrieves all elements that have the given string in their class attribute.

▪ Almost everything about the DOM data structure can be changed. The shape of the document tree can be modified by changing parent-child relationships. Nodes have a remove method to remove them from their current parent node. To add a child node to an element node, we can use appendChild, which puts it at the end of the list of children, or insertBefore, which inserts the node given as the first argument before the node given as the second argument.

▪ document.body.insertBefore(paragraphs[2], paragraphs[0]);

▪ A node can exist in the document in only one place. Thus, inserting paragraph Three in front of paragraph One will first remove it from the end of the document and then insert it at the front, resulting in Three/One/Two. All operations that insert a node somewhere will, as a side effect, cause it to be removed from its current position (if it has one).

▪ The replaceChild method is used to replace a child node with another one. It takes as arguments two nodes: a new node and the node to be replaced. The replaced node must be a child of the element the method is called on

▪ Note that both replaceChild and insertBefore expect the new node as their first argument.

▪ The loop that goes over the images starts at the end of the list. This is necessary because the node list returned by a method like getElementsByTagName (or a property like childNodes) is live.

▪ That is, it is updated as the document changes. If we started from the front, removing the first image would cause the list to lose its first element so that the second time the loop repeats, where i is 1, it would stop because the length of the collection is now also 1.

▪ If you want a solid collection of nodes, as opposed to a live one, you can convert the collection to a real array by calling Array.from.

▪ let arrayish = {0: "one", 1: "two", length: 2};
let array = Array.from(arrayish);
console.log(array.map(s => s.toUpperCase()));
// → ["ONE", "TWO"]

▪ To create element nodes, you can use the document.createElement method. This method takes a tag name and returns a new empty node of the given type.

▪ The following example defines a utility elt, which creates an element node and treats the rest of its arguments as children to that node.

▪ <br> function elt(type, ...children) {<br> let node = document.createElement(type);<br> for (let child of children) {<br> if (typeof child != "string") node.appendChild(child);<br> else node.appendChild(document.createTextNode(child));<br> }<br> return node;<br> }<br><br>▪ Some element attributes, such as href for links, can be accessed through a property of the same name on the element’s DOM object. This is the case for most commonly used standard attributes<br><br>▪ But HTML allows you to set any attribute you want on nodes. This can be useful because it allows you to store extra information in a document<br><br>▪ If you make up your own attribute names, though, such attributes will not be present as properties on the element’s node. Instead, you have to use the getAttribute and setAttribute methods to work with them.<br><br>▪ It is recommended to prefix the names of such made-up attributes with data- to ensure they do not conflict with any other attributes.<br><br>▪ There is a commonly used attribute, class, which is a keyword in the JavaScript language. For historical reasons—some old JavaScript implementations could not handle property names that matched keywords—the property used to access this attribute is called className.<br><br>▪ You can also access it under its real name, "class", by using the getAttribute and setAttribute methods.<br><br>▪ You may have noticed that different types of elements are laid out differently. Some, such as paragraphs (<p>) or headings (<h1>), take up the whole width of the document and are rendered on separate lines<br><br>▪ These are called block elements. Others, such as links (<a>) or the <strong> element, are rendered on the same line with their surrounding text. Such elements are called inline elements.<br><br>▪ The size and position of an element can be accessed from JavaScript. The offsetWidth and offsetHeight properties give you the space the element takes up in pixels.<br><br>▪ A pixel is the basic unit of measurement in the browser. It traditionally corresponds to the smallest dot that the screen can draw, but on modern displays, which can draw very small dots, that may no longer be the case, and a browser pixel may span multiple display dots.<br><br>▪ Similarly, clientWidth and clientHeight give you the size of the space inside the element, ignoring border width.<br><br>▪ The most effective way to find the precise position of an element on the screen is the getBoundingClientRect method. It returns an object with top, bottom, left, and right properties, indicating the pixel positions of the sides of the element relative to the top left of the screen. If you want them relative to the whole document, you must add the current scroll position, which you can find in the pageXOffset and pageYOffset bindings.<br><br>▪ Laying out a document can be quite a lot of work. In the interest of speed, browser engines do not immediately re-layout a document every time you change it but wait as long as they can.<br><br>▪ When a JavaScript program that changed the document finishes running, the browser will have to compute a new layout to draw the changed document to the screen.<br><br>▪ When a program asks for the position or size of something by reading properties such as offsetHeight or calling getBoundingClientRect, providing correct information also requires computing a layout.<br><br>▪ A program that repeatedly alternates between reading DOM layout information and changing the DOM forces a lot of layout computations to happen and will consequently run very slowly<br><br>▪ The way an <img> tag shows an image or an <a> tag causes a link to be followed when it is clicked is strongly tied to the element type. But we can change the styling associated with an element, such as the text color or underline.<br><br>▪ We won’t be using style sheets all that much in this book. Understanding them is helpful when programming in the browser, but they are complicated enough to warrant a separate book.<br><br>▪ Unlike methods such as getElementsByTagName, the object returned by querySelectorAll is not live. It won’t change when you change the document<br><br>▪ It is still not a real array, though, so you still need to call Array.from if you want to treat it like one.<br><br>▪ The querySelector method (without the All part) works in a similar way. This one is useful if you want a specific, single element. It will return only the first matching element or null when no element matches.<br><br>▪ The script uses requestAnimationFrame to schedule the animate function to run whenever the browser is ready to repaint the screen.<br><br>▪ The animate function itself again calls requestAnimationFrame to schedule the next update. When the browser window (or tab) is active, this will cause updates to happen at a rate of about 60 per second, which tends to produce a good-looking animation.<br><br>▪ If we just updated the DOM in a loop, the page would freeze, and nothing would show up on the screen. Browsers do not update their display while a JavaScript program is running, nor do they allow any interaction with the page<br><br>▪ This is why we need requestAnimationFrame—it lets the browser know that we are done for now, and it can go ahead and do the things that browsers do, such as updating the screen and responding to user actions.<br><br>▪ The animation function is passed the current time as an argument. To ensure that the motion of the cat per millisecond is stable, it bases the speed at which the angle changes on the difference between the current time and the last time the function ran<br><br>▪ If it just moved the angle by a fixed amount per step, the motion would stutter if, for example, another heavy task running on the same computer were to prevent the function from running for a fraction of a second.<br><br>▪ Math.cos and Math.sin are useful for finding points that lie on a circle around point (0,0) with a radius of one<br><br>▪ The constant π is available as Math.PI in JavaScript.<br><br>▪ Note that styles usually need units. In this case, we have to append "px" to the number to tell the browser that we are counting in pixels (as opposed to centimeters, “ems”, or other units). This is easy to forget.<br><br>▪ Using numbers without units will result in your style being ignored—unless the number is 0, which always means the same thing, regardless of its unit.<br><br>▪ JavaScript programs may inspect and interfere with the document that the browser is displaying through a data structure called the DOM<br><br>▪ This data structure represents the browser’s model of the document, and a JavaScript program can modify it to change the visible document.<br><br>▪ The DOM is organized like a tree, in which elements are arranged hierarchically according to the structure of the document. The objects representing elements have properties such as parentNode and childNodes, which can be used to navigate through this tree.<br><br>▪ JavaScript code can manipulate an element’s style directly through its style property.<br><br>▪ Some programs work with direct user input, such as mouse and keyboard actions. That kind of input isn’t available as a well-organized data structure—it comes in piece by piece, in real time, and the program is expected to respond to it as it happens.<br><br>▪ Imagine an interface where the only way to find out whether a key on the keyboard is being pressed is to read the current state of that key. To be able to react to keypresses, you would have to constantly read the key’s state so that you’d catch it before it’s released again. It would be dangerous to perform other time-intensive computations since you might miss a keypress.<br><br>▪ Some primitive machines do handle input like that. A step up from this would be for the hardware or operating system to notice the keypress and put it in a queue. A program can then periodically check the queue for new events and react to what it finds there.<br><br>▪ Of course, it has to remember to look at the queue, and to do it often, because any time between the key being pressed and the program noticing the event will cause the software to feel unresponsive. This approach is called polling. Most programmers prefer to avoid<br><br>▪ A better mechanism is for the system to actively notify our code when an event occurs. Browsers do this by allowing us to register functions as handlers for specific events.<br><br>▪ The window binding refers to a built-in object provided by the browser. It represents the browser window that contains the document<br><br>▪ Calling its addEventListener method registers the second argument to be called whenever the event described by its first argument occurs.<br><br>▪ Each browser event handler is registered in a context. In the previous example we called addEventListener on the window object to register a handler for the whole window. Such a method can also be found on DOM elements and some other types of objects. Event listeners are called only when the event happens in the context of the object they are registered on.<br><br>▪ That example attaches a handler to the button node. Clicks on the button cause that handler to run, but clicks on the rest of the document do not.<br><br>▪ Giving a node an onclick attribute has a similar effect. This works for most types of events—you can attach a handler through the attribute whose name is the event name with on in front of it.<br><br>▪ But a node can have only one onclick attribute, so you can register only one handler per node that way. The addEventListener method allows you to add any number of handlers so that it is safe to add handlers even if there is already another handler on the element.<br><br>▪ The removeEventListener method, called with arguments similar to addEventListener, removes a handler.<br><br>▪ The function given to removeEventListener has to be the same function value that was given to addEventListener. So, to unregister a handler, you’ll want to give the function a name (once, in the example) to be able to pass the same function value to both methods.<br><br>▪ Though we have ignored it so far, event handler functions are passed an argument: the event object<br><br>▪ This object holds additional information about the event. For example, if we want to know which mouse button was pressed, we can look at the event object’s button property.<br><br>▪ The information stored in an event object differs per type of event. We’ll discuss different types later in the chapter. The object’s type property always holds a string identifying the event (such as "click" or "mousedown").<br><br>▪ Propagation<br><br>For most event types, handlers registered on nodes with children will also receive events that happen in the children. If a button inside a paragraph is clicked, event handlers on the paragraph will also see the click event.<br><br>▪ But if both the paragraph and the button have a handler, the more specific handler—the one on the button—gets to go first<br><br>▪ The event is said to propagate outward, from the node where it happened to that node’s parent node and on to the root of the document.<br><br>▪ Finally, after all handlers registered on a specific node have had their turn, handlers registered on the whole window get a chance to respond to the event.<br><br>▪ At any point, an event handler can call the stopPropagation method on the event object to prevent handlers further up from receiving the event. This can be useful when, for example, you have a button inside another clickable element and you don’t want clicks on the button to activate the outer element’s click behavior.<br><br>▪ Most event objects have a target property that refers to the node where they originated. You can use this property to ensure that you’re not accidentally handling something that propagated up from a node you do not want to handle.<br><br>▪ It is also possible to use the target property to cast a wide net for a specific type of event. For example, if you have a node containing a long list of buttons, it may be more convenient to register a single click handler on the outer node and have it use the target property to figure out whether a button was clicked, rather than register individual handlers on all of the buttons.<br><br>▪ Many events have a default action associated with them. If you click a link, you will be taken to the link’s target. If you press the down arrow, the browser will scroll the page down. If you right-click, you’ll get a context menu. And so on.<br><br>▪ For most types of events, the JavaScript event handlers are called before the default behavior takes place. If the handler doesn’t want this normal behavior to happen, typically because it has already taken care of handling the event, it can call the preventDefault method on the event object.<br><br>▪ This can be used to implement your own keyboard shortcuts or context menu. It can also be used to obnoxiously interfere with the behavior that users expect. For example, here is a link that cannot be followed:<br><br><a href="https://developer.mozilla.org/">MDN</a><br><script><br> let link = document.querySelector("a");<br> link.addEventListener("click", event => {<br> console.log("Nope.");<br> event.preventDefault();<br> });<br>

▪ Depending on the browser, some events can’t be intercepted at all. On Chrome, for example, the keyboard shortcut to close the current tab (control-W or command-W) cannot be handled by JavaScript.

▪ When a key on the keyboard is pressed, your browser fires a "keydown" event. When it is released, you get a "keyup" event.

▪ Despite its name, "keydown" fires not only when the key is physically pushed down. When a key is pressed and held, the event fires again every time the key repeats. Sometimes you have to be careful about this. For example, if you add a button to the DOM when a key is pressed and remove it again when the key is released, you might accidentally add hundreds of buttons when the key is held down longer.

▪ The example looked at the key property of the event object to see which key the event is about. This property holds a string that, for most keys, corresponds to the thing that pressing that key would type. For special keys such as enter, it holds a string that names the key ("Enter", in this case). If you hold shift while pressing a key, that might also influence the name of the key—"v" becomes "V", and "1" may become "!", if that is what pressing shift-1 produces on your keyboard.

▪ But when looking for key combinations, you can also find out whether these keys are held down by looking at the shiftKey, ctrlKey, altKey, and metaKey properties of keyboard and mouse events.

▪ The DOM node where a key event originates depends on the element that has focus when the key is pressed

▪ Most nodes cannot have focus unless you give them a tabindex attribute, but things like links, buttons, and form fields can.

▪ When nothing in particular has focus, document.body acts as the target node of key events.

▪ When the user is typing text, using key events to figure out what is being typed is problematic

▪ Some platforms, most notably the virtual keyboard on Android phones, don’t fire key events

▪ But even when you have an old-fashioned keyboard, some types of text input don’t match key presses in a straightforward way, such as input method editor (IME) software used by people whose scripts don’t fit on a keyboard, where multiple key strokes are combined to create characters.

▪ To notice when something was typed, elements that you can type into, such as the and tags, fire "input" events whenever the user changes their content

▪ There are currently two widely used ways to point at things on a screen: mice (including devices that act like mice, such as touchpads and trackballs) and touchscreens. These produce different kinds of events.

▪ Pressing a mouse button causes a number of events to fire. The "mousedown" and "mouseup" events are similar to "keydown" and "keyup" and fire when the button is pressed and released. These happen on the DOM nodes that are immediately below the mouse pointer when the event occurs.

▪ After the "mouseup" event, a "click" event fires on the most specific node that contained both the press and the release of the button.

▪ if I press down the mouse button on one paragraph and then move the pointer to another paragraph and release the button, the "click" event will happen on the element that contains both those paragraphs

▪ If two clicks happen close together, a "dblclick" (double-click) event also fires, after the second click event.

▪ To get precise information about the place where a mouse event happened, you can look at its clientX and clientY properties, which contain the event’s coordinates (in pixels) relative to the top-left corner of the window, or pageX and pageY, which are relative to the top-left corner of the whole document (which may be different when the window has been scrolled).

▪ Every time the mouse pointer moves, a "mousemove" event is fired. This event can be used to track the position of the mouse. A common situation in which this is useful is when implementing some form of mouse-dragging functionality.

▪ As an example, the following program displays a bar and sets up event handlers so that dragging to the left or right on this bar makes it narrower or wider:

▪ Note that the "mousemove" handler is registered on the whole window. Even if the mouse goes outside of the bar during resizing, as long as the button is held we still want to update its size.

▪ We must stop resizing the bar when the mouse button is released. For that, we can use the buttons property (note the plural), which tells us about the buttons that are currently held down. When this is zero, no buttons are down. When buttons are held, its value is the sum of the codes for those buttons—the left button has code 1, the right button 2, and the middle one 4. With the left and right buttons held, for example, the value of buttons will be 3.

▪ Note that the order of these codes is different from the one used by button, where the middle button came before the right one.

▪ As mentioned, consistency isn’t really a strong point of the browser’s programming interface.

▪ The style of graphical browser that we use was designed with mouse interfaces in mind, at a time where touchscreens were rare. To make the Web “work” on early touchscreen phones, browsers for those devices pretended, to a certain extent, that touch events were mouse events

▪ If you tap your screen, you’ll get "mousedown", "mouseup", and "click" events.

▪ But this illusion isn’t very robust. A touchscreen works differently from a mouse: it doesn’t have multiple buttons, you can’t track the finger when it isn’t on the screen (to simulate "mousemove"), and it allows multiple fingers to be on the screen at the same time.

▪ Mouse events cover touch interaction only in straightforward cases—if you add a "click" handler to a button, touch users will still be able to use it. But something like the resizeable bar in the previous example does not work on a touchscreen.

▪ There are specific event types fired by touch interaction. When a finger starts touching the screen, you get a "touchstart" event. When it is moved while touching, "touchmove" events fire. Finally, when it stops touching the screen, you’ll see a "touchend" event.

▪ Because many touchscreens can detect multiple fingers at the same time, these events don’t have a single set of coordinates associated with them. Rather, their event objects have a touches property, which holds an array-like object of points, each of which has its own clientX, clientY, pageX, and pageY properties.

▪ You could do something like this to show red circles around every touching finger:

▪ You’ll often want to call preventDefault in touch event handlers to override the browser’s default behavior (which may include scrolling the page on swiping) and to prevent the mouse events from being fired, for which you may also have a handler.

▪ Whenever an element is scrolled, a "scroll" event is fired on it.

▪ This has various uses, such as knowing what the user is currently looking at (for disabling off-screen animations or sending spy reports to your evil headquarters) or showing some indication of progress (by highlighting part of a table of contents or showing a page number).

▪ The following example draws a progress bar above the document and updates it to fill up as you scroll down:

▪ Giving an element a position of fixed acts much like an absolute position but also prevents it from scrolling along with the rest of the document. The effect is to make our progress bar stay at the top

▪ The global innerHeight binding gives us the height of the window, which we have to subtract from the total scrollable height—you can’t keep scrolling when you hit the bottom of the document

▪ By dividing pageYOffset, the current scroll position, by the maximum scroll position and multiplying by 100, we get the percentage for the progress bar.

▪ Calling preventDefault on a scroll event does not prevent the scrolling from happening. In fact, the event handler is called only after the scrolling takes place.

▪ When an element gains focus, the browser fires a "focus" event on it. When it loses focus, the element gets a "blur" event.

▪ Unlike the events discussed earlier, these two events do not propagate. A handler on a parent element is not notified when a child element gains or loses focus.

▪ When a page finishes loading, the "load" event fires on the window and the document body objects. This is often used to schedule initialization actions that require the whole document to have been built.

▪ Elements such as images and script tags that load an external file also have a "load" event that indicates the files they reference were loaded.

▪ Like the focus-related events, loading events do not propagate.

▪ When a page is closed or navigated away from (for example, by following a link), a "beforeunload" event fires

▪ The main use of this event is to prevent the user from accidentally losing work by closing a document. If you prevent the default behavior on this event and set the returnValue property on the event object to a string, the browser will show the user a dialog asking if they really want to leave the page

▪ That dialog might include your string, but because some malicious sites try to use these dialogs to confuse people into staying on their page to look at dodgy weight loss ads, most browsers no longer display them.

▪ They are scheduled when the event occurs but must wait for other scripts that are running to finish before they get a chance to run.

▪ The fact that events can be processed only when nothing else is running means that, if the event loop is tied up with other work, any interaction with the page (which happens through events) will be delayed until there’s time to process it

▪ So if you schedule too much work, either with long-running event handlers or with lots of short-running ones, the page will become slow and cumbersome to use

▪ For cases where you really do want to do some time-consuming thing in the background without freezing the page, browsers provide something called web workers. A worker is a JavaScript process that runs alongside the main script, on its own timeline.

▪ Imagine that squaring a number is a heavy, long-running computation that we want to perform in a separate thread. We could write a file called code/squareworker.js that responds to messages by computing a square and sending a message back.

▪ To avoid the problems of having multiple threads touching the same data, workers do not share their global scope or any other data with the main script’s environment. Instead, you have to communicate with them by sending messages back and forth.

▪ let squareWorker = new Worker("code/squareworker.js");
squareWorker.addEventListener("message", event => {
console.log("The worker responded:", event.data);
});
squareWorker.postMessage(10);
squareWorker.postMessage(24);

▪ The postMessage function sends a message, which will cause a "message" event to fire in the receiver

▪ Only values that can be represented as JSON can be sent as messages—the other side will receive a copy of them, rather than the value itself.

▪ Sometimes you need to cancel a function you have scheduled. This is done by storing the value returned by setTimeout and calling clearTimeout on it.

▪ The cancelAnimationFrame function works in the same way as clearTimeout—calling it on a value returned by requestAnimationFrame will cancel that frame (assuming it hasn’t already been called).

▪ A similar set of functions, setInterval and clearInterval, are used to set timers that should repeat every X milliseconds.

▪ Some types of events have the potential to fire rapidly, many times in a row (the "mousemove" and "scroll" events, for example). When handling such events, you must be careful not to do anything too time-consuming or your handler will take up so much time that interaction with the document starts to feel slow.

▪ If you do need to do something nontrivial in such a handler, you can use setTimeout to make sure you are not doing it too often. This is usually called debouncing the event. There are several slightly different approaches to this.

▪ In the first example, we want to react when the user has typed something, but we don’t want to do it immediately for every input event. When they are typing quickly, we just want to wait until a pause occurs. Instead of immediately performing an action in the event handler, we set a timeout. We also clear the previous timeout (if any) so that when events occur close together (closer than our timeout delay), the timeout from the previous event will be canceled.

▪ Giving an undefined value to clearTimeout or calling it on a timeout that has already fired has no effect. Thus, we don’t have to be careful about when to call it, and we simply do so for every event.

▪ We can use a slightly different pattern if we want to space responses so that they’re separated by at least a certain length of time but want to fire them during a series of events, not just afterward. For example, we might want to respond to "mousemove" events by showing the current coordinates of the mouse but only every 250 milliseconds.

▪ Event handlers make it possible to detect and react to events happening in our web page. The addEventListener method is used to register such a handler.

▪ Each event has a type ("keydown", "focus", and so on) that identifies it. Most events are called on a specific DOM element and then propagate to that element’s ancestors, allowing handlers associated with those elements to handle them.

▪ When an event handler is called, it is passed an event object with additional information about the event. This object also has methods that allow us to stop further propagation (stopPropagation) and prevent the browser’s default handling of the event (preventDefault).

▪ Pressing a key fires "keydown" and "keyup" events. Pressing a mouse button fires "mousedown", "mouseup", and "click" events.

▪ Moving the mouse fires "mousemove" events.

▪ Touchscreen interaction will result in "touchstart", "touchmove", and "touchend" events.

▪ Scrolling can be detected with the "scroll" event, and focus changes can be detected with the "focus" and "blur" events

▪ When the document finishes loading, a "load" event fires on the window.

▪ Much of my initial fascination with computers, like that of many nerdy kids, had to do with computer games. I was drawn into the tiny simulated worlds that I could manipulate and in which stories (sort of) unfolded—more, I suppose, because of the way I projected my imagination into them than because of the possibilities they actually offered.

▪ I don’t wish a career in game programming on anyone. Much like the music industry, the discrepancy between the number of eager young people wanting to work in it and the actual demand for such people creates a rather unhealthy environment. But writing games for fun is amusing.

▪ This chapter will walk through the implementation of a small platform game. Platform games (or “jump and run” games) are games that expect the player to move a figure through a world, which is usually two-dimensional and viewed from the side, while jumping over and onto things.

▪ Our game will be roughly based on Dark Blue (www.lessmilk.com/games/10) by Thomas Palef. I chose that game because it is both entertaining and minimalist and because it can be built without too much code

▪ We will use the browser DOM to display the game, and we’ll read user input by handling key events.

▪ In games and other programs that should animate graphics and respond to user input without noticeable delay, efficiency is important. Although the DOM was not originally designed for high-performance graphics, it is actually better at this than you would expect.

▪ On a modern machine, a simple game like this performs well, even if we don’t worry about optimization very much.

▪ In the next chapter, we will explore another browser technology, the tag, which provides a more traditional way to draw graphics, working in terms of shapes and pixels rather than DOM elements.

▪ We’ll want a human-readable, human-editable way to specify levels. Since it is okay for everything to start out on a grid, we could use big strings in which each character represents an element—either a part of the background grid or a moving element.

▪ The plan for a small level might look like this:

let simpleLevelPlan = `
......................
..#................#..
..#..............=.#..
..#.........o.o....#..
..#.@......#####...#..
..#####............#..
......#++++++++++++#..
......##############..
......................`;

▪ Periods are empty space, hash (#) characters are walls, and plus signs are lava. The player’s starting position is the at sign (@). Every O character is a coin, and the equal sign (=) at the top is a block of lava that moves back and forth horizontally.

▪ We’ll support two additional kinds of moving lava: the pipe character (|) creates vertically moving blobs, and v indicates dripping lava—vertically moving lava that doesn’t bounce back and forth but only moves down, jumping back to its start position when it hits the floor.

▪ A whole game consists of multiple levels that the player must complete. A level is completed when all coins have been collected. If the player touches lava, the current level is restored to its starting position, and the player may try again.

▪ The following class stores a level object. Its argument should be the string that defines the level.

▪ So rows holds an array of arrays of characters, the rows of the plan. We can derive the level’s width and height from these

▪ But we must still separate the moving elements from the background grid. We’ll call moving elements actors. They’ll be stored in an array of objects. The background will be an array of arrays of strings, holding field types such as "empty", "wall", or "lava".

▪ As the game runs, actors will end up in different places or even disappear entirely (as coins do when collected). We’ll use a State class to track the state of a running game.

▪ The status property will switch to "lost" or "won" when the game has ended.

▪ Actor objects represent the current position and state of a given moving element in our game. All actor objects conform to the same interface. Their pos property holds the coordinates of the element’s top-left corner, and their size property holds its size.

▪ A type property contains a string that identifies the type of the actor—"player", "coin", or "lava". This is useful when drawing the game—the look of the rectangle drawn for an actor is based on its type.

▪ Actor classes have a static create method that is used by the Level constructor to create an actor from a character in the level plan

▪ The player class has a property speed that stores its current speed to simulate momentum and gravity.

▪ Coin actors are relatively simple. They mostly just sit in their place. But to liven up the game a little, they are given a “wobble”, a slight vertical back-and-forth motion. To track this, a coin object stores a base position as well as a wobble property that tracks the phase of the bouncing motion. Together, these determine the coin’s actual position (stored in the pos property).

▪ To avoid a situation where all coins move up and down synchronously, the starting phase of each coin is randomized.

▪ The task ahead is to display such levels on the screen and to model time and motion inside them.

▪ Most of the code in this chapter does not worry about encapsulation very much for two reasons. First, encapsulation takes extra effort. It makes programs bigger and requires additional concepts and interfaces to be introduced. Since there is only so much code you can throw at a reader before their eyes glaze over, I’ve made an effort to keep the program small.

▪ Second, the various elements in this game are so closely tied together that if the behavior of one of them changed, it is unlikely that any of the others would be able to stay the same. Interfaces between the elements would end up encoding a lot of assumptions about the way the game works. This makes them a lot less effective—whenever you change one part of the system, you still have to worry about the way it impacts the other parts because their interfaces wouldn’t cover the new situation.

▪ Some cutting points in a system lend themselves well to separation through rigorous interfaces, but others don’t. Trying to encapsulate something that isn’t a suitable boundary is a sure way to waste a lot of energy. When you are making this mistake, you’ll usually notice that your interfaces are getting awkwardly large and detailed and that they need to be changed often, as the program evolves.

▪ There is one thing that we will encapsulate, and that is the drawing subsystem. The reason for this is that we’ll display the same game in a different way in the next chapter. By putting the drawing behind an interface, we can load the same game program there and plug in a new display module.

▪ The display type we define in this chapter is called DOMDisplay because it uses DOM elements to show the level.

▪ The level’s background grid, which never changes, is drawn once. Actors are redrawn every time the display is updated with a given state. The actorLayer property will be used to track the element that holds the actors so that they can be easily removed and replaced.

▪ Our coordinates and sizes are tracked in grid units, where a size or distance of 1 means one grid block. When setting pixel sizes, we will have to scale these coordinates up—everything in the game would be ridiculously small at a single pixel per square

▪ The scale constant gives the number of pixels that a single unit takes up on the screen.

▪ As mentioned, the background is drawn as a element. This nicely corresponds to the structure of the rows property of the level—each row of the grid is turned into a table row (

element). The strings in the grid are used as class names for the table cell () elements.

▪ Moving things is easy. The difficult part is dealing with the interactions between the elements. When the player hits a wall or floor, they should not simply move through it.

▪ The game must notice when a given motion causes an object to hit another object and respond accordingly. For walls, the motion must be stopped. When hitting a coin, it must be collected. When touching lava, the game should be lost.

▪ Solving this for the general case is a big task. You can find libraries, usually called physics engines, that simulate interaction between physical objects in two or three dimensions. We’ll take a more modest approach in this chapter, handling only collisions between rectangular objects and handling them in a rather simplistic way.

▪ Vertical motion works in a similar way but has to simulate jumping and gravity. The player’s vertical speed (ySpeed) is first accelerated to account for gravity.

▪ For a game like this, we do not want keys to take effect once per keypress. Rather, we want their effect (moving the player figure) to stay active as long as they are held.

▪ We need to set up a key handler that stores the current state of the left, right, and up arrow keys. We will also want to call preventDefault for those keys so that they don’t end up scrolling the page.

▪ The requestAnimationFrame function, which we saw in Chapter 14, provides a good way to animate a game. But its interface is quite primitive—using it requires us to track the time at which our function was called the last time around and call requestAnimationFrame again after every frame.

▪ Let’s define a helper function that wraps those boring parts in a convenient interface and allows us to simply call runAnimation, giving it a function that expects a time difference as an argument and draws a single frame. When the frame function returns the value false, the animation stops.

▪ I have set a maximum frame step of 100 milliseconds (one-tenth of a second

▪ When the browser tab or window with our page is hidden, requestAnimationFrame calls will be suspended until the tab or window is shown again

▪ In this case, the difference between lastTime and time will be the entire time in which the page was hidden. Advancing the game by that much in a single step would look silly and might cause weird side effects, such as the player falling through the floor.

▪ This page feeds them to runGame, starting an actual game.




<br> runGame(GAME_LEVELS, DOMDisplay);<br> 


▪ The arrowKeys object is currently a global binding, and its event handlers are kept around even when no game is running. You could say they leak out of our system.

▪ Extend trackKeys to provide a way to unregister its handlers and then change runLevel to register its handlers when it starts and unregister them again when it is finished.

▪ It is traditional for platform games to have enemies that you can jump on top of to defeat. This exercise asks you to add such an actor type to the game.

▪ Browsers give us several ways to display graphics. The simplest way is to use styles to position and color regular DOM elements.

▪ But we’d be using the DOM for something that it wasn’t originally designed for. Some tasks, such as drawing a line between arbitrary points, are extremely awkward to do with regular HTML elements.

▪ The first is DOM-based but utilizes Scalable Vector Graphics (SVG), rather than HTML. Think of SVG as a document-markup dialect that focuses on shapes rather than text. You can embed an SVG document directly in an HTML document or include it with an ￼ tag.

▪ The second alternative is called a canvas. A canvas is a single DOM element that encapsulates a picture. It provides a programming interface for drawing shapes onto the space taken up by the node.

▪ The main difference between a canvas and an SVG picture is that in SVG the original description of the shapes is preserved so that they can be moved or resized at any time. A canvas, on the other hand, converts the shapes to pixels (colored dots on a raster) as soon as they are drawn and does not remember what these pixels represent.

▪ The only way to move a shape on a canvas is to clear the canvas (or the part of the canvas around the shape) and redraw it with the shape in a new position.

▪ The xmlns attribute changes an element (and its children) to a different XML namespace. This namespace, identified by a URL, specifies the dialect that we are currently speaking

▪ The and tags, which do not exist in HTML, do have a meaning in SVG—they draw shapes using the style and position specified by their attributes.

▪ Canvas graphics can be drawn onto a element. You can give such an element width and height attributes to determine its size in pixels.

▪ A new canvas is empty, meaning it is entirely transparent and thus shows up as empty space in the document.

▪ The tag is intended to allow different styles of drawing. To get access to an actual drawing interface, we first need to create a context, an object whose methods provide the drawing interface

▪ There are currently two widely supported drawing styles: "2d" for two-dimensional graphics and "webgl" for three-dimensional graphics through the OpenGL interface.

▪ This book won’t discuss WebGL—we’ll stick to two dimensions. But if you are interested in three-dimensional graphics, I do encourage you to look into WebGL. It provides a direct interface to graphics hardware and allows you to render even complicated scenes efficiently, using JavaScript.

▪ You create a context with the getContext method on the DOM element

▪ Just like in HTML (and SVG), the coordinate system that the canvas uses puts (0,0) at the top-left corner, and the positive y-axis goes down from there. So (10,10) is 10 pixels below and to the right of the top-left corner.

▪ In the canvas interface, a shape can be filled, meaning its area is given a certain color or pattern, or it can be stroked, which means a line is drawn along its edge. The same terminology is used by SVG.

▪ The fillRect method fills a rectangle. It takes first the x- and y-coordinates of the rectangle’s top-left corner, then its width, and then its height. A similar method, strokeRect, draws the outline of a rectangle.

▪ Neither method takes any further parameters. The color of the fill, thickness of the stroke, and so on, are not determined by an argument to the method (as you might reasonably expect) but rather by properties of the context object.

▪ The fillStyle property controls the way shapes are filled. It can be set to a string that specifies a color, using the color notation used by CSS

▪ The strokeStyle property works similarly but determines the color used for a stroked line

▪ The width of that line is determined by the lineWidth property, which may contain any positive number.

▪ When no width or height attribute is specified, as in the example, a canvas element gets a default width of 300 pixels and height of 150 pixels.

▪ A path is a sequence of lines

▪ The 2D canvas interface takes a peculiar approach to describing such a path. It is done entirely through side effects. Paths are not values that can be stored and passed around. Instead, if you want to do something with a path, you make a sequence of method calls to describe its shape.

▪ cx.beginPath();
for (let y = 10; y < 100; y += 10) {
cx.moveTo(10, y);
cx.lineTo(90, y);
}
cx.stroke();

▪ This example creates a path with a number of horizontal line segments and then strokes it using the stroke method.

▪ Each segment created with lineTo starts at the path’s current position. That position is usually the end of the last segment, unless moveTo was called.

▪ When filling a path (using the fill method), each shape is filled separately. A path can contain multiple shapes—each moveTo motion starts a new one. But the path needs to be closed (meaning its start and end are in the same position) before it can be filled. If the path is not already closed, a line is added from its end to its start, and the shape enclosed by the completed path is filled.

▪ cx.beginPath();
cx.moveTo(50, 10);
cx.lineTo(10, 70);
cx.lineTo(90, 70);
cx.fill();

▪ This example draws a filled triangle. Note that only two of the triangle’s sides are explicitly drawn. The third, from the bottom-right corner back to the top, is implied and wouldn’t be there when you stroke the path.

▪ You could also use the closePath method to explicitly close a path by adding an actual line segment back to the path’s start.

▪ A path may also contain curved lines. These are unfortunately a bit more involved to draw.

▪ cx.beginPath();
cx.moveTo(10, 90);
// control=(60,10) goal=(90,90)
cx.quadraticCurveTo(60, 10, 90, 90);
cx.lineTo(60, 10);
cx.closePath();
cx.stroke();

▪ We draw a quadratic curve from the left to the right, with (60,10) as control point, and then draw two line segments going through that control point and back to the start of the line

▪ You can see the effect of the control point: the lines leaving the lower corners start off in the direction of the control point and then curve toward their target.

▪ The bezierCurveTo method draws a similar kind of curve. Instead of a single control point, this one has two—one for each of the line’s endpoints

▪ cx.beginPath();
cx.moveTo(10, 90);
// control1=(10,10) control2=(90,10) goal=(50,90)
cx.bezierCurveTo(10, 10, 90, 10, 50, 90);
cx.lineTo(90, 10);
cx.lineTo(10, 10);
cx.closePath();
cx.stroke();

▪ The two control points specify the direction at both ends of the curve. The farther they are away from their corresponding point, the more the curve will “bulge” in that direction.

▪ The arc method is a way to draw a line that curves along the edge of a circle. It takes a pair of coordinates for the arc’s center, a radius, and then a start angle and end angle.

▪ cx.beginPath();
// center=(50,50) radius=40 angle=0 to 7
cx.arc(50, 50, 40, 0, 7);
// center=(150,50) radius=40 angle=0 to ½π
cx.arc(150, 50, 40, 0, 0.5 * Math.PI);
cx.stroke();

▪ Like other path-drawing methods, a line drawn with arc is connected to the previous path segment. You can call moveTo or start a new path to avoid this.

▪ To draw a pie chart, we draw a number of pie slices, each made up of an arc and a pair of lines to the center of that arc. We can compute the angle taken up by each arc by dividing a full circle (2π) by the total number of responses and then multiplying that number (the angle per response) by the number of people who picked a given choice.

▪ A 2D canvas drawing context provides the methods fillText and strokeText. The latter can be useful for outlining letters, but usually fillText is what you need. It will fill the outline of the given text with the current fillStyle.

▪ You can specify the size, style, and font of the text with the font property. This example just gives a font size and family name. It is also possible to add italic or bold to the start of the string to select a style

▪ The last two arguments to fillText and strokeText provide the position at which the font is drawn. By default, they indicate the position of the start of the text’s alphabetic baseline, which is the line that letters “stand” on, not counting hanging parts in letters such as j or p.

▪ You can change the horizontal position by setting the textAlign property to "end" or "center" and the vertical position by setting textBaseline to "top", "middle", or "bottom".

▪ In computer graphics, a distinction is often made between vector graphics and bitmap graphics. The first is what we have been doing so far in this chapter—specifying a picture by giving a logical description of shapes. Bitmap graphics, on the other hand, don’t specify actual shapes but rather work with pixel data (rasters of colored dots).

▪ The drawImage method allows us to draw pixel data onto a canvas. This pixel data can originate from an ￼ element or from another canvas

▪ But it cannot immediately start drawing from this picture because the browser may not have loaded it yet. To deal with this, we register a "load" event handler and do the drawing after the image has loaded.

▪ 
<br> let cx = document.querySelector("canvas").getContext("2d");<br> let img = document.createElement("img");<br> img.src = "img/hat.png";<br> img.addEventListener("load", () => {<br> for (let x = 10; x < 200; x += 30) {<br> cx.drawImage(img, x, 10);<br> }<br> });<br>

▪ By default, drawImage will draw the image at its original size. You can also give it two additional arguments to set a different width and height.

▪ When drawImage is given nine arguments, it can be used to draw only a fragment of an image. The second through fifth arguments indicate the rectangle (x, y, width, and height) in the source image that should be copied, and the sixth to ninth arguments give the rectangle (on the canvas) into which it should be copied.

▪ This can be used to pack multiple sprites (image elements) into a single image file and then draw only the part you need

▪ To animate a picture on a canvas, the clearRect method is useful. It resembles fillRect, but instead of coloring the rectangle, it makes it transparent, removing the previously drawn pixels.

▪ We know that each sprite, each subpicture, is 24 pixels wide and 30 pixels high. The following code loads the image and then sets up an interval (repeated timer) to draw the next frame:

▪ But what if we want our character to walk to the left instead of to the right? We could draw another set of sprites, of course. But we can also instruct the canvas to draw the picture the other way round.

▪ Calling the scale method will cause anything drawn after it to be scaled. This method takes two parameters, one to set a horizontal scale and one to set a vertical scale.

▪ Scaling by a negative amount will flip the picture around. The flipping happens around point (0,0), which means it will also flip the direction of the coordinate system

▪ When a horizontal scaling of -1 is applied, a shape drawn at x position 100 will end up at what used to be position -100.

▪ So to turn a picture around, we can’t simply add cx.scale(-1, 1)
before the call to drawImage because that would move our picture outside of the canvas, where it won’t be visible.

▪ You could adjust the coordinates given to drawImage to compensate for this by drawing the image at x position -50 instead of 0

▪ Another solution, which doesn’t require the code that does the drawing to know about the scale change, is to adjust the axis around which the scaling happens.

▪ There are several other methods besides scale that influence the coordinate system for a canvas. You can rotate subsequently drawn shapes with the rotate method and move them with the translate method.

▪ The interesting—and confusing—thing is that these transformations stack, meaning that each one happens relative to the previous transformations.

▪ To flip a picture around the vertical line at a given x position, we can do the following:

function flipHorizontally(context, around) {
context.translate(around, 0);
context.scale(-1, 1);
context.translate(-around, 0);
}

▪ Transformations stick around. Everything else we draw after drawing that mirrored character would also be mirrored. That might be inconvenient.

▪ It is possible to save the current transformation, do some drawing and transforming, and then restore the old transformation. This is usually the proper thing to do for a function that needs to temporarily transform the coordinate system.

▪ The save and restore methods on the 2D canvas context do this transformation management. They conceptually keep a stack of transformation states. When you call save, the current state is pushed onto the stack, and when you call restore, the state on top of the stack is taken off and used as the context’s current transformation.

▪ You can also call resetTransform to fully reset the transformation.

▪ cx.save();
cx.translate(0, length);
cx.rotate(-angle);
branch(length * scale, angle, scale);
cx.rotate(2 * angle);
branch(length * scale, angle, scale);
cx.restore();

▪ This object keeps a little more information than DOMDisplay. Rather than using the scroll position of its DOM element, it tracks its own viewport, which tells us what part of the level we are currently looking at. Finally, it keeps a flipPlayer property so that even when the player is standing still, it keeps facing the direction it last moved in.

▪ Because shapes on a canvas are just pixels, after we draw them there is no good way to move them (or remove them). The only way to update the canvas display is to clear it and redraw the scene. We may also have scrolled, which requires the background to be in a different position.

▪ We don’t bother waiting for the sprite image to load. Calling drawImage with an image that hasn’t been loaded yet will simply do nothing. Thus, we might fail to draw the game properly for the first few frames, while the image is still loading, but that is not a serious problem. Since we keep updating the screen, the correct scene will appear as soon as the loading finishes

▪ The first eight sprites contain a walking animation. When the player is moving along a floor, we cycle through them based on the current time. We want to switch frames every 60 milliseconds, so the time is divided by 60 first. When the player is standing still, we draw the ninth sprite.

▪ During jumps, which are recognized by the fact that the vertical speed is not zero, we use the tenth, rightmost sprite.

▪ Because the sprites are slightly wider than the player object—24 instead of 16 pixels to allow some space for feet and arms—the method has to adjust the x-coordinate and width by a given amount (playerXOverlap).

▪ When drawing something that is not the player, we look at its type to find the offset of the correct sprite. The lava tile is found at offset 20, and the coin sprite is found at 40 (two times scale).

▪ So when you need to generate graphics in the browser, you can choose between plain HTML, SVG, and canvas. There is no single best approach that works in all situations. Each option has strengths and weaknesses.

▪ Plain HTML has the advantage of being simple. It also integrates well with text. Both SVG and canvas allow you to draw text, but they won’t help you position that text or wrap it when it takes up more than one line.

▪ SVG can be used to produce crisp graphics that look good at any zoom level. Unlike HTML, it is designed for drawing and is thus more suitable for that purpose.

▪ Both SVG and HTML build up a data structure (the DOM) that represents your picture. This makes it possible to modify elements after they are drawn. If you need to repeatedly change a small part of a big picture in response to what the user is doing or as part of an animation, doing it in a canvas can be needlessly expensive. The DOM also allows us to register mouse event handlers on every element in the picture (even on shapes drawn with SVG). You can’t do that with canvas.

▪ But canvas’s pixel-oriented approach can be an advantage when drawing a huge number of tiny elements. The fact that it does not build up a data structure but only repeatedly draws onto the same pixel surface gives canvas a lower cost per shape.

▪ There are also effects, such as rendering a scene one pixel at a time (for example, using a ray tracer) or postprocessing an image with JavaScript (blurring or distorting it), that can be realistically handled only by a pixel-based approach.

▪ In some cases, you may want to combine several of these techniques. For example, you might draw a graph with SVG or canvas but show textual information by positioning an HTML element on top of the picture.

▪ For nondemanding applications, it really doesn’t matter much which interface you choose. The display we built for our game in this chapter could have been implemented using any of these three graphics technologies since it does not need to draw text, handle mouse interaction, or work with an extraordinarily large number of elements.

▪ A canvas node represents an area in a document that our program may draw on. This drawing is done through a drawing context object, created with the getContext method.

▪ The 2D drawing interface allows us to fill and stroke various shapes. The context’s fillStyle property determines how shapes are filled. The strokeStyle and lineWidth properties control the way lines are drawn.

▪ The fillRect and strokeRect methods draw rectangles, and the fillText and strokeText methods draw text.

▪ To create custom shapes, we must first build up a path.

▪ Calling beginPath starts a new path. A number of other methods add lines and curves to the current path.

▪ Moving pixels from an image or another canvas onto our canvas is done with the drawImage method.

▪ By default, this method draws the whole source image, but by giving it more parameters, you can copy a specific area of the image. We used this for our game by copying individual poses of the game character out of an image that contained many such poses.

▪ Transformations allow you to draw a shape in multiple orientations. A 2D drawing context has a current transformation that can be changed with the translate, scale, and rotate methods

▪ These will affect all subsequent drawing operations. A transformation state can be saved with the save method and restored with the restore method.

▪ When showing an animation on a canvas, the clearRect method can be used to clear part of the canvas before redrawing it.

▪ Use the requestAnimationFrame technique that we saw in Chapter 14 and Chapter 16 to draw a box with a bouncing ball in it. The ball moves at a constant speed and bounces off the box’s sides when it hits them.

▪ One unfortunate thing about transformations is that they slow down the drawing of bitmaps. The position and size of each pixel has to be transformed, and though it is possible that browsers will get cleverer about transformation in the future, they currently cause a measurable increase in the time it takes to draw a bitmap.

▪ Communication must be stateless in nature [...] such that each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server.

Roy Fielding, Architectural Styles and the Design of Network-based Software Architectures

▪ The Hypertext Transfer Protocol, already mentioned in Chapter 13, is the mechanism through which data is requested and provided on the World Wide Web

▪ If you type eloquentjavascript.net/18_http.html into your browser’s address bar, the browser first looks up the address of the server associated with eloquentjavascript.net and tries to open a TCP connection to it on port 80, the default port for HTTP traffic.

▪ If the server exists and accepts the connection, the browser might send something like this:

GET /18_http.html HTTP/1.1
Host: eloquentjavascript.net
User-Agent: Your browser's name

▪ Then the server responds, through that same connection.

HTTP/1.1 200 OK
Content-Length: 65585
Content-Type: text/html
Last-Modified: Mon, 08 Jan 2018 10:29:45 GMT


... the rest of the document

▪ The browser takes the part of the response after the blank line, its body (not to be confused with the HTML tag), and displays it as an HTML document.

▪ The information sent by the client is called the request. It starts with this line:

GET /18_http.html HTTP/1.1

▪ The first word is the method of the request. GET means that we want to get the specified resource. Other common methods are DELETE to delete a resource, PUT to create or replace it, and POST to send information to it.

▪ Note that the server is not obliged to carry out every request it gets. If you walk up to a random website and tell it to DELETE its main page, it’ll probably refuse.

▪ The part after the method name is the path of the resource the request applies to. In the simplest case, a resource is simply a file on the server, but the protocol doesn’t require it to be. A resource may be anything that can be transferred as if it is a file. Many servers generate the responses they produce on the fly. For example, if you open https://github.com/marijnh, the server looks in its database for a user named “marijnh”, and if it finds one, it will generate a profile page for that user.

▪ After the resource path, the first line of the request mentions HTTP/1.1 to indicate the version of the HTTP protocol it is using

▪ In practice, many sites use HTTP version 2, which supports the same concepts as version 1.1 but is a lot more complicated so that it can be faster. Browsers will automatically switch to the appropriate protocol version when talking to a given server, and the outcome of a request is the same regardless of which version is used

▪ Because version 1.1 is more straightforward and easier to play around with, we’ll focus on that.

▪ The server’s response will start with a version as well, followed by the status of the response, first as a three-digit status code and then as a human-readable string.

HTTP/1.1 200 OK

▪ Status codes starting with a 2 indicate that the request succeeded

▪ Codes starting with 4 mean there was something wrong with the request

▪ 404 is probably the most famous HTTP status code—it means that the resource could not be found.

▪ Codes that start with 5 mean an error happened on the server and the request is not to blame.

▪ The first line of a request or response may be followed by any number of headers. These are lines in the form name: value
that specify extra information about the request or response

▪ These headers were part of the example response:

Content-Length: 65585
Content-Type: text/html
Last-Modified: Thu, 04 Jan 2018 14:05:30 GMT

▪ For most headers, the client and server are free to decide whether to include them in a request or response. But a few are required.

▪ For example, the Host header, which specifies the hostname, should be included in a request because a server might be serving multiple hostnames on a single IP address, and without that header, the server won’t know which hostname the client is trying to talk to.

▪ After the headers, both requests and responses may include a blank line followed by a body, which contains the data being sent

▪ GET and DELETE requests don’t send along any data, but PUT and POST requests do.

▪ Similarly, some response types, such as error responses, do not require a body.

▪ As we saw in the example, a browser will make a request when we enter a URL in its address bar. When the resulting HTML page references other files, such as images and JavaScript files, those are also retrieved.

▪ A moderately complicated website can easily include anywhere from 10 to 200 resources. To be able to fetch those quickly, browsers will make several GET requests simultaneously, rather than waiting for the responses one at a time

▪ HTML pages may include forms, which allow the user to fill out information and send it to the server.

▪ 

Name: 


Message:


Send




▪ When you click the Send button, the form is submitted, meaning that the content of its field is packed into an HTTP request and the browser navigates to the result of that request.

▪ When the element’s method attribute is GET (or is omitted), the information in the form is added to the end of the action URL as a query string. The browser might make a request to this URL:

GET /example/message.html?name=Jean&message=Yes%3F HTTP/1.1

▪ The actual message encoded in the URL is “Yes?”, but the question mark is replaced by a strange code. Some characters in query strings must be escaped

▪ The question mark, represented as %3F, is one of those. There seems to be an unwritten rule that every format needs its own way of escaping characters. This one, called URL encoding, uses a percent sign followed by two hexadecimal (base 16) digits that encode the character code. In this case, 3F, which is 63 in decimal notation, is the code of a question mark character.

▪ JavaScript provides the encodeURIComponent and decodeURIComponent functions to encode and decode this format.

▪ If we change the method attribute of the HTML form in the example we saw earlier to POST, the HTTP request made to submit the form will use the POST method and put the query string in the body of the request, rather than adding it to the URL.

▪ POST /example/message.html HTTP/1.1
Content-length: 24
Content-type: application/x-www-form-urlencoded

name=Jean&message=Yes%3F

▪ GET requests should be used for requests that do not have side effects but simply ask for information.

▪ Requests that change something on the server, for example creating a new account or posting a message, should be expressed with other methods, such as POST.

▪ Client-side software such as a browser knows that it shouldn’t blindly make POST requests but will often implicitly make GET requests

▪ Fetch

The interface through which browser JavaScript can make HTTP requests is called fetch.

▪ console.log(response.headers.get("Content-Type"));
// → text/plain
});

▪ Calling fetch returns a promise that resolves to a Response object holding information about the server’s response, such as its status code and its headers.

▪ The headers are wrapped in a Map-like object that treats its keys (the header names) as case insensitive because header names are not supposed to be case sensitive. This means headers.get("Content-Type") and headers.get("content-TYPE") will return the same value.

▪ Note that the promise returned by fetch resolves successfully even if the server responded with an error code

▪ It might also be rejected if there is a network error or if the server that the request is addressed to can’t be found.

▪ The first argument to fetch is the URL that should be requested

▪ When that URL doesn’t start with a protocol name (such as http:), it is treated as relative, which means it is interpreted relative to the current document.

▪ When it starts with a slash (/), it replaces the current path, which is the part after the server name. When it does not, the part of the current path up to and including its last slash character is put in front of the relative URL.

▪ To get at the actual content of a response, you can use its text method

▪ fetch("example/data.txt")
.then(resp => resp.text())
.then(text => console.log(text));
// → This is the content of data.txt

▪ A similar method, called json, returns a promise that resolves to the value you get when parsing the body as JSON or rejects if it’s not valid JSON.

▪ By default, fetch uses the GET method to make its request and does not include a request body

▪ You can configure it differently by passing an object with extra options as a second argument.

▪ For example, this request tries to delete example/data.txt:

fetch("example/data.txt", {method: "DELETE"}).then(resp => {
console.log(resp.status);
// → 405
});

▪ The 405 status code means “method not allowed”, an HTTP server’s way of saying “I can’t do that”.

▪ To add a request body, you can include a body option

▪ To set headers, there’s the headers option.

▪ The browser will automatically add some request headers, such as “Host” and those needed for the server to figure out the size of the body

▪ But adding your own headers is often useful to include things such as authentication information or to tell the server which file format you’d like to receive.

▪ Making HTTP requests in web page scripts once again raises concerns about security. The person who controls the script might not have the same interests as the person on whose computer it is running

▪ More specifically, if I visit themafia.org, I do not want its scripts to be able to make a request to mybank.com, using identifying information from my browser, with instructions to transfer all my money to some random account.

▪ For this reason, browsers protect us by disallowing scripts to make HTTP requests to other domains (names such as themafia.org and mybank.com).

▪ This can be an annoying problem when building systems that want to access several domains for legitimate reasons. Fortunately, servers can include a header like this in their response to explicitly indicate to the browser that it is okay for the request to come from another domain:

Access-Control-Allow-Origin: *

▪ When building a system that requires communication between a JavaScript program running in the browser (client-side) and a program on a server (server-side), there are several different ways to model this communication.

▪ A commonly used model is that of remote procedure calls. In this model, communication follows the patterns of normal function calls, except that the function is actually running on another machine

▪ Calling it involves making a request to the server that includes the function’s name and arguments. The response to that request contains the returned value.

▪ When thinking in terms of remote procedure calls, HTTP is just a vehicle for communication, and you will most likely write an abstraction layer that hides it entirely.

▪ Another approach is to build your communication around the concept of resources and HTTP methods.

▪ Instead of a remote procedure called addUser, you use a PUT request to /users/larry. Instead of encoding that user’s properties in function arguments, you define a JSON document format (or use an existing format) that represents a user.

▪ The body of the PUT request to create a new resource is then such a document. A resource is fetched by making a GET request to the resource’s URL (for example, /user/larry), which again returns the document representing the resource.

▪ This second approach makes it easier to use some of the features that HTTP provides, such as support for caching resources (keeping a copy on the client for fast access).

▪ The concepts used in HTTP, which are well designed, can provide a helpful set of principles to design your server interface around.

▪ Data traveling over the Internet tends to follow a long, dangerous road. To get to its destination, it must hop through anything from coffee shop Wi-Fi hotspots to networks controlled by various companies and states. At any point along its route it may be inspected or even modified.

▪ If it is important that something remain secret, such as the password to your email account, or that it arrive at its destination unmodified, such as the account number you transfer money to via your bank’s website, plain HTTP is not good enough.

▪ The secure HTTP protocol, used for URLs starting with https://, wraps HTTP traffic in a way that makes it harder to read and tamper with.

▪ Before exchanging data, the client verifies that the server is who it claims to be by asking it to prove that it has a cryptographic certificate issued by a certificate authority that the browser recognizes

▪ Next, all data going over the connection is encrypted in a way that should prevent eavesdropping and tampering.

▪ Thus, when it works right, HTTPS prevents other people from impersonating the website you are trying to talk to and from snooping on your communication

▪ It is not perfect, and there have been various incidents where HTTPS failed because of forged or stolen certificates and broken software, but it is a lot safer than plain HTTP.

▪ Forms were originally designed for the pre-JavaScript Web to allow web sites to send user-submitted information in an HTTP request. This design assumes that interaction with the server always happens by navigating to a new page.

▪ But their elements are part of the DOM like the rest of the page, and the DOM elements that represent form fields support a number of properties and events that are not present on other elements. These make it possible to inspect and control such input fields with JavaScript programs and do things such as adding new functionality to a form or using forms and fields as building blocks in a JavaScript application.

▪ A web form consists of any number of input fields grouped in a tag. HTML allows several different styles of fields, ranging from simple on/off checkboxes to drop-down menus and fields for text input.

▪ A lot of field types use the tag. This tag’s type attribute is used to select the field’s style.

▪ Form fields do not necessarily have to appear in a tag. You can put them anywhere in a page

▪ Such form-less fields cannot be submitted (only a form as a whole can), but when responding to input with JavaScript, we often don’t want to submit our fields normally anyway.

▪ Multiline text fields have their own tag, , mostly because using an attribute to specify a multiline starting value would be awkward

▪ The tag requires a matching closing tag and uses the text between those two, instead of the value attribute, as starting text.

▪ Finally, the tag is used to create a field that allows the user to select from a number of predefined options.


Pancakes
Pudding
Ice cream


▪ Whenever the value of a form field changes, it will fire a "change" event.

▪ Unlike most elements in HTML documents, form fields can get keyboard focus

▪ When clicked or activated in some other way, they become the currently active element and the recipient of keyboard input.

▪ Thus, you can type into a text field only when it is focused

▪ For example, a menu tries to move to the option that contains the text the user typed and responds to the arrow keys by moving its selection up and down

▪ We can control focus from JavaScript with the focus and blur methods. The first moves focus to the DOM element it is called on, and the second removes focus

▪ The value in document.activeElement corresponds to the currently focused element.

▪ document.querySelector("input").focus();

▪ console.log(document.activeElement.tagName);
// → INPUT

▪ For some pages, the user is expected to want to interact with a form field immediately. JavaScript can be used to focus this field when the document is loaded, but HTML also provides the autofocus attribute, which produces the same effect while letting the browser know what we are trying to achieve.

▪ Browsers traditionally also allow the user to move the focus through the document by pressing the tab key.

▪ We can influence the order in which elements receive focus with the tabindex attribute.

▪ By default, most types of HTML elements cannot be focused. But you can add a tabindex attribute to any element that will make it focusable. A tabindex of -1 makes tabbing skip over an element, even if it is normally focusable.

▪ All form fields can be disabled through their disabled attribute

▪ It is an attribute that can be specified without value—the fact that it is present at all disables the element.

▪ Disabled fields cannot be focused or changed, and browsers make them look gray and faded.

▪ When a program is in the process of handling an action caused by some button or other control that might require communication with the server and thus take a while, it can be a good idea to disable the control until the action finishes. That way, when the user gets impatient and clicks it again, they don’t accidentally repeat their action.

▪ When a field is contained in a element, its DOM element will have a form property linking back to the form’s DOM element

▪ The element, in turn, has a property called elements that contains an array-like collection of the fields inside it.

▪ The name attribute of a form field determines the way its value will be identified when the form is submitted

▪ It can also be used as a property name when accessing the form’s elements property, which acts both as an array-like object (accessible by number) and a map (accessible by name).

▪ A button with a type attribute of submit will, when pressed, cause the form to be submitted. Pressing enter when a form field is focused has the same effect.

▪ Submitting a form normally means that the browser navigates to the page indicated by the form’s action attribute, using either a GET or a POST request

▪ But before that happens, a "submit" event is fired. You can handle this event with JavaScript and prevent this default behavior by calling preventDefault on the event object.

▪ Intercepting "submit" events in JavaScript has various uses. We can write code to verify that the values the user entered make sense and immediately show an error message instead of submitting the form

▪ Or we can disable the regular way of submitting the form entirely, as in the example, and have our program handle the input, possibly using fetch to send it to a server without reloading the page.

▪ Fields created by tags, or tags with a type of text or password, share a common interface. Their DOM elements have a value property that holds their current content as a string value. Setting this property to another string changes the field’s content.

▪ The selectionStart and selectionEnd properties of text fields give us information about the cursor and selection in the text.

▪ When nothing is selected, these two properties hold the same number, indicating the position of the cursor.

▪ When part of the field is selected, the two properties will differ, giving us the start and end of the selected text. Like value, these properties may also be written to.

▪ Imagine you are writing an article about Khasekhemwy but have some trouble spelling his name. The following code wires up a tag with an event handler that, when you press F2, inserts the string “Khasekhemwy” for you.

▪ The replaceSelection function replaces the currently selected part of a text field’s content with the given word and then moves the cursor after that word so that the user can continue typing.

▪ The "change" event for a text field does not fire every time something is typed. Rather, it fires when the field loses focus after its content was changed

▪ To respond immediately to changes in a text field, you should register a handler for the "input" event instead, which fires for every time the user types a character, deletes text, or otherwise manipulates the field’s content.

▪ The following example shows a text field and a counter displaying the current length of the text in the field:

▪ A checkbox field is a binary toggle. Its value can be extracted or changed through its checked property, which holds a Boolean value.

▪ The tag associates a piece of document with an input field. Clicking anywhere on the label will activate the field, which focuses it and toggles its value when it is a checkbox or radio button

▪ A radio button is similar to a checkbox, but it’s implicitly linked to other radio buttons with the same name attribute so that only one of them can be active at any time.

▪ Select fields are conceptually similar to radio buttons—they also allow the user to choose from a set of options. But where a radio button puts the layout of the options under our control, the appearance of a tag is determined by the browser

▪ Each tag has a value. This value can be defined with a value attribute. When that is not given, the text inside the option will count as its value

▪ The value property of a element reflects the currently selected option

▪ For a multiple field, though, this property doesn’t mean much since it will give the value of only one of the currently selected options.

▪ The tags for a field can be accessed as an array-like object through the field’s options property

▪ Each option has a property called selected, which indicates whether that option is currently selected.

▪ The property can also be written to select or deselect an option.

▪ File fields were originally designed as a way to upload files from the user’s machine through a form

▪ In modern browsers, they also provide a way to read such files from JavaScript programs.

▪ The field acts as a kind of gatekeeper. The script cannot simply start reading private files from the user’s computer, but if the user selects a file in such a field, the browser interprets that action to mean that the script may read the file.

▪ The files property of a file field element is an array-like object (again, not a real array) containing the files chosen in the field. It is initially empty

▪ The reason there isn’t simply a file property is that file fields also support a multiple attribute, which makes it possible to select multiple files at the same time.

▪ Objects in the files object have properties such as name (the filename), size (the file’s size in bytes, which are chunks of 8 bits), and type (the media type of the file, such as text/plain or image/jpeg).

What it does not have is a property that contains the content of the file.

▪ Since reading a file from disk can take time, the interface must be asynchronous to avoid freezing the document.

▪ let reader = new FileReader();
reader.addEventListener("load", () => {
console.log("File", file.name, "starts with",
reader.result.slice(0, 20));
});
reader.readAsText(file);
}
});

▪ Reading a file is done by creating a FileReader object, registering a "load" event handler for it, and calling its readAsText method, giving it the file we want to read. Once loading finishes, the reader’s result property contains the file’s content.

▪ FileReaders also fire an "error" event when reading the file fails for any reason. The error object itself will end up in the reader’s error property. This interface was designed before promises became part of the language. You could wrap it in a promise like this:

▪ Browsers do enforce a limit on the size of the data a site can store in localStorage. That restriction, along with the fact that filling up people’s hard drives with junk is not really profitable, prevents the feature from eating up too much space.

▪ Simple HTML pages with a bit of JavaScript can be a great format for “mini applications”—small helper programs that automate basic tasks. By connecting a few form fields with event handlers, you can do anything from converting between centimeters and inches to computing passwords from a master password and a website name.

▪ When such an application needs to remember something between sessions, you cannot use JavaScript bindings—those are thrown away every time the page is closed. You could set up a server, connect it to the Internet, and have your application store something there.

▪ The localStorage object can be used to store data in a way that survives page reloads. This object allows you to file string values under names.

▪ A value in localStorage sticks around until it is overwritten, it is removed with removeItem, or the user clears their local data.

▪ Sites from different domains get different storage compartments. That means data stored in localStorage by a given website can, in principle, be read (and overwritten) only by scripts on that same site.

▪ The following code implements a crude note-taking application. It keeps a set of named notes and allows the user to edit notes and create new ones.

▪ Reading a field that does not exist from localStorage will yield null. Passing null to JSON.parse will make it parse the string "null" and return null. Thus, the || operator can be used to provide a default value in a situation like this.

▪ There is another object, similar to localStorage, called sessionStorage. The difference between the two is that the content of sessionStorage is forgotten at the end of each session, which for most browsers means whenever the browser is closed.

▪ In this chapter, we discussed how the HTTP protocol works. A client sends a request, which contains a method (usually GET) and a path that identifies a resource. The server then decides what to do with the request and responds with a status code and a response body

▪ Both requests and responses may contain headers that provide additional information.

▪ The interface through which browser JavaScript can make HTTP requests is called fetch.

▪ Browsers make GET requests to fetch the resources needed to display a web page

▪ A page may also contain forms, which allow information entered by the user to be sent as a request for a new page when the form is submitted.

▪ HTML can represent various types of form fields, such as text fields, checkboxes, multiple-choice fields, and file pickers.

▪ Such fields can be inspected and manipulated with JavaScript. They fire the "change" event when changed, fire the "input" event when text is typed, and receive keyboard events when they have keyboard focus

▪ Properties like value (for text and select fields) or checked (for checkboxes and radio buttons) are used to read or set the field’s content.

▪ When a form is submitted, a "submit" event is fired on it.

▪ A JavaScript handler can call preventDefault on that event to disable the browser’s default behavior.

▪ Form field elements may also occur outside of a form tag.

▪ When the user has selected a file from their local file system in a file picker field, the FileReader interface can be used to access the content of this file from a JavaScript program.

▪ The localStorage and sessionStorage objects can be used to save information in a way that survives page reloads.

▪ One of the things HTTP can do is called content negotiation. The Accept request header is used to tell the server what type of document the client would like to get. Many servers ignore this header, but when a server knows of various ways to encode a resource, it can look at this header and send the one that the client prefers.

▪ Conway’s Game of Life is a simple simulation that creates artificial “life” on a grid, each cell of which is either alive or not. Each generation (turn), the following rules are applied:

Any live cell with fewer than two or more than three live neighbors dies.

Any live cell with two or three live neighbors lives on to the next generation.

Any dead cell with exactly three live neighbors becomes a live cell.

▪ Note that these rules are applied to the whole grid at once, not one square at a time. That means the counting of neighbors is based on the situation at the start of the generation, and changes happening to neighbor cells during this generation should not influence the new state of a given cell.

▪ Our application will be a pixel drawing program, where you can modify a picture pixel by pixel by manipulating a zoomed-in view of it, shown as a grid of colored squares. You can use the program to open image files, scribble on them with your mouse or other pointer device, and save them.

▪ The interface for the application shows a big element on top, with a number of form fields below it. The user draws on the picture by selecting a tool from a field and then clicking, touching, or dragging across the canvas. There are tools for drawing single pixels or rectangles, for filling an area, and for picking a color from the picture.

▪ We will structure the editor interface as a number of components, objects that are responsible for a piece of the DOM and that may contain other components inside them.

▪ To see why this is important, let’s consider the alternative—distributing pieces of state throughout the interface. Up to a certain point, this is easier to program. We can just put in a color field and read its value when we need to know the current color.

But then we add the color picker—a tool that lets you click the picture to select the color of a given pixel. To keep the color field showing the correct color, that tool would have to know that it exists and update it whenever it picks a new color. If you ever add another place that makes the color visible (maybe the mouse cursor could show it), you have to update your color-changing code to keep that synchronized.

▪ In effect, this creates a problem where each part of the interface needs to know about all other parts, which is not very modular. For small applications like the one in this chapter, that may not be a problem. For bigger projects, it can turn into a real nightmare.

▪ To avoid this nightmare on principle, we’re going to be strict about data flow. There is a state, and the interface is drawn based on that state. An interface component may respond to user actions by updating the state, at which point the components get a chance to synchronize themselves with this new state.

▪ In practice, each component is set up so that when it is given a new state, it also notifies its child components, insofar as those need to be updated. Setting this up is a bit of a hassle. Making this more convenient is the main selling point of many browser programming libraries. But for a small application like this, we can do it without such infrastructure.

▪ Updates to the state are represented as objects, which we’ll call actions. Components may create such actions and dispatch them—give them to a central state management function. That function computes the next state, after which the interface components update themselves to this new state.

▪ We’re taking the messy task of running a user interface and applying some structure to it. Though the DOM-related pieces are still full of side effects, they are held up by a conceptually simple backbone: the state update cycle.

▪ There are many variants of this approach, each with its own benefits and problems, but their central idea is the same: state changes should go through a single well-defined channel, not happen all over the place.

▪ With touch events, we have to do something similar, but using different events and making sure we call preventDefault on the "touchstart" event to prevent panning.

▪ We also need to be able to change the color, so let’s add a control for that. An HTML element with a type attribute of color gives us a form field that is specialized for selecting colors. Such a field’s value is always a CSS color code in "#RRGGBB" format (red, green, and blue components, two digits per color). The browser will show a color picker interface when the user interacts with it.

▪ When we’ve drawn our masterpiece, we’ll want to save it for later. We should add a button for downloading the current picture as an image file

▪ To get access to a file on the user’s computer, we need the user to select the file through a file input field. But I don’t want the load button to look like a file input field, so we create the file input when the button is clicked and then pretend that this file input itself was clicked.

▪ We’ll limit the size of images to 100 by 100 pixels since anything bigger will look huge on our display and might slow down the interface.

▪ Undo history

Half of the process of editing is making little mistakes and correcting them. So an important feature in a drawing program is an undo history.

▪ To be able to undo changes, we need to store previous versions of the picture. Since it’s an immutable value, that is easy. But it does require an additional field in the application state.

▪ Browser technology is amazing. It provides a powerful set of interface building blocks, ways to style and manipulate them, and tools to inspect and debug your applications. The software you write for the browser can be run on almost every computer and phone on the planet.

At the same time, browser technology is ridiculous. You have to learn a large number of silly tricks and obscure facts to master it, and the default programming model it provides is so problematic that most programmers prefer to cover it in several layers of abstraction rather than deal with it directly.

▪ And though the situation is definitely improving, it mostly does so in the form of more elements being added to address shortcomings—creating even more complexity. A feature used by a million websites can’t really be replaced. Even if it could, it would be hard to decide what it should be replaced with.

▪ Technology never exists in a vacuum—we’re constrained by our tools and the social, economic, and historical factors that produced them. This can be annoying, but it is generally more productive to try to build a good understanding of how the existing technical reality works—and why it is the way it is—than to rage against it or hold out for another reality.

▪ New abstractions can be helpful. The component model and data flow convention I used in this chapter is a crude form of that. As mentioned, there are libraries that try to make user interface programming more pleasant. At the time of writing, React and Angular are popular choices, but there’s a whole cottage industry of such frameworks. If you’re interested in programming web applications, I recommend investigating a few of them to understand how they work and what benefits they provide.

▪ On most browsers, when you select the draw tool and quickly drag across the picture, you don’t get a closed line. Rather, you get dots with gaps between them because the "mousemove" or "touchmove" events did not fire quickly enough to hit every pixel.

▪ A student asked, ‘The programmers of old used only simple machines and no programming languages, yet they made beautiful programs. Why do we use complicated machines and programming languages?’. Fu-Tzu replied, ‘The builders of old used only sticks and clay, yet they made beautiful huts.’

Master Yuan-Ma, The Book of Programming

▪ So far, we have used the JavaScript language in a single environment: the browser

▪ With it, you can build anything from small command line tools to HTTP servers that power dynamic websites.

▪ These chapters aim to teach you the main concepts that Node.js uses and to give you enough information to write useful programs for it. They do not try to be a complete, or even a thorough, treatment of the platform.

▪ One of the more difficult problems with writing systems that communicate over the network is managing input and output—that is, the reading and writing of data to and from the network and hard drive. Moving data around takes time, and scheduling it cleverly can make a big difference in how quickly a system responds to the user or to network requests.

▪ In such programs, asynchronous programming is often helpful. It allows the program to send and receive data from and to multiple devices at the same time without complicated thread management and synchronization.

▪ Node was initially conceived for the purpose of making asynchronous programming easy and convenient. JavaScript lends itself well to a system like Node. It is one of the few programming languages that does not have a built-in way to do in- and output. Thus, JavaScript could be fit onto Node’s rather eccentric approach to in- and output without ending up with two inconsistent interfaces.

▪ In 2009, when Node was being designed, people were already doing callback-based programming in the browser, so the community around the language was used to an asynchronous programming style.

▪ When Node.js is installed on a system, it provides a program called node, which is used to run JavaScript files. Say you have a file hello.js, containing this code:

let message = "Hello world";
console.log(message);

▪ You can then run node from the command line like this to execute the program:

$ node hello.js
Hello world

▪ The console.log method in Node does something similar to what it does in the browser. It prints out a piece of text. But in Node, the text will go to the process’s standard output stream, rather than to a browser’s JavaScript console. When running node from the command line, that means you see the logged values in your terminal.

▪ If you run node without giving it a file, it provides you with a prompt at which you can type JavaScript code and immediately see the result.

$ node
> 1 + 1
2

▪ The process binding, just like the console binding, is available globally in Node. It provides various ways to inspect and manipulate the current program

▪ The exit method ends the process and can be given an exit status code, which tells the program that started node (in this case, the command line shell) whether the program completed successfully (code zero) or encountered an error (any other code).

▪ To find the command line arguments given to your script, you can read process.argv, which is an array of strings

▪ node showargv.js one --and two
["node", "/tmp/showargv.js", "one", "--and", "two"]

▪ All the standard JavaScript global bindings, such as Array, Math, and JSON, are also present in Node’s environment. Browser-related functionality, such as document or prompt, is not.

▪ Beyond the bindings I mentioned, such as console and process, Node puts few additional bindings in the global scope

▪ The CommonJS module system, based on the require function, was described in Chapter 10. This system is built into Node and is used to load anything from built-in modules to downloaded packages to files that are part of your own program.

▪ The .js extension may be omitted, and Node will add it if such a file exists. If the required path refers to a directory, Node will try to load the file named index.js in that directory.

▪ When a string that does not look like a relative or absolute path is given to require, it is assumed to refer to either a built-in module or a module installed in a node_modules directory.

▪ For example, require("fs") will give you Node’s built-in file system module. And require("robot") might try to load the library found in node_modules/robot/. A common way to install such libraries is by using NPM, which we’ll come back to in a moment.

▪ The first one, called main.js, defines a script that can be called from the command line to reverse a string.

▪ NPM, which was introduced in Chapter 10, is an online repository of JavaScript modules, many of which are specifically written for Node. When you install Node on your computer, you also get the npm command, which you can use to interact with this repository.

▪ After running npm install
, NPM will have created a directory called node_modules

▪ Inside that directory will be an ini directory that contains the library. You can open it and look at the code.

▪ When we call require("ini"), this library is loaded, and we can call its parse property to parse a configuration file.

▪ By default NPM installs packages under the current directory, rather than in a central place

▪ If you are used to other package managers, this may seem unusual, but it has advantages—it puts each application in full control of the packages it installs and makes it easier to manage versions and clean up when removing an application.

▪ In the npm install
example, you could see a warning about the fact that the package.json file did not exist. It is recommended to create such a file for each project, either manually or by running npm init

▪ It contains some information about the project, such as its name and version, and lists its dependencies.

▪ When you run npm install
without naming a package to install, NPM will install the dependencies listed in package.json

▪ When you install a specific package that is not already listed as a dependency, NPM will add it to package.json.

▪ A package.json file lists both the program’s own version and versions for its dependencies

▪ Versions are a way to deal with the fact that packages evolve separately, and code written to work with a package as it existed at one point may not work with a later, modified version of the package.

▪ NPM demands that its packages follow a schema called semantic versioning, which encodes some information about which versions are compatible (don’t break the old interface) in the version number.

▪ A semantic version consists of three numbers, separated by periods, such as 2.3.0.

▪ Every time new functionality is added, the middle number has to be incremented.

▪ Every time compatibility is broken, so that existing code that uses the package might not work with the new version, the first number has to be incremented.

▪ A caret character (^) in front of the version number for a dependency in package.json indicates that any version compatible with the given number may be installed. So, for example, "^2.3.0" would mean that any version greater than or equal to 2.3.0 and less than 3.0.0 is allowed.

▪ The npm command is also used to publish new packages or new versions of packages

▪ If you run npm publish
in a directory that has a package.json file, it will publish a package with the name and version listed in the JSON file to the registry.

▪ Anyone can publish packages to NPM—though only under a package name that isn’t in use yet since it would be somewhat scary if random people could update existing packages.

▪ Since the npm program is a piece of software that talks to an open system—the package registry—there is nothing unique about what it does.

▪ Another program, yarn, which can be installed from the NPM registry, fills the same role as npm using a somewhat different interface and installation strategy.

▪ One of the most commonly used built-in modules in Node is the fs module, which stands for file system. It exports functions for working with files and directories.

▪ For example, the function called readFile reads a file and then calls a callback with the file’s contents.

let {readFile} = require("fs");
readFile("file.txt", "utf8", (error, text) => {
if (error) throw error;
console.log("The file contains:", text);
});

▪ There are several ways in which text can be encoded to binary data, but most modern systems use UTF-8. So unless you have reasons to believe another encoding is used, pass "utf8" when reading a text file

▪ If you do not pass an encoding, Node will assume you are interested in the binary data and will give you a Buffer object instead of a string. This is an array-like object that contains numbers representing the bytes (8-bit chunks of data) in the files.

▪ A similar function, writeFile, is used to write a file to disk.

▪ Here it was not necessary to specify the encoding—writeFile will assume that when it is given a string to write, rather than a Buffer object, it should write it out as text using its default character encoding, which is UTF-8.

▪ The fs module contains many other useful functions

▪ readdir will return the files in a directory as an array of strings

▪ stat will retrieve information about a file,

▪ rename will rename a file,

▪ unlink will remove one

▪ Most of these take a callback function as the last parameter, which they call either with an error (the first argument) or with a successful result (the second). As we saw in Chapter 11, there are downsides to this style of programming—the biggest one being that error handling becomes verbose and error-prone

▪ There is an object promises exported from the fs package since version 10.1 that contains most of the same functions as fs but uses promises rather than callback functions.

▪ Sometimes you don’t need asynchronicity, and it just gets in the way. Many of the functions in fs also have a synchronous variant, which has the same name with Sync added to the end. For example, the synchronous version of readFile is called readFileSync.

▪ Do note that while such a synchronous operation is being performed, your program is stopped entirely

▪ If it should be responding to the user or to other machines on the network, being stuck on a synchronous action might produce annoying delays.

▪ Another central module is called http. It provides functionality for running HTTP servers and making HTTP requests.

▪ const {createServer} = require("http");
let server = createServer((request, response) => {
response.writeHead(200, {"Content-Type": "text/html"});
response.write(`

Hello!


You asked for ${request.url}

`);
response.end();
});
server.listen(8000);
console.log("Listening! (port 8000)");

▪ The function passed as argument to createServer is called every time a client connects to the server

▪ The request and response bindings are objects representing the incoming and outgoing data.

▪ The first contains information about the request, such as its url property, which tells us to what URL the request was made.

▪ So, when you open that page in your browser, it sends a request to your own computer. This causes the server function to run and send back a response, which you can then see in the browser.

▪ To send something back, you call methods on the response object.

▪ The first, writeHead, will write out the response headers (see Chapter 18). You give it the status code (200 for “OK” in this case) and an object that contains header values. The example sets the Content-Type header to inform the client that we’ll be sending back an HTML document.

▪ Next, the actual response body (the document itself) is sent with response.write. You are allowed to call this method multiple times if you want to send the response piece by piece, for example to stream data to the client as it becomes available.

▪ Finally, response.end signals the end of the response.

▪ The call to server.listen causes the server to start waiting for connections on port 8000. This is why you have to connect to localhost:8000 to speak to this server, rather than just localhost, which would use the default port 80.

▪ When you run this script, the process just sits there and waits. When a script is listening for events—in this case, network connections—node will not automatically exit when it reaches the end of the script. To close it, press control-C.

▪ To act as an HTTP client, we can use the request function in the http module.

▪ const {request} = require("http");
let requestStream = request({
hostname: "eloquentjavascript.net",
path: "/20_node.html",
method: "GET",
headers: {Accept: "text/html"}
}, response => {
console.log("Server responded with status code",
response.statusCode);
});
requestStream.end();

▪ The first argument to request configures the request, telling Node what server to talk to, what path to request from that server, which method to use, and so on. The second argument is the function that should be called when a response comes in. It is given an object that allows us to inspect the response, for example to find out its status code.

▪ Just like the response object we saw in the server, the object returned by request allows us to stream data into the request with the write method and finish the request with the end method. The example does not use write because GET requests should not contain data in their request body.

▪ Making requests with Node’s raw functionality is rather verbose. There are much more convenient wrapper packages available on NPM. For example, node-fetch provides the promise-based fetch interface that we know from the browser.

▪ We have seen two instances of writable streams in the HTTP examples—namely, the response object that the server could write to and the request object that was returned from request.

▪ Writable streams are a widely used concept in Node.

▪ Such objects have a write method that can be passed a string or a Buffer object to write something to the stream.

▪ Their end method closes the stream and optionally takes a value to write to the stream before closing.

▪ Both of these methods can also be given a callback as an additional argument, which they will call when the writing or closing has finished.

▪ It is possible to create a writable stream that points at a file with the createWriteStream function from the fs module

▪ Then you can use the write method on the resulting object to write the file one piece at a time, rather than in one shot as with writeFile.

▪ Readable streams are a little more involved

▪ Both the request binding that was passed to the HTTP server’s callback and the response binding passed to the HTTP client’s callback are readable streams—a server reads requests and then writes responses, whereas a client first writes a request and then reads a response.

▪ Reading from a stream is done using event handlers, rather than methods.

▪ Objects that emit events in Node have a method called on that is similar to the addEventListener method in the browser. You give it an event name and then a function, and it will register that function to be called whenever the given event occurs.

▪ Readable streams have "data" and "end" events. The first is fired every time data comes in, and the second is called whenever the stream is at its end.

▪ This model is most suited for streaming data that can be immediately processed, even when the whole document isn’t available yet.

▪ A file can be read as a readable stream by using the createReadStream function from fs.

▪ This code creates a server that reads request bodies and streams them back to the client as all-uppercase text:

const {createServer} = require("http");
createServer((request, response) => {
response.writeHead(200, {"Content-Type": "text/plain"});
request.on("data", chunk =>
response.write(chunk.toString().toUpperCase()));
request.on("end", () => response.end());
}).listen(8000);

▪ The chunk value passed to the data handler will be a binary Buffer. We can convert this to a string by decoding it as UTF-8 encoded characters with its toString method.

▪ The following piece of code, when run with the uppercasing server active, will send a request to that server and write out the response it gets:

const {request} = require("http");
request({
hostname: "localhost",
port: 8000,
method: "POST"
}, response => {
response.on("data", chunk =>
process.stdout.write(chunk.toString()));
}).end("Hello server");
// → HELLO SERVER

▪ The example writes to process.stdout (the process’s standard output, which is a writable stream) instead of using console.log. We can’t use console.log because it adds an extra newline character after each piece of text that it writes, which isn’t appropriate here since the response may come in as multiple chunks.

▪ When we treat files as HTTP resources, the HTTP methods GET, PUT, and DELETE can be used to read, write, and delete the files, respectively. We will interpret the path in the request as the path of the file that the request refers to.

▪ This starts a server that just returns 405 error responses, which is the code used to indicate that the server refuses to handle a given method.

▪ When a request handler’s promise is rejected, the catch call translates the error into a response object, if it isn’t one already, so that the server can send back an error response to inform the client that it failed to handle the request.

▪ The status field of the response description may be omitted, in which case it defaults to 200 (OK). The content type, in the type property, can also be left off, in which case the response is assumed to be plain text.

▪ When the value of body is a readable stream, it will have a pipe method that is used to forward all content from a readable stream to a writable stream. If not, it is assumed to be either null (no body), a string, or a buffer, and it is passed directly to the response’s end method.

▪ To figure out which file path corresponds to a request URL, the urlPath function uses Node’s built-in url module to parse the URL. It takes its pathname, which will be something like "/file.txt", decodes that to get rid of the %20-style escape codes, and resolves it relative to the program’s working directory.

▪ const {parse} = require("url");

▪ const {resolve, sep} = require("path");

▪ const baseDirectory = process.cwd();

▪ File paths are strings in Node. To map such a string to an actual file, there is a nontrivial amount of interpretation going on. Paths may, for example, include ../ to refer to a parent directory. So one obvious source of problems would be requests for paths like /../secret_file.

To avoid such problems, urlPath uses the resolve function from the path module, which resolves relative paths. It then verifies that the result is below the working directory.

▪ The process.cwd function (where cwd stands for “current working directory”) can be used to find this working directory.

▪ The sep binding from the path package is the system’s path separator—a backslash on Windows and a forward slash on most other systems.

▪ The mime package (content type indicators like text/plain are also called MIME types) knows the correct type for a large number of file extensions.

▪ When a requested file does not exist, the correct HTTP status code to return is 404. We’ll use the stat function, which looks up information about a file, to find out both whether the file exists and whether it is a directory.

▪ methods.GET = async function(request) {
let path = urlPath(request.url);
let stats;
try {
stats = await stat(path);
} catch (error) {
if (error.code != "ENOENT") throw error;
else return {status: 404, body: "File not found"};
}
if (stats.isDirectory()) {
return {body: (await readdir(path)).join("\n")};
} else {
return {body: createReadStream(path),
type: mime.getType(path)};
}
};

▪ Because it has to touch the disk and thus might take a while, stat is asynchronous

▪ Since we’re using promises rather than callback style, it has to be imported from promises instead of directly from fs

▪ When the file does not exist, stat will throw an error object with a code property of "ENOENT". These somewhat obscure, Unix-inspired codes are how you recognize error types in Node.

▪ The stats object returned by stat tells us a number of things about a file, such as its size (size property) and its modification date (mtime property

▪ Here we are interested in the question of whether it is a directory or a regular file, which the isDirectory method tells us

▪ When an HTTP response does not contain any data, the status code 204 (“no content”) can be used to indicate this. Since the response to deletion doesn’t need to transmit any information beyond whether the operation succeeded, that is a sensible thing to return here.

▪ You may be wondering why trying to delete a nonexistent file returns a success status code, rather than an error. When the file that is being deleted is not there, you could say that the request’s objective is already fulfilled.

▪ The HTTP standard encourages us to make requests idempotent, which means that making the same request multiple times produces the same result as making it once. In a way, if you try to delete something that’s already gone, the effect you were trying to do has been achieved—the thing is no longer there.

▪ We again use pipe to move data from a readable stream to a writable one, in this case from the request to the file. But since pipe isn’t written to return a promise, we have to write a wrapper, pipeStream, that creates a promise around the outcome of calling pipe.

▪ Node is a nice, small system that lets us run JavaScript in a nonbrowser context

▪ It was originally designed for network tasks to play the role of a node in a network. But it lends itself to all kinds of scripting tasks, and if writing JavaScript is something you enjoy, automating tasks with Node works well.

▪ NPM provides packages for everything you can think of (and quite a few things you’d probably never think of), and it allows you to fetch and install those packages with the npm program

▪ Node comes with a number of built-in modules, including the fs module for working with the file system and the http module for running HTTP servers and making HTTP requests.

▪ All input and output in Node is done asynchronously, unless you explicitly use a synchronous variant of a function, such as readFileSync.

▪ When calling such asynchronous functions, you provide callback functions, and Node will call them with an error value and (if available) a result when it is ready.

▪ Though the DELETE method in our file server is able to delete directories (using rmdir

▪ Add support for the MKCOL method (“make collection”), which should create a directory by calling mkdir from the fs module

▪ MKCOL is not a widely used HTTP method, but it does exist for this same purpose in the WebDAV standard, which specifies a set of conventions on top of HTTP that make it suitable for creating documents.

▪ A common solution to this problem is called long polling, which happens to be one of the motivations for Node’s design

▪ We can arrange for the client to open the connection and keep it around so that the server can use it to send information when it needs to do so.

▪ But an HTTP request allows only a simple flow of information: the client sends a request, the server comes back with a single response, and that is it.

▪ There is a technology called WebSockets, supported by modern browsers, that makes it possible to open connections for arbitrary data exchange. But using them properly is somewhat tricky.

▪ In this chapter, we use a simpler technique—long polling—where clients continuously ask the server for new information using regular HTTP requests, and the server stalls its answer when it has nothing new to report.

▪ As long as the client makes sure it constantly has a polling request open, it will receive information from the server quickly after it becomes available

▪ When Iman submits a talk on Extreme Downhill Unicycling, the server will notice that Fatma is waiting for updates and send a response containing the new talk to her pending request.

▪ To prevent connections from timing out (being aborted because of a lack of activity), long polling techniques usually set a maximum time for each request, after which the server will respond anyway, even though it has nothing to report, after which the client will start a new request.

▪ Periodically restarting the request also makes the technique more robust, allowing clients to recover from temporary connection failures or server problems.

▪ A busy server that is using long polling may have thousands of waiting requests, and thus TCP connections, open. Node, which makes it easy to manage many connections without creating a separate thread of control for each one, is a good fit for such a system.

▪ We will use JSON as the format of our request and response body. Like in the file server from Chapter 20, we’ll try to make good use of HTTP methods and headers. The interface is centered around the /talks path. Paths that do not start with /talks will be used for serving static files—the HTML and JavaScript code for the client-side system.

▪ Since talk titles may contain spaces and other characters that may not appear normally in a URL, title strings must be encoded with the encodeURIComponent function when building up such a URL.

▪ Adding a comment to a talk is done with a POST request to a URL like /talks/Unituning/comments, with a JSON body that has author and message properties.

▪ Servers may include an ETag (“entity tag”) header in a response. Its value is a string that identifies the current version of the resource.

▪ We need something like this, where the client can tell the server which version of the list of talks it has, and the server responds only when that list has changed. But instead of immediately returning a 304 response, the server should stall the response and return only when something new is available or a given amount of time has elapsed.

▪ To distinguish long polling requests from normal conditional requests, we give them another header, Prefer: wait=90
, which tells the server that the client is willing to wait up to 90 seconds for the response.

▪ The server will keep a version number that it updates every time the talks change and will use that as the ETag value.

▪ GET /talks HTTP/1.1
If-None-Match: "4"
Prefer: wait=90

(time passes)

HTTP/1.1 200 OK
Content-Type: application/json
ETag: "5"
Content-Length: 295

[....]

▪ A router is a component that helps dispatch a request to the function that can handle it.

▪ You can tell the router, for example, that PUT requests with a path that matches the regular expression /^\/talks\/([^\/]+)$/ (/talks/ followed by a talk title) can be handled by a given function.

▪ In addition, it can help extract the meaningful parts of the path (in this case the talk title), wrapped in parentheses in the regular expression, and pass them to the handler function.

▪ There are a number of good router packages on NPM, but here we’ll write one ourselves to illustrate the principle.

▪ I opted for ecstatic. This isn’t the only such server on NPM, but it works well and fits our purposes.

▪ When a GET request comes in for /talks, it may be either a regular request or a long polling request.

▪ Callback functions for delayed requests are stored in the server’s waiting array so that they can be notified when something happens.

▪ The waitForChanges method also immediately sets a timer to respond with a 304 status when the request has waited long enough.

▪ We don’t allow the user interface to directly manipulate the state or send off HTTP requests. Rather, it may emit actions that describe what the user is trying to do.

▪ When the request fails, we don’t want to have our page just sit there, doing nothing without explanation. So we define a function called reportError, which at least shows the user a dialog that tells them something went wrong.

▪ We’ll use an approach similar to the one we saw in Chapter 19, splitting the application into components. But since some of the components either never need to update or are always fully redrawn when updated, we’ll define those not as classes but as functions that directly return a DOM node

▪ The "submit" event handler calls form.reset to clear the form’s content after creating a "newComment" action.

▪ When creating moderately complex pieces of DOM, this style of programming starts to look rather messy. There’s a widely used (non-standard) JavaScript extension called JSX that lets you write HTML directly in your scripts, which can make such code prettier (depending on what you consider pretty). Before you can actually run such code, you have to run a program on your script to convert the pseudo-HTML into JavaScript function calls much like the ones we use here.

▪ It runs an infinite loop that, on each iteration, retrieves the list of talks—either normally or, if this isn’t the first request, with the headers included that make it a long polling request.

▪ When a request fails, the function waits a moment and then tries again.

▪ When the server gives back a 304 response, that means a long polling request timed out, so the function should just immediately start the next request

▪ If the response is a normal 200 response, its body is read as JSON and passed to the callback, and its ETag header value is stored for the next iteration.

▪ When the talks change, this component redraws all of them. This is simple but also wasteful

▪ The skill-sharing server keeps its data purely in memory. This means that when it crashes or is restarted for any reason, all talks and comments are lost.

▪ Extend the server so that it stores the talk data to disk and automatically reloads the data when it is restarted. Do not worry about efficiency—do the simplest thing that works.

▪ The wholesale redrawing of talks works pretty well because you usually can’t tell the difference between a DOM node and its identical replacement. But there are exceptions. If you start typing something in the comment field for a talk in one browser window and then, in another, add a comment to that talk, the field in the first window will be redrawn, removing both its content and its focus.
