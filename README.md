# Website Performance Optimization portfolio project

## How to get started

1. Check out my repository: https://github.com/ElenaBabenko/udportfolio
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

## How to test

### Testing index.html

2. Copy the URL from ngrok and add index.html to the end of it.
2. Go to [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) and enter the URL in the field.
2. Click Analyze and review the results.

### Testing pizza.html

3. To test pizza.html copy the URL from ngrok and add /views/pizza.html to the end of it.
2. Open the page in Chrome browser.
3. Go to View > Developer > Developer tools to test.

## Optimizations I performed

### For index.html

PageSpeed Mobile score - 94/100, desktop score - 100/100.

- Cleaned up (removed unused styles) and minified CSS
- JS and CSS are served asynchronosly
- Made a small optimized version or pizza image to reduce file size
- Optimized font delivery

Didn't have time to figure out what to do with analytics JS and minification tools. But the score is above 90.

### For pizza.html

#### Overall:

- Optimized pizzaria.jpeg from over 2 MB to 200 KB
- Minified CSS
- Moved all static width and height styling from JS to CSS files
- Replaced repeated selectors with a variables where possible
- Cached variables where possible

#### For the moving pizzas:

- Replaced document.querySelectorAll with document.getElementsByClassName where possible
- Moved layout calculations outside of the loop
- In updatePositions() replaced basicLeft with translate3D
- Added will-change: transform; and backface-visibility: hidden; to .mover to optimize brower rendering


#### For the pizza size switcher:

- Switched how pizza images sizes are updated. Instead of changing each column width on the fly I just assign a different class (eg, small-size) to the parent container and control width of the child elements thru css coming from the stylesheet.
- Added will-change: width; to .randomPizzaContainer to optimize brower rendering
- in CSS added media queries and changed column sizes to better control how pizza images appear on small screens. Before, if you go to screen less than ~600px and select small size the images won't have enough space to render and won't show up at all.
