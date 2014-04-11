#CSS Style Guide

###Table of Contents

* [BEM Syntax](#bem-syntax)

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

