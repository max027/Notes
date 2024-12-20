* Jsx allows developers to write html directly inside javascript code
* html code inside return must be wrape inside top level html tags

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

