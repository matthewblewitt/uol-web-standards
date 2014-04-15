#CSS Style Guide

This document defines formatting and style rules CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.


###Table of Contents

* [BEM Syntax](#bem-syntax)
* [Style Rules](#style-rules)
	* [Style Rules](#style-rules)
* [CSS Formatting Rules](#css-formatting-rules)
* [CSS Meta Rules](#css-meta-rules)

##BEM Syntax

BEM stands for block, element, modifier. It's a smart way of naming your CSS classes to give them more transparency and meaning to other developers. They are far more strict and informative, which makes the BEM naming convention ideal for teams of developers on larger projects that might last a while. It is important to note that the naming scheme is based on BEM, but honed by Nicolas Gallagher.

The naming convention follows this pattern:

```css
.block {}
.block__element {}
.block--modifier {}
```

* `.block` represents the higher level of an abstraction or component.
* `.block__element` represents a descendent of .block that helps form `.block` as a whole.
* `.block--modifier` represents a different state or version of `.block`.

The point of BEM is to tell other developers more about what a piece of markup is doing from its name alone. By reading some HTML with some classes in, you can see how – if at all – the chunks are related; something might just be a component, something might be a child, or element, of that component, and something might be a variation or modifier of that component. To use an analogy/model, think how the following things and elements are related:

```css
.person {}
.person__hand {}
.person--female {}
.person--female__hand {}
.person__hand--left {}
```

Here's an example of how a form might look:

```html
<form class="site-search  site-search--full">
    <input type="text" class="site-search__field">
    <input type="Submit" value ="Search" class="site-search__button">
</form>
```

We can see that we have a block called .site-search which has an element which lives inside it called .site-search__field. We can also see that there is a variation of the .site-search called .site-search--full.

####When not to use BEM

When you are using BEM, though, it is important to remember that you don’t need to use it for everything. Take for example:

```css
.caps { text-transform: uppercase; }
```

Here we have our logo; it could be BEMmed up like so:

```css
.header {}
.header__logo {}
```

But that is unecessary. The trick with BEM is knowing when something falls into a relevant category. Just because something happens to live inside a block it doesn’t always mean is is actually a BEM element. In the case of our site logo it lives in the .header purely coincidentally; it could just as easily be in our sidebar or footer. An element’s scope can start in any context, so you need to make sure you only apply BEM as far as you need to.

#####External Resources

* [MindBEMding – getting your head ’round BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)

***

##Style Rules

###Specificity - Should we use ID's to style elements?

It's generally best to style with classes. This is what OOCSS and SMACSS and modern writing about CSS is teaching. Not just "use classes smartly" but also "don't use ID's". 

ID's are 255 times more specific than classes. The difference is so big it can get out of control quickly in CSS. If you agree with yourself and team to never use them, you don't get in these arms races. These override predicaments can always be solved another way - through code refactoring and nesting a class.

###When to use ID's

ID's can be used as fragment identifiers for marking landmarks in the page (e.g. jump to content links in pages) and in Javascript.

###ID and Class Naming

Use meaningful or generic ID and class names.
Instead of cryptic names, always use ID and class names that reflect the purpose of the element in question, or that are otherwise generic.

Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change.

Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers.”

Using functional or generic names reduces the probability of unnecessary document or template changes.

```css
/* Not recommended: meaningless */
#yee-1901 {}

/* Recommended: specific */
#gallery {}
.login {}
.video {}

/* Recommended: generic */
.aux {}
.alt {}
```

Use ID and class names that are as short as possible but as long as necessary.
Try to convey what an ID or class is about while being as brief as possible.

Using ID and class names this way contributes to acceptable levels of understandability and code efficiency.

```css
/* Not recommended */
.navigation {}
.atr {}

/* Recommended */
.nav {}
.author {}
```

###Type Selectors

Avoid qualifying ID and class names with type selectors.
Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes.

Avoiding unnecessary ancestor selectors is useful for performance reasons.

```css
/* Not recommended */
ul.example {}
div.error {}

/* Recommended */
.example {}
.error {}
```

###Shorthand Properties

Use shorthand properties where possible.
CSS offers a variety of shorthand properties (like font) that should be used whenever possible, even in cases where only one value is explicitly set.

Using shorthand properties is useful for code efficiency and understandability.

```css
.class {
	/* Not recommended */
	border-top-style: none;
	font-family: palatino, georgia, serif;
	font-size: 100%;
	line-height: 1.6;
	padding-bottom: 2em;
	padding-left: 1em;
	padding-right: 1em;
	padding-top: 0;

	/* Recommended */
	border-top: 0;
	font: 100%/1.6 palatino, georgia, serif;
	padding: 0 1em 2em;
}
```

###0 and Units

Omit unit specification after “0” values.
Do not use units after 0 values unless they are required.

```css
.class {
	margin: 0;
	padding: 0;
}
```

###Leading 0s

Omit leading “0”s in values.
Do not use put 0s in front of values or lengths between -1 and 1.

```css
.class {
	font-size: .8em;
}
```

###Hexadecimal Notation

Use 3 character hexadecimal notation where possible.
For color values that permit it, 3 character hexadecimal notation is shorter and more succinct.

```css
.class {
	/* Not recommended */
	color: #eebbcc;
	/* Recommended */
	color: #ebc;
}
```
###ID and Class Name Delimiters

Separate words in classes names by a hyphen. Separate words in ID's names by a underscore.
Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.

```css
/* Not recommended: does not separate the words “demo” and “image” */
.demoimage {}

/* Not recommended: uses underscore instead of hyphen */
.error_status {}

/* Recommended */
#video_id {}
.ads-sample {}
```

### A note on !important

It is okay to use !important on helper classes only. To add !important preemptively is fine, e.g. .error { color: red !important }, as you know you will always want this rule to take precedence.

Using !important reactively, e.g. to get yourself out of nasty specificity situations, is not advised. Rework your CSS and try to combat these issues by refactoring your selectors. Keeping your selectors short and avoiding IDs will help out here massively.

###Comments

####Table of contents

At the top of CSS files create a table of contents that maps to the section titles in the document, here's an example:

```css
/*------------------------------------*\
    $CONTENTS
\*------------------------------------*/
/**
 * CONTENTS............You’re reading it!
 * RESET...............Set our reset defaults
 * FONT-FACE...........Import brand font files
 */
```

This will tell the next developer(s) exactly what they can expect to find in this file. Each item in the table of contents maps directly to a section title.

If you are working in one big stylesheet, the corresponding section will also be in that file. If you are working across multiple files then each item in the table of contents will map to an include which pulls that section in.

####Section titles

Denote each section (layout, type, tables etc) of CSS thus:

```css
/*------------------------------------*\
    $MAIN
\*------------------------------------*/
```

This section heading is prepended with a `$`. This is so that--when you search for a section--you actually searchd for $MAIN and not MAIN. This means that you are only ever searching within section headings. A search for $MAIN will only ever find a section with that name whereas a search for MAIN could find something like:

```css
.s{
    background-image:url(/img/css/sprites/main.png);
}
```

Being able to search just in the scope of headings is very, very useful.

I also leave five carriage returns between each section, for example:

```css
/*------------------------------------*\
    $RESET
\*------------------------------------*/
[Our
reset
styles]





/*------------------------------------*\
    $FONT-FACE
\*------------------------------------*/
```

This means that when scrolling quickly through a stylesheet you know that any gaps in the code are likely to be new sections.

###Classes in Javascript - JS hooks

Never use a CSS styling class as a JavaScript hook. Attaching JS behaviour to a styling class means that we can never have one without the other.

If you need to bind to some markup use a JS specific CSS class. This is simply a class namespaced with .js-, e.g. .js-toggle, .js-drag-and-drop. This means that we can attach both JS and CSS to classes in our markup but there will never be any troublesome overlap.

```html
<th class="is-sortable  js-is-sortable">
</th>
```

The above markup holds two classes; one to which you can attach some styling for sortable table columns and another which allows you to add the sorting functionality.

###Hacks

Avoid user agent detection as well as CSS “hacks”—try a different approach first.
It’s tempting to address styling differences over user agent detection or special CSS filters, workarounds, and hacks. Both approaches should be considered last resort in order to achieve and maintain an efficient and manageable code base. Put another way, giving detection and hacks a free pass will hurt projects in the long run as projects tend to take the way of least resistance. That is, allowing and making it easy to use detection and hacks means using detection and hacks more frequently—and more frequently is too frequently.

##CSS Formatting Rules

###Declaration Order

Alphabetize declarations.
Put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain.

```css
.class {
	background: fuchsia;
	border: 1px solid;
	-webkit-border-radius: 4px;
	   -moz-border-radius: 4px;
	        border-radius: 4px;
	color: black;
	text-align: center;
	text-indent: 2em;
}
```

###Vendor prefixes

Write vendor prefixes so that the values all line up vertically; this makes them quicker to scan and compare values.

```css
.island{ 
    padding:1.5em;
    margin-bottom:1.5em;
    -webkit-border-radius:4px;
       -moz-border-radius:4px;
            border-radius:4px;
}
```

###Block Content Indentation

Indent all block content.
Indent all block content, that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

```css
@media screen, projection {
	html {
		background: #fff;
		color: #444;
	}
}
```

###Declaration Stops

Use a semicolon after every declaration.
End every declaration with a semicolon for consistency and extensibility reasons.

```css
/* Not recommended */
.test {
	display: block;
	height: 100px
}
/* Recommended */
.test {
	display: block;
 	height: 100px;
}
```

###Property Name Stops

Use a space after a property name’s colon.
Always use a single space between property and value (but no space between property and colon) for consistency reasons.

```css
/* Not recommended */
h3 {
	font-weight:bold;
}
/* Recommended */
h3 {
 	font-weight: bold;
}
```

###Declaration Block Separation

Use a space between the last selector and the declaration block.
Always use a single space between the last selector and the opening brace that begins the declaration block.

The opening brace should be on the same line as the last selector in a given rule.

```css
/* Not recommended: missing space */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}
/* Recommended */
#video {
  margin-top: 1em;
}
```

###Selector and Declaration Separation

Separate selectors and declarations by new lines.
Always start a new line for each selector and declaration.

```css
/* Not recommended */
a:focus, a:active {
	position: relative; top: 1px;
}
/* Recommended */
h1,
h2,
h3 {
	font-weight: normal;
	line-height: 1.2;
}
```

###Rule Separation

Separate rules by new lines.
Always put a blank line (two line breaks) between rules.

```css
html {
	background: #fff;
}

body {
	margin: auto;
	width: 50%;
}
```

###CSS Quotation Marks

Use single quotation marks for attribute selectors and property values.
Use single ('') rather than double ("") quotation marks for attribute selectors or property values. Do not use quotation marks in URI values (url()).

Exception: If you do need to use the @charset rule, use double quotation marks—single quotation marks are not permitted.

```css
/* Not recommended */
@import url("//www.google.com/css/maia.css");

html {
	font-family: "open sans", arial, sans-serif;
}
/* Recommended */
@import url(//www.google.com/css/maia.css);

html {
	font-family: 'open sans', arial, sans-serif;
}
```

###SASS Nested Selectors

To prevent uncessary complied css output from sass indentation we follow the following rule:

The Inception Rule: don’t go more than four levels deep.

This basically means that you shouldn't be too specific or mimicking the DOM at any point. If you find yourself more than four levels deep, that's a red flag. Of course there are times when you'll be forced to go there, but it's not something you should be doing too much.

```css
.header {}
.header .site-nav {}
.header .site-nav li {}
.header .site-nav li a {}
```
Would be wholly unnecessary in normal CSS, so the following would be bad Sass:

```css
.header {
    .site-nav {
        li {
            a {}
        }
    }
}
```

If you were to Sass this up you’d write it as:

```css
.header {}
.site-nav {
    li {}
    a {}
}
```

##CSS Meta Rules

###Section Comments

Group sections by a section comment (optional).
If possible, group style sheet sections together by using comments. Separate sections with new lines.


```css
/* Header */

#adw-header {}

/* Footer */

#adw-footer {}

/* Gallery */

.adw-gallery {}
```

###Parting Words

Be consistent.

If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. We present global style rules here so people know the vocabulary, but local style is also important. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.







