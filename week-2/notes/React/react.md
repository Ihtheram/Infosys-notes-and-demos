# Single Page Applications

Single Page Applications or (SPA's) are webapps that render on a single page in the browser where all of Javascript, HTML, and CSS are loaded in and ready for the browser in one page load. During navigation, the browser never refreshes on that app because we are on the same page.

Advantages
-   Fast and responsive
-   Caching capability
-   Pleasant user experience across multiple platforms

Disadvantages
-   Don't perform well with SEO (Search Engine Optimization)
-   Less secure against Cross-site scripting
-   The page may take longer to load initially

# React Overview

React is a lightweight, Javascript **Library** created in 2011 by Facebook. It is meant to be used in conjunction with other modules to create front-end user interfaces for web applications.

## Framework vs Library

Framework is an entity that takes the developer's code and executes many abstracted-away processes. While the pros for a framework are that they do a lot of work for you, the cons include:
- more features, bloat the size of the framework
- less flexible with how features are used
- must use the entire framework for one feature
- less customizable

React is a library, that is only designed to enable users to declaratively describe their user interfaces
- it doesn't benefit from the opinionated nature of frameworks
- smaller/less bulky because it is only made to do one thing
- use other libraries/modules that you NEED to expand the functionality
- instead of a framework doing everything for you, the developer is responsible for connecting each component

## Tradeoffs and Cons of React

React doesn't use HTML templates, you simply write your components in a JS/TS file, this means you must have a better understanding of JS/TS.
React doesn't follow a traditional MVC design pattern, all data for a component is stored in that one file, and the components should be separated by concern.
React uses JSX/TSX instead of HTML, and JSX/TSX differs slightly from HTML, so must learn the new syntax.
React versioning is updated frequently so version changes and forward compatibility need to be taken into account
Online resources for React could be outdated (stackoverflow posts)

Since React is so flexible, there can be a lot of decision fatigue. There are a lot of choices you have to make, which normally fall into these categories
- What dev environment
- Class or functional components
- Types, States, and Styling

# create-react-app

The easiest way to create a new React application is with the `create-react-app` CLI

Install it with `npm i -g create-react-app`

To create your react app:

`npx create-react-app name-of-app`

When we use create-react-app it will create a newly generated React application that comes preconfigured with the baseline dependencies such as babel, webpack, jest, and more

## React with Typescript vs Javascript

React provides the flexibility to use either Javascript or Typescript to build components, and the create-react-app tool allows you to create an app for Typescript out of the box

We will be using Typescript to develop our React application

You can either create a react app with the typescript template or install the typescript module for react

`npx create-react-app name-of-app --template typescript`

Or to convert an existing application:

`npm i --save typescript @types/node @types/react @types/react-dom @types/jest`

Then create the tsconfig

`npx tsc --init`

Then finish up with setting the application configs however you like

## Special React Type Definitions

Since Typescript is known for its static typing, when you setup React to work with Typescript, you also have to install the special types as we saw above, and we will see these soon

# React Component Architecture
a software architecture that focuses on breaking the application into individual functional or logical components. These components communicate with one another to create a larger application. These components should follow the Single Responsibility Principle.

## Single Responsibility Principle
the programming principle that every module/component should have responsibility over not more than a single part of the application functionality. Component-based architectures help ensure component reusability and increased reliability due to the reuse of existing components. React follows a component-based architecture, and one should design the components in compliance with the Single Responsibility principle.

## Functional vs Class Components

Two ways of creating components:
- Traditional class-based
- New, recommended way with functions

Back before something known as hooks, function components were not as useful because they did not have access to react life cycle, and could not manage state, but now function components have nearly the same functionality, in less code, and nicer looking code. There is actually talk now, that class components may become deprecated in the future.

## React JSX

used to create the template for React components. It looks like HTML, but it is written inside of JavaScript. This gets injected into the virtual DOM and displayed on the browser. JSX uses Babel to compile it to ES6 or ES5 before everything is rendered. JSX unlike HTML is case sensitive, lowercase tags are rendered as HTML elements, and uppercase tags are rendered as react components. It is important to remember to wrap the entire JSX in a single root tag, this is because of the way React handles the DOM.

## React Virtual DOM

React renders the components to display them to the view.

Our react components are injected into the root html element to be displayed on the page, in fact, we never leave that one HTML page, we just swap components in the root element of index.html.

React uses a virtual DOM to map the component's view to the actual DOM object (because we don't write actual HTML in React). The reason behind a virtual DOM is that rendering the page and updating the real DOM is costly in performance. So the virtual DOM is much more lightweight than the actual DOM, for this reason React uses it only to update the Real DOM when necessary.

# Class Components Overview

React components start with an Uppercase and follow the PascalCase naming convention

