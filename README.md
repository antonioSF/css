# CSS / Sass Style Guide

WSA Internal CSS Coding Standards Guide

> **Note**: The purpose of these guides are to provide coding standards and conventions for the majority of WSA projects. Some elements might not be required depending on the project specifications. It also assumes you have a basic or no knowledge of Front-End technologies and Responsive Web Design. It is meant to be an on-going collaboration project.


Other Style Guides

  - [HTML5](https://github.com/antonioSF/html)
  - [JavaScript](https://github.com/antonioSF)
  - [Environment / Scaffolding / Bundles / deployments](https://github.com/antonioSF)

## Table of Contents
1. [Terminology](#terminology)
	* Rule Declaration
	* Selectors
	* Properties
2. Basic Structure
	* Mobile first
3. Formating
4. Comments
5. Methodologies
	* BEM
	* OOCSS
6. Media Queries
7. Sass
	* Syntax
	* Ordering
	* Variables
	* Mixins
	* Nested selectors
8. [Best Practices](#best-practices)

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

* Avoid nesting with Sass - do no more than 3 levels deep of nesting if you have to.

* @extend should be avoided.

* Avoid @import.

* DRY up your stylesheets.

* Minify and concatenate your stylesheets.

* Validate your CSS.

* CSS tested on CSS Lint.

* Website passed the [WSA Checklist](http://wsa.pt/checklist/).

* Consider embedding critical CSS in the ```<head>``` for instant first render.

* Consider loading asynchronously non-critical CSS - use [loadCSS](https://github.com/filamentgroup/loadCSS/).


---

**[Back to top](#table-of-contents)**