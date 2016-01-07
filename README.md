# FluentCSS

**Fluent**
*adjective*

1. able to express oneself easily and articulately.

## Introduction
FluentCSS is a methodology to help write CSS smoothly, gracefuly and effortless. The Following documentation is a result of my experience with CSS and trying alot of frameworks, naming-conventions.

I hope this repository will generate discussion, exploration and thoughts on how to create a consistent **unified** approach to CSS development.

The pre-processor I will be using in this repository is SASS, I found Stylus & [Sass](http://sass-lang.com/) to be the most natural for me.

### Current Issues

Frameworks often come with a tonne of class's that are not used, this comes at a cost the end user with an increased bandwidth. We need to find a balance between a class for everything and a scaffolding of useful class's.


## Noteworthy frameworks & Reading Material

I have used, played with, studied, loved, hated & found inspiration, from using the following frameworks. They are all worthy of your time to study and trial in atleast one project, you will learn a great deal from actually using each one in an application.

* [BEM](https://en.bem.info/method/)
* [Bootstrap](http://getbootstrap.com)
* [SuitCSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [Foundation](http://http://foundation.zurb.com)
* [ITCSS](http://itcss.io/)
* [Pure](https://github.com/yahoo/pure/)
* [Semantic-ui](http://semantic-ui.com)


## 1. File Structure
The files must be imported in the correct order to maintain the correct inheritance of styles.
All files should be imported in a single .scss file, this will be the **only** file in your application that does not begin with _.

**Note:** Consider trialing the use of folders intead of dot seperated files, a project currently being worked on is beginning to get tough to find the files in the current format.

**Note:** Consider explicitly prefixing the files with a level number, this will help force the developer to consider what order the files will be imported in. I am trialing the use of 2 digits.

<pre>
.
├── init.scss
├── base
│   ├── _01.variables.scss
│   ├── _02.functions.scss
│   ├── _03.normalize.scss
│   ├── _04.global.scss
├── components
│   ├── _**.*.scss
</pre>

<pre>init.scss</pre>

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

## Thoughts

Explore class names in a similar manner to semantic-ui.
Explore use a seperator in html to break each class

[class*="float left"]
class="float left | bold font | hidden on small"