Class-based components are simply Javascript Classes that extend `React.Component` class which includes:
- render(): returns the JSX that is "the structure of the component" / "what it is going to look like"
- constructor(): gets called when the component is instantiated, where you might want to initialize any state for your component
    - if a component takes in any properties, use the `super()` in the constructor


```tsx
export class GenericComponent extends React.Component<props:Prop,state:State> {

    state:State = {
        //some default state
    }

    //constructor for passing props, initializing state
    constructor(props:Prop){
        super(props);

        state = {
            //some initialized state
        }
    }

    render(
        return(
            <div>
                The content of the component
            </div>
        )
    )

}
```

# Functional Components in React

React allows you to create components based on functions
- These are more straightforward to write
- With the inclusion of Hooks, functional components are now (almost) as powerful as more bulky class-based components
- The only thing with function-based components, is that they must return JSX/TSX

# React Styling Components

In React we style components the same way we style HTML pages. We can include inline CSS or export the CSS into style sheets which is the preferred method because we can then share styles across multiple components. Since we are styling JSX/TSX and not HTML, the keyword to set a class on an element is `className` instead of just class. To link the CSS to the component, we simply use node module imports and it will be linked to the component

```
import './component.css'
```


# React Component Life Cycle

* Class-based components have built-in lifecycle methods for `Mounting`, `Unmounting`, `Updating`, and `Error Handling`
* The constructor is primarily used for initializing data in a component.
* `componentDidMount` is primarily used for grabbing/fetching data after the page loads (component loads).
* `componentWillUnmount` is primarily used for cleaning when a component is being destroyed.
* Function-based components don't extend React Component Class, so they did not have direct access to these until React version 16.8 when we introduced hooks.


# State in React

State stores information/data about the component, it is completely encapsulated in the component.
- No outside component can access the state of another component unless nested and passed as a prop.

State is special because it cannot be mutated directly, you must use the correct mutators/hooks

## Immutability of State in React

To set state in a class, we use the constructor or declare a field called state, then to mutate, we use the `this.setState` method of the React component class

To set state in a function component, we use the `useState` hook provided by React

# Data Binding

In React we can inject a variable value into a component JSX with curly braces `{varname}` this is considered data binding

# Nested Components

React allows components to be nested inside one another, which creates a hierarchy or parent-child relationship. Parent components can share state with their child through something called props

# Props:
How we pass data from one parent component to a child component, we include the prop we want to pass down in the child components tag. Props are immutable, they cannot be changed inside of the child class

## One-way data flow

In React data can flow only one way, from the top down. We can pass props only from a parent to its child, not the other way around, without doing some fancy magic called "Lifting State".

# Hooks

Built-in functions that allow us to "hook" into React state and lifecycle methods from functional components. This gave function components the same amount of power as class-based components.

## Basic Hooks: `useState`, `useEffect`, `useContext`, `useReducer`

`useState`:
- allows us to store and mutate state inside of a function component
- declare a state variable and a mutator inside of square brackets, then use the `useState(defaultVal)` to set the state originally
    - `const [state, setState] = useState("")`
- use the declared mutator to change and update the state
- with `useState`, the state does not have to be an object as it does in classes

`useEffect`:
- allows us to perform some logic at a specific point in the application life
- it takes in a callback function that performs logic
- it can be used to watch for specific events/changes in state to perform some logic
- If you only want it to run once at the beginning of the component's life, you can give it an empty array
- You can watch specific state members, by adding them to the array

`useContext`:
- used to access values being stored in the ContextAPI
- Context is a way to store application state

`useReducer`:
- used as an advanced in-component state manager, could also be used in conjunction with the Context API
- Instead of storing just a state value, it also takes in a reducer function, which describes how the state's data should be modified

# Create Function-based components in React

# Event Handling in React

Event handing in React is similar to HTML, however, with JSX you must use camelCase for the event name, and pass the handler as a JS reference rather than a string.

## Synthetic Events
Cross-browser wrapper around the browser's native event, this is used when an event occurs in React. Used because it is capable of pooling, which means the `SyntheticEvent` Objects are reused to improve performance, however, issues can arise because after the callback is called, the properties are nullified

# React Conditional Rendering

In React we can decide if/when components should be displayed with conditional rendering. We will typically see conditional rendering looking at some state of a parent component, and either `render` the child component or `render` nothing using a ternary operator.

# Mapping Elements from a list

If we want to render a list of elements in React, it is typically done with the `.map()` function on the array object.
However, React expects a unique key to be provided for each element that is being mapped through
- This helps React identify which items have been changed, added, or removed

The only time we should use an index (of the array) as a key, is when we have no other options.

# Additional Resources

- [React Website](https://reactjs.org/)

- [Getting Started with React](https://reactjs.org/docs/getting-started.html)

- [React Tutorial](https://reactjs.org/tutorial/tutorial.html)

- [Class Component Resources](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/class_components/)
