# Photobox HTML styleguide

* A mostly stolen guide to HTML.  Info regarding templates coming soon...

## Table of Contents

  1.  [Document Type](#doctype)
  1.  [HTML Validity](#validity)
  1.  [Semantics](#semantics)
  1.  [Multimedia fallback](#media-fallback)
  1.  [Entity References](#entities)
  1.  [type Attributes](#type-atttributes)
  1.  [Void elements](#void-elements)
  1.  [HTML formatting](#formatting)
  1.  [Capitalisation](#capitalisation)
  1.  [Quotation Marks](#quotation)

## Document Type

- [1](#1) <a name="1"></a> Use HTML5, it is preferred for all HTML documents.
`!<DOCTYPE html>`.  It is recommended that the content-type header for HTML documents is set 
to `text/html`.  Do not use XHTML (`application/xhtml+xml`) as it lacks both browser and 
infrastructure support and offers less room for optimation than HTML.

**[⬆ back to top](#table-of-contents)**

## HTML Validity

- [2](#2) <a name="2"></a>  Always ensure your HTML documents are valid.  You can use the 
[W3C HTML validator](http://validator.w3.org/nu/) to test your HTML.

Using valid HTML is a measurable baseline quality attribute that contributes to learning about technical requirements and constraints, and that ensures proper HTML usage.

```html
<!-- Bad -->
<title>Test</title>
<article>This is a only a test.

<!-- Good -->
<!DOCTYPE html>
<meta charset="utf=8">
<title>Test</title>
<article>This is only a test.</article>
```

**[⬆ back to top](#table-of-contents)**

## Semantics

- [3](#3) <a name="3"></a> 