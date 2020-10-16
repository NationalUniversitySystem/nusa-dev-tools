# Accessibility

## Tools

### Accessibility Testing Browser Plugins
- [Wave Plugin (Chrome and Firefox)](https://wave.webaim.org/extension/)
- [Siteimprove Accessibility Plugin (Chrome)](https://siteimprove.com/en-us/core-platform/integrations/browser-extensions/)

---

## Common Issues
This is a guide of the most common accessibility issues and how to avoid them. Please note where specific site suggestions are mentioned, since those suggestions may only apply to specific sites.

#### Link identified only by color
This issue occurs when color is the only distinguishing feature about links in blocks of text. Make sure there are other visual indicators of links besides the color, such as underline or bold

How to fix this issue specifically on...
- **National University (www)**:
  - Wrapping an anchor element within a `<p>` will add `text-decoration: underline` to the link.
  - For links within ordered `<ol>` or unordered `<ul>` lists, make sure to add `list list--reset list-gold` classes to the `<ul>/<ol>` tag.

#### Heading not nested properly
The headings on the page must be hierarchically organized. Headings should also go in order and not skip levels, ie:

```html
    <h2>Heading 1</h2>
        <h3>Heading 1.1</h3>
        <h3>Heading 1.2</h3>
    <h2>Heading 2</h2>
        <h3>Heading 2.1</h3>
        <h3>Heading 2.2</h3>
            <h4>Heading 2.2.1</h4>
            <h4>Heading 2.2.2</h4>
    <h2>Heading 3</h2>
```

Tip for **National University (www)**: If you need to add custom styles to a heading element (`<h1>` - `<h6>`), use our utility classes: `heading--one`, `heading--two`, `heading--three`, `heading--four`, `heading--five`, `heading--bold`.

[How to Structure Headings for Web Accessibility](https://www.nomensa.com/blog/2017/how-structure-headings-web-accessibility)

#### Non-distinguishable landmarks
The page contains two or more `HTML5` or `WAI-ARIA` landmarks of the same type that has not been named. Users might not know the difference if it's not somehow explained. Use the WAI-ARIA attributes `aria-label` or `aria-labelledby` to create unique names that describe the purpose of each landmark.

`<section>` elements require labels so that screen reader users are able to quickly identify what content they can find inside that particular section of the site.

There are three ways to label a sectioning element:
- Method 1: Add an `aria-label` attribute
- Method 2: Use an `aria-labelledby` attribute

[You need to label your sections. Here are three methods.](https://css-tricks.com/how-to-section-your-html/#you-need-to-label-your-sections-here-are-three-methods)

#### Image with no alt attribute
The image does not have an `alt` attribute (`alt=""`). **It’s important all images have the attribute for alternative text regardless of whether an alternative text is added.**

Pro-tip:
- End the alt-text with a period. This makes screen readers pause a bit after the last word in the alt-text, creating a natural pause before the next bit of text.
