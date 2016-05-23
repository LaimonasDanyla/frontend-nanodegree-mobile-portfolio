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
    - define as var randPizzaCont = document.querySelectorAll(".randomPizzaContainer"); in orde to move out var definition out of the loop
    - remove var dx and newWidth and corresponding dx and newWidth lines inside the loop.
    - remove old unused code with determineDx.     
