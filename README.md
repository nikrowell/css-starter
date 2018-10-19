# CSS Starter

This repository is meant to be downloaded and used as the starting point for other projects. Drop the **scss** folder into your project and update your watch or build scripts accordingly.

## Features

- Minimal reset - somewhere between [normalize.css](https://necolas.github.io/normalize.css/) and the trusty &nbsp;`* { margin: 0; padding: 0; box-sizing; border-box;  }`
- An index.scss entry point for all partials
- CSS variables to help manage layout, responsive font sizes and spacing
- A set of flexbox column utilities for when you don't want to (or can't) use CSS grid
- An [ITCSS](https://itcss.io/)-like approach (Inverted Triangle CSS) with fewer layers
- Follows the [Airbnb CSS Style Guide](https://github.com/airbnb/css), with the minor exception of tigher formatting in a few places
- A components folder for all of your project-specific [BEM](http://getbem.com/) components
- Environmentally friendly print styles

index.html file with commonly used `<head>` meta tags.

## Files and Folders

### abstracts
### base
### components (BEM)
### utilities
Not familiar with utility-first CSS? Check out [CSS Utility Classes and "Separation of Concerns"](https://adamwathan.me/css-utility-classes-and-separation-of-concerns/) and [In Defense of Utility-First CSS](https://frontstuff.io/in-defense-of-utility-first-css).

#### background
No responsive breakpoints.

* bg-top
* bg-right
* bg-bottom
* bg-left
* bg-left-top
* bg-left-bottom
* bg-right-top
* bg-right-bottom
* bg-repeat-x
* bg-repeat-y
* bg-no-repeat
* bg-center
* bg-contain
* bg-cover

#### border
No responsive breakpoints. Configurable variables are `---border-width` and `---border-radius`

* border
* border-top
* border-right
* border-bottom
* border-left
* circle
* rounded
* no-border

#### color
Color ultility classes are generated based on keys defined in a `$colors` [SASS map](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#maps). Use semantic (primary, success, error) or declarative (red, green, papayawhip) color variables as desired.
* bg-`color`
* border-`color`
* text-`color`
* hover:bg-`color`
* hover:border-`color`
* hover:text-`color`

#### columns
The columns utility classes provide simple flexbox grid with support for responsive breakpoints. The number of columns and the column gap can be configured via SASS variables at the top of `utilities/_columns.scss`. By default, these values are 12 columns with a 20px gap.
```html
<div class="columns">
  <div class="col-6 md:col-5 lg:col-2">col</div>
  <div class="col-3 md:col-5 lg:col-5">col</div>
  <div class="col-3 md:col-2 lg:col-5">col</div>
</div>
```
#### display
#### easing
CSS custom properties for various cubic-bezier easing functions.

Property            | Easing Function
------------------- | ----------------------------------------------
--ease-in-quad      | cubic-bezier(.55,.085,.68,.53)
--ease-in-cubic     | cubic-bezier(.550,.055,.675,.19)
--ease-in-quart     | cubic-bezier(.895,.03,.685,.22)
--ease-in-quint     | cubic-bezier(.755,.05,.855,.06)
--ease-in-expo      | cubic-bezier(.95,.05,.795,.035)
--ease-in-circ      | cubic-bezier(.6,.04,.98,.335)
--ease-out-quad     | cubic-bezier(.25,.46,.45,.94)
--ease-out-cubic    | cubic-bezier(.215,.61,.355, 1)
--ease-out-quart    | cubic-bezier(.165,.84,.44, 1)
--ease-out-quint    | cubic-bezier(.23, 1,.32, 1)
--ease-out-expo     | cubic-bezier(.19, 1,.22, 1)
--ease-out-circ     | cubic-bezier(.075,.82,.165, 1)
--ease-in-out-quad  | cubic-bezier(.455,.03,.515,.955)
--ease-in-out-cubic | cubic-bezier(.645,.045,.355, 1)
--ease-in-out-quart | cubic-bezier(.77, 0,.175, 1)
--ease-in-out-quint | cubic-bezier(.86, 0,.07, 1)
--ease-in-out-expo  | cubic-bezier(1, 0, 0, 1)
--ease-in-out-circ  | cubic-bezier(.785,.135,.15,.86)

```css
.my-component {
  position: fixed;
  right: 0;
  top: 0;
  width: 300px;
  height: 100%;
  transform: translate3d(100%,0,0);
  transition: transform 0.3s var(--ease-out-expo);
}
.my-component.active {
  transform: translate3d(0,0,0);
}
```

#### flexbox
#### position
#### sizing
#### spacing
#### text

## Development

```bash
npm install
npm start
```

This installs [node-sass](https://www.npmjs.com/package/node-sass) for processing scss files and [live-server](https://www.npmjs.com/package/live-server) for starting a development server with live reload.

## Browser Support

Due to the use of [CSS custom properties](https://caniuse.com/#feat=css-variables), only modern browsers are supported by default. If you need to support IE11, you can either add fallback styles _before_ using `var(--my-property)` or load a custom stylesheet (which can be used to address other IE quirks). Here's a snippet for that:

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