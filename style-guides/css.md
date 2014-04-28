#CSS Style Guide

This document defines formatting and style rules CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.


###Table of Contents

* [BEM Syntax](#bem-syntax)
* [The Principles Of OOCSS](#the-principles-of-oocss)
* [Style Rules](#style-rules)
* [CSS Formatting Rules](#css-formatting-rules)
* [SASS Guide](#sass-guide)
* [Parting Words](#parting-words)

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

##The Principles Of OOCSS

As with any object-based coding method, the purpose of OOCSS is to encourage code reuse and, ultimately, faster and more efficient stylesheets that are easier to add to and maintain.

As described on the OOCSS GitHub repo’s Wiki page, OOCSS is based on two main principles.

###Seperate Structure from Skin

Almost every element on a styled Web page has different visual features (i.e. “skins”) that are repeated in different contexts. Think of a website’s branding — the colors, subtle uses of gradients, or visible borders. On the other hand, other generally invisible features (i.e. “structure”) are likewise repeated.

When these different features are abstracted into class-based modules, they become reusable and can be applied to any element and have the same basic result. Let’s compare some before and after code so you can see what I’m talking about.

Before applying OOCSS principles, you might have CSS that looks like this:

```css
#button {
	width: 200px;
	height: 50px;
	padding: 10px;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222);
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}

#box {
	width: 400px;
	overflow: hidden;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222);
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}

#widget {
	width: 500px;
	min-height: 200px;
	overflow: auto;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222);
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}
```

The three elements above have styles that are unique to each, and they’re applied with the non-reusable ID selector to define the styles. But they also have a number of styles in common. The common styles might exist for branding purposes or consistency of design.

With a little bit of planning and forethought, we can abstract the common styles so the CSS would end up instead like this:

```css
.button {
	width: 200px;
	height: 50px;
}

.box {
	width: 400px;
	overflow: hidden;
}

.widget {
	width: 500px;
	min-height: 200px;
	overflow: auto;
}

.skin {
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222);
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}
```

Now all the elements are using classes, the common styles are combined into a reusable “skin” and nothing is unnecessarily repeated. We just need to apply the “skin” class to all the elements and the result will be the same as what the first example would produce, except with less code and a possiblity for further reuse.

###Seperate Containers from Content

The second principle described on the OOCSS GitHub wiki page is the separation of containers from their content. To illustrate why this is important, take the following CSS:

```css
#sidebar h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: .8em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}
```

These styles will apply to any third-level headings that are children of the `#sidebar` element. But what if we want to apply the exact same styles to third-level headings that appear in the footer, with the exception of a different font size and a modified text shadow?

Then we would need to do something like this:

```css
#sidebar h3, #footer h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 2em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}

#footer h3 {
	font-size: 1.5em;
	text-shadow: rgba(0, 0, 0, .3) 2px 2px 4px;
}
```
Or we might end up with something worse:

```css
#sidebar h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 2em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}

/* other styles here.... */

#footer h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 1.5em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 2px 2px 4px;
}
```
Now we’re unnecessarily duplicating styles, and might not realize it (or simply don’t care). With OOCSS, we’re encouraged to give more forethought to what is common among different elements, then separate those common features into modules, or objects, that can be reused anywhere.

The styles that are declared using the descendant selector in those above examples are not reusable, because they are dependent on a particular container (in this case either the sidebar or the footer).

When we use OOCSS’s class-based module building, we ensure that our styles are not dependent on any containing element. This means they can then be reused anywhere in the document, regardless of structural context.

###The Media Object

One of the pioneers of the OOCSS movement is Nicole Sullivan. She’s created a reusable module called the media object which, as she explains, can save hundreds of lines of code.

The media object is a great example of the power of OOCSS because it can contain a media element of any size with content to its right. Although many of the styles that apply to the content inside of it — and even the size of the media element itself — could change, the media object itself has common base styles that help avoid needless repetition.

####Implementation Details

How does it work? The hard part is making sure that the image can be any width, so that the element is reusable. It means our content area needs to be flexible so that it can fill in all the remaining space available. We’ll have to create a new formatting context to make a flexible column.

The HTML:

```html
<div class="media attribution">

  <a href="http://twitter.com/stubbornella" class="img">
    <img src="http://stubbornella.com/profile_image.jpg" alt="me" />
  </a>

  <div class="bd">
    @Stubbornella 14 minutes ago
  </div>

</div>
```

The CSS:

```css
/* ====== media ====== */
.media {margin:10px;}
.media, .bd {overflow:hidden; _overflow:visible; zoom:1;}
.media .img {float:left; margin-right: 10px;}
.media .img img{display:block;}
.media .imgExt{float:right; margin-left: 10px;}
```

We clearfix both the wrapper element, media, and the inner content wrapper, bd (body) using the secret benefits of overflow. There are other ways we could have implemented the clearfix plus new formatting context. More on that in a later post.

Then we float our image wrapper (generally a link) left and our optional right region to the right.

Finally, we set some margins and paddings to keep everything lining up nicely. You might choose to set margins via a class which extends the .img object if you have several different kinds of images with different spacing and decoration.

Voila, we’re done. It is a very simple object, but it is very powerful. We can eliminate a lot of lines of code abstracting this repeating pattern. The code for the media block and many other “web Lego” are available on the Object Oriented CSS open source project.

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

##SASS Guide

###SASS order

####List @extend(s) First

```scss
.weather {
  @extend %module; 
  ...
}
```

Knowing right off the bat that this class inherits another whole set of rules from elsewhere is good.

####List "Regular" Styles Next

```scss
.weather {
  @extend %module; 
  background: LightCyan;
  ..
}
```

####List @include(s) Next

```scss
.weather {
  @extend %module; 
  background: LightCyan;
  @include transition(all 0.3s ease-out);
  ...
}
```

This visually separates the @extend and @include as well as groups the @include for easier reading. You might also want to make the call on separating user-authored @include and vendor-provided @include.

####Nested Selectors Last

```scss
.weather {
	@extend %module; 
	background: LightCyan;
	@include transition(all 0.3s ease);
	> h3 {
		border-bottom: 1px solid white;
		@include transform(rotate(90deg));
	}
}
```

Nothing goes after the nested stuff. And the same order as above within the nested selector would apply.

###Nested Selectors

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

```scss
.header {
    .site-nav {
        li {
            a {}
        }
    }
}
```

If you were to Sass this up you’d write it as:

```scss
.header {}
.site-nav {
    li {}
    a {}
}
```

###Use semantic variable names

Imagine for a moment that you client's primary brand color is red and you called that variable $red. Six months go by and the marketing department decides to re-brand the company and the primary brand color is now blue.

Changing the value of $red is easy enough, but the variable has no description of its intended purpose.

Instead of describing what a variable looks like in the name, describe its function or purpose. In other words, try to choose semantic names for your variables.

```scss
// Bad
$red: red;
$yellow: yellow;

// Better
$brand-color: red;
$accent-color: yellow;
```

###Variablize All Common Numbers, and Numbers with Meaning

If you find yourself using a number other than 0 or 100% over and over, it likely deserves a variable. Since it likely has meaning and controls consistency, being able to tweak it enmasse may be useful.

If a number clearly has strong meaning, that's a use case for variablizing as well.

```scss
$zHeader: 2000;
$zOverlay: 5000;
$zMessage: 5050;

.header {
  z-index: $zHeader;
}
.overlay {
  z-index: $zOverlay;
}
.message {
  z-index: $zMessage;
}
```

Those numbers are probably in a separate file @import-ed as a dependency. That way you can keep track of your whole z-index stack in one place.

###Variablize All Colors

Except perhaps white and black. Chances are a color isn't one-off, and even if you think it is, once it's in a variable you might see uses for it elsewhere. Variations on that color can often be handled by the Sass color functions like lighten() and darken() - which make updating colors easier (change in one place, whole color scheme updates).

###Nest and Name Your Media Queries

The ability to nest media queries in Sass means 1) you don't have to re-write the selector somewhere else which can be error prone 2) the rules that you are overriding are very clear and obvious, which is usually not the case when they are at the bottom of your CSS or in a different file.

```scss
.sidebar {
  float: right;
  width: 33.33%;
  @include bp(mama-bear) {
    width: 25%;
  }
}
```

More on this and the importance of naming them well.

###Shame Last

In your global stylesheet, @import a _shame.scss file last.

```scss
@import "compass"

...

@import "shame"
```

If you need to make a quick fix, you can do it here. Later when you have proper time, you can move the fix into the proper structure/organization. See more.

####Partials are named _partial.scss
This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependancies that would make it impossible to compile by itself. Personally I like dashes in the "actual" filename though, like _dropdown-menu.scss.

##Parting Words

Be consistent.

If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. We present global style rules here so people know the vocabulary, but local style is also important. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.







