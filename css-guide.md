# CSS GUIDE

## General Formatting

* use all lowercase and dashes for class names (eg. my-class, not my_class or myClass)
* multi-line css (I tend to make an exception to this if there's only a single rule within the selector.)
* for rules with multiple selectors, each selector gets it's own line
* if you're not using a pre-processor, use indent blocks to reflect HTML heirarchy

	__Example__

		` 
		.my-class,
		.my-other-class {
			background: #000;
			color: #fff;
		}

		.yet-another-class { color: #000;}

		nav {
			....
		}

			nav li {
				...
			}

				nav li a {

				}
		`
* use a table of contents at the top of your file
* use a prefix (like `::` or `$`) ahead of section labels so you can easily find the section from your text editor
	__Example__
	`
	/* -------------------------------------------------- 
   	Table of Contents
	-----------------------------------------------------
	Global Typography
	Shared Styles
	Contact Us
	About Us
	*/

	/* -----------------------------------------
   	::Global Typography
	----------------------------------------- */

	* -----------------------------------------
   	::Shared Styles
	----------------------------------------- */
	`

## HTML decoupling and naming conventions

* Try to avoid IDs. I'm not wholly against them, but you'll avoid a lot of nasty specificity wars by sticking mostly to classes, especially on container elements.
* Use common prefixes for related elements. (eg. news-photo and news-pullquote)
* Try to make general, reusable classes and styles where appropriate (eg. a single `button` class that can accomodate a button with text of any with)

## Typography

* set body font-size as a percentage (100% ~= 16px, 87.5% ~= 14px etc. )
* declare all other font sizes in ems from there
** if using a pre-processor (I prefer LESS), just do the em calculation within your font-size declaration

	__Example__

		`h1 {font-size: 20em / 16em } /* where 16px is your base body font-size */ `

## Responsive Web Desgin

Most of the sites I build lately are responsive, so as much as possible I try to keep things flexible. This includes:

* font sizes in ems
* element sizing with percentage widths/margins/padding
* avoid setting vertical height explicitly (allow the elements to size themselves)
* I've been loving [Foundation](http://foundation.zurb.com/)'s responsive fluid grid lately -- it's lightweight, easy to customize, and had many responsively-minded layout options that go beyond standard responsive grids