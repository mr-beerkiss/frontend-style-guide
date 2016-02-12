# Photobox front-end code style guides

Mostly reasonable.  Mostly stolen from AirBnB and Google.  Completely enforced.

## Guides

- [Javascript](javascript/)
- [CSS and Sass](css/)
- [HTML](html/)

## Table of Contents

1. [Protocol](#protocol)
1. [Encoding](#indentation)
1. [Whitespace](#whitespace)
  1.  [Indentation](#indentation)
  1.  [Trailing Whitespace](#trailing-whitespace)
  1.  [Newlines](#newlines)
1. [Line lengths](#line-lengths)
1. [Action Items](#actionitems)
  1.  [TODO](#todo)
  1.  [FIXME](#fixme§)
1. [.editorconfig](#.editorconfig)
1. [Links and more info][#links-and-more-info]

## Protocol

Omit the protocol (`http:`, `https:`) from URLs pointing to images and other media files,
style sheets and scripts unless the respective files are not available over both protocols.  

Omitting the protocol, which makes the url relative, prevents mixed content issues and results in
minor file savings.

```html
<!-- bad -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>

<!-- good -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>
```

```css
/* bad */
.example {
  background: url(http://www.photobox.com/images/logo.png)
}

/* good */
.example {
  background: url(//www.photobox.com/images/logo.png) 
}
```

**[⬆ back to top](#table-of-contents)**

## Encoding

Make sure your editor uses UTF-8 character encoding, without a byte order mark.  Specify the 
encoding in HTML templates and documents via `<meta charset="utf-8">`. Do not specify the encoding 
of style sheets as these assume UTF-8.

(More on encodings and when and how to specify them can be found in 
[Handling character encodings in HTML and CSS](http://www.w3.org/International/tutorials/tutorial-char-enc/))

**[⬆ back to top](#table-of-contents)**

## Whitepace

> This section is under review.  Please do not refactor source files to 2 spaces unless you have
> been explicity sold to do so.

### Indentation

Ident by 2 spaces at a time.  Do not mix tabs and spaces for indentation.

```html
<ul>
  <li>Good</li>
  <li>Job</li>
</ul>
```

```css
.example {
  color: green;
} 
```

```js
function() {
  return 'Excellent';
}
```

### Trailing whitespace

Never leave trailing white space at the end of a line.

```html
<!-- bad -->
<p>Why would you do that?</p>   

<!-- good -->
<p>Much better</p>
```

### New lines

Make sure to leave a new line at the end of a file
```javascript
// bad
(function() {
  myAwesomeModule();
})();
```

```javascript
// good
(function() {
  myAwsomeModule();  
})();
↵
```

**[⬆ back to top](#table-of-contents)**

## Line lengths

Any line of source code should not exceed 100 characters.  The way lines should be broken is 
dependant on the type of technology in use.  Please refer to each of the guide for more info
on how to line break.

The exception to the line length rule are links defined in markdown which may well exceed 100 
characters.  

**[⬆ back to top](#table-of-contents)**

## Action Items

### TODO

Hightlight todos by using the `TODO` keyword only, not other common formats like `@@`.

Append action items after a colon as in `TODO: action item`

```html
<!-- TODO: Move centering to css -->
<center>Test</center>
```

### FIXME

Mark hacks, work arounds and no-essential issues with `FIXME`.

Simiarly to [todos](#4.1), hightlight fixmes with the `FIXME` keyword only.

```javascript
// FIXME: Use regular for loop instead of for-in
for ( k in arr ) {
  console.log(arr[k]);
}
```

**[⬆ back to top](#table-of-contents)**

## .editorconfig

Ensure your IDE or text editor is configured to use an `.editorconfig ` file. One should be located 
in the root of any project every work on.  

More info on `.editorconfig` can be found at [their website](http://editorconfig.org/).

**[⬆ back to top](#table-of-contents)**

## Links and more info

If you would like to round out your knowledge of front-end technologies, these links are a good 
place to get started.

- [Mozilla Developer Network](https://developer.mozilla.org/en-US/)
- [Google Web Fundamentals](https://developers.google.com/web/fundamentals/?hl=en)
- [HTML Rocks](http://www.html5rocks.com/en/)
- [Can I use...](http://caniuse.com/)
- [ECMA International](http://www.ecma-international.org/)
- [W3C](https://www.w3.org/)

**[⬆ back to top](#table-of-contents)**