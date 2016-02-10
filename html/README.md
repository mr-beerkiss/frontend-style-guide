# Photobox HTML styleguide

* A mostly stolen guide to HTML.  Info regarding templates coming soon...

## Table of Contents

  1.  [Document Type](#doctype)
  1.  [HTML Validity](#validity)
  1.  [Semantics](#semantics)
  1.  [Multimedia fallback](#media-fallback)
  1.  [Separation of Concerns](#separation-of-concerns)
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

- [3](#3) <a name="3"></a> Use HTML elements (sometimes incorrectly referred to as _tags_) according to their purpose.

For instance use `h[n]` elements for headings, `p` elements for pagagraphs, `a` elements for achors and so on.

This is important for accessibility, reuse and code efficiency.

```html
<!-- Bad -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Good -->
<a href="/recommendations">All recommendations</a>
```

**[⬆ back to top](#table-of-contents)**

## Multimedia fallbacks

- [4][#4] <a name="4"></a> Always offer alternative content to multimedia such as `<audio>`, `<video>`, `<img>` and `<canvas>` elements.  For `<img>` elements this means providing meaningful content to the `alt` attribute and providing transcripts, captions or descriptions for `<audio>`, `<video>` and `<canvas>` elements respectively.

```html
<!-- Bad -- >
<img src="mug.png">

<!-- Good --> 
<img src="mug.png" alt="Colourful mug">

<!-- Bad -->
<video width="320" height="240" controls>
  <source src="mugs.mp4" type="video/mp4">
</video>

<!-- Good -->
<video width="320" height="240" controls>
  <source src="mugs.mp4" type="video/mp4">
  <track label="English" kind="subtitles" srclang="en" src="captions/vtt/mugs-en.vtt" default>
</video>
```

Refer to [these MDN pages](https://developer.mozilla.org/en-US/Apps/Build/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) for more information.  

**[⬆ back to top](#table-of-contents)**

## Separation of concerns

- [5](#5) <a name="4"></a>  It is imperative to keep separate structure (markup), presentation (styling) and behaviour (scripting).  Also keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.  

Sepearating structure from presentation and behaviour is critical to improve maintainability and reuse.

`<style>` and `<script>` may be inlined for page load performance reasons but these should contain the absolute minimum CSS and JS needed to perform the initial page render.

```html
<!-- Bad -->
<!DOCTYPE html>
<style>
  .my-style {
    color: blue;
  }
</style>
<script>
  window.onload = function() {
    myAwesomeFunctionality();
  };
</script>
<h1 style="font-size: 1em; text-align: center;">HTML Sucks</h1>
<p class="my-style" style="font: Arial;">HTML is silly</p>

<!-- Good -->
<!DOCTYPE html>
<link rel="stylesheet" href="styles.css">
<h1 class="heading">HTML Sucks</h1>
<p class="my-paragraph">HTML is silly</p>
<script src="behaviour.js"></script>
```

## Entity References

- [6](#6) <a name="6"></a>  Do not use entity references (eg. `&mdash;`, `&requo;`, `&#x263a;` etc) since the same file encoding (UTF-8) should be used consistently between teams.  The only exceptions are for characters that have special meaning in html (eg. `<` and `& `) as well as control or "invisible" characters (eg. `&nbsp;`)

```html
<!-- Bad -->
The currency symbol for the Euro is &ldquo;&eur;&ldquo;.

<!-- Good -->
The currency symbol for the Euro is “€”.

**[⬆ back to top](#table-of-contents)**

## `type` Attributes

- [7](#7) <a name="7"></a> Omit `type` attributes for stylesheets and scripts, unless you are not using CSS for stylesheets and Javascript for scripts.  The types `text/css` and `text/javascript` are implied in HTML5 and you only need specify the type if you wish to use something else inside those tags.  

The `type` attribute can be safely ommited for older browsers.

```html
<!-- Bad -->
<link rel="stylesheet" href="site.css" type="text/css">

<!-- Good -->
<link rel="stylesheet" href="site.css">

<!-- Bad -->
<script src="behaviour.js" type="text/javascript"></script>

<!-- Good -->
<script src="behaviour.js"></script>
```

**[⬆ back to top](#table-of-contents)**

