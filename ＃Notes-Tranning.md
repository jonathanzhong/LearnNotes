＃#Notes - HTML Basic

07/22/2015
### Overall:

<!doctype html> to inform what version of html for the browser to render.
### Header Section:

- <meta> tags
for `keyword` and `description`; or more! Like viewport definition for mobile view.

- <scritp> tag 
for JS `function` (inline) or JS `files` (external);
live in **head** or **body** (for performance reason).
`document.write('String');`


`<p>always has a blank line before the tag.</p>`

### Body Section:
- Display Content: `<body>` tag
```
<h1> ... <h6>
<sup></sup>, <sub></sub>, <strong></strong>, <em></em>.
```

For **hightlight*

- Hyperlinks: <a> tag
Inside attribute, target attribute "_blank" open a new tab in browser.
Link to an e-mail address:
`<a href="mailto:example@example.com?subject=Bug+Report"></a>`


- Image: `<img>` tag
When we want to resize the image, we can just specify only `height` or `wideth`;
Or we can just define them in percentage %(abolute measure for the image).

- Horizontal Line: `<hr>` tag 

- Order Lists: `<ol>` tag
Attribute: type A, a, I, or i;
Display as number, english character or roman character;

- Unorder Lists: `<ul>` tag
Attribute: type disc, circle.

- Definition lists: `<dl>` tag
  `<dl>` -> `<dt>`(term) -> `<dd>`(definition)

- Special Characters:
[Click Here for more!](https://www.utexas.edu/learn/html/spchar.html)

- Block and inline Element
Block element: `<div>, <table>, <hr>, <p>`;

Inline element: `<span>`(userful for modify specific portion of text), `<a>`;

- Table: `<table>` tag
 -> `<tr>`: table row - `<td>`: table data
