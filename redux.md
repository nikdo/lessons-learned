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

## WebSockets and Redux

WebSocket connection [belongs to the middleware](https://redux.js.org/faq/code-structure#where-should-websockets-and-other-persistent-connections-live) in Redux.

An example of WebSocket middleware: [Write your own WebSocket middleware](https://dev.to/aduranil/how-to-use-websockets-with-redux-a-step-by-step-guide-to-writing-understanding-connecting-socket-middleware-to-your-project-km3)

Middleware can be used to solve many different architectural problems: [You Aren’t Using Redux Middleware Enough](https://medium.com/@jacobp100/you-arent-using-redux-middleware-enough-94ffe991e6)

## Loading flags

Loading and error state should be stored in *Operations* part of the store as described [The 5 Types Of React Application State](http://jamesknelson.com/5-types-react-application-state/) article.

An interesting concept how to handle error / loading states for all endpoints is to parse action type constant: [Better Way to Handle Loading Flags in Your Reducers](https://medium.com/stashaway-engineering/react-redux-tips-better-way-to-handle-loading-flags-in-your-reducers-afda42a804c6)

## Component state vs Redux state

Dan Abramov [answers question](https://github.com/reduxjs/redux/issues/1287#issuecomment-175351978) How to choose between Redux's store and React's state:

> Use React for ephemeral state that doesn't matter to the app globally and doesn't mutate in complex ways. For example, a toggle in some UI element, a form input state. Use Redux for state that matters globally or is mutated in complex ways. For example, cached users, or a post draft.

> Sometimes you'll want to move from Redux state to React state (when storing something in Redux gets awkward) or the other way around (when more components need to have access to some state that used to be local).

> The rule of thumb is: do whatever is less awkward.


## Combining API requests

Combining multiple API requests into single atomic Redux action to abstract from API complexities does not play well with [API middleware abstraction](https://github.com/reduxjs/redux/blob/master/examples/real-world/src/middleware/api.js). More advanced tool like redux-saga or redux-observable might be a better fit.


## Immutable.js

Immutable.js [has drawbacks](https://github.com/reduxjs/redux/blob/885a2db6ef8721bb8facd1a6df2fcff979237ee4/docs/recipes/UsingImmutableJS.md#what-are-the-issues-with-using-immutablejs) that do not outweigh benefits. With careful coding I can prevent mutations without using this library. The benefit of [`getIn`](https://immutable-js.github.io/immutable-js/docs/#/getIn) handling incomplete nested structures is also not worth it.

## Redux-simple-router

There are only few benefits of using it:
1. Keeping current URL in Redux state to be able to snapshot and time-travel.
2. Ability to change URL from action creator by using their action 
3. Ability listen to path changes in reducer.

Currently I don't need it.