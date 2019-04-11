# Redux

Redux is the winner from all Flux implementations.
- most popular, mentioned as winner in many discussions
- works with react-router - same contributors
- isomorphic in mind

State is an object tree in a single store. Too change state, action has to be dispatched. Action describes *what happend*. Reducer handles action, but it doesn't mutate state, it returns new state.

Reducer can be splitted into multiple reducers. They handle different actions and changing different parts of the object tree.

Proper way of building Redux and React app:

1. Create actions and action creators.

    Separate user input action from data fetching action as they may occur independetnly. Handle request failures.

2. Design state shape.

    Keep flat structure and reference objects by IDs. Separate UI state from content. Caching and fetching information should be stored along with content (isFetching, didInvalidate, lastUpdated, etc.).

3. Define logic with reducers (and write tests).

4. Code all React dummy components, feed them with static data.

5. Connect with Redux.


**Redux middleware** provides a third-party extension point between dispatching an action and the moment it reaches the reducer. It can be used by libraries like *redux-thunk* to perform async call to API and dispatch multiple actions in the process. Or it can be used for routing.

See [Redux Basics tutorial](http://rackt.org/redux/docs/basics/index.html) to dig deeper.

Redux and Relay are [exclusive](https://github.com/rackt/redux/issues/1036).

## Application State

It is useful to differentiate between different types of client application state and handle these states differently: [The 5 Types Of React Application State](http://jamesknelson.com/5-types-react-application-state/)


## Redux-simple-router

There are only few benefits of using it:
1. Keeping current URL in Redux state to be able to snapshot and time-travel.
2. Ability to change URL from action creator by using their action 
3. Ability listen to path changes in reducer.

Currently I don't need it.