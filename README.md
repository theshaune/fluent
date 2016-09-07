![Fluent](logo.gif)

**Fluent**
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. This is a result of [my](http://twitter.com/shaunewest) experience with CSS. Through the years I have  made an effort to try as many frameworks and naming-conventions as I can.

I hope this repository will generate discussion, exploration and ideas on how to create a consistent **unified** approach to CSS development. *The Best CSS framework is one that works for the entire team, not just the indivual.*


### Noteworthy frameworks & Reading Material

#### Frameworks

There are far too many to list. I have used, played with, studied, loved, hated & found inspiration, from using the following frameworks. They are all worthy of your time to study and trial in atleast one project, you will learn a great deal from actually using each one in an application. 

My preferred framework is SuitCSS, FluentCSS follows a similar naming convention to [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md) with the exception of modifer classes, resposive classes, utility classes and the addition of pipes in the markup to seperate classes.

* [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [BEM](https://en.bem.info/method/)
* [Bootstrap](http://getbootstrap.com)
* [Foundation](http://http://foundation.zurb.com)
* [ITCSS](http://itcss.io/)
* [InuitCSS](https://github.com/inuitcss/)
* [Pure](http://purecss.io/)
* [Semantic-ui](http://semantic-ui.com)

#### Reading Material

* [Escaping CSS selectors](https://mathiasbynens.be/demo/crazy-class)
* [Consistent naming conventions](http://cereal.co/creating-a-consistent-naming-convention-for-css-with-special-characters/)


## 1. Naming Convention

#### HTML

```html
<div class = "ParentName | grid">
  <div class="ParentName-childName -modifierOne | .grid-item 1of3 sm-3of3"></div>
  <div class="ParentName-childName -modifierTwo is-active | .grid-item 1of3 sm-3of3"></div>
  <div class="ParentName-childName -modifierTwo | .grid-item 1of3 sm-3of3"></div>
</div>
```


#### CSS

**Components**

```css
.ParentName
.ParentName-childName
.ParentName-childName.-modifier
.ParentName-childName.is-active
.ParentName-childName.has-x
```

**Utilites & Global classes**

```css
.camelCase
```


## 2. Folder Structure
*Note: Consider prefixing files that rely on a specific inheritance order as this may help force the developer to consider what order the files will be imported in.*

<pre>
.
├── init.scss
├── base
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
├── external-libraries
│   ├── _*.scss
├── components
│   ├── _*.scss
├── utilities
│   ├── _*.scss
├── pages
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

## TODO

- **Refactor. Simplify. Flatten. Pug it.**
- Move grid better place for the grid import. component/structure? @import 'base/04.grid'; is a grid nessercary, hasn't been used at all in the previous 2 projects. 
- Consider folders with readme per component, opposed to inline commenting.
- Create a _better_ consistent commenting system.
- Consider renaming init.scss to fluent.css.
- Implement .wysiwyg class for CMS based inputs.
  - Consider optional parametors for `wysiwyg(h1, h2)` mixin.
- Media Query function needs to be implemented.
- Clean up _variables.scss
- Create guidlines for reserved classnames. eg.
  - .header, .body, .footer, .page-x, .content-x, .container, .wrapper, .contents
- Provide more of a description on how to abstract names for better modularity, eg. brand-logo is better than apple-logo in terms of allowing the file to be re-used in future projects.

## Thoughts

Explore use of escaped characters such as @ to represent media()
*class="12of12 | @sm-6of12 | @md-4of12"*
- This worked well, It was visually easy to identify and quick to learn, consider implementing.

Explore the use of brackets.
*padding(-1), padding(0), padding(1), p(-1), p(0), p(1)*
- This was slightly strange, need more discussion on merit. However It did work well for negative values.


Exlpore the use of descriptive namespacing.

- should be used to help indicate what the class for.
- Doesn't apply any styles on it owns.
- A sugar coated prefix.
- Possibly Captilized?
- example: class="Global Navigation store" .Global.Naviation.store

Explore the use of indicative + random names.

As the classname is 100% entirely used to identify and apply styles/changes to the markup, and we know that it doesn't make any difference if hte class is "x" or "X". A solution to help identify components could be to use a name that indicates what it is and then a name to identify the styles. This combined with a styleguide could lead to an easy to use library of components. example `.Page-Header.hollywood`

*Exlpore* the use of .Component .child,

- as some components will never be mixed, it can be over the top to use the strict naming convention
- children classes already adhere to pascal case. So in some instances there is almost no chance of a clash
- jQuery could clash two classes such as `price`. explore this.


*Explore* a flatter structure, closer to the nature of css.

Possible structure

- Collections
- Components
- Utitlies < base may be able to live here.
