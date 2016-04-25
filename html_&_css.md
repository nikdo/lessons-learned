# HTML & CSS

## Responsive Design

The [best way](https://responsivedesign.is/strategy/page-layout/defining-breakpoints) how to define *breakpoint* is to start **mobile-first** and add breakpoint when there is too much whitespace and design becomes terrible. Breakpoint shouldn't be linked to some device screen to be future-proof. Take the device resolution out of the equation.

Or use [**The Goldilocks Approach**](http://goldilocksapproach.com/article/): start with optimum paragraph width and then work up and down. For smaller viewports, cut down margins, etc. For larger viewports, expand to multiple columns.

Optimal characters per line: 66
Maximum characters per line: 80

**Do not set default font size**, device manufacturer or user has already done it and website shouldn't mess with that. **Use ems instead of pixels.**

Pick [minor breakpoints if necessary](https://developers.google.com/web/fundamentals/design-and-ui/responsive/fundamentals/how-to-choose-breakpoints?hl=en#pick-minor-breakpoints-when-necessary) to tune the design a bit for the whitespace gained.

In my opinion, it would be better to store breakpoints in variables and group code by design elements, not by device.

Set up **maximal and minimal content width** to avoid design breakdown for super-large and super-small devices:
```
#container
	width 70%
	max-width 80rem
```

[Shrink lines and move items up](https://www.youtube.com/watch?v=sOuLv-PRbt4) for wide but short devices like landscape tablet.

## CSS Best Practices

**Object Oriented CSS** is good for large websites. Websites where large pack of developers with different skill-level are working on it. It's not wise to use it for small to medium projects. [It's OK to use IDs and descendant selectors instead.](http://www.zeldman.com/2012/11/21/in-defense-of-descendant-selectors-and-id-elements/)

[Remove the forward slash](http://learn.shayhowe.com/html-css/writing-your-best-code/) at the end of self-closing elements

## Stylus

Media queries [can be stored](http://1pixelout.net/2015/10/02/simple-breakpoint-media-queries-with-stylus/) in hash and there can be mixin to call them easily.