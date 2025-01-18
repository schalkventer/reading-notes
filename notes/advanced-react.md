Advanced React: Deep Dives, Investigations, Performance Patterns and Techniques (2023)

Nadia Makarevich

---

▪ And, finally, re-rendering. This is when React updates an already existing component with some new information.

▪ Compared to mounting, re-rendering is lightweight: React just re-uses the already existing instance, runs the hooks, does all the necessary calculations, and updates the existing DOM element with the new attributes.

▪ The important thing to remember here is that React never goes "up" the render tree when it re-renders components. If a state update originated somewhere in the middle of the components tree, only components "down" the tree will re-render.

▪ The only way for components at the "bottom" to affect components at the "top" of the hierarchy is for them either to explicitly call state update in the "top" components or to pass components as functions.

▪ Normal React behavior is that if a state update is triggered, React will re-render all the nested components regardless of their props

▪ If I have a component with props, and I try to change those props without triggering a state update, something like this:

const App = () => {
// local variable won't work
let isOpen = false;
return (


{/* nothing will happen */}
(isOpen = true)}>
Open dialog

{/* will never show up */}
{isOpen ? (
(isOpen = false)} />
) : null}


);
};

▪ When the Button is clicked, the local isOpen variable will change. But the React lifecycle is not triggered, so the render output is never updated, and the ModalDialog will never show up.

▪ In the context of re-renders, whether props have changed or not on a component matters only in one case: if the said component is wrapped in the React.memo higher-order component.

▪ Then, and only then, will React stop its natural chain of re-renders and first check the props. If none of the props change, then re-renders will stop there. If even one single prop changes, they will continue as usual.

▪ Wrapping them in React.memo will prevent them from re-rendering in this case, this is true. But React.memo has many caveats and complexities around it

▪ Essentially, we just created a new sub-branch inside our render tree and moved our state down to it.

▪ Because the hook hides the fact that we have state in the app. But the state is still there! Every time it changes, it will still trigger a re-render of the component that uses this hook. It doesn't even matter whether this state is used in the App directly or even whether the hook returns anything.

▪ The entire App component will re-render on every resize, even though this value is not even returned from the hook!

▪ Hooks are essentially just pockets in your trousers. If, instead of carrying a 10-kilogram dumbbell in your hands, you put it in your pocket, it wouldn't change the fact that it's still hard to run: you have 10 kilograms of additional weight on your person.

▪ So, where you put state is very important

▪ Ideally, to avoid future performance problems, you'd want to isolate it as much as possible to as tiny and light components as possible

▪ Re-rendering is how React updates components with new data. Without re-renders, there will be no interactivity in our apps

▪ State update is the initial source of all re-renders

▪ If a component's re-render is triggered, all nested components inside that component will be re-rendered

▪ During the normal React re-renders cycle (without the use of memoization), props change doesn't matter: components will re-render even if they don't have any props

▪ We can use the pattern known as "moving state down" to prevent unnecessary re-renders in big apps

▪ State update in a hook will trigger the re-render of a component that uses this hook, even if the state itself is not used.

▪ How passing components as props can improve the performance of our apps

▪ Why components as props are not affected by re-renders

▪ What an Element is, how it's different from a Component, and why it's important to know that distinction

▪ The basics of React reconciliation and diffing

▪ The rest of the slow components are passed through props, they are outside of that component. In the "hierarchical" components tree, they belong to the parent. And remember? React never goes "up" that tree when it re-renders a component.

▪ As you can see, it's just a function. What makes a component different from any other function is that it returns Elements, which React then converts into DOM elements and sends to the browser to be drawn on the screen.

▪ An Element is simply an object that defines a component that needs to be rendered on the screen. In fact, the nice HTML-like syntax is nothing more than syntax sugar for the React.createElement function[1]. We can even replace that element with this: React.createElement(Child, null, null)
and everything will work as expected.

▪ Elements are not limited to components; they can be just normal DOM elements

▪ Now to re-render. What we usually refer to as "re-render" is React calling those functions and executing everything that needs to be executed in the process (like hooks).

▪ From the return of those functions, React builds a tree of those objects. We know it as the Fiber Tree now, or Virtual DOM sometimes.

▪ In fact, it's even two trees: before and after re-render. By comparing ("diffing") those, React will then extract information that goes to the browser: which DOM elements need to be updated, removed, or added. This is known as the "reconciliation" algorithm.

▪ The part that matters for this chapter's problem is this: if the object (Element) before and after re-render is exactly the same, then React will skip the re-render of the Component this Element represents and its nested components.

▪ And by "exactly the same," I mean whether Object.is(ElementBeforeRerender, ElementAfterRerender)
returns true. React doesn't perform the deep comparison of objects.

▪ If the comparison returns false, this is the signal to React that something has changed. It will look at the type then. If the type is the same, then React will re-render this component. If the type changes, then it will remove the "old" component and mount the "new" one.

▪ When setState is called, React will know to re-render the Parent component. So it will call the Parent function and compare whatever it returns before and after state changes.

▪ And it returns an object that is defined locally to the Parent function. So on every function call (i.e. re-render), this object will be re-created, and the result of Object.is on "before" and "after" 
objects will be false.

▪ Hope this made sense and you're now confident with the "components as props" and "children as props" patterns.

▪ A Component is just a function that accepts an argument (props) and returns Elements that should be rendered when this Component renders on the screen

▪ An Element is an object that describes what needs to be rendered on the screen

▪ with the type either a string for DOM elements or a reference to a Component for components.

▪ Re-render is just React calling the Component's function.

▪ A component re-renders when its element object changes, as determined by Object.is comparison of it before and after re-render.

▪ When elements are passed as props to a component, and this component triggers a re-render through a state update, elements that are passed as props won't re-render.

▪ "children" are just props and behave like any other prop when they are passed via JSX nesting syntax:

▪ How conditional rendering of components influences performance.

▪ How to set default props for components passed as props by using the cloneElement function, and what the downsides of that are.

▪ Whether doing something like this for a Button is a good idea or not is sometimes debatable, of course. It highly depends on how strict your design is and how much deviation it allows for those who implement product features.

▪ leftColumn={}
middleColumn={}
rightColumn={}
/>

▪ Essentially, an element as a prop for a component is a way to tell the consumer: give me whatever you want, I don't know or care what it is, I am just responsible for putting it in the right place. The rest is up to you.

▪ Always remember: "children" in this context are nothing more than a prop, and the "nested" syntax is just syntax sugar for it!

▪ One of the biggest concerns that sometimes arises with this pattern is the performance of it. Which is ironic, considering that in the previous chapter, we discussed how to use it to improve performance.

▪ All we did when we declared the footer variable (footer = 
) was create an Element, nothing more. From the React and code perspective, it's just an object that sits in memory quietly and does nothing. And creating objects is cheap (at least compared to rendering components).

▪ This is what makes routing patterns, like in one of the versions of React router, completely safe:

const App = () => {
return (

} />
} />
...

);
};

▪ There is no condition here, so it feels like the App owns and renders both 
and 
at the same time. But it doesn't. It just creates small objects that describe those pages

▪ One of the objections against passing those icons as props is that this pattern is too flexible.

▪ In the real world, the Button would need to have some degree of control over the icons. If the button has the isDisabled property, you'd likely want the icon to appear "disabled" as well. Bigger buttons would want bigger icons by default. Blue buttons would want white icons by default, and white buttons would want black icons.

▪ However, if we leave the implementation as it is now, this will be problematic: it will be up to the Button's consumers to remember all that.

▪ Half of the time, it will be forgotten, and the other half misunderstood.

▪ What we need here is to assign some default values to those icons that the Button can control while still preserving the flexibility of the pattern.

▪ Luckily, we can do exactly that. Remember that these icons in props are just objects with known and predictable shapes. And React has APIs that allow us to operate on them easily.

▪ In our case, we can clone the icon in the Button with the help of the React.cloneElement function[2], and assign any props to that new element that we want.

▪ Speaking of magic: the fact that setting default values works seemingly magically can be a big downside.

▪ So be very careful with this pattern, and make sure you always override the default props with the actual props. And if you feel uneasy about it - no worries. In React, there are a million ways to achieve exactly the same result.

