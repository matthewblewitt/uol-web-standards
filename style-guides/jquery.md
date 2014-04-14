# jQuery Best Practices

## Loading jQuery

  * Always try to use a CDN to include jQuery on the page. [Benefits of using a CDN](http://www.sitepoint.com/7-reasons-to-use-a-cdn/)
  * If possible, keep all your JavaScript and jQuery includes at the bottom of your page 
  * DO NOT use jQuery version 2.x if you support Internet Explorer 6/7/8. 
  * If you are using other libraries like Prototype, MooTools, Zepto etc. that uses $ sign as well, try not to use $ for calling jQuery functions and instead use jQuery simply. You can return control of $ back to the other library with a call to $.noConflict().

## Variables

  * All variables that are used to store/cache jQuery objects should have a name prefixed with a $. 
  * Always cache your jQuery selector returned objects in variables for reuse
    
    
    ```html
    var $myDiv = $("#myDiv");
    $myDiv.click(function(){...});
    ```

  * Use camel case for naming variables.

## Selectors

  * Use ID selector whenever possible. It is faster because they are handled using document.getElementById().
  * When using class selectors, don't use the element type in your selector. [Performance Comparison](http://jsperf.com/jqeury-selector-test)
    
    ```html
    var $products = $("div.products"); // SLOW
    var $products = $(".products"); // FAST
    ```

  * Use find for Id->Child nested selectors. The .find() approach is faster because the first selection is handled without going through the Sizzle selector engine. More Info 
    
    ```html
    // BAD, a nested query for Sizzle selector engine
    var $productIds = $("#products div.id");
    // GOOD, #products is already selected by document.getElementById() so only div.id needs to go through Sizzle selector engine
    var $productIds = $("#products").find("div.id");
    ```

  * Be specific on the right-hand side of your selector, and less specific on the left [More info](http://learn.jquery.com/performance/optimize-selectors/)
    
    ```html
    // Unoptimized
    $("div.data .gonzalez");
    // Optimized
    $(".data td.gonzalez");
    ```

  * Avoid Excessive Specificity. [More Info](http://learn.jquery.com/performance/optimize-selectors/). 
    
    ```html
    $(".data table.attendees td.gonzalez");
     
    // Better: Drop the middle if possible.
    $(".data td.gonzalez");
    ```

  * Give your Selectors a Context. 
    
    ```html
    // SLOWER because it has to traverse the whole DOM for .class
    $('.class');
    // FASTER because now it only looks under class-container.
    $('.class', '#class-container');
    ```

  * Avoid Universal Selectors. [More Info](http://learn.jquery.com/performance/optimize-selectors/)
    
    ```html
    $('div.container > *'); // BAD
    $('div.container').children(); // BETTER
    ```

  * Avoid Implied Universal Selectors. When you leave off the selector, the universal selector (*) is still implied. [More info](http://learn.jquery.com/performance/optimize-selectors/)
    
    ```html
    $('div.someclass :radio'); // BAD
    $('div.someclass input:radio'); // GOOD
    ```

  * Don't Descend Multiple IDs or nest when selecting an ID. ID-only selections are handled using document.getElementById() so don't mix them with other selectors. 
    
    ```html
    $('#outer #inner'); // BAD
    $('div#inner'); // BAD
    $('.outer-container #inner'); // BAD
    $('#inner'); // GOOD, only calls document.getElementById()
    ```

## DOM Manipulation

  * Always detach any existing element before manipulation and attach it back after manipulating it. [More Info](http://learn.jquery.com/performance/detach-elements-before-work-with-them/)
    
    ```html
    var $myList = $("#list-container > ul").detach();
    //...a lot of complicated things on $myList
    $myList.appendTo("#list-container");
    ```

  * Use string concatenation or array.join() over .append(). [More Info](http://learn.jquery.com/performance/append-outside-loop/)
    
    ```html
    // BAD
    var $myList = $("#list");
    for(var i = 0; i < 10000; i++){
    		    $myList.append("
      * "+i+"
    ");
    }
     
    // GOOD
    var $myList = $("#list");
    var list = "";
    for(var i = 0; i < 10000; i++){
    		    list += "
      * "+i+"
    ";
    }
    $myList.html(list);
     
    // EVEN FASTER
    var array = []; 
    for(var i = 0; i < 10000; i++){
    		    array[i] = "
      * "+i+"
    "; 
    }
    $myList.html(array.join(''));
    ```

  * Don't Act on Absent Elements. [More Info](http://learn.jquery.com/performance/dont-act-on-absent-elements/)
    
    ```html
    // BAD: This runs three functions before it realizes there's nothing in the selection
    $("#nosuchthing").slideUp();
     
    // GOOD
    var $mySelection = $("#nosuchthing");
    if ($mySelection.length) {
        $mySelection.slideUp();
    }
    ```

## Events

  * Use only one Document Ready handler per page. It makes it easier to debug and keep track of the behavior flow. 
  * DO NOT use anonymous functions to attach events. Anonymous functions are difficult to debug, maintain, test, or reuse. 
    
    ```html
    $("#myLink").on("click", function(){...}); // BAD
     
    // GOOD
    function myLinkClickHandler(){...}
    $("#myLink").on("click", myLinkClickHandler);
    ```  

  * Document ready event handler should not be an anonymous function. Once again, anonymous functions are difficult to debug, maintain, test, or reuse. 
    
    ```html
    $(function(){ ... }); // BAD: You can never reuse or write a test for this function.
     
    // GOOD
    $(initPage); // or $(document).ready(initPage);
    function initPage(){
        // Page load event where you can initialize values and call other initializers.
    }
    ```

  * Document ready event handlers should be included from external files and inline JavaScript can be used to call the ready handle after any initial setup. 
    
    ```html
    <script src="my-document-ready.js"></script>
    <script>
    // Any global variable set-up that might be needed.
    $(document).ready(initPage); // or $(initPage);
    </script>
    ```

  * DO NOT use behavioral markup in HTML (JavaScript inlining), these are debugging nightmares. Always bind events with jQuery to be consistent so it's easier to attach and remove events dynamically. 
    
    ```html
    <a id="myLink" href="#" onclick="myEventHandler();">my link</a> 
    $("#myLink").on("click", myEventHandler); // GOOD
    ```

  * When possible, use custom namespace for events. It's easier to unbind the exact event that you attached without affecting other events bound to the DOM element. 
    
    ```html
    $("#myLink").on("click.mySpecialClick", myEventHandler); // GOOD
    // Later on, it's easier to unbind just your click event
    $("#myLink").unbind("click.mySpecialClick");
    ```  

## Effects and Animations

  * Adopt a restrained and consistent approach to implementing animation functionality.
  * DO NOT over-do the animation effects until driven by the UX requirements. 
    * Try to use simeple show/hide, toggle and slideUp/slideDown functionality to toggle elements.
    * Try to use predefined animations durations of "slow", "fast" or 400 (for medium).

## Plugins

  * Always choose a plugin with good support, documentation, testing and community support. 
  * Check the compatibility of plugin with the version of jQuery that you are using
  * Any common reusable component should be implemented as a [jQuery plugin](http://jqueryboilerplate.com/)

## Chaining

  * Use chaining as an alternative to variable caching and multiple selector calls. 
    
    ```html
    $("#myDiv").addClass("error").show();
    ```

  * Whenever the chain grows over 3 links or gets complicated because of event assignment, use appropriate line breaks and indentation to make the code readable. 
    
    ```html
    $("#myLink")
        .addClass("bold")
        .on("click", myClickHandler)
        .on("mouseover", myMouseOverHandler)
        .show();
    ```

  
  Source: http://lab.abhinayrathore.com/jquery-standards/


  * ## Resources

  * jQuery Performance: [http://learn.jquery.com/performance](http://learn.jquery.com/performance)
  * jQuery Learn: [http://learn.jquery.com](http://learn.jquery.com)
  * jQuery API Docs: [http://api.jquery.com/](http://api.jquery.com/)
  * jQuery Coding Standards and Best Practice: [http://www.jameswiseman.com/blog/2010/04/20/jquery-standards-and-best-practice](http://www.jameswiseman.com/blog/2010/04/20/jquery-standards-and-best-practice)
  * jQuery Plugin Boilerplate: [http://stefangabos.ro/jquery/jquery-plugin-boilerplate-revisited](http://stefangabos.ro/jquery/jquery-plugin-boilerplate-revisited)
