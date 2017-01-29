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
<!-- Working on a naming convention for modifiers, whether -large, or is-large prefixed. more discussion is required. -->
<div class="parentName | grid">
  <div class="parentName-childName -modifier is-eventModifier has-eventModifier | grid-item 4of4 2of4@sm-lg 1of4@lg+"></div>
  <div class="parentName-childName | grid-item 4of4 2of4@sm+ 1of4@md+"></div>
  <div class="parentName-childName | grid-item 4of4 2of4@sm+ 1of4@md+"></div>
  <div class="parentName-childName | grid-item 4of4 2of4@sm+ 1of4@md+"></div>
</div>

<!-- Semantic Example -->
<header class="header is-large is-branded ">
  <div class="header-container">
    <h1 class="header-title"></h1>
    <p class="header-description"></p>
  </div>
</header>
```


#### CSS

**Components**

```css
.parentName
.parentName-childName
.parentName-childName.is-modified
.parentName-childName.is-active
.parentName-childName.has-x

body.has-open-parentName
body.parentName--is-open
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
├── init.scss
├── 01-base
│   ├── functions
│       ├── _*.scss
│   ├── mixins
│       ├── _*.scss
│   ├── _01.variables.scss
│   ├── _02.functions.scss
│   ├── _03.mixins.scss
│   ├── _04.grid.scss
│   ├── _05.normalize.scss
│   ├── _06.global-elements.scss
├── 02-external-libraries
│   ├── _*.scss
├── 03-elements
│   ├── _*.scss
├── 04-components
│   ├── _*.scss
├── 05-compositions
│   ├── _*.scss
</pre>


## 3. init.scss

Located in the root directory this file importas all of our `_.scss` files. 
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

Explore the use of semantic grid names. For example, using `.grid`, `grid-i`, inside of a `.component` can break it up and make it *feel* a little strange. by using selectors that target anything with `-grid` affixed we can keep the semantic classes, keep the css dry and the added benifit of now being able to target specific grid areas semanticaly.
Although this seems like a nice idea, i believe it would be difficult to get across to an entire team and i belive it may be difficult to keep consistent, almost too abstract an relies on a strong knowledge of advanced css selectors. But it definitely worth exploring the potential for this.

### Media Queries

Explore use of escaped characters such as @ to represent media()
~~*class="12of12 | @sm-6of12 | @md-4of12"*~~
~~- This worked well, It was visually easy to identify and quick to learn, consider implementing.~~
~~I have added the current way that i believe is semantic and very easy to understand to the documentation, I am not sure if I have got it completely correct, possily using @-sm, @-md may be better for max-width use cases, this can be closed once this has been explored.~~

... thinking.

- `className@small`
- `className@small+`
- `className@small-large`
- `className@small-`

- `@small--className`
- `@small(className)`
- `@from-small(className)`

- `@media(small)`
- `@media(medium)`
- `@media(large)`

- `@media-from(small)`
- `@media-from(medium)`
- `@media-from(large)`

- `@media-until(small)`
- `@media-until(medium)`
- `@media-until(large)`

- `@(small)`
- `@(medium)`
- `@(large)`

- `@from(small)`
- `@from(medium)`
- `@from(large)`

- `@until(small)`
- `@until(medium)`
- `@until(large)`


### Explore naming conventions for types of UI objects

- elements
  - buttons
  - form inputs
- components
  - cards
  - navbar
- compositions/ui/layout
  - grids

### Explore the use of indicative + random names.

**Warning: At first this may seem insane, but hear me out ...**

As the classname is 100% entirely used to identify and apply styles/changes to the markup, and we know that it doesn't make any difference if hte class is "x" or "X". A solution to help identify components could be to use a name that indicates what it is and then a name to identify the styles. This combined with a styleguide could lead to an easy to use library of components. example `.Page-Header.hollywood`

This may seem a little counter-intuitive in the begining but if we think of the definition of a name, it can become more of a natural and sensible suggestion. Considering this, creating a set of headers each with given names can acutally help us keep to a more semantic approach. 

**name**
*noun*

1. a word or set of words by which a person or thing is known, addressed, or referred to.

Although this is a scenerio where it is unlikely to happen unless we have a large and complex website with many different areas. But let's say we have 4 different header styles, all large *hero header* type sections. They are not specific to a pge, but rather simply selected by the user in a CMS to suit whatever the user decides is relevant to their article...

**Some examples may be;**

- modern
- contemporary
- abstract
- illustrative

**Or even as generic as;**

- brooklyn
- nyc
- sfc
- berlin

I am yet to explore whether this should be a modifier based on a an empty parent class such;

```scss
.header {
  &.is-modern {}
  &.is-contemporary {}
  // etc
}
```

or seperate classes;

```scss
.header-isModern {}
.header-isContemporary {}
```

--

### Modifiers

```scss
.class.isModified {}
.class.is-modified {}
.class--Modifier {}
```

Concerns to address with modifiers;

- What way is the most natural?
- Will it work with modifications to Javascript?
- Does it hae the correct CSS specificity?


*Explore* a flatter structure, closer to the nature of css.

### Possible structure

- Collections
- ~~Components~~
- Utitlies ~~< base may be able to live here.~~