▪ When a component renders another component, the configuration of which is controlled by props, we can pass the entire component element as a prop instead, leaving the configuration concerns to the consumer.

▪ If a component that has elements as props is rendered conditionally, then even if those elements are created outside of the condition, they will only be rendered when the conditional component is rendered.

▪ If we need to provide default props to the element from props, we can use the cloneElement function for that

▪ But elements as props, however great they are, don't solve everything for us. If a component that accepts other components through props needs to influence their props or pass some state to them in some explicit non-magical way, then elements as props and the cloneElement function are no help here.

▪ This is where the pattern known as "render props" comes in handy.

▪ What the render props pattern is and what kind of configuration concerns it solves, but elements as props can't.

▪ Why we shouldn't actually do that these days, now that we have hooks.

▪ When the render props for sharing logic pattern can still be useful, even in the hooks era.

▪ In this case, instead of passing elements as a prop, we can pass them as a render prop (or render function). A render prop is nothing more than just a function that returns an Element. That function is almost the same as a Component. Only a Component you wouldn't call directly - React does it for you. But a render function is under your command.

▪ Hooks replaced that pattern in almost 99% of cases. And rightfully so.

▪ Render props for configuration and flexibility use cases, described at the beginning, are still very viable

▪ If you are working on a project that is a few years old, this pattern will be all over the codebase. It was really popular before the introduction of hooks, especially for encapsulating form validation logic. A few popular libraries still use it to this day.

▪ It can still be useful for specific scenarios, such as when the logic and state that you want to share depend on a DOM element.

▪ Render props were very useful when we needed to share stateful logic between components without lifting it up.
But hooks replaced that use case in 99% of cases.

▪ More precisely, let's discuss the topic that is strongly associated with improving performance in React, but in reality, doesn't work as we intend to at least half the time we're doing it. Memoization.

▪ And I'm not joking or exaggerating about half the time by the way. Doing memoization properly is hard, much harder than it seems

▪ What is the problem we're trying to solve with memoization (and it's not performance per se!).

▪ se!).
How useMemo and useCallback work under the hood, and what is the difference between them

▪ Why memoizing props on a component by itself is an anti-pattern

▪ What React.memo is, why we need it, and what are the basic rules for using it successfully

▪ How to use it properly with the "elements as children" pattern

▪ What is the role of useMemo in expensive calculations

▪ When we create a variable with an object const a = { id: 1 }
, the value stored there is not the actual value. It's just a reference to some part of the memory that holds that object.

▪ As you can see, there is a slight difference in the API. useCallback accepts the function that we want to memoize as the first argument, while useMemo accepts a function and memoizes its return value

▪ And our hooks are just functions integrated into the React lifecycle, nothing more.

▪ It caches the very first function that is passed as an argument and then just returns it every time if the dependencies of the hook haven't changed

▪ With useMemo, it's pretty much the same, only instead of returning the function, React calls it and returns the result:

▪ However, there is this belief that sometimes pops up here and there that useMemo is better for performance than useCallback, since useCallback re-creates the function passed to it with each re-render, and useMemo doesn't do that. As you can see, this is not true. The function in the first argument will be re-created for both of them.

▪ Unfortunately, this useCallback here is just useless. There is this widespread belief that even ChatGPT seems to hold, that memoizing props prevents components from re-rendering

▪ But as we know already from the previous chapters, if a component re-renders, every component inside that component will also re-render.

▪ So whether we wrap our onClick function in useCallback or not doesn't matter at all here. All we did was make React do a little more work and make our code a little harder to read.

▪ When it's just one useCallback, it doesn't look that bad. But it's never just one, is it? There will be another, then another, they will start depending on each other, and before you know it, the logic in the app is just buried under the incomprehensible and undebuggable mess of useMemo and useCallback.

▪ There are only two major use cases where we actually need to memoize props on a component.

▪ The first one is when this prop is used as a dependency in another hook in the downstream component.

▪ And the second one is when a component is wrapped in React.memo.

▪ This is where useMemo and useCallback shine:

▪ But making sure that all props are memoized is not as easy as it sounds. We're doing it wrong in so many cases! And just one single mistake leads to broken props check, and as a result - every React.memo, useCallback, and useMemo become completely useless.

▪ everything that is JSX is just syntax sugar for React.createElement and actually just an object.

▪ ParentMemo will behave as if it is not wrapped in React.memo - its children are actually not memoized!

▪ And this object is just an object, it's not memoized by itself. So again, from the memoization and props perspective, we have a ParentMemo component that has a children prop that contains a non-memoized object. Hence, broken memoization on ParentMemo.

▪ To fix it, we need to memoize the object itself:

const Component = () => {
const child = useMemo(() => , []);
return {child};
};

▪ And then we might not even need the ChildMemo at all. Depends on its content and our intentions, of course. At least for the purpose of preventing ParentMemo from re-rendering, ChildMemo is unnecessary, and it can return back to being just a normal Child:

▪ First of all, what is an "expensive calculation"? Is concatenating strings expensive? Or sorting an array of 300 items? Or running a regular expression on a text of 5000 words? I don't know. And you don't. And no one knows until it's actually measured:

▪ Sorting an array of 300 items on my laptop, even with a 6x slowed-down CPU, takes less than 2ms. But on some old Android 2 mobile phone, it might take a second.

▪ Executing a regular expression on a text that takes 100ms feels slow. But if it's run as a result of a button click, once in a blue moon, buried somewhere deep in the settings screen, then it's almost instant. A regular expression that takes 30ms to run seems fast enough. But if it's run on the main page on every mouse move or scroll event, it's unforgivably slow and needs to be improved.

▪ It always depends. "Measure first" should be the default thinking when there is an urge to wrap something in useMemo because it's an "expensive calculation."

▪ More likely than not, anything that is calculated within useMemo will be an order of magnitude faster than re-rendering actual elements anyway. For example, sorting that array of 300 items on my laptop took less than 2ms. Re-rendering list elements from that array, even when they were just simple buttons with some text, took more than 20ms.

▪ If I want to improve the performance of that component, the best thing to do would be to get rid of the unnecessary re-renders of everything, not memoizing something that takes less than 2ms.

▪ So an addition to the "measure first" rule, when it comes to memoization, should be: "don't forget to measure how long it takes to re-render component elements as well."

▪ But considering so many caveats and complexities that surround it, I would recommend using composition-based optimization techniques as much as possible first. React.memo should be the last resort when all other things have failed.

▪ Memoizing props on a component makes sense only when: 
This component is wrapped in React.memo.
This component uses those props as dependencies in any of the hooks.
This component passes those props down to other components, and they have either of the situations from above.

▪ When memoizing props, remember that "children" is also a non-primitive prop that needs to be memoized.

▪ We now know that when we create React Elements, such as const a = 
, we're actually creating objects. The HTML-like syntax (JSX) is just syntax sugar that is transformed into the React.createElement function.

▪ None of it seems connected at first glance, but all of this is part of the same story: how React determines which components need to be re-rendered, which components need to be removed, and which ones need to be added to the screen.

▪ How React's Diffing and Reconciliation algorithm works

▪ Why we shouldn't create components inside other components

▪ Why we would use the "key" attribute outside of dynamic lists.

▪ It's all because of the DOM[4]. Or to be precise, the fact that we don't have to deal with it directly when we're writing React code. This is very convenient for us: instead of doing appendChild or comparing attributes manually, we just write components. And then React transforms whatever we give to it into DOM elements on the screen with appropriate data.

▪ it iterates over that tree and does the following:

If the "type" is a string, it generates the HTML element of that type.
If the "type" is a function (i.e., our component), it calls it and iterates over the tree that this function returned.

Until it eventually gets the entire tree of DOM nodes that are ready to be shown.

▪ If the type is the same, the Input component will be marked as "needs update," and its re-render will be triggered. If the type has changed, then React, during the re-render cycle, will remove (unmount) the "previous" component and add (mount) the "next" component.

▪ You guessed the result, right? "Type" has changed from Input to TextPlaceholder references, so React will unmount Input and remove everything associated with it from the DOM. And it will mount the new TextPlaceholder component and append it to the DOM for the first time.

▪ This is what we usually call re-mounting. And normally it's not intentional and it's terrible for performance - re-mounting will take at least twice as long as a normal re-render.

