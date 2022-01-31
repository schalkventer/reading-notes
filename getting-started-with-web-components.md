▪ Web components are web specifications that provide the user with a component-driven methodology for development. It also provides encapsulation and allows you to use a component-driven methodology without any dependencies.

▪ You can also use this book to learn about and get into component-driven methodologies

▪ Web Components, as the name indicates, are components that can be reused across different sections of a website by keeping encapsulation in check

▪ They can even be published on the web, and be used by another site with the help of a simple import.

▪ You will be able to encapsulate your Web Components with the help of a shadow DOM, and you will be able to use templates to achieve reusability.

▪ Custom element: The ability to create custom HTML tags and make sure that the browser understands how to use this HTML tag

▪ Shadow DOM: The ability to encapsulate the contents of the component from other parts of the DOM

▪ Template: Being able to create a reusable DOM structure that can be modified on the fly and output desired results

▪ Autonomous custom element: Any element that can be used by itself, without depending on another HTML element can be considered an autonomous custom element

▪ Customized built-in element: This type of custom element can extend the functionality of an already existing HTML tag

▪ Hello World

▪ You can check whether a custom element is already defined or not with the help of the following code:

customElements.get('smiley-emoji');

▪ This is the second specification for Web Components and this one is responsible for encapsulation

▪ Both the CSS and DOM can be encapsulated so that they are hidden from the rest of the page

▪  What a shadow DOM does is let you create a new root node, called shadow root, that is hidden from the normal DOM of the page.

▪ This shadow root can have any HTML inside and can work as any normal HTML DOM structure with events and CSS. But this shadow root can only be accessed by a shadow host attached to the DOM. 

▪ Notice that there is a tag in the shadow root. Even though this tag is present inside the

tag, the shadow root does not let JavaScript APIs touch it. This is how the shadow DOM encapsulates code inside itself.

▪ Pretty simple, right? Remember, we are still discussing the shadow DOM spec. We haven't started implementing it inside a custom element yet.

▪ The template specification provides a way to hold HTML on the browser without actually rendering it on the page.

▪ Similarly, we can have any number of templates on the page, which can be used by any JavaScript code

▪ Inside the HTML file, index.html, instead of type=text/javascript, we can use type=module to tell the browser that the file that we are importing is a module

▪ We then talked about templates and how they provide an element of reusability inside a Web Component.

▪ A life cycle event is an event that occurs during the life cycle of a Web Component. This chapter deals with these events and how to access them with the help of callback methods.

▪ Life cycle events are events that are triggered inside a web component when it reaches a certain stage of execution

▪ There are four life cycle callbacks available to Web Components as of now

▪ connectedCallback()

▪ disconnectedCallback()

▪ adoptedCallback()

▪ attributeChangedCallback()

▪ This interface/callback gets invoked every time a copy of a Web Component gets added to the DOM

▪ As you can see in the code, we are now making a call to fetch the student list inside the connectedCallback() method. This makes sure that the code gets executed, once the Web Component is attached to the web page

▪ Event handlers consume memory, and, when the DOM associated with them is removed, the event handler is still on the page, listening to events, still consuming memory. The callback, disconnectedCallback(), gives Web Components a way to write code that can handle these scenarios. 

▪ When you are running this Web Component on a page, you can manually remove the component and see that disconnectedCallback() gets called automatically. I prefer going to the dev console and typing the following code to see it happen:

document.querySelector('custom-button').remove();

▪ adoptedCallback()

This callback gets triggered when the Web Component is moved from one parent to another.

▪ Since all the custom elements act and behave like any other HTML element, they also have the ability to have attributes inside them

▪ But, in order to make a Web Component use the attributes provided, we will first ask it to observe certain attributes, which we can provide in an array like this:

static get observedAttributes() {
return ['fullname'];
}

▪ Once we have started observing these attributes, we can then use the attributeChangedCallback() to make necessary changes to custom elements as per the requirement. I am simply updating the name in the following callback: 

▪ attributeChangedCallback(name, oldValue, newValue) {
if (name == 'fullname') {
this.innerText = 'Hello, my name is ' + newValue;
}
}

▪ While we can add CSS inside the shadow root with the help of selectors, we do not have a selector associated with the shadow root itself, which acts as a container for the HTML. So, we can have CSS attached to this shadow root with the help of the :host selector.

▪ We are again using the :host selector as a way to add CSS to the shadow root of our Web Component.

▪ When you are creating a Web Component, you need to make sure that your Web Components are accessible at least up to a certain extent

▪ So, let's talk about it. The Gold Standard Checklist is a working draft (see https://github.com/webcomponents/gold-standard/wiki) that tells the creators of a Web Component what things should be taken care of in order to create a good, reusable component. 

▪ Once you are done with this, you can simply go to https://www.webcomponents.org/publish and scroll down to the section where it says Ready To Publish?, and simply put your npm package name and click on the Publish button:

▪ In this section, we will extend our current knowledge of Web Components and use the concept of slots to put HTML content inside our Web Components

▪ A slot is a placeholder for any HTML markup that can be placed inside a Web Component

▪ A slot can have a name, and this slot can have HTML or plain text that can be used inside our component.

▪ In a Web Component, there can be any number of slots. It totally depends on your use case

▪ We will be looking at an example of an  tag:



If you look at it carefully, we have an attribute called value giving it some default value. So if you want to get the value of this tag, you can get it by using the following code:

document.querySelector('input').getAttribute('value');

So, you are directly referencing the attribute for this tag to get the value. But there is another way in which you can get this value. And that is as follows:

document.querySelector('input').value;

This time, we are grabbing the value from the property value of the tag.

▪ Polymer and Stencil. In the background, these two libraries use Web Components, but both of them come with their own features.

▪ A major difference between the vanilla Web Components and Polymer is that Polymer comes with its own data system

▪ Also, instead of using HTMLElement, we are using PolymerElement. And then, we are registering the class as a custom element. 

▪ Stencil is a compiler for Web Components. It uses TypeScript and JSX to create Web Components

▪ It even comes with a lot of features that are missing in the vanilla Web Components that can be used to make good single-page web apps

▪ When we talk about technical jargon, we will be calling this @Component as @Component decorator

▪ In this section, we will use one more decorator called the @Prop decorator to declare the variables that will act as properties which can be passed onto other components. 

▪ With the help of this @Prop decorator, we are defining two properties: first and last. The first property also has reflectToAttr set to true, which means that this property can be seen as an attribute when it gets called inside the component:
