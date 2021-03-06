Website performance optimization  - project 4

Tools:
  -nodejs
  -grunt

Optimization solution hosted on github gh-pages branch, link:
http://laimonasdanyla.github.io/frontend-nanodegree-mobile-portfolio/

Initial result on PageSpeed insights:
  -28/100 on mobile  
  -30/100 on desktop

Image optimization:
  - size reduction based on suggestion by PageSpeed or inspecting elements
  at chrome devtools.
  - Images compressed at https://compressor.io

main.js optimization:
  - call updatePositions with requestAnimationFrame(updatePositions);
  - reduce the number of pizzas to be painted  - 20 pizzas is sufficient to
  cover the screen.

  - Loops:
    -all static numbers at function updatePositions are moved to variables
    above the loop.
    - document.body.scrollTop moved to var scrolling above the loop.
    - var phase is defined above the loop.
    - var elem is defined above the loop.

  Function changePizzaSizes:
    - add switch(size) function

    - define as var randPizzaCont =
    document.querySelectorAll(".randomPizzaContainer");
    in orde to move out var definition out of the loop

    - remove var dx and newWidth and
    corresponding dx and newWidth lines inside the loop.

    - remove old unused code with determineDx.  

Page Speed Score with the optimization above: 91/100 for Desktop, 77 for mobile.


Rendering optimization:
Index.html:
    - move common css styles to inline code in html.
    - move print.css to the end of the head.
    - make analytics.js async.
    - add media query to <link href="css/print.css" rel="stylesheet" media="print">
    - move both css links to bottom of page

----------------------------------------------
After code review
----------------------------------------------

  - use getElementById at resizePizzas function
  - the use of "use strict"; to resizePizzas function caused errors -
  so statement was removed.
  - at var randPizzaCont use document.getElementsByClassName("randomPizzaContainer");
  - set amout of pizzas to 60, to fit most of screens
  (iPhone5 had longest and needed most of moving pizzas)
  - at randPizzaCont loop move measurements of lengthto local variable, set min
  and max value, e.g.: for (var i = 0, len = len1; i < len; i++)
  - declare pizzaDiv outside the loop
  - move measuring of length into local var at updatePositions:
      var itemsLength1 = items.length;
        for (var i = 0, itemsLength = itemsLength1; i < itemsLength; i++) {
  - update: use getElementById for movingPizzas1
  - move getElementById("movingPizzas1"); outside the loop
  - move randomPizzaContainer styling from JS to CSS File
  - fix: reduce moving pizza image size, compress and update main.js with
  new reduced image file
  - update: move randomPizzaContainer width property from html to css
  - fix: comment out width porperty from .randomPizzaContainer:after
  to make all pizzas bigger and uniform
  - fix: remove will-change: transfrom;  from .mover class - was causing too
  many layouts
  - fix: put back will-change: transfrom; to .mover class to reduce
  the painting time
  - move the bootstrap css link before the custom style.css
  - will-change: transfrom; move to the first position of at .mover class
  - move out some calculations from the loop at updatePositions function
  - dynamic calculation of required amount of pizzas added for a loop
  - fix: move .container from bottom to below <body> styling,
  uncomment <form> styling
  - inline styling of h2 move to css, rearrange order of styling elements at css
  - Separated scroll and updatePositions set to requestAnimationFrame
  - order of styling items at css rearranged.    
  - fix: run updatePositions after elem is loaded -  
  to distribute moving pizzas on page after page is loaded.
  - instead of style.top use style.cssText, line 533: elem.style.cssText =
  ' top:' + (Math.floor(i / cols) * h) + 'px;';
  - updatePositions style.left change to transform: translateX
  - add bootstrap grid for uniform pizza sizes in html, and main.js: add com-md-4.
  - adjust pizza sizes: small 65%, medium 75%, large 100%.
  - adjust pizza size to medium 75% after reload at style.css  
  - remove width and height styling of randomPizzaContainer:after at style.css
  - add webkit prefixes to css (http://autoprefixer.github.io/)
  - run updatePositions if scrolled / animated - set a condition to do so
  (example and idea from discussion forum)
  - fix: "animating" change to "scroll".  
  - move some variable outside the updatePositions function
  - make styling with style.transform = translateX instead of style.left
  - reduceSpeed set to 5000 (was 1250)
  ---------------------------
  After Second review
  ---------------------------

  Getting back to original moving pattern of pizzas:
  - set var s instead of var h  at 572
  - make a separate loop to calculate values of modulusCalc outside the main
  loop at updatePositions
  - use items[i].style.left original line as transform: translateX modifies the movement way of pizzas, adjust the further code in this line

  Changing back of pizza resizing sizes:
  - remove bootstrapClass col-md-4 from pizzaElementGenerator function
  - remove col-md-4 from pizza.html for randomPizzaContainer
  - remove width 75%, set width 33.33% and height 325px for randomPizzaContainer (before and after) at style.css

---------------------
Third review - bug in pizza resizing sizes, not matching the original size
--------------------
 - remove font-size: 1em from randomPizzaContainer at style.css
 - main.js - pizza medium size set to 33.33, was 33.3.
 - remove width and height properties from randomPizzaContainer:after at style.css  - this was a bug.