▪ Declaring components inside other components like this can be one of the biggest performance killers in React.

▪ There are at least two easy ways to fix it: arrays and keys.

▪ During re-render, when React sees an array of children instead of an individual item, it just iterates over it and then compares "before" and "after" elements and their "type" according to their position in the array.

▪ And voila! Magically, by changing the inputs' position in the render output, without changing anything else in the logic, the bug is fixed, and inputs behave exactly as I would expect!

▪ There is another way to fix the same bug: with the help of the "key" attribute.

▪ The "key" should be familiar to anyone who has written any lists in React. React forces us to add it when we iterate over arrays of data:

▪ Now, React faces an interesting task: all components in that array are of the same type. How to detect which one is which? If the order of those items changes:

▪ This is why we need "key": it's basically React's version of a unique identifier of an element within children's array that is used between re-renders

▪ If an element has a "key" in parallel with "type," then during re-render, React will re-use the existing elements, with all their associated state and DOM, if the "key" and "type" match "before" and "after."

▪ Now, with the key present, React will know that after re-render, it needs to re-use an already created element that used to be in the first position. So it will just swap input DOM nodes around.

▪ One of the most common misconceptions about the key attribute and lists is that key is needed there for performance reasons. That adding key to the dynamic array prevents array items from re-rendering. As you can see from the above, that's not how the key works.

▪ Key helps React to identify which already existing instance it should re-use when it re-renders those items. Re-render will still happen, like with any components rendered inside another component.

▪ Fun fact: "key" is just an attribute of an element, it's not limited to dynamic arrays

▪ This technique is known as "state reset". It has nothing to do with state per se, but it's sometimes used when there is a need to reset the state of an uncontrolled component (like an input field) to a default value. You don't even have to have two components for this, like I had above. One will do.

▪ If you want to force state reset on URL change, for example, it could be as simple as this:

const Component = () => {
// grab the current url from our router solution
const { url } = useRouter();
// I want to reset that input field when the page URL changes
return ;
};

▪ But be careful here, though. It's not just "state reset" as you can see. It forces React to unmount a component completely and mount a new one from scratch. For big components, that might cause performance problems. The fact that the state is reset is just a by-product of this total destruction.

▪ " So it will think that the Input component just changed its position in the array and will re-use the already created instance for it. If we type something, the state is preserved even though the Inputs are technically different.

▪ For this particular example, it's just a curious behavior, of course, and not very useful in practice. But I could imagine it being used for fine-tuning the performance of components like accordions, tabs content, or some galleries.

▪ Try to predict what will happen if I type something in those inputs and toggle the boolean on and off.

▪ React will compare elements between re-renders with elements in the same place in the returned array on any level of hierarchy. The first one with the first one, the second with the second, etc.

▪ If the type of the element and its position in the array is the same, React will re-render that element. If the type changes at that position, then React will unmount the previous component and mount the new one.

▪ An array of children will always have the same number of children (if it's not dynamic). Conditional elements (isSomething ? : 
) will take just one place, even if one of them is null.

▪ If the array is dynamic, then React can't reliably identify those elements between re-renders. So we use the key attribute to help it. This is important when the array can change the number of its items or their position between re-renders (re-order, add, remove), and especially important if those elements are wrapped in React.memo.

▪ We can use the key outside of dynamic arrays as well to force React to recognize elements at the same position in the array with the same type as different. Or to force it to recognize elements at different positions with the same type as the same.

▪ We can also force unmounting of a component with a key if that key changes between re-renders based on some information (like routing). This is sometimes called "state reset".

▪ There is one final composition technique that we need to discuss before moving on to other parts of React: higher-order components

▪ Before hooks took over, this was one of the most popular patterns for sharing stateful logic and context data. It's still used here and there even today, especially in older libraries or in projects that started their life before hooks. So while it's probably not the best idea to introduce them in new code, understanding what they are and how they work is still more or less mandatory.

▪ In English, it's a function that accepts a component as one of its arguments, executes some logic, and then returns another component that renders the component from the argument.

▪ // accept a Component as an argument
const withSomeLogic = (Component) => {
// do something
// return a component that renders the component from the argument
return (props) => ;
};

▪ The simplest and most common use case would be to inject props into components. We can, for example, implement a withTheming component that extracts the current theme of the website (dark or light mode) and sends that value into the theme prop.

▪ Before the introduction of hooks, higher-order components were widely used for accessing context and any external data subscriptions. Redux's old connect[7] or React Router's withRouter[8] functions are higher-order components: they accept a component, inject some props into it, and return it back.

▪ As you can see, higher-order components are quite complicated to write and understand. So when hooks were introduced, it's no wonder everyone switched to them.

▪ Now, instead of creating complicated mental maps of which prop goes where and trying to figure out how theme ended up in props, we can just write:

const Button = () => {
// we see immediately where the theme is coming from
const { theme } = useTheme();
return Button
};

▪ This is the first use case where hooks are of no use, but higher-order components could come in handy.

▪ Instead of copy-pasting the "click happened → log data" logic everywhere, I can create a withLoggingOnClick function that:

Accepts a component as an argument.
Intercepts its onClick callback.
Sends the data that I need to whatever external framework is used for logging.
Returns the component with the onClick callback intact for further use.

▪ What we can do instead is, again, implement a higher-order component. This time it will accept a component, wrap it in a div with onKeyPress callback attached, and return the component unchanged.

▪ Now, when this modal is open and focused, any key press event will bubble up through the elements' hierarchy until it reaches our div in withSuppressKeyPress that wraps the modal and will stop there. Mission accomplished, and developers who implement the Modal component don't even need to know or care about it.

▪ A higher-order component is just a function that accepts a component as an argument and returns a new component

▪ We can inject props or additional logic into the components that are wrapped in a higher-order component.

▪ However, what is often underestimated or not known at all is that Context can prevent unnecessary re-renders and significantly improve the performance of our apps as a result. When applied correctly and carefully, of course.

▪ The kind of performance improvement Context can offer.
The caveats of using Context.
How to get the most out of Context and prevent unnecessary re-renders caused by it.

▪ While technically, it will work, it's not the best solution. Firstly, our Sidebar and MainPart now have props that they don't use but merely pass to the components below - their API becomes bloated and harder to read.

▪ And as we know from Chapter 1. Intro to re-renders, state update will cause this component and every component inside, including their children, to re-render.

▪ We can probably memoize the intermediate slow components that don't depend on that state. But the code of that will become even more bloated: all of them would have to be memoized!

▪ const NavigationController = ({ children }) => {
const [isNavExpanded, setIsNavExpanded] = useState();
const toggle = () => setIsNavExpanded(!isNavExpanded);
return children;
};

This is the "children as props" pattern.

▪ As covered in Chapter 2. Elements, children as props, and re-renders, children when passed like this are nothing more than props, and props are not affected by state changes.

▪ Now every component that happens to be rendered down the tree from that provider (even if they are passed as props like our children!) will now have access to that value through the useContext hook.

▪ It's not all sunshine and roses when dealing with Context, of course. Otherwise, it wouldn't have such a bad reputation

▪ There are three major things that you need to know like the back of your hand when introducing Context into the app:

▪ Context consumers will re-render when the value on the Provider changes.

▪ All of them will re-render, even if they don't use the part of the value that actually changed.

▪ Those re-renders can't be prevented with memoization (easily).

▪ Every time we change state, the value object changes, so every component that uses this Context through useNavigation will re-render.

▪ This is natural and expected: we want everyone to have access to the latest value, and the only way in React to update components is to re-render them.

However, what will happen if the NavigationController re-renders for any other reason other than its own state change? If, for example, this re-render is triggered in its parent component? NavigationController will also re-render: it's React's natural chain of re-renders. The value object will be re-created, and we're again in the situation where React needs to compare objects between re-renders.

▪ In the case of our small app, it's not a problem: the provider sits at the very top, so nothing above it can re-render. However, this won't always be the case. And in large, complicated apps, it's more likely than not that someone will introduce something one day that triggers the re-render of that provider.

▪ Fortunately, all of this is easily preventable. We just need to use useMemo and useCallback to memoize the value passed to the provider:

