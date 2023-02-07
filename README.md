# Interneting Is Hard - Responsive Design and Responsive Images

This is a solution to the [Responsive Design tutorial No. 10 of HTML & CSS Is Hard](https://www.internetingishard.com/html-and-css/responsive-design/) and [Responsive Images tutorial No. 11 of HTML & CSS Is Hard](https://www.internetingishard.com/html-and-css/responsive-images/).

## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

### Screenshot

![Responsive Design screenshot](./responsive-design.png)

### Links

- Solution URL: [Responsive Design solution](https://github.com/jugglingdev/responsive-design)
- Live Site URL: [Responsive Design live site](https://jugglingdev.github.io/responsive-design/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties

### What I learned

I enjoyed working with responsive design in this tutorial.  I deeply appreciate making sites user friendly on your phone just as much as your desktop, so it was neat to peek behind the curtain.

The biggest tool in today's toolbox was media queries.  These set conditions based on screen size.  Samples of the media queries code are below.

This tutorial took a mobile-first approach in design.  This keeps the base styles outside the media queries for easy updating.

While the mobile and tablet media queries had fluid widths, the desktop width was fixed and centered with auto-margins.  The neat thing with flexbox is that the order was easily changed around for desktop widths using the `order` property.

One thing to remember to add to the `<head>` of the document is the code to disable viewport zooming so mobile devices can actually use the mobile layout.  The code for this is below.

On to responsive images.

It's first important to note that retina screens have two or even three times as many pixels as standard screens.  This makes the images smaller.  Keep this in mind moving forward with responsive images.

SVGs are awesome in this scenario because they scale for retina screens.  In this tutorial, we just need to set `.illustration` to `width: 100%` (so the image is fluid across devices) and then add an inline style to the `<img>` tag so `style='max-width: 500px'` (so the desktop image doesn't get too large).

What about PNG, GIF, and JPG?  If you want to be lazy, then you can just use a high-resolution image (1000x500), assuming every screen is a retina screen.  

For image optimization, there are 3 options:

1. Retina Optimization Using `srcset`

```html
<!-- This attribute defines which image a browser should use.  1x is for standard and 2x is for retina -->
<img src="illustration-small.png"
    srcset="images/illustration-small.png 1x,
            images/illustration-big.png 2x"
    style="max-width: 500px">
```

2. Screen Width Optimization

```html
<!-- Here, we're optimizing based on image dimension and not just device screen resolution -->
<img src="images/photo-small.jpg"
    srcset="images/photo-big.jpg 2000w,
            images/photo-small.jpg 1000w"
    sizes="(min-width: 960px) 960px, 100vw">
```

3. Art Direction with `<picture>`

```html
<!-- Use this when you're want to use a tall image for mobile and wide image for desktop -->
<picture>
  <source media="(min-width: 401px)"
          srcset="images/photo-big.jpg">
  <source media="(max-width: 400px)"
          srcset="images/photo-tall.jpg">
  <img src="images/photo-small.jpg">
</picture>
```

Use option 1 for images less than 600px wide.  Use option 2 for bigger photos.  Use option 3 for when you're trying to do something fancy with your designer.

That's a wrap on responsive design!

Other code snippets from this tutorial include:

```css
/* Mobile Styles */
@media only screen and (max-width: 400px) {
  body {
    background-color: #F09A9D;
  }
}

/* Tablet Styles */
@media only screen and (min-width: 401px) and (max-width: 960px) {
  body {
    background-color: #F5CF8E;
  }
}

/* Desktop Styles */
@media only screen and (min-width: 961px) {
  body {
    background-color: #B2D6FF;
  }
}
```

```html
<!-- Code to disable viewport zooming -->
<meta name="viewport"
      content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
```

### Continued development

Okay, there was a lot here.  I most would like practice with each of the 3 responsive image scenarios.

### Useful resources

- [MDN @media](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) - More details on media queries.

- [Learn Responsive Design](https://web.dev/learn/design/intro/) - Great explanation of responsive design.

## Author

- GitHub - [@jugglingdev](https://github.com/jugglingdev)

- freeCodeCamp - [@jugglingdev](https://www.freecodecamp.org/jugglingdev)

- Frontend Mentor - [@jugglingdev](https://www.frontendmentor.io/profile/jugglingdev)

- LinkedIn - [Kayla Paden](https://www.linkedin.com/in/kayla-marie-paden)

## Acknowledgments

Shoutout to Oliver James for his dedication to publishing and maintaining InternetingIsHard.com.  His tutorials were the first that really clicked for me.