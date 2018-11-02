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

##REDUX

Generally, you’ll start by creating a JavaScript file in your project called actions.js

Within it, you’ll
ACTIONS
Export const setSearchField = (text) => ({
	type: CHANGE_SEARCH_FIELD,
	payload: text
})

Payload is a common term to refer to whatever is being delivered by the action, which in this case would be whatever the user enters.

The type is a constant, and constants are capitalized. With just a string, we might misspell something, but with a constant, we’ll get an error.


###REDUCERS

const initialState = {
    searchField: ''
}

export const searchRobots = (state=initialState, action={}) => {
    switch(action.type) {
        case CHANGE_SEARCH_FIELD:
            return Object.assign({}, state, {searchField: action.payload})
        default:
            return state;
    }
}


Our actions are objects that we are returning, and our reducer gets the input of a state and an actions and if the reducer cares about the action, such as one related to searching Robots, we’ll act upon the state.

Our reducer needs to return a new state, rather than modify our existing state. Remember: state is read only. 


###PROVIDERS (react-redux)

In the Store, you want to make sure you combine all of your reducers into one rootReducer. You can then pass the Store down into the main App component.

React-redux gives us a nice feature in the Provider component, which allows us to wrap our main react app component in a Provider component, as shown below:

const store = createStore(searchRobots);

ReactDOM.render(
    <Provider store={store}>
        <App />, document.getElementById('root')
    </Provider>
    );


Connect is a method which allows us to provide information down through our components from the Provider parent. Normally we would use a .subscribe function to make any component aware of Redux, but Connect allows us to make the component redux-aware.


const mapStateToProps = state => {
  return {
    searchField: state.searchRobots.searchField
  }
}

const mapDispatchToProps = (dispatch) => {
  return{
    onSearchChange: (event) => dispatch(setSearchField(event.target.value))
  }
  }

export default connect(mapStateToProps, mapDispatchToProps)(App);

Connect is a higher order function, so it runs, and whatever connect does, it will return another function which takes the App as a parameter.

mapStateToProps - what state connect is listening to

mapDispatchToProps - what action to listen to

Connect will listen to the state for certain actions and give the values to the Apps as props.