# CSS / Sass Style Guide

WSA Internal CSS Coding Standards Guide

> **Note**: The purpose of these guides are to provide coding standards and conventions for the majority of WSA projects. Some elements might not be required depending on the project specifications. It also assumes you have a basic or no knowledge of Front-End technologies and Responsive Web Design. It is meant to be an on-going collaboration project.


Other Style Guides

  - [HTML5](https://github.com/antonioSF/html)
  - [JavaScript](https://github.com/antonioSF)
  - [Environment / Scaffolding / Bundles / deployments](https://github.com/antonioSF)

## Table of Contents
1. [Introduction](#introduction)
2. [Terminology](#terminology)
	* [Rule Declaration](#rule-declaration)
	* [Selectors](#selectors)
	* [Properties](#properties)
3. [Formating](#formating)
4. [Comments](#comments)
5. [Structure](#structure)
  * BEM
6. Media Queries
7. Methodologies
	* BEM
	* OOCSS
8. Sass
	* Syntax
	* Ordering
	* Variables
	* Mixins
	* Nested selectors
9. Frameworks
10. [Best Practices](#best-practices)
8. Sass
  * Syntax
10. test
  * test

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
> **Note**: This method must not be used.

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
#### Properties
Are human-readable identifiers that indicate which stylistic features (e.g. font, width, background color) you want to change. Properties are key-value pairs, and a rule declaration can contain one or more property declarations.

```css

/* selector */ {
  display: block;
  background-color: green;
  color: red;
}
```

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

## Structure

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