const NavigationController = ({ children }) => {
const [isNavExpanded, setIsNavExpanded] = useState();
const toggle = useCallback(() => {
setIsNavExpanded(!isNavExpanded);
}, [isNavExpanded]);
const value = useMemo(() => {
return { isNavExpanded, toggle };
}, [isNavExpanded, toggle]);
return (

{children}

);
};

▪ This is one of the few cases where always memoizing by default is actually not premature optimization. It will prevent much bigger problems in the future that will almost inevitably occur.

▪ On top of the fact that all context consumers re-render when the value changes, it's important to emphasize not only the "value changes" part but also that all of them will do that. If I introduce open and close functions to our navigation API that don't actually depend on the state:

▪ The SomeComponent will re-render when the value on the Context provider changes, despite the fact that the open function doesn't actually change.

And no amount of memoization will prevent it. This, for example, won't work:

const useNavOpen = () => {
const { open } = useNavigation();
return useCallback(open, []);
};

▪ We can, however, use an interesting technique called "splitting providers" to achieve the desired result.

It works like this. Instead of just one Context that holds everything, we can create two: one will hold the value that changes, and another one will hold those that don't.

▪ The values that we pass to those providers will be the data that has the state and api that only holds references to open and close functions.

▪ useReducer is a different way to manage a component's state. Instead of being aware of the state we're changing and manipulating it manually, the reducers pattern allows us just to dispatch named "actions". This is usually very convenient when you have a complicated state or complex operations on that state, and you want a more structured approach to managing them.

▪ In something like Redux, we'd use memoized state selectors in this case. Unfortunately, for Context, this won't work - any change in context value will trigger the re-render of every consumer.

▪ But that doesn't solve anything yet: the heavy component will still re-render every time the Context value changes. We need the final step here: memoize the component we passed as an argument inside the HOC itself:

const withNavigationOpen = (AnyComponent) => {
// wrap the component from the arguments in React.memo here
const AnyComponentMemo = React.memo(AnyComponent);
return (props) => {
const { open } = useContext(Context);
// return memoized component here
// now it won't re-render because of Context changes
// make sure that whatever is passed as props here don't change between re-renders!
return ;
};
};

▪ I hope this chapter has given you an idea of how useful Context can be when it comes to re-renders. And for reducing props on components, for that matter. I'm not advocating for using Context everywhere, of course: its caveats are pretty serious. So for larger, more complex apps, it's probably better to go with an external state management solution right away. Any solution that supports memoized selectors. But it could work for smaller apps, where you have just a few places that could benefit from the Context mental

▪ With Context (or any context-like state management library), we can pass data directly from one component to another deep in the render tree without the need to wire it through props.

▪ Passing data in this way can improve the performance of our apps, as we'll avoid the re-rendering of all components in between.

▪ Context, however, can be dangerous: all components that use it will re-render if the value in the Context provider changes. This re-render can't be stopped with standard memoization techniques.

▪ To minimize Context re-renders, we should always memoize the value we pass to the provider.

▪ We can split the Context provider into multiple providers to further minimize re-renders. Switching from useState to useReducer can help with this.

▪ Even though we don't have proper selectors for Context, we can imitate their functionality with higher order components and React.memo.

