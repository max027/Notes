# Component
* React applications are built from isolated pieces of UI called components. A React component is a JavaScript function that you can sprinkle with markup.
* Components can be as small as a button, or as large as an entire page
* Each React component is a JavaScript function that may contain some markup that React renders into the browser. 
## Props
* React components use props to communicate with each other.
* Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, functions, and even JSX!

# props.children
* The { props.children } property allows you to create a generic template component that can be modified by 
the parent when it is invoked.

* In React the data flow in unidirectional i.e from parent to child
* two types of data in react props data and states data
    - props data is data outside the component and cannot mutate
    - state data is data inside the component and can mutate

# hooks

* let you hook into react state and lifecycle features from component
* e.g useState(val)
* Hooks also come with a set of rules, that you need to follow while using them. 
    - You can only call hooks at the top level of your component or your own hooks. 
    - You cannot call hooks inside loops or conditions. 
    - You can only call hooks from React functions, and not regular JavaScript functions. 

## useRef
* There are situations where accessing the DOM directly is needed, and this is where 
the useRef hook comes into play.
*  Unlike useState, useRef doesn't trigger re-renders when its value changes.


## State and useState
* Data in component that determines behavior
*  prop drilling is a situation where you are passing data from a parent to a child component,
then to a grandchild component, and so on, until it reaches a more distant component further down the component tree,
where this data is required.


## useContext
Context lets the parent component make some information available to any component in the tree below it—no matter 
how deep—without passing it explicitly through props.


# Assets
* In react assets can be images,stylesheet,fonts or any other file needed by your application
*  SSR, React components are rendered to HTML on the server, and the visitor downloads the finished HTML code. 

# Controlled components
Controlled inputs accept their current value as a prop and a callback to change that value. 
That implies that the value of the input has to live in the React state somewhere

## Value attribute
The value attribute in React allows an input field to be controlled by React state, meaning:
* The displayed value is always determined by React state.
* Any changes to the input field trigger an event that updates the state.
* React fully controls the input's value instead of the browser.

# Keeping Components Pure
 a pure function is a function with the following characteristics:

* It minds its own business. It does not change any objects or variables that existed before it was called.
* Same inputs, same output. Given the same inputs, a pure function should always return the same result.

# Understanding Your UI as a Tree
React, and many other UI libraries, model UI as a tree. 
# Adding Interactivity
React lets you add event handlers to your JSX. Event handlers are your own functions that will be triggered in response to interactions like clicking, hovering, focusing form inputs, and so on.
## Event propagation
Event handlers will also catch events from any children your component might have. We say that an event “bubbles” or “propagates” up the tree: it starts with where the event happened, and then goes up the tree.

