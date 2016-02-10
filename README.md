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
1. [Action Items](#actionitems)
1. [.editorconfig](#.editorconfig)

## Protocol

- [1](#1) <a name="1"></a> Omit the protocol (`http:`, `https:`) from URLS pointing to images and other media files,
style sheets and scripts unless the respective files are not available over both protocols.  
Although there should be a good reason why any resource should not be available over both.

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

- [2](#2) <a name="2"></a> Use UTF-8 (no BOM).  Make sure your editor uses UTF-8 character encoding, without a 
byte order mark.  Specify the encoding in HTML templates and documents via `<meta charset="utf-8">`.
Do not specify the encoding of style sheets as these assume UTF-8.

(More on encodings and when and how to specify them can be found in 
[Handling character encodings in HTML and CSS](http://www.w3.org/International/tutorials/tutorial-char-enc/))

**[⬆ back to top](#table-of-contents)**

## Whitepace

- [3.1](#3.1) <a name="3.1"></a> Ident by 2 spaces at a time.  Do not mix tabs and spaces for indentation.

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

- [3.2](#3.2) <a name="3.2"></a> Never leave trailing white space at the end of a line
```html
<!-- bad -->
<p>Why would you do that?</p>   

<!-- good -->
<p>Much better</p>
```

- [3.3](#3.3) <a name="3.3"></a> Make sure to leave a new line at the end of a file
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

## Action Items

- [4.1](#4.1) <a name="4.1"></a> Mark todos and action items with `TODO`.

Hightlight todos by using the `TODO` keyword only, not other common formats like `@@`.

Append action items after a colon as in `TODO: action item`

```html
<!-- TODO: Move centering to css -->
<center>Test</center>
```

- [4.2](#4.2) <a name="4.2"></a>  Mark hacks, work arounds and no-essential issues with `FIXME`.

Simiarly to [todos](#4.1), hightlight fixmes with the `FIXME` keyword only.

Append action items after a colon as in `FIXME: use recursive setTimeout instead of setInterval`

```javascript
// FIXME: Use regular for loop instead of for-in
for ( k in arr ) {
  console.log(arr[k]);
}
```

**[⬆ back to top](#table-of-contents)**

## .editorconfig

- [5](#5) <a name="5"></a> Make sure you IDE is configured to make use of the `.editorconfig `file which should be located in the root of any project you work on.  More info on `.editorconfig` can be found at [their website](http://editorconfig.org/).