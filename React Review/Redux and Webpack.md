#Redux and Webpack

When considering the critical render path, there are two main bottlenecks for JavaScript:

1) Minimizing DOM manipulation through JavaScript
2) Improving how we deliver JavaScript to the front end

DOM -> CSSOM -> Render Tree -> Layout -> Paint

The better we deliver our JavaScript, the faster we get to the Render Tree step. From there, we want to be smart about how much re-rendering we do. Every time JavaScript changes something in the DOM, the browser returns to the Render Tree and relayouts and repaints.


##Redux and State Management

What does Redux improve?

When building a React app, we have State, which describes what our app looks like. State management becomes a hard problem as our apps start to grow. All of the small components push updates to the state, forcing re-renders.

Redux solves this problem for us by removing all of the state from the components, instead leaving it up to properties. The state is maintained in a store, a massive object at the top of the pyramid. The state is passed down through the components as properties.

Why Redux?

Most companies are using Redux in tandem with React. It's good for managing large state, useful for sharing data between containers and allows for predictable state management using the 3 principles:

1) Single Source of Truth
2) State is read only
3) Changes are made using pure functions

Redux Process

Action (user clicks on something) -> Reducer (a pure function that receives an input and creates an output) -> Store (the State is updated) -> Changes (changes are made)

With redux, we make sure all actions flow through one reducer, which always returns the same State based on the action and updates the Store.

Redux uses an architectural pattern called a Flux Pattern:

Action -> Dispatcher -> Store -> View