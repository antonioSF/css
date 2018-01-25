# CSS / Sass Guide

WSA Internal CSS Guide

> **Note**: The purpose of these guides are to provide coding standards and conventions for the majority of WSA projects. Some elements might not be required depending on the project specifications. It also assumes you have a basic or no knowledge of Front-End technologies and Responsive Web Design. It is meant to be an on-going collaboration project.


Other Guides

  - [HTML5](https://github.com/antonioSF/html)
  - [JavaScript](https://github.com/antonioSF)
  - [Environment / Scaffolding / Bundles / deployments](https://github.com/antonioSF)

## Table of Contents
1. [Introduction](#introduction)
2. [Terminology](#terminology)
    * [Rule Declaration](#rule-declaration)
    * [Selectors](#selectors)
    * [Naming Conventions](#naming-conventions)
    * [Pseudo-classes](#pseudo-classes)
    * [Pseudo-elements](#pseudo-elements)
    * [Properties](#properties)
3. [Formating](#formating)
4. [Comments](#comments)
5. [Architecture](#architecture)
    * [The Cascade & Principles](#the-cascade--principles)
    * [Mobile first & Media Queries](#mobile-first--media-queries)
6. [Layout](#layout)
    * [Positioning](#positioning)
    * [Floats](#floats)
    * [Flexbox](#flexbox)
    * [Grid](#grid)
7. [Methodologies](#methodologies)
    * [BEM](#bem)
8. [Sass](#sass)
    * [Syntax](#syntax)
    * [Ordering](#ordering)
    * [Variables](#variables)
    * [Mixins](#mixins)
    * [Nested selectors](#nested-selectors)
9. Frameworks
10. [Best Practices](#best-practices)

## Introduction
If HTML is for content and presentation mainly, CSS (Cascading Style Sheets) is used to style and design that content. When a Web browser displays a document, it first loads the HTML, parses it and creates a DOM (Document Object Model) from it. Only then parses the CSS. 
There are three different ways to apply CSS to an HTML document:

* **External Stylesheet**: An external file usually referenced by a ```<link>``` in the ```<head>``` of the HTML Document.
```html

<head>
    <link rel="stylesheet" href="/path/to/styles/main.css">
</head>
```
> **Note**: This method is the one you should use for a variety of reasons (separation of concerns, consistency, scalable, styles for multiple documents, ...).

* **Internal Stylesheet**: When you place your CSS inside a ```<style>``` element in the ```<head>```.
```html

<head>
    <style>
        .example {
            color: red;
        }
    </style>
</head>
```
> **Note**: This method should be avoided and only considered if there's a valid reason for it.

* **Inline Styles**: CSS declarations that affect one element only, contained within a style attribute.

```html

<p style="color:red;">Example</p>
```
> **Note**: This method must be avoided and only considered if there's a valid reason for it (CSS in JS, ...).

---

**[Back to top](#table-of-contents)**

## Terminology
CSS is a declarative language, which makes its syntax fairly easy and straight forward to understand.
At its most basic level, CSS consists of **rule declarations - rulesets**.

#### Rule Declaration
A Rule declaration or **ruleset** is the name given to a **selector** (or a group of selectors) and the corresponding declaration block. A declaration block is formed by a **property** and a **value** pair.

```html

[selector] {
 [property]: [value];
}
```

#### Selectors
Are patterns that reference some elements in the DOM tree. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. 

```css

header {
    /* ... */
}

.my-class {
    /* ... */
}

[aria-hidden] {
    /* ... */
}
```

That being said, you should also follow some rules:

* Do not use ID's.
* Avoid referencing [data-*].
* Prefer classes.
* Name your HTML classes with meaning and reason. Their intent must be clear.
 ```html

<nav class="menu">
  ...
</nav>
```

#### Naming Conventions
Naming conventions in CSS are hugely useful in making your code more strict, more transparent, and more informative. A good naming convention will tell you and your team:

* what type of thing a class does;
* where a class can be used;
* what (else) a class might be related to.

Unless you have a valid reason for it, strings should be delimited with a hyphen (-):

 ```html

<nav class="main-menu">
  ...
</nav>
```

```css

.main-menu { }
```

Avoid camel case and underscores:

 ```html

<nav class="mainMenu">
  ...
</nav>
```
```css

.mainMenu { }
```

 ```html

<nav class="main_menu">
  ...
</nav>
```
```css

.main_menu { }
```
For a more detailed and complex naming approach, read about the use of [BEM Methodology](#bem).

#### Pseudo-classes
A pseudo-class  **specifies a special state** of the selected element(s). For example, :hover can be used to change a button's color when the user hovers over it.

```html

<button class="btn">Click me</button>
```

```css

.btn {
  [property]: [value];
}

.btn:hover {
  [property]: [other value];
}
```
A pseudo-class is always prefixed by (:)  ```:hover```, ```:active```, ```:focus```,  ```valid```,  etc.

You can view a full list of pseudo-classes [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes).

#### Pseudo-elements
A pseudo-element lets you style a specific part of the selected element(s). For example, ::after can be used to add cosmetic content to an element.

```html

<button class="btn">Click me</button>
```

```css

.btn::after {
  [property]: [value];
}
```

Although, since CSS2, browsers accept one colon (:) ```:pseudo-element```, you should use CSS3 two colons (::) ```::pseudo-element``` to avoid confusion with pseudo-classes.

You can view a full list of pseudo-elements [here](https://developer.mozilla.org/en-US/docs/Web/CSS/pseudo-elements).

#### Properties
Are human-readable identifiers that indicate which stylistic features (e.g. font, width, background color) you want to change. Properties are key-value pairs, and a rule declaration can contain one or more property declarations.

```css

/* selector */ {
    display: block;
    background-color: green;
    color: red;
}
```

There are so many CSS properties that it can be overwhelming. 
You can follow these lists for reference:
* [Properties | CSS-Tricks](https://css-tricks.com/almanac/properties/)
* [CSS Properties Index · Jens Oliver Meiert](https://meiert.com/en/indices/css-properties/)
* [CSS reference - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

##### References
> * [Selectors - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)
> * [CSS Guidelines (2.2.5) - Selectors](https://cssguidelin.es/#css-selectors)
> * [CSS Guidelines (2.2.5) - Naming Conventions](https://cssguidelin.es/#naming-conventions)
> * [Naming UI components in OOCSS](https://csswizardry.com/2014/03/naming-ui-components-in-oocss/)
> * [Pseudo-classes - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
> * [Pseudo-elements - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/pseudo-elements)
> * [CSS reference - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)
> * [Properties | CSS-Tricks](https://css-tricks.com/almanac/properties/)
> * [CSS Properties Index · Jens Oliver Meiert](https://meiert.com/en/indices/css-properties/)

---

**[Back to top](#table-of-contents)**

## Formating
Having a standard way of writing CSS provides effiency across development within a team.
**Code that looks clean feels clean**.

* Use 2 spaces for indentation.
* Do not use ID selectors.
```css

/* bad */
#foo {
    display: block;
}

/* good */
.foo {
    display: block;
}
```
* When using multiple selectors in a rule declaration, give each selector its own line.
```css

/* bad */
.foo, .bar {
    display: block;
}

/* good */
.foo,
.bar {
    display: block;
}
```

* Properties and values on the same line;
* Each declaration on its own new line;
```css

/* bad */
.bar{display: block;background-color: green;}

/* good */
.foo {
    display: block;
    background-color: green;
}
```

* A trailing semi-colon (;) on our last declaration.
* Put a space before the opening brace { in rule declarations
* Put closing braces } of rule declarations on a new line.
* In properties, put a space after, but not before, the : character.
```css

/* bad */
#foo, .bar{
    display:block;background-color:green;
    color:red;}

/* good */
.foo,
.bar {
    display: block;
    background-color: green;
    color: red;
}
```
* Put blank lines between rule declarations.
```css

/* bad */
.foo {
    display: block;
}
.bar {
    background-color: green;
}

/* good */
.foo {
    display: block;
}

.bar {
    background-color: green;
}
```
* Use dashes over camelCasing in class names.
```css

/* bad */
.fooBar {
    display: block;
}

/* good */
.foo-bar {
    display: block;
}
```

---

**[Back to top](#table-of-contents)**

## Comments
A CSS comment is used to add explanatory notes to the code.

* Block comments should differ from section comments. Make them distinctive.

* Begin every new major section of a CSS project with a title.
```css


/*------------------------------------*\
    #SECTION-TITLE
\*------------------------------------*/

.selector { }




/*------------------------------------*\
    #ANOTHER-SECTION-TITLE
\*------------------------------------*/

.another-selector { }
```
* Avoid end-of-line comments.

* Prefer line comments to block comments.
```css

/*
 * Long comments should not be larger than 80 characters.
 * They should describe, in detail, the CSS that follows.
 */
 .selector { }

//comment in Sass
.another-selector { }

/* Comment */
.foo { }
```

---

**[Back to top](#table-of-contents)**

## Architecture

#### The Cascade & Principles
CSS is an acronym of Cascading Style Sheets, which indicates that the notion of the cascade is important.
It indicates that the order of CSS rules matter, but it's more complex than that. What selectors win out in the cascade depends on three factors from top to bottom:

* Source order

* Specificity

* Importance

```html


<button class="btn-positive">Aprove action</button>

...

<button class="btn-negative">Cancel action</button>
```

```css

.btn-positive {
    width: 100px;
    height: 60px;
    padding: 10px;
    text-align: center;
    color: white;
    background-color: green !important;
}


.btn-negative {
    width: 100px;
    height: 60px;
    padding: 10px;
    text-align: center;
    color: white;
    background-color: red;
}
```
In the above example, although source order matters, due to the ```!important``` declaration, it will overide the ```.btn-negative```selector down the line. This is error prone and should be avoided.

You should favour source order. To achieve this, keep your declarations short and generic. Avoid specificity early on. Consider creating utility classes like ```.u-text-right``` if you must do very temporary important or implementation specific changes. 

Let's try to make it better, applying some CSS principles:

```html


<button class="btn btn--positive">Aprove action</button>

...

<button class="btn btn--negative">Cancel action</button>
```

```css

.btn {
    width: 100px;
    height: 60px;
    padding: 10px;
    text-align: center;
}

.btn--positive {
    color: white;
    background-color: green;
}


.btn--negative {
    color: white;
    background-color: red;
}
````
In the above example, we've **abstracted** the ```.btn``` properties keeping it generic. We've also used **specificity** and **extended** new features instead of modifying the base class ```.btn```. We've built the skeleton for our buttons and later extended them with theming/skin providing them reason and semantic (positive/negative). 

With this, we've already introduced some CSS principles like: 
* **Object-Oriented CSS (OOCSS)**. 
* **Single Responsibility Principle**. 
* **The Open/Closed Principle**.
* **DRY -  Don't Repeat Yourself**.


##### References
> * [Cascade and inheritance - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)
> * [CSpecificity - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
> * [CSS Guidelines (2.2.5)](https://cssguidelin.es/#architectural-principles)

---

**[Back to top](#table-of-contents)**

#### Mobile-first & Media Queries
A mobile-first approach while architecting your CSS has enormous benefits to development.
While it may be related to Responsive Web Design, mobile-first approach also allow us to better implement some best practices:

* **DRY code**.
* **Scalability**.
* **Maintainability**.
* **Light-weight**.

Using this approach and following CSS principles, developers can build powerful designs while keeping the source code **clean and lean**.

Below is an example of a structure using the mobile-first approach. From top to bottom: generic to specific, ending with Media Queries. Using Media Queries we can target different widths/heights/resolutions/print/etc.

```css

/*------------------------------------*\
    #RESETS
\*------------------------------------*/

html { }

....

/*------------------------------------*\
    #LAYOUT
\*------------------------------------*/

.layout { }

....

/*------------------------------------*\
    #SECTION
\*------------------------------------*/

.some-section { }

...

/*------------------------------------*\
    #BUTTON
\*------------------------------------*/

.btn { }

/* some modifier */
.btn--submit { }

...

/*------------------------------------*\
    #MEDIA QUERIES
\*------------------------------------*/

/* specific styles */

```
> **Note**: Following this structure, your code will be a lot cleaner and error free. 
Since all CSS that isn't inside a media query will get parsed by your mobile-devices no-matter what, target the smallest devices and build from there.

##### Media Queries
Media queries are a key component of Responsive Web Design, which make it possible for CSS to adapt based on various parameters or device characteristics. A media query can apply different styles depending on a device's general type (such as **print vs. screen**), specific characteristics (such as the **width of the browser viewport**, device in **portrait or landscape mode**, or environment (such as **ambient light conditions**).

###### Syntax
The **@media** at-rule is used to conditionally apply styles to a document and it is composed of one or more media queries, each of which consists of an optional **media type** and any number of **media feature** expressions. Multiple queries can be combined in various ways by using **logical operators**, and are case-insensitive.

```css

@media [media type] {
  
}

@media [media feature] {
  
}

@media [logical operator] [media type] [logical operator] [media feature] {
  
}
```

Media types:
* **all**: Suitable for all devices.
* **print**: Intended for paged material and for documents viewed on screen in print preview mode.
* **screen**: Intended primarily for color computer screens.
* **speech**: Intended for speech synthesizers.

Media features:
* **width**: Width of the viewport.
* **height**: Height of the viewport.
* **aspect-ratio**: Width-to-height aspect ratio of the viewport.
* **orientation**: Orientation of the viewport.
* **resolution**: Pixel density of the output device.
* ... you can view all of the media features available [here](https://developer.mozilla.org/en-US/docs/Web/CSS/@media#Media_features)

Logical Operators:
* **and**: Used for combining multiple media features together into a single media query.
* **not**: Used to negate a media query, returning true if the query would otherwise return false.
* **only**: Used to apply a style only if an entire query matches.

```css

/* target only screen media where browser width is bigger than 640px */
@media only screen and (min-width: 640px) {
  .some-selector { }
}

/* target media where browser width is bigger than 1024px and smaller than 1440px */
@media only screen and (min-width: 1024px) and (max-width: 1440px) {
  .some-selector { }
}

...

/* target only print media */
@media print {
  .some-selector { }
}
```

> **Note**: Most of the times, you should follow the pattern of mobile-first using the ```min-width: ``` feature when targeting screen media types. At the most basic you'll target medium, large and extra-large devices. Favor media features based on your content and not devices. 
However, be careful not to bloat your code with the overuse of media queries. If you notice a lot of media queries then something must be wrong with your code.


##### References
> * [Media queries - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries)
> * [Using media queries - CSS | MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
> * [@media - CSS | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media)
> * [Mobile-first CSS – mrmrs – Medium](https://medium.com/@mrmrs_/mobile-first-css-48bc4cc3f60f)
> * [How To Write Mobile-first CSS | Zell Liew](https://zellwk.com/blog/how-to-write-mobile-first-css/)

---

**[Back to top](#table-of-contents)**

## Layout

---

**[Back to top](#table-of-contents)**

---

## Methodologies
CSS methodologies help developers **maintain and scale** the front-end as a set of small, isolated modules. Rather than as one massive lump of indivisible code. [SMACSS](https://smacss.com/) and [BEM](http://getbem.com/) are two of the most well known options.
We'll focus on the later one - BEM - since it encapsulates code, which is crucial in today's Web Applications  context.


#### BEM
BEM - **Block Element Modifier** - started as a set of guidelines created by developers working at Yandex.
BEM splits components classes into three groups:

* **Block**: Root of the component;
* **Element**: Element that depends upon the block;
* **Modifier**: Changes the style of the block based on appearance, behavior or state.

Syntax:
```html

<div class="[block block--modifier]">
  <div class="[block__element block__element--modifier]">
    ...
  </div>

  <div class="[block__element]">
    ...
  </div>
</div>
```

```css

[block] {
  ...
}

[block__element] {
  ...
}

[block__element--modifier] {
  ...
}
```

* Block name should be semantic and expressive.
* Block strings are delimited with only one regular dash.
* Elements are delimited with two (2) underscores (__);
* Modifiers are delimited by two (2) hyphens (--).
* JavaScript specific classes/ID's are prefixed by js- (e.g. ```js-menu```).

```html

<nav class="menu menu--visible js-menu">
  <ul class="menu__list">
    <li class="menu__item menu__item--active">
      ...
    </li>
    <li class="menu__item">
      <a class="menu__link">Click me</a>
    </li>
  </ul>
</nav>
```
```css

/* block */
.menu { }

/* elements */
.menu__list { }

.menu__item { }

.menu__link { }

/* modifiers */
.menu--visible { 
  display: block;
}

.menu--hidden { 
  display: none;
}

.menu__item--active { }
```

> **Note**: You may disagree or not feel confortable about these usage. If that's the case, talk with the team, expose your obstacles and together find a mutual concession. These methodologies and naming conventions were created to help developers. They may be customized to the flavour of the team. The important note is to keep it clean, consistent and logical.

##### References
> * [BEM — Block Element Modifier](http://getbem.com/)
> * [BEM](https://en.bem.info/)
> * [BEM 101 | CSS-Tricks](https://css-tricks.com/bem-101/)
> * [CSS Guidelines (2.2.5) - BEM like naming](https://cssguidelin.es/#bem-like-naming)
> * [MindBEMding - Harry Roberts](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
> * [About HTML semantics and front-end architecture – Nicolas Gallagher](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
> * [BEM and SMACSS: Advice From Developers Who've Been There — SitePoint](https://www.sitepoint.com/bem-smacss-advice-from-developers/)
> * [SMACSS - Scalable and Modular Architecture for CSS](https://smacss.com/)

---

**[Back to top](#table-of-contents)**

## Sass
A **CSS preprocessor** helps you write maintainable, future-proof code and it will seriously reduce the amount of CSS you have to write. There are many CSS preprocessors to choose from, however most CSS preprocessors will add some features that don't exist in pure CSS. **Sass** lets you use features like variables, nesting, mixins, inheritance, etc.

#### Syntax
* Use the .scss syntax.
* Indent with the same two (2) spaces, and also leave a blank line before and after the nested ruleset.

#### Ordering
* Partial files start with an underscore (e.g. ```_partial.scss```).
* Partial files are used with the @import directive and comes first by order.
```scss

// here we are importing _reset.scss and _base.scss
@import 'reset';
@import 'base';

.content {
  ...
}
```
* Keep variables and mixins at the top of your files.
```scss

$font-stack: "Roboto", "Helvetica Neue", Helvetica, Arial, sans-serif;
$primary-color: #333;

....

.some-element {
  font-family: $font-stack;
  font-size: 1rem;
  color: $primary-color;
}
```
* Standard declarations goes first, then @includes and only then, if necessary, nested selectors.
```scss

.some-element {
  display: block;
  position: relative;
  ...
  @include border-radius(10px);
}
```
* Nested selectors. If necessary, go last and nothing comes after them.

```scss

.menu {
  display: block;
  position: relative;
  @include border-radius(10px);

  .item {
    color: white;
  }
}
```
#### Variables
Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the ```$``` symbol to make something a variable.

* Again, keep variables at the top of your files.
* Use dash-cased variable names over camelCased or snake_cased.
```scss

//don't
$primaryColor: #333;
$primary_color: #333;

//do
$primary-color: #333;
```

#### Mixins
A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can pass in values to make your mixin more flexible. After you create your mixin, you can then use it as a CSS declaration starting with ```@include``` followed by the name of the mixin.

* Again, keep mixins at the top of your files.
```scss

@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

...


.some-element {
  display: block;
  position: relative;
  @include border-radius(2px);
}
```
> **Note**: Mixins should be used to DRY up your code, add clarity, or abstract complexity.


#### Nested selectors
Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML.
* Avoid Nesting due to specificity.
* Do not nest selectors more than three levels deep.
```scss

nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;

    li {
      display: inline-block;

      //stop nesting
    }
  }
}
```

> **Note**: As a rule, if a selector will work without it being nested then do not nest it.

> * [Sass: Syntactically Awesome Style Sheets](http://sass-lang.com/)
> * [6 Current Options for CSS Preprocessors — SitePoint](https://www.sitepoint.com/6-current-options-css-preprocessors/)
> * [CSS Guidelines (2.2.5) - Misconceptions](https://cssguidelin.es/#misconceptions)
> * [CSS preprocessor - Glossary | MDN](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor)

---

**[Back to top](#table-of-contents)**

## Frameworks

---

**[Back to top](#table-of-contents)**

## Best Practices

* Split your CSS across multiple files.

* Document your code - CSS needs more comments.

* Be semantic with your selectors.

* Do not use ID selectors.

* **Avoid Shorthand Syntax** when affecting properties you don't need to modify.

* You should only ever **do as little as you need** to do and nothing more.

* Keep your CSS Declarations short.

* Use a preprocessor - in this case, use Sass.

* Use an **autoprefixer**.

* Provide a consistent and bug-free baseline to every browser (use Normalize.css, sanitize.css, ...).

* Avoid nesting with Sass - do no more than 3 levels deep of nesting, if you have to.

* @extend should be avoided.

* Avoid @import.

* Only use !important proactively, not reactively.

* DRY up your stylesheets.

* Duplication is better than the wrong abstraction.

* Minify and concatenate your stylesheets.

* Validate your CSS.

* CSS tested on CSS Lint.

* Website passed the [WSA Checklist](http://wsa.pt/checklist/).

* Consider embedding critical CSS in the ```<head>``` for instant first render.

* Consider loading asynchronously non-critical CSS - use [loadCSS](https://github.com/filamentgroup/loadCSS/).


---

**[Back to top](#table-of-contents)**