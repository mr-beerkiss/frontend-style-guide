# Photobox HTML styleguide

* A mostly stolen guide to HTML.  Info regarding templates coming soon...

## Table of Contents

  1.  [Document Type](#document-type)
  1.  [HTML Validity](#html-validity)
  1.  [Semantics](#semantics)
  1.  [Multimedia fallback](#multimedia-fallbacks)
  1.  [Separation of Concerns](#separation-of-concerns)
  1.  [Entity References](#entity-references)
  1.  [type Attributes](#type-attributes)
  1.  [Void elements](#void-elements)
  1.  [HTML formatting](#html-formatting)
  1.  [Capitalisation](#capitalisation)
  1.  [Quotation Marks](#quotation-marks)

## Document Type

Use HTML5 (`<!DOCTYPE html>`), it is preferred for all HTML documents.  It is recommended that the 
content-type header for HTML documents is set to `text/html`.  Do not use XHTML 
(`application/xhtml+xml`) as it lacks both browser and infrastructure support and offers less 
room for optimation than HTML.

**[⬆ back to top](#table-of-contents)**

## HTML Validity

Always ensure your HTML documents are valid.  You can use the 
[W3C HTML validator](http://validator.w3.org/nu/) to test your HTML.

Using valid HTML is a measurable baseline quality attribute that contributes to learning about 
technical requirements and constraints, and that ensures proper HTML usage.

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

Use HTML elements (sometimes incorrectly referred to as _tags_) according to their 
[purpose](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document).

For instance use `<h1>` elements for page headings, `<p>` elements for paragraphs, `<a>` elements 
for achors and so on.

This is critical for accessibility, reuse and code efficiency.

```html
<!-- Bad -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Good -->
<a href="/recommendations">All recommendations</a>
```

**[⬆ back to top](#table-of-contents)**

## Multimedia fallbacks

Always offer alternative content to multimedia such as `<audio>`, 
`<video>`, `<img>` and `<canvas>` elements.  For `<img>` elements provide meaningful content to the
`alt` attribute; provide [transcripts or captions](https://developer.mozilla.org/en-US/Apps/Build/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) for `<audio>` and `<video>` elements; and 
provide fallback content for the `<canvas>` element.

```html
<!-- Bad -->
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

<!-- Bad -->
<canvas width="640" height="360"></canvas>

<!-- Good -->
<canvas width="640" height="360">
  <img src="cavnaserror.png" alt="Your browser does not support the canvas element">
</canvas>
```

**[⬆ back to top](#table-of-contents)**

## Separation of concerns

It is imperative to keep separate structure (markup), presentation (styling) and behaviour (scripting).  Also keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.  

Sepearating structure from presentation and behaviour is critical to improve maintainability and reuse.

`<style>` and `<script>` may be inlined for page load performance reasons, but these should only 
contain the absolute minimum CSS and JS needed to [perform the initial page render](https://developers.google.com/speed/docs/insights/PrioritizeVisibleContent).

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

**[⬆ back to top](#table-of-contents)**

## Entity References

Do not use entity references (eg. `&mdash;`, `&requo;`, `&#x263a;` etc) since the same file 
encoding should be used consistently between teams.  The only exceptions are for characters that 
have special meaning in html (eg. `<` and `& `) as well as control or "invisible" characters 
(eg. `&nbsp;`).

```html
<!-- Bad -->
The currency symbol for the Euro is &ldquo;&eur;&ldquo;.

<!-- Good -->
The currency symbol for the Euro is “€”.
```
**[⬆ back to top](#table-of-contents)**

## `type` Attributes

Omit `type` attributes for stylesheets and scripts, unless you are not using CSS for stylesheets and Javascript for scripts.  The types `text/css` and `text/javascript` are implied in HTML5 and you only need specify the type if you wish to use something else inside those tags.  

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

## Void Elements

Do not void close elements.

```html
<!-- Bad -->
<br/>

<!-- Good -->
<br>
```

**[⬆ back to top](#table-of-contents)**

## HTML formatting

Put every block, list or table element on a new line and indent as such for every child element.  In-line elements should _not_ be placed on a new line, even for readibility purposes since new lines have special meaning in HTML.

These rules _should_ be applied regardless of any styling that may change the role of an element via the `display` property.

The only exception is to put `<li>` elements onto one line if you encounter issues with whitespace around a list.

```html
<!-- Bad -->
<div class="outer"><div class="inner">
<span>
  Some text
  <em>emphasied text</em>
</span>
</div></div>

<!-- Good -->
<div class="outer">
  <div class="inner"><span>Some text <em>emphasied text</em></span></div>
</div>

<!-- Bad -->
<table><thead>
  <tr><th scope="col">Date</th><th scope="col">Amount</th></tr></thead>
  <tbody>
    <tr><td>12/06/2025</td><td>£5.00</td></tr>
  </tbody>
</table>

<!-- Good -->
<table>
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>12/06/2025</td>
      <td>£5.00</td>
    </tr>
  </tbody>
</table>

<!-- This is bad, but acceptable if you are facing issues with white space -->
<ul><li>Apples</li><li>Bananas</li><li>Oranges</li></ul>

<!-- Better -->
<ul>
  <li>Apples</li>
  <li>Bananas</li>
  <li>Oranges</li>
</ul>
```

**[⬆ back to top](#table-of-contents)**

# Capitalisation

All html code _must_ be lowercase.  This applies to element names, attributes, attribute values 
(unless `text/CDATA`).  Obviously this doesn't apply to the content of elements or string values.

```html
<!--Bad -->
<A Class="link" HREF="/">Home</A>

<!-- Good -->
<a class="link" href="/">Home</a>
```

**[⬆ back to top](#table-of-contents)**

# Quotation Marks

- [10](10) <a href="10"></a> Always use double (`""`) rather than single quotes for HTML attributes (`''`)

```html
<!-- Bad -->
<a class='link' href='/'>Home</a>

<!-- Good -->
<a class="link" href="/">Home</a>
```

**[⬆ back to top](#table-of-contents)**