▪ What forwardRef is, how to use it, and how to avoid using it (you'll see why!)

▪ Why we still need imperative APIs in React, and how to implement them with or without useImperativeHandle.

▪ Detecting a click outside of a component when showing popup-like elements.

▪ Manually scrolling to an element after it appears on the screen.

▪ Calculating sizes and boundaries of components on the screen to correctly position something like a tooltip.

▪ A Ref is a mutable object that React preserves between re-renders.

▪ The initial value is cached, so if we compare ref.current between re-renders, the reference will be the same. It's the same as if we'd just used the useMemo hook on that object.

▪ One of the biggest and most visible differences between Refs and state is that Refs update don't cause re-renders

▪ If I use that component in our Form where we saved the value in Ref, it just won't work.

const Form = () => {
const ref = useRef();
const onChange = (e) => {
ref.current = e.target.value;
};
return (


{/* will never be updated */}


);
};

▪ And the second big difference is that Ref updates are synchronous. We are just mutating an object after all, which is a synchronous operation in JavaScript.

▪ State, however, is typically asynchronous. It's even more than asynchronous: state updates are run in "snapshots". React has a complicated system that manages it and makes sure that the data and components within one "snapshot" are consistent and updated properly. Ref, however, has none of that: we're modifying an object directly, and that's all there is to it.

▪ const Form = () => {
const [value, setValue] = useState();
const onChange = (e) => {
console.log('before', value);
setValue(e.target.value);
console.log('after', value); // same as before
};
};

Both "before" and "after" values in the code above will be the same.

▪ When we call setValue, we're not updating the state right away. We're just letting React know that it needs to schedule a state update with the new data after it's done with whatever it's doing now.

▪ We modified an object, the data in that object is available right away, but nothing from the React lifecycle is triggered.

▪ Ask yourself these questions:

Is this value used for rendering components, now or in the future?
Is this value passed as props to other components in any way, now or in the future?

▪ We can use Ref, for example, to store some "dev" information about components. Maybe we're interested in counting how many times a component renders:

useEffect(() => {
ref.current = ref.current + 1;
console.log('Render number', ref.current);
});

▪ And, of course, assign DOM elements to Ref. This is one of Ref's most important and most popular use cases

▪ We can do this as simply as creating a Ref with the useRef hook and then passing that Ref to a DOM element via the ref attribute:

const Component = () => {
const ref = useRef(null);
// assing ref to an input element
return ;
};

▪ The important thing to remember here is that ref will be assigned only after the element is rendered by React and its associated DOM element is created. We need something to assign to that Ref, isn't it? That means that the ref.current value won't be available right away

▪ logic like this will just not work:

const Component = () => {
const ref = useRef(null);
// trying to access ref value before it was actually assigned
// input will never be rendered here
if (!ref.current) return null;
return ;
};

▪ We should only read and write ref.current either in the useEffect hook or in callbacks.

▪ How can I tell the input to "focus itself" from the Form component? The "normal" way to control data and behavior in React is to pass props to components and listen to callbacks. I could try to pass the prop "focusItself" to InputField that I would switch from false to true, but that would only work once.

▪ In case you're wondering why I named the prop inputRef, rather than just ref: it's actually not that simple. ref is not a real prop; it's kind of a "reserved" name.

▪ But functional components don't have class instances. So instead, we just get a warning in the console: "Function components cannot be given refs. Attempts to access this ref will fail. Did you mean to use React.forwardRef()?"

▪ we need to signal to React that this ref is actually intentional, and we want to do stuff with it. We can do it with the help of the forwardRef function: it accepts our component and injects the Ref from the ref attribute as a second argument of the component's function. Right after the props.

▪ // normally, we'd have only props there
// but we wrapped the component's function with forwardRef
// which injects the second argument - ref
// if it's passed to this component by its consumer
const InputField = forwardRef((props, ref) => {
// the rest of the code is the same
return ;
});

▪ And now the Form can just pass the Ref to the InputField component as if it were a regular DOM element:

return ;

▪ Whether you should use forwardRef or simply pass the Ref as a prop is just a matter of personal taste: the end result is the same.

▪ React is declarative and expects us to write our code accordingly. But sometimes we just need a way to trigger something imperatively. Fortunately, React gives us an escape hatch for this: useImperativeHandle[9] hook.

▪ This hook is slightly mind-boggling to understand. I had to read the docs twice, try it out a few times, and go through its implementation in the actual React code to really get what it's doing.

▪ The useImperativeHandle hook simply attaches this object to the Ref object's "current" property, that's all.

▪ This is how it does it:

const InputField = () => {
useImperativeHandle(
someRef,
() => ({
focus: () => {},
shake: () => {},
}),
[],
);
};

▪ What closures are, how they appear, and why we need them.

▪ What a stale closure is, and why they occur.

▪ What the common scenarios in React are that cause stale closures, and how to fight them

▪ React.memo has a thing called comparison function[10]. It allows us more granular control over props comparison in React.memo.

▪ Except for one tiny problem: it doesn't actually work. If you type something in the input and then press that button, the value that we log in onClick is undefined. But it can't be undefined, the input works as expected, and if I add console.log outside of onClick it logs it correctly. Just not inside onClick.

▪ What's going on?

This is known as the "stale closure" problem. And in order to fix it, we first need to dig a bit into probably the most feared topic in JavaScript: closures and how they work.

▪ By doing that, we created a local scope: an area in our code where variables declared inside won't be visible from the outside.

▪ This is achieved by creating what is known as "closure". The function inside "closes" over all the data from the outside. It's essentially a snapshot of all the "outside" data frozen in time stored separately in memory.

▪ We call our something function with the value "first" and assign the result to a variable

▪ It's like taking a photograph of some dynamic scene: as soon as you press the button, the entire scene is "frozen" in the picture forever. The next press of the button will not change anything in the previously taken picture.

▪ Everything in useEffect or useCallback hook is a closure:

▪ Every single function inside a component is a closure since a component itself is just a function.

▪ But all of the above, although slightly unusual if you're coming from a language that doesn't have closures, is still relatively straightforward. You create a few functions a few times, and it becomes natural. It's even unnecessary to understand the concept of "closure" to write apps in React for years.

▪ So what is the problem, then? Why are closures one of the most terrifying things in JavaScript and a source of pain for so many developers?

▪ It's because closures live for as long as a reference to the function that caused them exists. And the reference to a function is just a value that can be assigned to anything.

▪ Here's our function from above, that returns a perfectly innocent closure:

const something = (value) => {
const inside = () => {
console.log(value);
};
return inside;
};

▪ We just created what is known as the "stale closure". Every closure is frozen at the point when it's created.

▪ When we call the something function the next time, instead of creating a new function with a new closure, we return the one that we created before. The one that was frozen with the "first" variable forever.

▪ If you remember the Memoization with useMemo, useCallback, and React.memo chapter, the code above should look familiar. And indeed, we just implemented exactly what the useCallback hook does for us.

▪ This dependencies array is what makes React refresh that cached closure, exactly as we did when we compared value !== prevValue
. If I forget about that array, our closure becomes stale:

▪ The second most common way to introduce the stale closure problem, after useCallback and useMemo hooks, is Refs.

▪ On the surface, it does look simpler: just pass a function to useRef and access it through ref.current. No dependencies, no worries.

▪ This trick is absolutely mind-blowing: it's very simple, but it can forever change how you memoize functions in React

▪ In order for the function to have access to the latest state, it needs to be re-created with every re-render. There is no getting away from it, it's the nature of closures, nothing to do with React.

▪ But when a closure freezes everything around it, it doesn't make objects immutable or frozen. Objects are stored in a different part of the memory, and multiple variables can contain references to exactly the same object.

▪ Closures are formed every time a function is created inside another function.

▪ Since React components are just functions, every function created inside forms a closure, including such hooks as useCallback and useRef.

▪ When a function that forms a closure is called, all the data around it is "frozen", like a snapshot.

▪ To update that data, we need to re-create the "closed" function. This is what dependencies of hooks like useCallback allow us to do.

▪ If we miss a dependency, or don't refresh the closed function assigned to ref.current, the closure becomes "stale".

▪ Let's briefly refresh what "debounce" and "throttle" are, just in case you haven't had a chance to use them yet. "Debouncing" and "Throttling"[12] are techniques that allow us to skip function execution if that function is called too many times over a certain time period.

▪ But a skilled typist can type at the speed of 70 words per minute, which is roughly 6 keypresses per second. In this implementation, it will result in 6 onChange events, i.e., 6 requests to the server per second! Not every backend can handle that. Nor does it need to.

▪ Instead of sending that request on every keypress, we can wait a little bit until the user stops typing, and then send the entire value in one go.

▪ The difference will be obvious if we use not an async search example, but an editing field with auto-save functionality: if a user types something in the field, we want to send requests to the backend to save whatever they type "on the fly", without them pressing the "save" button explicitly. If a user is writing a poem in a field like that really, really fast, the "debounced" onChange callback will be triggered only once. And if something breaks while typing, the entire poem will be lost. The "throttled" callback will be triggered periodically, the poem will be regularly saved, and if a disaster occurs, only the last milliseconds of the poem will be lost. Much safer approach.

▪ As we already know, when using functions in Refs, we need to update them in useEffect. Otherwise, the closure becomes stale.

▪ We use debounce and throttle when we want to skip some function's executions that were fired too often.

▪ Everything we need to know about useLayoutEffect.

▪ When and why we'd want to use it instead of useEffect.

▪ How SSR plays a role here.

▪ The only way to get the actual sizes is to make the browser render the items and then extract the sizes via a native JavaScript API, like getBoundingClientRect.

▪ Again, we can only get its width if we render it in the browser. So we have to add the button explicitly during the initial render:

▪ The reason for that flash should be pretty obvious: we render those items and make them visible before removing unnecessary items

▪ And we have to render them first, otherwise, the fancy responsiveness won't work. So one possible fix would be to still render that first pass, but invisibly: with opacity set to 0, or in some div somewhere outside the visible area. And only after we extract the dimensions and the magic number, make them visible. This is how we used to handle cases like this in the past.

▪ In React version from ~16.8 (the one with the hooks), however, all we need to do is replace our useEffect hook with useLayoutEffect.

▪ Why don't we just use it everywhere instead of useEffect? The docs explicitly say that useLayoutEffect can hurt performance[14] and should be avoided. Why is that? It also says that it is fired "before the browser repaints the screen," which implies that useEffect is fired after. But what exactly does this mean in a practical sense? Do I need to think about low-level concepts like browser painting when writing simple dropdowns now?

▪ The first thing we need here is "browser rendering." In the React world, it is also known as "painting" just to differentiate it from React's rendering - those are very different!

▪ Normally, modern browsers try to maintain a 60 FPS rate, 60 frames per second. One slide changes to the next one ~every 13 milliseconds. This is what we refer to as "painting" in React.

▪ The information that updates these slides is split into "tasks." Tasks are put in a queue. The browser grabs a task from the queue and executes it. If it has more time, it executes the next task, and so on, until no more time is left in that ~13ms gap, and then it refreshes the screen.

▪ What is a "task"? When it comes to normal JavaScript, it's everything that we put in the script tag and execute synchronously.

▪ Consider this code:

const app = document.getElementById('app');
const child = document.createElement('div');
child.innerHTML = '

Heyo!

';
app.appendChild(child);
child.style = 'border: 10px solid red';
child.style = 'border: 20px solid green';
child.style = 'border: 30px solid black';

▪ I grab an element by its id, store it in the app variable, create a div, update its HTML, append that div to the app, and change the div's border three times. The entire thing will be considered as just one task for the browser

▪ So it will execute every single line, and only then draw the final result: the div with the black border.

You won't be able to see this red-green-black transition on the screen.

▪ What will happen if a "task" takes longer than 13ms? Well, that's unfortunate. The browser can't stop it or split it. It will continue with it until it's done, and then paint the final result.

▪ If I add 1-second synchronous delays between those border updates:

const waitSync = (ms) => {
let start = Date.now(),
now = start;
while (now - start < ms) {
now = Date.now();
}
};
child.style = 'border: 10px solid red';
waitSync(1000);
child.style = 'border: 20px solid green';
waitSync(1000);
child.style = 'border: 30px solid black';
waitSync(1000);

we still won't be able to see the "in-between" result. We'll just stare at the blank screen until the browser sorts it out and enjoy the final black border in the end. This is what we refer to as "blocking render" or "blocking painting" code.

▪ Now, although React is just JavaScript, it's not executed as one single task, of course.

▪ The way to "break" a giant task like rendering an entire app into smaller ones is by using various "asynchronous" methods: callbacks, event handlers, promises, and so on.

▪ If I simply wrap those style adjustments in setTimeout, even with 0 delay:

setTimeout(() => {
child.style = 'border: 10px solid red';
wait(1000);
setTimeout(() => {
child.style = 'border: 20px solid green';
wait(1000);
setTimeout(() => {
child.style = 'border: 30px solid black';
wait(1000);
}, 0);
}, 0);
}, 0);

Then every one of those timeouts will be considered a new "task." So the browser will be able to re-paint the screen after finishing one and before starting the next one. And we'll be able to see the slow but glorious transition from red to green to back, rather than meditating at the white screen for three seconds.

▪ This is what React does for us. Essentially, it's a crazy complicated and very efficient engine that splits our giant, giant blobs of hundreds of npm dependencies combined with our own coding into the smallest possible chunks that browsers are able to process in under 13 ms (ideally).

▪ useLayoutEffect is something that React runs synchronously during component updates.

▪ Whatever we render inside the Component will be run with useLayoutEffect as the same "task". React guarantees this. Even if we update state inside useLayoutEffect, which we usually think of as an asynchronous task, React will still make sure that the entire flow is run synchronously.

▪ The first one renders the "initial" pass of navigation with all the buttons. The second one removes those children that we don't need. With screen re-painting in between! Exactly the same situation as with borders inside timeouts.

▪ So to answer the questions we had at the beginning. Is it safe to use useLayoutEffect? Yep! Can it hurt performance? Absolutely! The last thing we need is for our entire React app to turn into one giant synchronous "task".

▪ Use useLayoutEffect only when you need to get rid of the visual "glitches" caused by the need to adjust the UI according to the real sizes of elements. For everything else, useEffect is the way to go. And you might not even need that one either[15].

▪ While React will try to optimize it as much as possible, there are cases when it can run before the browser paint and block it as a result. One of those cases is when you already have useLayoutEffect somewhere in the chain of updates.

▪ So useEffect has to run before the new cycle starts. So if the state update is triggered inside useLayoutEffect, which is synchronous, React has no choice but to run useEffect synchronously as well.

▪ Server-side rendering. A cool feature that some frameworks support by default. And a real pain when it comes to things like this.

▪ useEffect will only run on the client, so the initial SSR pass will show us the substitute component. Then, the client code will kick in, useEffect will run, the state will change, and React will replace it with the normal responsive navigation.

▪ We can prevent this behavior with the useLayoutEffect hook. This hook is run synchronously. From the browser's perspective, it will be one large, unbreakable task. So the browser will wait and will not paint anything until the task is complete and the final dimensions are calculated.

▪ You might have heard that we need Portals in React to escape it when rendering elements inside elements with overflow: hidden
. Every second article on the internet about Portals has this example. This is actually not true: we can escape content "clipping" with just pure CSS. We need Portals for other reasons.

▪ In our case, it just works by accident: because I don't have any positioned elements between my modal dialog and the root of the app.

If the dialog happens to be rendered inside a div with position: relative
(or sticky or absolute) and this div is not in the middle of the page, then it all falls apart. The modal will be positioned in the middle of that div, not in the middle of the screen.

▪ Normally, elements are stacked in the order of their appearance in the DOM

▪ Elements with the position set to absolute or relative, however, will always be pushed forward. If I just add position: relative
to the red div, the green suddenly appears under it.

▪ To fix this situation, we have the z-index CSS property. This property allows us to manipulate that Z-axis within the same Stacking Context. By default, it's zero. So if I set the z-index of the dialog to a negative value, it will appear behind all the divs. If set to positive, then it will appear on top of all the divs.

▪ And it's not only the combination of position and z-index that triggers it, by the way. The transform property will do it. So any of your leftover CSS animations have the potential to mess the positioned elements up. Or z-index on Flex or Grid children. Or a bunch of other different properties[19].

▪ And, of course, finally, the elements with overflow. By the way, just setting overflow on an element won't clip the absolutely positioned div inside; it needs to be in combination with position: relative
. But yeah, if an absolutely positioned dialog is rendered inside the div with overflow and position, then it will be clipped.

▪ There is another position value that we can use to escape the normal document flow: the fixed value. It's similar to absolute, only it positions the elements not relative to their positioned parents but relative to the viewport

▪ Also, since it's positioned relative to the screen, this position actually allows us to escape the overflow trap. So, in theory, we could have used it for our dialogs and tooltips.

▪ However, even position: fixed
cannot escape the rules of the Stacking Context. Nothing can. It's like a black hole: as soon as it forms, everything within its gravitational reach is gone. No one gets out.

If the grey div has z-index: 1
and the red div is with z-index: 2
- it's game over for modals. They will appear underneath.

▪ Another issue with position: fixed
is that it's not always positioned relative to the viewport. It's actually positioned relative to what is known as the Containing Block. It just happens to be the viewport most of the time

▪ Properties that trigger the forming of the new Containing Block[20] for position: fixed
are relatively rare, but they include transform, and that one is widely used for animation.

▪ Okay, all of this is really fun but a bit theoretical. Would a situation like the Stacking Context trap even happen in a real app? Of course! And quite easily, actually.

The prime candidates are all sorts of animations or "sticky" blocks like headers or columns. Those are the most likely places where we'd be forced to set either position with z-index, or translate. And those will form a new Stacking Context.

Just open a few of your favorite popular websites that have "sticky" elements or animations, open Chrome Dev Tools, find some block deep in the DOM tree, set its position to fixed with a high z-index, and move it around a bit. Just for the fun of it, I checked Facebook, Airbnb, Gmail, OpenAI, and LinkedIn. On three of those, the main area is a trap: any block with position: fixed
and z-index: 9999
within it will appear underneath the sticky header.

▪ There is only one way to escape from that trap: to make sure that the modal is not rendered inside the DOM elements that form the Stacking Context. In the world without React, we'd just append that modal to the body or some div at the root of the app

▪ Let's do a very simple app: a header with position: sticky
, the "collapsible" navigation on the left, and the modal dialog inside our main area.

▪ Except for one thing: the modal dialog in the main area is now completely busted. It used to be positioned in the middle of the screen, but not anymore. And when I scroll with it open, it appears under the header. Everything in the code is reasonable, there are no random position: relative
, and still, that happened. The Stacking Context trap.

▪ In the real world, it's not going to be that simple. More likely than not, the button will be buried deep inside the render tree, and propagating state up will be a massive pain and performance killer. Context could help, but it has its own caveats.

Instead, we can use the createPortal function that React gives us.

▪ It accepts two arguments:

What we want to teleport in the form of a React Element (our 
)
Where we want to teleport it to in the form of a DOM element. Not an id, but the element itself!

▪ From a React perspective, this modal dialog is part of the render tree of the component that created the 
element. In our case, the App component. If I trigger the re-render of the App, all components rendered inside of it will re-render, including our dialog, if it's open.

▪ If our App has access to Context, the dialog will have access to exactly the same Context.

If the part of the app where the dialog is created unmounts, the dialog will also disappear.

▪ If I want to intercept a click event that happens in the modal, the onClick handler on the "main" div will be able to do that. "Click" here is part of synthetic events, so they "bubble" through the React tree, not the regular DOM tree. Same story with any synthetic events that React manages[21].

▪ From the DOM perspective, this dialog is no longer part of the "main" app. So everything that is DOM-related will change.

If you rely on CSS inheritance and cascading to style the dialog in the "main" part, it won't work anymore.

▪ And finally, onSubmit on elements. This is the least obvious thing about this. It feels the same as onClick, but in reality, the submit event is not managed by React[22]. It's a native API and DOM elements thing. If I wrap the main part of the app in , then clicking on the buttons inside the dialog won't trigger the "submit" event!

▪ position: absolute
positions an element relative to a positioned parent

▪ position: fixed
positions an element relative to the viewport unless a new Containing Block is formed.

▪ position: absolute
elements will be clipped inside the overflow: hidden
elements.

▪ elements.
position: fixed
elements can escape the overflow: hidden
problem, but they can't escape the Stacking Context

▪ Nothing can escape the Stacking Context. If you are trapped there, it's game over

▪ Stacking Context is formed by setting position and z-index, by setting translate, and so many other things

▪ things.
Portals allow you to easily render some elements, like modal dialogs, outside of their current DOM position so that the Stacking Context doesn't trap them

▪ Fetching data in the frontend world is hard, and React is no exception, unfortunately.

▪ Have you tried recently to wrap your head around what the latest on data fetching is? The chaos of endless data management libraries, GraphQL or not GraphQL, useEffect is evil since it causes waterfalls, Suspense is supposed to save the world, but at the moment of publishing this book, it is still not officially ready for data fetching. And then the patterns like fetch-on-render, fetch-then-render, and render-as-you-fetch that confuse even people who write about them sometimes. What on Earth is going on? Why do I suddenly need a PhD to just make a simple GET request?

▪ And what is the actual "right way" to fetch data in React?

▪ Generally speaking, in the modern frontend world, we can loosely separate the concept of "data fetching" into two categories: initial data fetching and data fetching on demand.

▪ Data on demand is something that you fetch after a user interacts with a page in order to update their experience. All the various autocompletes, dynamic forms, and search experiences fall under this category. In React, the fetch of this data is usually triggered in callbacks.

▪ Initial data is the data you'd expect to see on a page right away when you open it. It's the data we need to fetch before a component ends up on the screen. It's something that we need to be able to show users some meaningful experience as soon as possible. In React, if no SSR is involved, fetching data like this usually happens in useEffect (or in componentDidMount for class components).

▪ Short answer - no. And yes. Depends on your use case. If you actually just need to fetch a bit of data once and forget about it, then no, you don't need anything. A simple fetch in the useEffect hook will do just fine:

▪ But as soon as your use case exceeds "fetch once and forget," you're going to face tough questions. What about error handling? What if multiple components want to fetch data from this exact endpoint? Should I cache that data? For how long? What about race conditions? What if I want to remove the component from the screen? Should I cancel this request? What about memory leaks? And so on and so forth.

▪ Not a single question from that list is even React-specific; it's a general problem of fetching data over the network. To solve these problems (and more!), there are only two paths: you either need to reinvent the wheel and write a lot of code to solve these. Or rely on some existing library that has been doing this for years.

▪ Some libraries, like Axios[23], will abstract some concerns, like canceling requests, but will have no opinion on React-specific API. Others, like swr[24], will handle pretty much everything for you, including caching.

▪ No library or Suspense in the world can improve the performance of your app just by itself. They just make some things easier at the cost of making some things harder. You always need to understand the fundamentals of data fetching and data orchestration patterns and techniques in order to write performant apps.

▪ How do you know whether an app is "performant"? It's relatively straightforward with a simple component: you just measure how long it takes to render it, and voila! The smaller the number, the more "performant" (i.e., faster) your component is.

▪ And let's say the app is implemented in three different ways:

Shows a loading state until all the data is loaded, and then renders everything in one go. Takes ~3 seconds.

Shows a loading state until sidebar data is loaded first, renders sidebar, and keeps loading state until the data is finished in the main part. The sidebar to appear takes ~1 second, the rest of the app appears in ~3 seconds. Overall, it takes ~4 seconds.

Shows a loading state until the main issue data is loaded, then renders it, keeps the loading state for sidebar and comments. When sidebar loaded - renders it, comments are still in the loading state. The main part appears in ~2 seconds, the sidebar in ~1 second after that, it takes another ~2 seconds for the comments to appear. Overall takes ~5s to appear.

▪ And the answer is, of course, tricky, and the most performant app is not the one that you chose, but… None of them. Or all of them. Or any of them. It depends.

▪ when is it okay to start fetching data?
what can we do while the data fetching is in progress?
what should we do when the data fetching is done?

▪ What about this code for the Parent:

const Parent = () => {
// set loading to true initially
const [isLoading, setIsLoading] = useState(true);
// child is now here! before return
const child = ;
if (isLoading) return 'loading';
return child;
};

The functionality is the same: if isLoading is set to false, show Child, if true - show the loading state. But the 
element this time is before the if condition. Will the useEffect in Child be triggered this time? And the answer is now less intuitive, and I've seen a lot of people stumble here. The answer is still the same - no, it won't.

▪ When we write const child = 
, we don't "render" the Child component. 
is nothing more than syntax sugar for a function that creates a description of a future element

▪ It is only rendered when this description ends up in the actual visible render tree - i.e., returned from the component. Until then, it just sits there idly as an object and does nothing.

▪ Did you know that browsers have a limit on how many requests in parallel to the same host they can handle?

▪ Assuming the server is HTTP1 (which is still 70% of the internet), the number is not that big. In Chrome, it's just 6[25]. 6 requests in parallel! If you fire more at the same time, all the rest of them will have to queue and wait for the first available "slot."

▪ What we did here is implement a classic waterfall of requests. Remember the React lifecycle part? Only components that are actually returned will be mounted, rendered, and as a result, will trigger useEffect and data fetching in it.

▪ In our case, every single component returns a "loading" state while it waits for data. And only when data is loaded does it switch to a component next in the render tree, triggers its own data fetching, returns a "loading" state, and the cycle repeats itself.

▪ The first and easiest solution is to pull all of those data-fetching requests as high in the render tree as possible

▪ One thing to note here is that in this solution, we're triggering state change three times independently, which will cause three re-renders of the parent component. And considering that it's happening at the top of the app, unnecessary re-render like this might cause half of the app to re-render unnecessarily. The performance impact really depends on the order of your components, of course, and how big they are, but it's something to keep in mind

▪ Lifting data loading up like in the examples above, although good for performance, is terrible for app architecture and code readability

▪ Fortunately, there is an easy(ish) solution to this: we can introduce the concept of "data providers" to the app. "Data provider" here would be just an abstraction around data fetching that gives us the ability to fetch data in one place of the app and access that data in another, bypassing all components in between

▪ One final trick to learn about fighting waterfalls

▪ React-integrated libraries with hooks and a query-like API like swr[29] additionally abstract away dealing with useCallback, state, and many other things like error handling and caching. Instead of this monstrosity of code that still needs a lot of things to be production-ready:

▪ Data fetching on the frontend is a complicated topic. Probably a whole book can be written just about it.

▪ We can separate the client's data fetching into two broad categories: initial and on demand

▪ We can use the simple fetch instead of using data fetching libraries, but a lot of concerns we'd have to implement manually

▪ A "performant" app is always subjective and depends on the message we're trying to convey to the users

▪ When fetching data, especially initially, we need to be aware of browser limitations on parallel requests

▪ Waterfalls appear when we trigger data fetching not in parallel, but conditionally or in sequence.

▪ We can use techniques such as Promise.all, parallel promises, or data providers with Context to avoid waterfalls.

▪ We can pre-fetch critical resources even before React is initialized, but we need to remember browser limitations while doing so.

▪ What Promises are and how very innocent code can create a race condition without us noticing it.

▪ What are the reasons for race conditions to appear.

▪ How to fix them in at least four different ways.

▪ Essentially, a Promise is a... promise.

▪ By the way, do you remember that scary warning "Can't perform a React state update on an unmounted component"? It used to appear in exactly these situations: when an asynchronous operation like data fetching finishes after the component is already gone. "Used to", since it's gone as well. It was removed quite recently[34].

▪ If the result returns the id that was used to generate the url, we can just compare them. And if they don't match, ignore them

▪ Your results don't return anything that identifies them reliably? No problem, we can just compare the url instead:

▪ Don't like the previous solution or think that using a ref for something like this is weird? No problem, there is another way. useEffect has something called a "cleanup" function, where we can clean up stuff like subscriptions.

▪ The cleanup function[35] is run after a component is unmounted, or before every re-render with changed dependencies.

▪ Instead of cleaning up or comparing results, we can simply cancel all the previous requests. If they never finish, the state update with obsolete data will never happen, and the problem won't exist. We can use the AbortController[38] interface for this.

It's as simple as creating an AbortController in useEffect and calling .abort() in the cleanup function.

▪ useEffect(() => {
// create controller here
const controller = new AbortController();
// pass controller as signal to fetch
fetch(url, { signal: controller.signal })
.then((r) => r.json())
.then((r) => {
setData(r);
});
return () => {
// abort the request here
controller.abort();
};
}, [url]);

▪ Aborting a request in progress will cause the promise to reject, so you'd want to catch errors to get rid of the scary warnings in the console. But handling Promise rejections properly is a good idea regardless of AbortController, so it's something you'd want to do with any strategy

▪ AbortController will give a specific type of error, making it easy to exclude it from regular error handling.

fetch(url, { signal: controller.signal })
.then((r) => r.json())
.then((r) => {
setData(r);
})
.catch((error) => {
// error because of AbortController
if (error.name === 'AbortError') {
// do nothing
} else {
// do something, it's a real error!
}
});

▪ We can fix it by: 
Forcing a re-mount of a component with the "old" data that we don't need.
Comparing the returned result with the variable that triggered the promise and not setting state if they don't match.
Tracing the latest promise via the clean-up function in the useEffect and dropping the result of all "old" promises.
Using AbortController to cancel all previous requests.

▪ We all want our apps to be stable, work perfectly, and cater to every edge case imaginable, don't we? But the sad reality is that we are all humans (at least that is my assumption), we all make mistakes, and there is no such thing as bug-free code

▪ No matter how careful we are or how many automated tests we write, there will always be a situation when something goes terribly wrong. The important thing, when it comes to user experience, is to predict that terrible thing, localize it as much as possible, and deal with it in a graceful way until it can be actually fixed.

▪ In the final chapter, let's take a look at error handling in React:

What we can do if an error happens.
What the caveats of different approaches to error catching are.
How to mitigate them.

▪ But first things first: why is it vitally important to have some error-catching solution in React?

The answer is simple: starting from version 16, an error thrown during the React lifecycle will cause the entire app to unmount itself if not stopped.

▪ We have our good old try/catch[39] statement, which is more or less self-explanatory: try to do stuff, and if they fail - catch the mistake and do something to mitigate it:

try {
// if we're doing something wrong, this might throw an error
doSomething();
} catch (e) {
// if error happened, catch it and do something with it without stopping the app
// like sending this error to some logging service
}

▪ This also works with async functions with the same syntax:

try {
await fetch('/bla-bla');
} catch (e) {
// oh no, the fetch failed! We should do something about it!
}

▪ If we wrap useEffect with try/catch, it simply won't work:

try {
useEffect(() => {
throw new Error('Hulk smash!');
}, []);
} catch (e) {
// useEffect throws, but this will never be called
}

This happens because useEffect is called asynchronously after rendering, so from the try/catch perspective, everything went successfully. It's the same story as with any Promise

▪ In order for errors inside useEffect to be caught, try/catch should be placed inside as well:

useEffect(() => {
try {
throw new Error('Hulk smash!');
} catch (e) {
// this one will be caught
}
}, []);

▪ This applies to any hook that uses useEffect or to anything asynchronous really. As a result, instead of just one try/catch that wraps everything, you'd have to split it into multiple blocks: one for each hook.

▪ try/catch won't be able to catch anything that happens inside children components. You can't just do this:

const Component = () => {
let child;
try {
child = ;
} catch (e) {
// useless for catching errors inside Child component, won't be triggered
}
return child;
};

or even this:

const Component = () => {
try {
return ;
} catch (e) {
// still useless for catching errors inside Child component, won't be triggered
}
};

▪ This happens because when we write 
, we're not actually rendering this component. What we're doing is creating a component Element, which is nothing more than a component's definition. It's just an object that contains necessary information like component type and props that will be used later by React itself, which will actually trigger the render of this component.

▪ Simple code like this, for example, will cause an infinite loop of re-renders if an error happens:

const Component = () => {
const [hasError, setHasError] = useState(false);
try {
doSomethingComplicated();
} catch (e) {
// don't do that! will cause infinite loop in case of an error
// see codesandbox below with live example
setHasError(true);
}
};

▪ To summarize this section: if we rely solely on try/catch in React, we will either miss most of the errors or turn every component into an incomprehensible mess of code that will probably cause errors by itself.

Fortunately, there is another way.

▪ React ErrorBoundary component

▪ To mitigate the limitations from above, React gives us what is known as "Error Boundaries"[40]: a special API that turns a regular component into a try/catch statement in a way, only for React declarative code.

▪ But React doesn't give us the component per se, it just gives us a tool to implement it. The simplest implementation would look something like this:

class ErrorBoundary extends React.Component {
constructor(props) {
super(props);
// initialize the error state
this.state = { hasError: false };
}
// if an error happened, set the state to true
static getDerivedStateFromError(error) {
return { hasError: true };
}
render() {
// if error happened, return a fallback component
if (this.state.hasError) {
return ;
}
return this.props.children;
}
}

▪ We create a regular class component (going old-school here, no hooks for error boundaries available) and implement the getDerivedStateFromError method - this turns the component into a proper error boundary.

▪ Another important thing to do when dealing with errors is to send the error info somewhere where it can wake up everyone who's on-call. For this, error boundaries give us the componentDidCatch method:

class ErrorBoundary extends React.Component {
// everything else stays the same
componentDidCatch(error, errorInfo) {
// send error to somewhere here
log(error, errorInfo);
}
}

▪ There is one caveat in this error-free world though: it doesn't catch everything.

▪ Error boundaries only catch errors that happen during the React lifecycle. Things that happen outside of it, like resolved promises, async code with setTimeout, various callbacks, and event handlers, will disappear if not dealt with explicitly.

▪ const Component = () => {
useEffect(() => {
// this one will be caught by ErrorBoundary component
throw new Error('Destroy everything!');
}, []);
const onClick = () => {
// this error will just disappear into the void
throw new Error('Hulk smash!');
};
useEffect(() => {
// if this one fails, the error will also disappear
fetch('/bla');
}, []);
return click me;
};
const ComponentWithBoundary = () => {
return (



);
};

▪ The common recommendation here is to use regular try/catch for these types of errors. And at least here we can use state safely (more or less): callbacks of event handlers are exactly the places where we usually set state anyway. So technically, we can just combine two approaches and do something like this:

const Component = () => {
const [hasError, setHasError] = useState(false);
// most of the errors in this component and in children will be caught by the ErrorBoundary
const onClick = () => {
try {
// this error will be caught by catch
throw new Error('Hulk smash!');
} catch (e) {
setHasError(true);
}
};
if (hasError) return 'something went wrong';
return click me;
};
const ComponentWithBoundary = () => {
return (



);
};

▪ We can, of course, instead of dealing with those errors on a component level, just propagate them up to the parent that has ErrorBoundary via props or Context. This way, at least we can have a "fallback" component in just one place:

▪ Interestingly enough, we actually can catch all errors with ErrorBoundary! There is a cool trick to achieve exactly that[41].

▪ The trick here is to catch those errors first with try/catch. Then inside the catch statement, trigger a normal React re-render, and then re-throw those errors back into the re-render lifecycle. That way, ErrorBoundary can catch them like any other error. And since a state update is the way to trigger a re-render, and the state set function can actually accept an updater function[42] as an argument, the solution is pure magic:

const Component = () => {
// create some random state that we'll use to throw errors
const [state, setState] = useState();
const onClick = () => {
try {
// something bad happened
} catch (e) {
// trigger state update, with updater function as an argument
setState(() => {
// re-throw this error within the updater function
// it will be triggered during state update
throw e;
});
}
};
};

▪ The final step here would be to abstract this hack away so we don't have to create random states in every component. We can get creative here and make a hook that gives us an async error thrower:

▪ const useThrowAsyncError = () => {
const [state, setState] = useState();
return (error) => {
setState(() => throw error)
}
}

And use it like this:

const Component = () => {
const throwAsyncError = useThrowAsyncError();
useEffect(() => {
fetch('/bla')
.then()
.catch((e) => {
// throw async error here!
throwAsyncError(e);
});
});
};

▪ Or, we can create a wrapper for callbacks like this:

const useCallbackWithErrorHandling = (callback) => {
const [state, setState] = useState();
return (...args) => {
try {
callback(...args);
} catch(e) {
setState(() => throw e);
}
}
}

▪ For those of you who hate reinventing the wheel or just prefer libraries for already solved problems, there is a nice library called "react-error-boundary"[43] that implements a flexible ErrorBoundary component and has a few useful utils similar to those described above.

▪ Uncaught errors in the React lifecycle after version 16 will unmount the entire app. So at least a few ErrorBoundaries in strategic places are non-negotiable.

▪ A simple try/catch will catch errors in callbacks or in promises just fine, but it won't be able to catch errors that are coming from any nested components, and you won't be able to wrap useEffect or the return of the component in try/catch.

▪ The ErrorBoundary component is the opposite. It will catch errors originated in any component down the render tree, but it will skip promises and callbacks (anything async).

▪ We can merge them together and create an uber ErrorBoundary component if we catch the async errors with try/catch and re-throw them into the normal React lifecycle.

▪ We can either implement a simple useAsyncError hook for that or just use the react-error-boundary library, which operates on similar principles.. 
