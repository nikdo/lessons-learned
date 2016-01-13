# React

[Whole React component lifecycle in a code comment]( https://github.com/facebook/react/blob/master/src/renderers/shared/reconciler/ReactCompositeComponent.js#L49-L74)

## Animations

Animated elements has to have **key attribute** even if it is animated switch between two elements. Otherwise React rewrites existing element to new one. It works without key attribute if the element is removed in the second state.

*ReactCSSTransitionGroup* must be **outside** the condition causing animation. If it is inside it is mounted alongside the content and it doesn't work.

*ReactCSSTransitionGroup* waits for an animation to complete before removing DOM node. This means, it’s **whole conent has to be animated** otherwise React throws errors and fails to remove DOM node.

### Problems:
- Animating different children differently.
- Animating only specific element indside element that will appear.
- Animating element differently for different viewports (teaser).

## PropType Validation

Dan Abramov validates [in his examples](http://rackt.org/redux/docs/basics/UsageWithReact.html) all props in every component even if it means that he repeats validation of child components.

## Smart & Dumb Components

Smart components shouldn't render DOM and should be only smart container of dumb components. Smart components should hold state from Flux store and pass it as props to dumb components.

Dumb components also shouldn't dispatch actions. Smart component should pass callbacks for that.

Dumb components can be rendered on a single page with styles to run screen shot regression tests.

This will also extract layout components like *Page*, *Sidebar*.

See [Smart and Dumb Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.d83x3rplr) by Dan Abramov for more details.