# React

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