# Simplest Grid

![Simplest Grid](http://herrkessler.de/simplest-grid/SimplestGrid-lg.png)

## Why?

You will see that this grid is quite close to [thoughtbot's](https://github.com/thoughtbot) fantastic [Bourbon Neat](https://github.com/thoughtbot/neat) Grid and might ask yourself: **"Why does pretty, pretty similiar grid exist??"**

I just needed a solution for a combined unsemantic and semantic grid I could use for myself prototyping with [Codekit](https://incident57.com/codekit/) or [Gulp](http://gulpjs.com/) or [Grunt](http://gruntjs.com/) and final development with [TYPO3](http://typo3.org/). Don't get me wrong, I am very, very happy with [Bourbon Neat](https://github.com/thoughtbot/neat), but give Neat a try when not being able to use semantic markup or Rails or Node or ...

So maybe you find this project helpful, too. And be aware this is work in progress!

Have a look at the [example page](http://herrkessler.de/simplest-grid/).

## Requirements

* SASS
* or Nothing

## Getting Started

There are two ways of using this grid: either as a semantic grid with SASS or an ol' unsemantic CSS grid, like 960.gs back then... with lots of class names!

### SASS

With SASS you can set the grid variables in the _grid-settings.sass and then add both the _grid-settings.sass and _grid.sass to your base imports.

<pre>
// --------------------------
// Grid Settings
// --------------------------

$grid-width:      1088px
$columns:         12
$gutter:          2%

// --------------------------
// Breakpoints
// --------------------------

$mobile:          480px
$tablet:          768px
$screen:          1024px

// --------------------------
// Import Grid
// --------------------------
</pre>

In your base import stylesheet.

<pre>
@import grid-settings
@import grid
</pre>

First set the container e.g.

<pre>
.wrapper
	+container
</pre>

Then add a row e.g.

<pre>
.row
	+row
</pre>

Now you can @extend your divs with any grid width you might need. The standard grid has twelve columns with a margin of 2%. You can change the margin or the amount of columns as you like. There is a full width version on the grid without margins.

<pre>
.element
	+column(12)
	
.element
	+column(4)
	
.element-full-width
	+column(4, full)
</pre>

There is also an omega() mixin like in Neat if you need to have a undefined list of elements, e.g.

<pre>
ul
	+row
ul .li
	+columns(4)
	+omega(4n)
</pre> 

And last but not least, use the standard media queries or define them in the settings yourself.

<pre>
.element
	+column(3)
	+media($tablet)
		+column(6)
	+media($mobile)
		+column(12)
</pre>

### CSS

With good ol' CSS, just add the simplest-grid.css to your head section or import it into your stylesheet. Have a look at the [working example](http://herrkessler.de/simplest-grid/) with all available classes: standard, responsive, full width and combinations of all of them.

<pre>
link href='css/simplest-grid.css' rel='stylesheet'
---
@import: url('simplest-grid.css')
</pre>

Then add the preconfigured CSS classes to your divs. (The numbers stand for width in percentage, e.g. div.g-50 : 50% width. div.g-12 is actually 12.5%)

<pre>
div.container
	div.row
		div.g-100 
	div.row
		div.g-50
		div.g-50
	div.row
		div.g-30
		div.g-30
		div.g-30
	div.row
		div.g-25
		div.g-25
		div.g-25
		div.g-25
	div.row
		div.g-16
		div.g-16
		div.g-16
		div.g-16
		div.g-16
		div.g-16
	div.row
		div.g-12
		div.g-12
		div.g-12
		div.g-12
		div.g-12
		div.g-12
		div.g-12
		div.g-12
</pre>

In order to get the whole thing responsive with the standard breakpoints (1024px, 768px, 480px), use the .res class

<pre>
div.g-100.res, div.g-50.res, div.g-30.res, div.g25.res, ...
</pre>

If you want the grid to span the full column width without any margins use the .full class

<pre>
div.g-100.full, div.g-50.full, div.g-30.full, ...
</pre>

And guess what, you can combine both versions!

<pre>
div.g-100.full.res, div.g-50.full.res, ...
</pre>

If you don't know what's coming up in a row you can add some .omega classes, there are .two-n, .four-n, .six-n, .eight-n, .odd & .even, e.g.:

<pre>
div.g-25.omega.four-n, div.g-25.omega.four-n, div.g-25.omega.four-n, div.g-25.omega.four-n, ...
</pre>

### So is this cross-browser tested?


**Works - so far - in**:

* Chrome
* Safari
* Firefox
* IE9+
* IE8 (with selectivizr only and no media queries)

### What comes next?

There are subpixel rendering problems in Safari ~~that I will take care of next~~. 

Skipped subpixel rendering problems... Take a look at A List Apart article on [Fluid Grids](http://alistapart.com/article/fluidgrids). Even my archetype Bourbon Neat can't cope with that. 