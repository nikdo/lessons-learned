# React

## Redux and Relay

GitBook allows you to organize your book into chapters, each chapter is stored in a separate file like this one.

[Redux and Relay are exclusive](https://github.com/rackt/redux/issues/1036)

Redux is currently the winner from all Flux implementations.
- most popular, mentioned as winner in many discussions
- works with react-router - same contributors
- isomorphic in mind

## React Animations

Animated elements has to have **key attribute** even if it is animated switch between two elements. Otherwise React rewrites existing element to new one. It works without key attribute if the element is removed in the second state.

ReactCSSTransitionGroup must be **outside** the condition causing animation. If it is inside it is mounted alongside the content and it doesn't work.

*ReactCSSTransitionGroup* waits for an animation to complete before removing DOM node. This means, it’s **whole conent has to be animated** otherwise React throws errors and fails to remove DOM node.

### Problems:
- Animating different children differently.
- Animating only specific element indside element that will appear.
- Animating element differently for different viewports (teaser).
