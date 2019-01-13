# SVG in HTML

Options:

1. `<img src="foo.svg" height="16" />`
	- 👍 alt attribute, simple
	- 👎 CSS styling, JS manipulation
2. `<svg width="16" height="16" ...`
	- 👍 CSS styling, JS manipulation
	- 👎 no separate caching, no alt attribute
3. `.foo { background-image: url('foo.svg'); }`
4. Icon font.
