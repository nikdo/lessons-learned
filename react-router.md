# React-router

## Change Selected Spot Lifecycle

New *React Router* passes new URL params as component props on route change. Routing components have all the information I need as properties.

In [their example](https://github.com/rackt/react-router/blob/latest/docs/guides/advanced/ComponentLifecycle.md#fetching-data) they load data during `componentDidUpdate`. This happens **after** component recieved new URL params as props and flushed changes to DOM. It is too late to render data from store based on URL parameter. But it is OK because what we want really is to dispatch action to fetch data as they may be on the server.

If I am 100% certain that selected spot is in the store, I can use the `componentWillRecieveProps` to store the get the selected spot from store and save it into `this.state` for the render.

But do I need to **keep selected spot ID in store**? What would be the benefit? Components has always access to it in props from react-router.

React-router wants to take part in state management as it manages the routing state (including params). One reason is that **Redux snapshotting and replaying** is then [broken](http://jlongster.com/A-Simple-Way-to-Route-with-Redux). But this can be fixed by *redux-simple-router* which keeps URL as serialized *react-router* state in Redux store.

That leads back to more generic questions:
Where to keep different kind of data?
Should store be the single point of truth?

## Types of Data in State

- content
	- persisted in server → server response → cached in memory
	- not persisted yet
		- last valid state (for example coordinates for map)
		- current state
- UI state 
	- examples: displayed page, component, tab, spinner, section, pagination
	- not persisted / persisted in URL (route, parameters), cookie, server

See [Redux introductions](http://rackt.org/redux/docs/introduction/Motivation.html) for more on this topic from Dan Abramov.

“You’ll often find that you need to store some data, as well as some UI state, in the state tree. This is fine, but try to keep the data separate from the UI state.”
-- from [Redux reducers documentation](http://rackt.org/redux/docs/basics/Reducers.html)
