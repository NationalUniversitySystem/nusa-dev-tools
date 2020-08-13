# HTML

## Syntax
* Don't capitalize tags, including the doctype.
* Use tabs to indent. (Should be set up in the project's `.editorconfig` file.)
* Always use double quote, never single quotes, on attributes.
* Don't include a trailing slash in self-closing elements—the [HTML5 spec](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag) says they're optional.
* Don’t omit optional closing tags (e.g. `</li>` or `</body>`).

```html
<!doctype html>
<html lang="eng">
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1">
		<link rel="profile" href="http://gmpg.org/xfn/11">
		<title>Page title</title>
	</head>
	<body>
		<img src="images/company-logo.png" alt="Company">
		<h1 class="hello-world">Hello, world!</h1>
	</body>
</html>
```

## Attribute Order
HTML attributes should come in the order where common and shared values are first and attributes unique to the element are last.

Shared, common, functionality, uniqueness, accessibility.

For example, classes and data attributes first, then `id` and `href`
- `class`
- `data-*`
- `src, for, type, href, value`
- `id, name`
- `title, alt`
- `role, aria-*`

```html
<a class="..." data-toggle="modal" id="..." href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

## Boolean Attributes
A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

For further reading, consult the [WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):

> The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

If you _must_ include the attribute's value, and **you don't need to**, follow this WhatWG guideline:

> If the attribute is present, its value must either be the empty string or [...] the attribute's canonical name, with no leading or trailing whitespace.

**In short, don't add a value.**

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
	<option value="1" selected>1</option>
</select>
```

## Reducing Markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.

```html
<!-- Not so great -->
<span class="avatar">
	<img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```
