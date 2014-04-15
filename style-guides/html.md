#HTML Style Guide

##General Formatting

Use a new line for every block, list, or table element, and indent every such child element.
Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.

Also, indent them if they are child elements of a block, list, or table element.

(If you run into issues around whitespace between list items it’s acceptable to put all li elements in one line. A linter is encouraged to throw a warning instead of an error.)

```html
<blockquote>
	<p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
	<li>Moe
	<li>Larry
	<li>Curly
</ul>

<table>
	<thead>
		<tr>
			<th scope="col">Income</th>
			<th scope="col">Taxes</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>$ 5.00</td>
			<td>$ 4.50</td>
		</tr>	
	</tbody>
</table>
```

###Whitespace

This one is hard to quantify, but it's preferable to use whitespace to loosely reflect the separation of elements that you might see once rendered. Group and space elements with whitespace as you would expect them to be grouped visually in the rendered page, for example:

```html
<dl>

    <dt>Lorem</dt>
    <dd>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</dt>

    <dt>Ipsum</dt>
    <dd>Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante.</dt>

    <dt>Dolor</dt>
    <dd>Morbi in sem quis dui placerat ornare. Pellentesque odio nisi euismod in pharetra.</dt>

</dl>

<div class=promo>

    <p><strong>Pellentesque habitant morbi tristique</strong> senectus et netus et malesuada fames ac turpis egestas.</p>    
    <a href=# class=btn>Lorem</a>

</div>
```

A mixture of no, single and double lines of whitespace help to separate elements, or show their visual relationship to one another. For example, the <dt>s and <dd>s belong with each other, but are separate from other groupings.


###HTML Quotation Marks

When quoting attributes values, use double quotation marks.
Use double ("") rather than single quotation marks ('') around attribute values.

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>

<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```


