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
	* Rule Declaration
	* Selectors
	* Properties
3. Basic Structure
	* Mobile first
4. Formating
5. Comments
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

## Introduction
If HTML is for content and presentation mainly, CSS (Cascading Style Sheets) is used to style and design that content. When a Web browser displays a document, it first loads the HTML, parses it and creates a DOM (Document Object Model) from it. Only then parses the CSS. 
There are three different ways to apply CSS to an HTML document

* **External Stylesheet**: An external file usually referenced by a ```<link>``` in the ```<head>``` of the HTML Document.
```html

<head>
	<link rel="stylesheet" href="/path/to/styles/main.css">
</head>
```
> **Note**: This method is arguably the best and the one you should use.

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


```html

<head>
	<style>
	  p {
	  	color: red;
	  }
	</style>
</head>
```
---

**[Back to top](#table-of-contents)**

## Terminology

---

**[Back to top](#table-of-contents)**

## Best Practices

* Split your CSS across multiple files.

* Document your code - CSS needs more comments.

* Be semantic with your selectors.

* Do not use ID selectors.

* **Avoid Shorthand Syntax** when affecting properties you don't need to modify.

* You should only ever **do as little as you need** to do and nothing more.

* Use a preprocessor - in this case, use Sass.

* Use an **autoprefixer**.

* Provide a consistent and bug-free baseline to every browser (use Normalize.css, sanitize.css, ...).

* Keep your CSS Declarations short.

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