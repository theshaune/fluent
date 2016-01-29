# FluentCSS

**Fluent**
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. This is a result of [my](http://twitter.com/shaunewest) experience with CSS. Through the years I have  made an effort to try as many frameworks and naming-conventions as I can.

I hope this repository will generate discussion, exploration and ideas on how to create a consistent **unified** approach to CSS development.

*The Best CSS framework is one that works for the entire team, not just the indivual.*

### Noteworthy frameworks & Reading Material

I have used, played with, studied, loved, hated & found inspiration, from using the following frameworks. They are all worthy of your time to study and trial in atleast one project, you will learn a great deal from actually using each one in an application.

* [BEM](https://en.bem.info/method/)
* [Bootstrap](http://getbootstrap.com)
* [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [Foundation](http://http://foundation.zurb.com)
* [ITCSS](http://itcss.io/)
* [InuitCSS](https://github.com/inuitcss/)
* [Pure](http://purecss.io/)
* [Semantic-ui](http://semantic-ui.com)


# FLUENTCSS

## 1. Naming Convention

FluentCSS follows a very similar naming convention to [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md) with the expection of modifer classes and the addition of pipes in the markup to seperate classes.

```html
<div class = "ParentName | .grid">
  <div class="ParentName-childName +modifierOne | .grid-item 1of3 sm-3of3"></div>
  <div class="ParentName-childName +modifierTwo is-active | .grid-item 1of3 sm-3of3"></div>
  <div class="ParentName-childName +modifierTwo | .grid-item 1of3 sm-3of3"></div>
</div>
```

```css
.ParentName
.ParentName-childName
.ParentName-childName.+modifier
.ParentName-childName.is-active
.ParentName-childName.has-x
```

## 2. File Structure
The files must be imported in the correct order to maintain the correct inheritance of styles.
All files should be imported in a single .scss file, this will be the **only** file in your application that does not begin with _.

*Note: Consider prefixing files that rely on a specific inheritance order as this may help force the developer to consider what order the files will be imported in.*
<pre>
.
├── init.scss
├── base
│   ├── functions
│       ├── _\*\*.\*.scss
│   ├── mixins
│       ├── _\*\*.\*.scss
│   ├── _01.variables.default.scss
│   ├── _02.functions.scss
│   ├── _03.mixins.scss
│   ├── _04.grid.scss
│   ├── _05.normalize.scss
│   ├── _06.global-elements.scss
├── external-libraries
│   ├── _\*\*.\*.scss
├── components
│   ├── _\*\*.\*.scss
├── utilities
│   ├── _\*\*.\*.scss
├── functions
│   ├── _\*\*.\*.scss
├── mixins
│   ├── _\*\*.\*.scss
</pre>


## 3. init.scss

Located in the root directory this file importas all of our `_.scss` files. 

*Note: It is very important to import the files in the correct order.*

<pre>init.scss</pre>

```scss
@charset "UTF-8";

/* 1. External Libraries */
@import '../../node_modules/modularscale-sass/stylesheets/modular-scale';

/* 2. Base */
@import 'base/01.variables.default';
@import 'base/02.functions';
@import 'base/03.mixins';
@import 'base/04.grid';
@import 'base/05.normalize';
@import 'base/06.global-elements';

/* 3. Components ... */
/* 4. Functions  ... */
/* 5. Utilities  ... */

```

## TODO

- Move grid better place for the grid import. component/structure? @import 'base/04.grid';
- Consider folders with readme per component, opposed to inline commenting.
- Work out a better commenting system.
- Consider renaming init.scss to fluent.css.
- Media Query function needs to be implemented.
- Clean up _variables.scss
- Consdier + prefix for .is-active


## Thoughts

Explore class names in a similar manner to semantic-ui.
Explore use a seperator in html to break each class
Explore use a escaped characters such as @ to represent media()


[class*="float left"]
class="float left | bold font | hidden on small"
class="12of12 | @sm-6of12 | @md-4of12"

**https://mathiasbynens.be/demo/crazy-class** Escaping CSS selectors
