Kanso-Font-Awesome
==================

Font-Awesome Less files wrapped in a Kanso package

Using the package
-----

This package assumes you are using less to style your pages.
If you aren't see the bottom of this readme for instructions

Add the `@FontAwesomePath` variable to your main .less file so it matches your rewrites
then import thr font-awesome.less file.

```css
@FontAwesomePath: "../font";
@import "font-awesome.less";
```

If you're adding bootstrap's less files manually, replace `@import "bootstrap/sprites.less"` with `@import "font-awesome.less"` in your main .less or bootsrap.less file. Otherwise, you can also just `@import "font-awesome.less"` after importing `bootstrap.less`.

You're done! See [Font Awesome](http://fortawesome.github.io/Font-Awesome/) for more.


Adding less-precompiler and a less file so you can use this package
-----

These are instructions on adding a less file if your project doesn't already use them.
Adding the less-precompiler package is easy to-do
It is a dependency of kanso-font-awesome but you'll need to add it separately so you can tell it to compile your .less

Add it to dependencies in your kanso.json

```json
"dependencies": {
		"less-precompiler": null,
        "kanso-font-awesome": null,
        ...
	}
```

Create a .less file so you can compile and attach it to your couchAPP

lets say you have one called "main.less" and put in a folder called css now in your app we have: css/main.less

inside this .less file we include font-awesome

```css
@FontAwesomePath: "../font";
@import "font-awesome.less";
```

Now we tell less-precompiler to compile and attach your less file
Back in your kanso.json add this:

```json
"less": {
		"compress": true,
		"compile": ["css/main.less"],
		"remove_from_attachments": true
	}
```

Your kanso.json should look something like this now

```json
{
	"attachments": ["index.html", "css", "js", "img"],
	"less": {
		"compress": true,
		"compile": ["css/main.less"],
		"remove_from_attachments": true
	},
	"dependencies": {
		"attachments": null,
		"less-precompiler": null,
		"bootstrap": null,
        "kanso-font-awesome": null
	}
}
```

Finally in your html files you will need to load the css

```html
<link rel="stylesheet" type="text/css" href="css/main.css" />
```
