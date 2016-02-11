# Photobox CSS / Sass Styleguide

*A mostly reasonable approach to CSS and Sass*

## Table of Contents

  1. [Terminology](#terminology)
    1. [Rule Declaration](#rule-declaration)
    1. [Selectors](#selectors)
    1. [Properties](#properties)
  1. [CSS](#css)
    1. [Validity](#validity)
    1. [ID Selectors](#id-selectors)
    1. [Shorthand Properties](#shorthand-properties)
    1. [0 and Units](#0-and-units)
    1. [Leading 0s](#leading-0s)
    1. [Hexidecimal Notation](#hexidecimal-notation)
    1. [Declaration Order](#declaration-order)
    1. [Formatting](#formatting)
    1. [Quotation Marks](#quotation-marks)
    1. [Comments](#comments)
    1. [JavaScript hooks](#javascript-hooks)
  1. [Sass](#sass)
    1. [Syntax](#syntax)
    1. [Ordering](#ordering-of-property-declarations)
    1. [Mixins](#mixins)
    1. [Extend directive](#extend-directive)
    1. [Nested selectors](#nested-selectors)
  1. [OOCSS and BEM](#oocss-and-bem)
  1. [Parting Notes](#parting-notes)
    1. [Hacks](#hacks)
    1. [Consistency](#consistency)

## Terminology

### Rule declaration

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

**[⬆ back to top](#table-of-contents)**

### Selectors

In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:

```css
/* element selector */
html {
  
}

/* class selector */
.my-element-class {
  /* ... */
}

/* property selector */
[aria-hidden] {
  /* ... */
}
```

**[⬆ back to top](#table-of-contents)**

### Properties

Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
}
```

**[⬆ back to top](#table-of-contents)**

## CSS

### Validity

Always use valid CSS where possible.  Use tools such as the [W3C CSS validator](http://jigsaw.w3.org/css-validator/) to validate your CSS.

It is permitted have broken validation when working around [validator bugs](https://github.com/w3c/css-validator/issues), or when you require proprietary syntax.

Valid CSS ensures proper CSS usage and allows the ability to spot CSS that has no effect so that it may be removed.

**[⬆ back to top](#table-of-contents)**

### ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.

For more on this subject, read [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) on dealing with specificity.

**[⬆ back to top](#table-of-contents)**

### Shorthand Properties

CSS offers a variety of [shorthand](http://www.w3.org/TR/CSS21/about.html#shorthand) properties (like `font`) that should be used whenever possible, even in cases when only one value is set.

Shorthand properties are useful for code efficiency and understandability.  Additional properties are easily be added to the short-hand form.

```css
/* Bad */
font-family: Arial, sans-serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

/* Good */
font: 100%/1.6 Arial, sans-serif;
padding: 0 1em 2em;
```

**[⬆ back to top](#table-of-contents)**

### 0 and Units

Do not use units after `0` values.

```css
/* Bad */
margin: 0em;
padding: 0px;

/* Good */
margin: 0;
padding: 0;
```

**[⬆ back to top](#table-of-contents)**

### Leading 0s

Do not place a leading `0` in front of values or lengths between -1 and 1

```css
/* Bad */
font-size: 0.8em;
margin-left: -0.5em;

/* Good */
font-size: .8em;
margin-left: -.5em;
```

**[⬆ back to top](#table-of-contents)**

### Hexidecimal Notation

- Always write hexidecimal numbers in lower case
- Use 3 character notation where possible

```css
/* Bad */
color: #FEABCD;

/* Good */
color: #feabcd;

/* Bad */
color: #ffffff;

/* Good */
color: #fff
```

**[⬆ back to top](#table-of-contents)**

### Declaration order

Put your property declarations in alphabetical order. The exception is for properties which contain vendor-specific prefixes. These should be ordered according to the property to which they prefix, and then in alphabetical order of the prefixes (ie `-moz` comes before `-webkit`)  

This rule does not apply to Sass directives, which should be specified after the built-in CSS property types.  See Sass [Ordering](#ordering-of-property-declarations) for details

```css
/* Bad */
margin: 0 auto;
font: 1em bold;
color: green;
-webkit-boder-radius: 4px;
border-radius: 4px;
-moz-border-radius: 4px;

/* Good */
border-radius: 4px;
-moz-border-radius: 4px;
-webkit-border-radius: 4px;
color: green;
font: 1em bold;
margin: 0 auto;
```

**NOTE** Vendor prefixes should not be used in plain CSS.  Use a `@mixin` where possible or better yet; make use of an [`autoprefixer`](https://github.com/postcss/autoprefixer)

**[⬆ back to top](#table-of-contents)**

### Formatting

* Always use lowercase and dashes for class names.  Do not use CamelCase in your CSS.  Underscores are OK if you're using BEM (see [OOCSS and BEM](#oocss-and-bem) below).
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace `{` in rule declarations
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line
* Put blank lines between rule declarations
* Never write a rule on one line

```css

/* Bad */
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
.center { margin: 0 auto; padding: 0 }


/* Good */
```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}

.center {
  margin: 0 auto;
  padding: 0;
}
```

**[⬆ back to top](#table-of-contents)**

### Quotation Marks

Use single quotes (`''`) rather than double quotes (`""`) for attribute selectors and property values.  _Do not_ use quotation marks in URI values (even `url()`)

Exception: If you need to use the `@charset` rule, then use double quotation marks as [single quotation marks are not permitted](http://www.w3.org/TR/CSS21/syndata.html#charset).

```css
/* Bad */
background: url("//www.photobox.co.uk/images/logo.png");
font-family: "open sans", arial, sans-serif;

/* Good */
background: url(//www.photobox.co.uk/images/logo.png);
font-family: 'open sans', arial, sans-serif;
```

**NOTE** Remember that URIs should omit the protocol (`http:`, `https:`) where possible as specified in the [General guidelines](..)

**[⬆ back to top](#table-of-contents)**

### Comments

* Prefer line comments (`//` in Sass-land) to block comments.
* Prefer comments on their own line. Avoid end-of-line comments.
* Write detailed comments for code that isn't self-documenting:
  - Uses of z-index
  - Compatibility or browser-specific hacks

**[⬆ back to top](#table-of-contents)**

### JavaScript hooks

Avoid binding to the same class in both your CSS and JavaScript. Conflating the two often leads to, at a minimum, time wasted during refactoring when a developer must cross-reference each class they are changing, and at its worst, developers being afraid to make changes for fear of breaking functionality.

We recommend creating JavaScript-specific classes to bind to, prefixed with `.js-`:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

**[⬆ back to top](#table-of-contents)**

## Sass

### Syntax

* Use the `.scss` syntax, never the original `.sass` syntax
* Order your regular CSS and `@include` declarations logically (see below)

**[⬆ back to top](#table-of-contents)**

### Ordering of property declarations

The manner in which each subset of property declarations defined is ordered are subject to the [Declaration Order](#declaration-order) defined above.  Please ensure you follow this rule in combination with the specific ordering of Sass declarations (i.e [alphabetise!](https://www.youtube.com/watch?v=i0TyUOJfpQo))

1. Property declarations
  
    List all standard property declarations, anything that isn't an `@include` or a nested selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

    **[⬆ back to top](#table-of-contents)**

2. `@include` declarations

    Grouping `@include`s at the end makes it easier to read the entire selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

    **[⬆ back to top](#table-of-contents)**

3. Nested selectors

    Nested selectors, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.  Make sure you understand the rules relating to [Nested selectors](#nested-selectors).

    ```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);

      .icon {
        margin-right: 10px;
      }
    }
    ```

    **TIP** You can use the `&` character to [reference the parent](http://thesassway.com/intermediate/referencing-parent-selectors-using-ampersand) when nesting.  You should never to do this if you write your Sass well.  But it is worth knowing, even for purely academic purposes.

    **[⬆ back to top](#table-of-contents)**

### Mixins

Mixins should be used to [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) up your code, add clarity, or abstract complexity--in much the same way as well-named functions. Mixins that accept no arguments can be useful for this, but note that if you are not compressing your payload (e.g. gzip), this may contribute to unnecessary code duplication in the resulting styles. 

> Note at Photobox we _do_ gzip our text payloads.

**[⬆ back to top](#table-of-contents)**

### Extend directive

`@extend` should be avoided because it has unintuitive and potentially dangerous behavior, especially when used with nested selectors. Even extending top-level placeholder selectors can cause problems if the order of selectors ends up changing later (e.g. if they are in other files and the order the files are loaded shifts). Gzipping should handle most of the savings you would have gained by using `@extend`, and you can DRY up your stylesheets nicely with mixins.

**[⬆ back to top](#table-of-contents)**

### Nested selectors

**Do not nest selectors more than three levels deep!**

```scss
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```

When selectors become this long, you're likely writing CSS that is:

* Strongly coupled to the HTML (fragile) *—OR—*
* Overly specific (powerful) *—OR—*
* Not reusable

Again: **never nest ID selectors!**

If you must use an ID selector in the first place (and you should really try not to), they should never be nested. If you find yourself doing this, you need to revisit your markup, or figure out why such strong specificity is needed. If you are writing well formed HTML and CSS, you should **never** need to do this.

**[⬆ back to top](#table-of-contents)**

### OOCSS and BEM

> This section is under review.  Please avoid using OOCSS and BEM for now.
> This section is inlcuded for reference only.

We encourage some combination of OOCSS and BEM for these reasons:

  * It helps create clear, strict relationships between CSS and HTML
  * It helps us create reusable, composable components
  * It allows for less nesting and lower specificity
  * It helps in building scalable stylesheets

**OOCSS**, or “Object Oriented CSS”, is an approach for writing CSS that encourages you to think about your stylesheets as a collection of “objects”: reusuable, repeatable snippets that can be used independently throughout a website.

  * Nicole Sullivan's [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine's [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**BEM**, or “Block-Element-Modifier”, is a _naming convention_ for classes in HTML and CSS. It was originally developed by Yandex with large codebases and scalability in mind, and can serve as a solid set of guidelines for implementing OOCSS.

  * CSS Trick's [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts' [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

**Example**

```html
<article class="listing-card listing-card--featured">

  <h1 class="listing-card__title">Adorable 2BR in the sunny Mission</h1>

  <div class="listing-card__content">
    <p>Vestibulum id ligula porta felis euismod semper.</p>
  </div>

</article>
```

```css
.listing-card { }
.listing-card--featured { }
.listing-card__title { }
.listing-card__content { }
```

  * `.listing-card` is the “block” and represents the higher-level component
  * `.listing-card__title` is an “element” and represents a descendant of `.listing-card` that helps compose the block as a whole.
  * `.listing-card--featured` is a “modifier” and represents a different state or variation on the `.listing-card` block.

**[⬆ back to top](#table-of-contents)**

## Parting Notes

### Hacks

Avoid using hacks where possible and only resort to one when and your peers have run out of all better ideas.  When you introduce a hack, you set a precedent that makes it acceptable for other people to use hacks to solve problems.  

If you must, make clear in the code comments why this hack was used and what could potentially be done in future to remove the hack.

This is particularly important to instances of `position: absolute` and over use of `z-index`.

**[⬆ back to top](#table-of-contents)**

### Consistency

Be _consistent_.  When you're working on code that you didn't write, take some time to look around and determine the style of the code and adapt the changes you are making to reflect the overall style.  While it is important that these guidelines are followed for _new_ code, there is still older code to maintain and in these instances it is important not to deviate from the code styles that may already be defined in these older bits of code.  Do not refactor unless you have been explicity told to do so.

**[⬆ back to top](#table-of-contents)**
