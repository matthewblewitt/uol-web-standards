# Accessibility

Objective: Comply with the [Disability Discrimination Act (DDA)](http://www
.shaw-trust.org.uk/about-us/facts-about-disability/disability-discrimination-
act-your-obligations-as-an-employer/) and promote a culture of accessibility
and inclusion.

The W3C offers three different levels of compliance.

  1. **Priority 1 guidelines**, (which must be satisfied according to the W3C) will almost certainly have to be adhered to. 

  2. **Priority 2 guidelines** (which should be satisfied and are the EU recommended level of compliance), or some part of, will probably need to be adhered to too (http://www.webcredible.co.uk/user-friendly-resources/web-accessibility/uk-website-legal-requirements.shtml). 

  3. **Priority 3 guidelines**, A Web content developer may address this checkpoint. Otherwise, one or more groups will find it somewhat difficult to access information in the document. Satisfying this checkpoint will improve access to Web documents.


## Priority 1 checkpoints

A Web content developer must satisfy this checkpoint. Otherwise, one or more
groups will find it impossible to access information in the document.
Satisfying this checkpoint is a basic requirement for some groups to be able
to use Web documents.

  1. Provide a meaningful (`<img src="cows.jpg" alt="Cows grazing in a field on a sunny day.">`) text equivalent for every non-text element (e.g., via "alt", "longdesc", or in element content). 

Includes:images, graphical representations of text (including symbols), image
map regions, animations (e.g., animated GIFs), applets and programmatic
objects, ascii art, frames, scripts, images used as list bullets, spacers,
graphical buttons, sounds (played with or without user interaction), stand-
alone audio files, audio tracks of video, and video.

[WC3 1.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-text-equivalent)

  2. Ensure that all information conveyed with color is also available without color, for example from context or markup. 

[WC3 2.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-convey)

  3. Clearly identify changes in the natural language of a document's text and any text equivalents (e.g., captions) 

[WC3 4.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-changes)

  4. Organize documents so they may be read without style sheets. For example, when an HTML document is rendered without associated style sheets, it must still be possible to read the document. 

[WC3 6.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-order-style-
sheets)

  5. Ensure that equivalents for dynamic content are updated when the dynamic content changes.

[WC3 6.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-dynamic-source)

  6. Until user agents allow users to control flickering, avoid causing the screen to flicker 

[WC3 7.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-flicker)

  7. Use the clearest and simplest language appropriate for a site's content. 

[WC3 14.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-simple-and-
straightforward)

  8. IMAGES: Provide redundant text links for each active region of a server-side image map. 

[WC3 1.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-redundant-server-
links)

  9. Provide client-side image maps instead of server-side image maps except where the regions cannot be defined with an available geometric shape 

[WC3 9.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-client-side-maps)

  10. TABLES: For data tables, identify row and column headers. 

[WC3 5.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-headers)

  11. For data tables that have two or more logical levels of row or column headers, use markup to associate data cells and header cells. 

[WC3 5.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-structure)

  12. FRAMES: Title each frame to facilitate frame identification and navigation. 

[WC3 12.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-titles)

  13. APPLETS/SCRIPTS: Ensure that pages are usable when scripts, applets, or other programmatic objects are turned off or not supported. If this is not possible, provide equivalent information on an alternative accessible page. 

[WC3 6.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-scripts)

  14. MULTIMEDIA: Until user agents can automatically read aloud the text equivalent of a visual track, provide an auditory description of the important information of the visual track of a multimedia presentation. 

[WC3 1.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-auditory-
descriptions)

  15. For any time-based multimedia presentation (e.g., a movie or animation), synchronize equivalent alternatives (e.g., captions or auditory descriptions of the visual track) with the presentation. 

[WC3 1.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-synchronize-
equivalents)

  16. If, after best efforts, you cannot create an accessible page, provide a link to an alternative page that uses W3C technologies, is accessible, has equivalent information (or functionality), and is updated as often as the inaccessible (original) page. 

[WC3 11.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-alt-pages)

## Priority 2 checkpoints

A Web content developer should satisfy this checkpoint. Otherwise, one or more
groups will find it difficult to access information in the document.
Satisfying this checkpoint will remove significant barriers to accessing Web
documents

  1. Ensure that foreground and background color combinations provide sufficient contrast when viewed by someone having color deficits or when viewed on a black and white screen 

[WC3 2.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-contrast)

  2. When an appropriate markup language exists, use markup rather than images to convey information. http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use- 

[WC3 3.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-markup)

  3. Create documents that validate to published formal grammars. For example, include a document type declaration at the beginning of a document that refers to a published DTD (e.g., the strict HTML 4.0 DTD). 

[WC3 3.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-grammar)

  4. Use style sheets to control layout and presentation. 

[WC3 3.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-style-sheets)

  5. Use relative rather than absolute units in markup language attribute values and style sheet property values. 

[WC3 3.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-relative-units)

  6. Use header elements to convey document structure and use them according to specification. 

[WC3 3.5](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-logical-headings)

  7. Mark up lists and list items properly. 

[WC3 3.6](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-list-structure)

  8. Mark up quotations. Do not use quotation markup for formatting effects such as indentation. 

[WC3 3.7](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-quotes)

  9. Ensure that dynamic content is accessible or provide an alternative presentation or page. 

[WC3 6.5](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-fallback-page)

  10. Until user agents allow users to control blinking, avoid causing content to blink (i.e., change presentation at a regular rate, such as turning on and off). 

[WC3 7.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-blinking)

  11. Until user agents provide the ability to stop the refresh, do not create periodically auto-refreshing pages. 

[WC3 7.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-periodic-
refresh)

  12. Until user agents provide the ability to stop auto-redirect, do not use markup to redirect pages automatically. Instead, configure the server to perform redirects. 

[WC3 7.5](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-auto-forward)

  13. Until user agents allow users to turn off spawned windows, do not cause pop-ups or other windows to appear and do not change the current window without informing the user. 

[WC3 10.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-pop-ups)

  14. Use W3C technologies when they are available and appropriate for a task and use the latest versions when supported 

[WC3 11.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-latest-w3c-
specs)

  15. Avoid deprecated features of W3C technologies 

[WC3 11.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-
deprecated)

  16. Divide large blocks of information into more manageable groups where natural and appropriate 

[WC3 12.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-group-
information)

  17. Clearly identify the target of each link 

[WC3 13.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-meaningful-
links)

  18. Provide metadata to add semantic information to pages and sites. 

[WC3 13.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-metadata)

  19. Provide information about the general layout of a site (e.g., a site map or table of contents). 

[WC3 13.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-site-
description)

  20. Use navigation mechanisms in a consistent manner. 

[WC3 13.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-clear-nav-
mechanism)

  21. TABLES: Do not use tables for layout unless the table makes sense when linearized. Otherwise, if the table does not make sense, provide an alternative equivalent (which may be a linearized version). 

[WC3 5.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-table-for-
layout)

  22. If a table is used for layout, do not use any structural markup for the purpose of visual formatting 

[WC3 5.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-layout)

  23. FRAMES: Describe the purpose of frames and how frames relate to each other if it is not obvious by frame titles alone. 

[WC3 12.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-longdesc)

  24. FORMS: Until user agents support explicit associations between labels and form controls, for all form controls with implicitly associated labels, ensure that the label is properly positioned. 

[WC3 10.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-unassociated-
labels)

  25. Associate labels explicitly with their controls. 

[WC3 12.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-associate-
labels)

  26. APPLETS/SCRIPTS: For scripts and applets, ensure that event handlers are input device-independent 

[WC3 6.4](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-
operable-scripts)

  27. Until user agents allow users to freeze moving content, avoid movement in pages. 

[WC3 7.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-movement)

  28. Make programmatic elements such as scripts and applets directly accessible or compatible with assistive technologies (Priority 1 if functionality is important and not presented elsewhere, otherwise Priority 2). 

[WC3 8.1](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-directly-
accessible)

  29. Ensure that any element that has its own interface can be operated in a device-independent manner 

[WC3 9.2](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-
operable)

  30. For scripts, specify logical event handlers rather than device-dependent event handlers.

[WC3 9.3](http://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-device-
independent-events)

# Semantic Markup and WAI-ARIA

Where possible use semantic HTML elements such as <header>, <footer>, and
<article> to help computers identify key areas of the content on the page.

If use of the new semantic elements is not possible, greater meaning can be
given to elements through WAI-ARIA (Accessible Rich Web Applications). It
essentially defines a number of _roles_ that a page element can have such as
<div role="article">...</div>. More information can be found in the article
[Introduction to WAI-ARIA](http://dev.opera.com/articles/view/introduction-to-
wai-aria/)

# Using the tabindex attribute

The tabindex attribute gives you a way of specifying the order in which inputs
should be focused when the tab key is being used to navigate through a web
form.

```html
<label for="name">Name:
<input type="text" name="name" id="name" tabindex="1">
   
<label for="email">Email:
<input type="email" name="email" id="email" tabindex="3">

<label for="phone">Phone:
<input type="tel" name="phone" id="phone" tabindex="2">
``` 

In the example above the focus order will move from the name input to the
phone input and then finally to the email input.

# Accessible Links

There are two accessibility considerations to make when creating links. The
first is to think about the anchor text that will become the clickable link.
This text should make sense if it was taken out of the context of the page.
'Click here' is a really bad example of anchor text.

The second consideration is the use of a title attribute. This can be used to
add a description of the page that you are linking to. This description will
then be displayed in a tool-tip when the user hovers their mouse over the link
and may also be read aloud by a screen reader.

```html    
<a href="http://website.com" title="Learn how to build websites at website.com">Learn how to build websites</a>
```  

# Tables

## Captions

The `<caption>` element can be used to add a description of the data in the
table. This should be placed directly after the opening tag of the <table>
element. Screen readers will read the caption aloud before continuing on to
the data. This helps to give the user more context around the data in the
table.

    
    
    <table>
      <caption>
        Table 1.1 shows the exam scores of 120 pupils in the Physics exam.
      </caption>
      ...
    </table>
    

Captions will be displayed on the page so you think about how to style them
using CSS.
