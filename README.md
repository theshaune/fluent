![Fluent](logo.gif)

**Fluent**
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. This is a result of [my](http://twitter.com/shaunewest) experience with CSS. This repo is essentially a notepad of thoughts, tests and ideas.

I hope this repository will generate discussion, exploration and ideas on how to create a consistent **unified** approach to CSS development. ***The Best CSS framework is one that works for the entire team, not just the individual.***


### Noteworthy frameworks & Reading Material

#### Frameworks

There are far too many to list. I have used, played with, studied, loved, hated & found inspiration, from using the following frameworks. They are all worthy of your time to study and trial in atleast one project, you will learn a great deal from actually using each one in an application. 

My preferred framework is SuitCSS, FluentCSS follows a naming convention similar to [Bulma](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md) with the exception of modifer classes, responsive classes, utility classes and the addition of pipes in the markup to seperate classes.

* [BEM](https://en.bem.info/method/)
* [Bootstrap](http://getbootstrap.com)
* [Bulma](http://bulma.io/)
* [Foundation](http://http://foundation.zurb.com)
* [InuitCSS](https://github.com/inuitcss/)
* [ITCSS](http://itcss.io/)
* [Pure](http://purecss.io/)
* [Semantic-ui](http://semantic-ui.com)
* [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [Tachyons](http://tachyons.io/)

#### Reading Material

* [Escaping CSS selectors](https://mathiasbynens.be/demo/crazy-class)
* [Consistent naming conventions](http://cereal.co/creating-a-consistent-naming-convention-for-css-with-special-characters/)


## 1. Naming Convention

#### HTML

```html
<!-- Component -->
<div class="parentName">
  <div class="parentName-childName repsonive@lg isModified hasEventModifier"></div>
  <div class="parentName-childName"></div>
  <div class="parentName-childName"></div>
  <div class="parentName-childName"></div>
</div>

<!-- Grid -->
<div class="grid">
  <div class="grid-item 12of12 6of12@sm 3of12@md"></div>
  <div class="grid-item 12of12 6of12@sm 3of12@md"></div>
</div>
```


#### CSS

**Components**

```css
.parentName
.parentName-childName
.parentName-childName.class@breakpoint
.parentName-childName.isModified
.parentName-childName.hasActivity

body.componentName--isOpen
```

**Responsive classes**

We can make us of the `@` symbol to denote any class that is a media query. This visual indication allows devlopers to quickly and confidently identify which breakpoints the class effect. It naturally provides a clean way to write the class, with the syntax of `.className@breakpoint`. Which literally translates to className at breakpoint.

When we write these classes in css we must escape the ampersand character as shown below.

```css
@media screen and (min-width: $sm) {
  .class\@sm {}
}
@media screen and (min-width: $md) {
  .class\@md {}
}
@media screen and (min-width: $lg){ 
  .class\@lg {}
}
```

**Comments**
```css
  /**
   * Documentation of styles and notes should use the single or multi-line syntax 
   * // Forward slash commenting should be reserved for code.
   */
  
  /* Parent to all the things. */
  .parent {
    display: block;
    // color: pink;
  }
```

## 2. Folder Structure
*Note: Consider prefixing folders & files that rely on a specific inheritance order as this may help force the developer to consider what order the files will be imported in.*

<pre>
.
├── index.scss
├── core
│   ├── functions
│       ├── _*.scss
│   ├── mixins
│       ├── _*.scss
│   ├── _01.variables.scss
│   ├── _02.functions.scss
│   ├── _03.mixins.scss
│   ├── _04.normalize.scss
│   ├── _05.typography.scss
├── components
│   ├── _grid.scss
│   ├── _*.scss
</pre>


## 3. index.scss

Located in the root directory this file imports all of our `_.scss` files. 
The files must be imported in the correct order to maintain the correct inheritance of styles.
This will be the **only** file in the application that does not begin with _.

*Note: It is very important to import the files in the correct order.*

<pre>init.scss</pre>

```scss
@charset "UTF-8";

/* 1. External Libraries */
@import '../../node_modules/modularscale-sass/stylesheets/modular-scale';

/* 2. Base */
@import 'base/_01.variables';
@import 'base/_02.functions';
@import 'base/_03.mixins';
@import 'base/_04.grid';
@import 'base/_05.normalize';
@import 'base/_06.global-elements';

/* 4. Components ... */
@import 'components/_form';
@import 'components/_*';

/* 5. Utilities ... */
@import 'utilities/_*';

/* 5. Pages ... */
@import 'pages/_*';
```

## 4. Resets

Section coming soon ... maybe 😅

## TODO

- Reset guidlines.
- **Refactor. Simplify. Flatten.**
- Move grid better place for the grid import. component/structure? @import 'base/04.grid'; is a grid nessercary, hasn't been used at all in the previous 2 projects. 
- Consider renaming init.scss to fluent.css or index.scss.
- Implement .wysiwyg class/component/mixin for CMS based inputs.
- Media Query function needs to be implemented.
- Clean up _variables.scss
- Create guidlines for reserved classnames. eg.
  - .header, .body, .footer, .page-x, .content-x, .container, .wrapper, .contents
- Provide more of a description on how to abstract names for better modularity, eg. brand-logo is better than apple-logo in terms of allowing the file to be re-used in future projects.

### Explore naming conventions for types of UI objects

- elements
  - buttons
  - form inputs
- components
  - cards
  - navbar
- compositions/ui/layout
  - grids


**Elements**
*noun*

1. a component or constituent of a whole or one of the parts into which a whole may be resolved by analysis:

**Components**
*noun*
1. a constituent part; element; ingredient.

**composition**
*noun*
1. The act of combining parts or elements to form a whole.

## Thoughts

This repo was created as a way to help get my thoughts out onto paper and to explain my process when meeting developers/sharing ideas.

I've since spent more time in react and less time in css, therefore it hasn't got the love it once did.

In time I may explore it again, and hopefuly end up with a Simple, Natural & Intuitive Guideline.
