#General React Review

##State of Front-End Development
At the end of the day, Front-End libraries/frameworks are just tools. Things continue to change, and Vue/React expertise may no longer be important in five years.

Angular is opinionated and might be better for legacy code. React is for a strong dev team that needs to be flexible. Vue would be a simple way for writing code and great for junior developers.

Facebook, Instagram and other larger companies use React. React tries to maintain the idea of JavaScript purity, which uses jsx to write psued-html.

Vue, meanwhile, is more traditional in the sense of the framework using HTML templating. 

Both frameworks are fairly lightweight; Vue is open-source.

##React 1.6 Updates

###React Render Return Types
We won't need to wrap list items in an extra element anymore, and we can also return strings without needing to have them saved in a span.

###Better error handling
React 16 uses a more resilient error handling strategy. Normally, if an error is thrown inside a component's render or lifecycle methods, the whole component tree is unmounted from the root. We can use error boundaries as special components that capture errors inside their subtree and display a fallback UI in their place.

In actual implementation, we would define an Error Boundary component and wrap components dependent on external data calls in it. The Error Boundary component would have a state where the Error is set to False, and a lifecycle method called componentDidCatch(error, info) which would set state to true if an error is caught.

From there, the render method would have an if to check if this.state.hasError, returning an error UI. Otherwise, it return this.props.children, or the children of the existing object.