# Infrastructure

## NPM

*devDependencies* are [not installed in production](http://stackoverflow.com/a/22004559). That means most hosting providers (including OpenShift) won't install it during git push deployment.

## webpack

### How to Distribute Static Files
	
1. [Require everything from JavaScript](http://stackoverflow.com/a/27651720/5763764).
	- [copy index.html](http://stackoverflow.com/a/33519539/5763764)
	- [generate index.html](https://github.com/ampedandwired/html-webpack-plugin) 
2. Copy folder with static files [using webpack plugin](http://stackoverflow.com/a/33374807/5763764).
3. Copy static files using *npm* script.
4. Static files versioned in *dist* folder.

**Selected**: option 1 with copying index.html

Static files:
- `index.html`
- `robots.txt`
- images
	- but they are required on certain places, why not to use webpack
- vendor JavaScripts
	- examples: ion.sound, piecon, moderniz, picturefill, bootstrap
	- but they should be ideally bundled too or served from CDN