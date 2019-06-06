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

## Resources
- https://www.zachleat.com/web/comprehensive-webfonts/
- https://github.com/bramstein/fontfaceobserver
- https://www.html5rocks.com/en/tutorials/speed/high-performance-animations/
- https://css-tricks.com/almanac/properties/w/will-change/
