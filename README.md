# MOCSSS (Modern Organized CSS Starter)

This repository is meant to be downloaded and used as the starting point for other projects. Drop the **scss** folder into your project and update your watch or build scripts accordingly.

## Features

- Minimal reset - somewhere between [normalize.css](https://necolas.github.io/normalize.css/) and the trusty &nbsp;`* { margin: 0; padding: 0; box-sizing; border-box;  }`
- An index.scss entry point for all SASS partials
- CSS variables to help manage layout, responsive font sizes and spacing
- A familar flexbox column layout for when you don't want to (or can't) use CSS grid
- An [ITCSS](https://itcss.io/)-like approach (Inverted Triangle CSS) with fewer confusing layers
- Environmentally friendly print styles
- Follows the [Airbnb CSS Style Guide](https://github.com/airbnb/css), with the minor exception of tigher formatting in a few places
- An empty components folder for all of your project-specific [BEM](http://getbem.com/) components

The (soon-to-be-included) example index.html file contains a list commonly used `<head>` meta tags.

## Files and Folders

#### abstracts
#### base
#### blocks (think OOCSS)
#### components (think BEM)

## Blocks vs Components

## Containers vs Sections

## Development and Hacking

```bash
npm install
npm start
```

This installs [node-sass](https://www.npmjs.com/package/node-sass) for processing SASS files (which seems to be faster than the ruby gem) and [live-server](https://www.npmjs.com/package/live-server) for starting a development server with live reload.

## Browser Support

Modern browsers due to the use of [CSS custom properties](https://caniuse.com/#feat=css-variables). If you need to support IE11, you can either add fallback styles _before_ using `var(--my-property)` or load a custom stylesheet (which can be used to address other IE quirks). Here's a snippet for that:

```js
// only Internet Explorer has this property defined
if (document.documentMode) {
  document.documentElement.classList.add('msie');
  var link = document.createElement('link');
  link.rel = 'stylesheet';
  link.href = '/css/msie.css';
  document.head.appendChild(style);
}
```
```css
/* msie.css */
.msie .my-component {
  margin-top: 2em;
  margin-bottom: 2em;
}
```