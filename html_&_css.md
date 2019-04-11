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

## SVG in HTML

Options:

1. `<img src="foo.svg" height="16" />`
	- 👍 alt attribute, simple
	- 👎 CSS styling, JS manipulation
2. `<svg width="16" height="16" ...`
	- 👍 CSS styling, JS manipulation
	- 👎 no separate caching, no alt attribute
3. `.foo { background-image: url('foo.svg'); }`
4. Icon font.


## URL Types

- absolute: `https://domain.tld:80/dir/file.ext`
- relative: `file.ext`; `./file.ext`; `../dir/file.ext`
- root-relative: `/dir/file.ext`

Browser interprets relative and root-relative URLs. It uses current page URL to translate it to absolute URL.

If `base` tag is defined, browser uses it to interpret relative and root-relative URLs instead of current page URL. This unfortunately [applies too on anchors and query strings](http://stackoverflow.com/a/1889957/5763764).

[Correct URI naming according to RFC](http://stackoverflow.com/a/17407082/5763764):
- absolute URI
- relative URI with relative path
- relative URI with absolute path

Sometimes different incorrect and confusing naming is used:
- absolute = fully-qualified
- root-relative = absolute

## Breakpoints

Do not use device-sepecifice breakpoints: [The 100% correct way to do CSS breakpoints](https://medium.freecodecamp.org/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862)

[Material Design Breakpoints](https://material.io/design/layout/responsive-layout-grid.html#breakpoints)

## Viewport Whitespace

How to set content to viewport whitespace?

Research results:

They never set margin or padding to body. It is always sections that have margins or paddings. They never use negative section margin to make it full width on body with padding.

Pages end with footer most of the time, so there is no need for bottom page padding. Bottom padding is achieved by section bottom padding or last element bottom margin.

## Color Names

Use color names to be able to reason about them.

- [Giving Colors More Colorful Names](https://www.viget.com/articles/naming-colors/)
- [Naming Colors](https://thoughtbot.com/blog/naming-colors)



## CSS Best Practices

**Object Oriented CSS** is good for large websites. Websites where large pack of developers with different skill-level are working on it. It's not wise to use it for small to medium projects. [It's OK to use IDs and descendant selectors instead.](http://www.zeldman.com/2012/11/21/in-defense-of-descendant-selectors-and-id-elements/)

[Remove the forward slash](http://learn.shayhowe.com/html-css/writing-your-best-code/) at the end of self-closing elements

## Fonts
If you haven't set the font size anywhere on the page, then it is the browser default, which is probably **16px**. ([mdn](https://developer.mozilla.org/en/docs/Web/CSS/font-size#Ems))

### Font Smoothing

There is a [difference](https://www.joelonsoftware.com/2007/06/12/font-smoothing-anti-aliasing-and-sub-pixel-rendering/) how fonts are smoothed on Mac and Windows. Google Fonts and Font Squirrel use both `-webkit-font-smoothing: antialiased;`, Sketch seems to do the same. To match designs with output, this setting has to be used.


## Stylus

Media queries [can be stored](http://1pixelout.net/2015/10/02/simple-breakpoint-media-queries-with-stylus/) in hash and there can be mixin to call them easily.

## Bootstrap

There are [tree options for customizing Bootstrap](https://www.smashingmagazine.com/2013/03/customizing-bootstrap/) from the most basic to the most sensitive:
1. Override CSS
2. Generate custom build
3. Modularized LESS code