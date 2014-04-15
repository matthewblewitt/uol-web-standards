#Style Guide

Every major open-source project has its own style guide: a set of conventions (sometimes arbitrary) about how to write code for that project. It is much easier to understand a large codebase when all the code in it is in a consistent style.

“Style” covers a lot of ground, from “use camelCase for variable names” to “never use global variables” to “never use exceptions.” These documents hold the style guidelines we use.

### Navigation

* [CSS](css.md)
* [HTML](html.md)
* [Javascript](javascript.md)
* [jQuery](jquery.md)

##General Style Rules

###Protocol

Omit the protocol from embedded resources.
Omit the protocol portion `(http:, https:)` from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.

Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

```html
<!-- Not recommended -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```
```css
/* Not recommended */
.example {
  background: url(http://www.google.com/images/example);
}
/* Recommended */
.example {
  background: url(//www.google.com/images/example);
}
```

###General Formatting Rules

####Indentation

Indent by 4 spaces at a time. Don’t use tabs or mix tabs and spaces for indentation.

```html
<ul>
	<li>Fantastic
	<li>Great
</ul>
```
```css
.example {
 	color: blue;
}
```

####Capitalization

Use only lowercase. All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless `text/CDATA`), CSS selectors, properties, and property values (with the exception of strings).

```html
<!-- Not recommended -->
<A HREF="/">Home</A>
<!-- Recommended -->
<img src="google.png" alt="Google">
```
```css
/* Not recommended */
color: #E5E5E5;
/* Recommended */
color: #e5e5e5;
```

###General Meta Rules

####Encoding

Use UTF-8 (no BOM).Make sure your editor uses UTF-8 as character encoding, without a byte order mark.

Specify the encoding in HTML templates and documents via `<meta charset="utf-8">`. Do not specify the encoding of style sheets as these assume UTF-8.

(More on encodings and when and how to specify them can be found in Handling character encodings in HTML and CSS.)

####Comments

Explain code as needed, where possible.
Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred?

(This item is optional as it is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML and CSS code and depends on the project’s complexity.)

####Action Items

Mark todos and action items with `TODO`. Highlight todos by using the keyword TODO only, not other common formats like `@@`.

Append a contact (username or mailing list) in parentheses as with the format `TODO(contact)`.

Append action items after a colon as in `TODO: action item`.

```html
{# TODO(john.doe): revisit centering #}
<center>Test</center>
<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```

