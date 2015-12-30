# Google Maps

## Destroying Google Map Instance

Google Map doesn't work very well with React.

Google [sugestion](http://stackoverflow.com/a/10660672/4398388) for single-page applications to work with single map instance and preserve it because they do not officially support destroying map instance scenario.

This is problem, because React effectively removes map element from DOM when navigating to different route and it is [not possible](http://stackoverflow.com/questions/8073655/google-maps-api-v3-change-map-div) to add existing map instance to a new DOM element. Contrary module local variables holding instance of map, markers, etc. are preserved.

The only viable solution is (trying) to **destroy everything on umount**: map instance, components and bound events. This is suggested by some guy from Google in [Stack Overflow thread](http://stackoverflow.com/a/10660672/4398388) and also by Revelry CTO in comment under article [Google Maps + React](http://revelry.co/development/2015/02/19/react-google-maps/).


## Google Map vs. React State

What React does from DOM elements, it cannot do for Google Map elements. [Some libraries](https://github.com/pieterv/react-googlemaps/issues/16) solve this by re-rendering whole map and it's components on state change (like for example selecting marker), but this has some severe drawbacks:
- decreased performance
- map elements flickering 
- elements z-index change

The only solution is to persist previous state of map (and it's components) and **implement similar diffing algorithm manually**.