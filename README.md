## Image Optimization
- Prefer Loosy images
- Svg for icons and illustrations
- Mp4 instead of gif. ( even giffy doesn't use it. )
- [JPNG.svg](https://codepen.io/shshaw/full/LVKEdv) instead of transparent png
- Moderate or lower quality JPG for everything else

## Font Loading
- Problem: Ist is a Render Blocking Resource
- Problem: Content invisible while loading ( FOIT -  Flash of Invisible Text FOUT - Flash of unstyled text )
- Problem: Websites can be broken for old browsers when during bad font loading 
- Use preload attr in script tag
- Customize font with [Font Squirrel](https://www.fontsquirrel.com/tools/webfont-generator)
- Use third party tool if its necessary like [fontfaceobserver](https://github.com/bramstein/fontfaceobserver)
- Using system font always best for optimizing

## Painting and Animation Performance
It is an expensive process. Browser engine processes the pixels and drawing on the screen. 
Some dangeorus panting properties listed below. Use it wisely.
- background
- color
- box-shadow
- fixed position & background

Triggerring **Composite** instead of **Painting** gives much better performance
Some properties can be used
- opacity
- transform

Also you can add `will-change: transform;` for optimizing repainting concepts.
In chrome dev tools painting and repainting can be observed. `inspect > paint flashing in rendering panel`

**TLDR**
- Try to do not animate layer properties
- Be careful fixed content caused repeatetly repainting
- Animate using transform and opacity
- Always do tests

## Critical Rendering
- Analyze the page what is critical and most important what is not

**Render Blocking Resources**
- stylesheet
- scripts
- fonts

**What is Critical?**
- Case by case ( Contents should prioritized based on user interacts with )
- Usally above the fold ( not always but frequently user interacts the content above the fold first - good to start here) 
- User prioritized content

**How?**
- split most important css and js content and load them first (like header.css, header.js - chunking)
- avoid blocking less critical css and js by loading them as a `preload`( use [third-party tool](https://github.com/filamentgroup/loadCSS) if doesn't supported by browsers )
  - another third party tool: `webpack-plugin-critical`

## Script Loading
**Traditional Script Loading**
- Parsing HTML
- Parsing Render Blocked
  - Downloading scripts
  - parsing & running downloaded scripts
- Parsing HTML

**`async` Script Loading**
Downloaded while the browser is parsing the HTML. As soon as scripts downloaded will executed regardless the parsing completed or not. 

- Parsing HTML
  - Downloading scripts
- HTML Blocked
  - parsing & running downloaded scripts
- Parsing HTML

**`defer` Script Loading**
The main differences between `defer` and `async` the `defer` will executed after parsing html completed.
- Parsing HTML
  - Downloading scripts
- Parsing HTML
  - parsing & running downloaded scripts

### Benefit of `async` and `defer`
- The key benefit of using `async` and `defer` is downloading the js earlier while not blocking HTML parsing. 
- Load scripts with this tags into the header. You won't get much benefit if its placed into the body. Because document will be already created.

**TLDR**
- Avoid to use script inside of the header. If your thinking it has to be placed inside of the header move it into the end of the body
- Use `async` when you want to modularize small piece of js not depend on any other script such as analytics, metrica etc... -  - Use `defer` for everything else. 

## Lazy Loading
- Great for reducing render blocking media content
- Can also be applied using infinite scroll
- Prune hundreds of kb
- Can be implemented by developer using with [`IntersectionObserver`](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) instead of using huge size of libraries 
- Don't forget to apply `<noscript>` scenario if performance is optimized by the js solution

## Minification
- Bundling is important but gzipping is essential. 
- Gzipping also solves repeating text problem.  
- Gzipping works on the backend just before the HTTP response. 
- Project isn't "production ready" if it is not compressed or minified

## Loading Indicators 
Best practices:
- **quick load**: Skeleton screens
- **< 2s** : Spinner
- **> 2s** : Progress bar
- **> 6s** : progress bar with explaination

## Resources
- https://www.zachleat.com/web/comprehensive-webfonts/
- https://github.com/bramstein/fontfaceobserver
- https://www.html5rocks.com/en/tutorials/speed/high-performance-animations/
- https://css-tricks.com/almanac/properties/w/will-change/ 
- https://www.html5rocks.com/en/tutorials/speed/high-performance-animations/ 
- https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path
