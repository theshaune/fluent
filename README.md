![Fluent](logo.gif)

**Fluent**
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. This is a result of [my](http://twitter.com/shaunewest) experience with CSS. This repo is essentially a notepad of thoughts, tests and ideas.

I hope this repository will generate discussion, exploration and ideas on how to create a consistent **unified** approach to CSS development. ***The Best CSS framework is one that works for the entire team, not just the indivual.***


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

#### Reading Material

* [Escaping CSS selectors](https://mathiasbynens.be/demo/crazy-class)
* [Consistent naming conventions](http://cereal.co/creating-a-consistent-naming-convention-for-css-with-special-characters/)


## 1. Naming Convention

#### HTML

```html
<!-- Component -->
<div class="parentName">
  <div class="parentName-childName is-modified has-eventModifier"></div>
  <div class="parentName-childName"></div>
  <div class="parentName-childName"></div>
  <div class="parentName-childName"></div>
</div>

<!-- Grid -->
<div class="grid">
  <div class="grid-item 4of4 2of4@sm-lg 1of4@lg+"></div>
  <div class="grid-item 4of4 2of4@sm+ 1of4@md+"></div>
  <div class="grid-item 4of4 2of4@sm+ 1of4@md+"></div>
  <div class="grid-item 4of4 2of4@sm+ 1of4@md+"></div>
</div>
```


#### CSS

**Components**

```css
.parentName
.parentName-childName
.parentName-childName.is-modified
.parentName-childName.is-active
.parentName-childName.has-x

body.componentName--is-open
```

**Responsive classes**

```css

@media screen and (max-width: $sm) {
  .class\@sm- {}
}
@media screen and (max-width: $md) {
  .class\@md- {}
}
@media screen and (max-width: $lg){ 
  .class\@lg- {}
}

@media screen and (min-width: $sm) {
  .class\@sm+ {}
}
@media screen and (min-width: $md) {
  .class\@md+ {}
}
@media screen and (min-width: $lg){ 
  .class\@lg+ {}
}

@media screen and (min-width: $sm) and (max-width: $md){ 
  .class\@sm-md {}
}
@media screen and (min-width: $sm) and (max-width: $lg){ 
  .class\@sm-lg {}
}
@media screen and (min-width: $md) and (max-width: $lg){ 
  .class\@md-lg {}
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

## Thoughts

Simple Natural & Intuitive

Explore the use of semantic grid names. For example, using `.grid`, `grid-i`, inside of a `.component` can break it up and make it *feel* a little strange. by using selectors that target anything with `-grid` affixed we can keep the semantic classes, keep the css dry and the added benifit of now being able to target specific grid areas semanticaly.
Although this seems like a nice idea, i believe it would be difficult to get across to an entire team and i belive it may be difficult to keep consistent, almost too abstract an relies on a strong knowledge of advanced css selectors. But it definitely worth exploring the potential for this.

### Media Queries

Explore use of escaped characters such as @ to represent media()

- `className@small`
- `className@small+`
- `className@small-`
- `className@small-large`
- `className@fromSmall`
- `className@UntilSmall`

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
