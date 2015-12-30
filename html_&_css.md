# HTML & CSS

## Responsive Design

The [best way](https://responsivedesign.is/strategy/page-layout/defining-breakpoints) how to define *breakpoint* is to start **mobile-first** and add breakpoint when there is too much whitespace and design becomes terrible. Breakpoint shouldn't be linked to some device screen to be future-proof. Take the device resolution out of the equation.

Or use [**The Goldilocks Approach**](http://goldilocksapproach.com/article/): start with optimum paragraph width and then work up and down. For smaller viewports, cut down margins, etc. For larger viewports, expand to multiple columns.

Optimal characters per line: 66
Maximum characters per line: 80

**Do not set default font size**, device manufacturer or user has already done it and website shouldn't mess with that. **Use ems instead of pixels.**

Pick [minor breakpoints if necessary](https://developers.google.com/web/fundamentals/design-and-ui/responsive/fundamentals/how-to-choose-breakpoints?hl=en#pick-minor-breakpoints-when-necessary) to tune the design a bit for the whitespace gained.

In my opinion, it would be better to store breakpoints in variables and group code by design elements, not by device.

Set up maximum and minimum content width to avoid design breakdown for super-large and super-small devices:
```
#container
	width 70%
	max-width 80rem
```


## Stylus

Media queries [can be stored](http://1pixelout.net/2015/10/02/simple-breakpoint-media-queries-with-stylus/) in hash and there can be mixin to call them easily.