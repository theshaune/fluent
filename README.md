# Fluent { css }
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. The Following documentation is a result of my experience with CSS and trying alot of frameworks, naming-conventions, I have found that this methodology **currently works best for me**. I know it will not suit everyone and it is not intended to be a perfect solution.

I have used, played with, studied, loved, hated & found inspiration, from using the following repos. They are all worthy of your time to study and trial in atleast one project, you will learn a great deal from actually using each one in an application.

* [BEM](https://en.bem.info/method/)
* [Bootstrap](http://getbootstrap.com)
* [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [Foundation](http://http://foundation.zurb.com)
* ITCSS

## 1. File Structure
The files must be imported in the correct order to maintain the correct inheritance of styles.
All files should be imported in a single .scss file, this will be the **only** file in your application that does not begin with _.

<pre>
@charset "UTF-8";

/* 1. base.x */
@import 'base.functions';
@import 'base.variables.default';
@import 'base.variables.theme';
@import 'base.normalize';
@import 'base.global';

/* 2. ui.x */
@import 'ui.grid';
@import 'ui.layout';
@import 'ui.menu';
@import 'ui.megaMenu';

/* 3. site.x */
@import 'site';
@import 'site.header';
@import 'site.body';
@import 'site.footer';

/* 4. component.x ... */
</pre>


