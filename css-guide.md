# CSS GUIDE

## General Formatting

* use all lowercase and dashes for class names (eg. my-class, not my_class or myClass)
* multi-line css (I tend to make an exception to this if there's only a single rule within the selector.)
* for rules with multiple selectors, each selector gets it's own line
* if you're not using a pre-processor, use indent blocks to reflect HTML heirarchy
	__Example__

		
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

* group and order your declarations by purpose: layout, then base visual styles, then typography 

	__Example__ (line breaks added for clarity of the example only)
		
		.widget {	
			position: absolute; /*start layout styles*/
			display: block;
			top: 0;
			left: 0;
			width: 100%;
			margin: 0 1em;
			padding: 20px; /*end layout styles*/

			background-color: #000; /*start base visual styles */
			border-radius: 50%; 
			box-shadow: 1px 2px 0 0 rgba(0,0,0,0.4); /*end base visual styles */
			
			color: #fff; /*start typography */
			font-size: 1.2em;
			font-style: italic; /*end typography */
		}

* use a table of contents at the top of your file
* use a prefix (like `::` or `$`) ahead of section labels so you can easily find the section from your text editor
	
	__Example__
	
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

* _Alternately,_ if you're using Sass, and especially for large sites, breaking your file into smaller partials for each TOC section is an even better way to organize your CSS

	__Example__
	
		scss
		|-- components
		|   `-- _buttons.scss
		|   `-- _forms.scss
		|-- regions.scss
		|   `-- _header.scss
		|   `-- _footer.scss
		|   `-- _contact-page.scss
		`-- _typography.scss
		`-- _grid.scss
		`-- style.scss
	

## HTML decoupling and naming conventions

* Try to avoid IDs. I'm not wholly against them, but you'll avoid a lot of nasty specificity wars by sticking mostly to classes, especially on container elements.
* Use common prefixes for related elements. (eg. news-photo and news-pullquote)
* Try to make general, reusable classes and styles where appropriate (eg. a single `button` class that can accomodate a button with text of any with)

## Typography

* Set body font-size as a percentage (100% ~= 16px, 87.5% ~= 14px etc. )
* Declare all other font sizes in ems from there. If using a pre-processor (I prefer Sass), you can make the em calculation within your font-size declaration

	__Example__

		h1 {font-size: 20/16*1em } /* where 16px is your base body font-size */ 

## Responsive Web Desgin

Most of the sites I build lately are responsive, so as much as possible I try to keep things flexible. This includes:

* font sizes in ems
* element sizing with percentage widths/margins/padding
* use 'box-sizing: border-box' globally. It will save you a lot of headaches when using percentage widths.
* avoid setting vertical height explicitly (allow the elements to size themselves)
* try to generate visual design with CSS as much as possible instead of using an image. It's inherently flexible and is better for performance anyhow (eg. a CSS gradient bg on a button instead of cutting out a button bg image)
* I've been loving [Foundation](http://foundation.zurb.com/)'s responsive fluid grid lately -- it's lightweight, easy to customize, and had many responsively-minded layout options that go beyond standard responsive grids
