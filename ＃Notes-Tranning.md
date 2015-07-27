##Notes - HTML Basic

## HTML
`07/22/2015`
### Overall:
<!doctype html> to inform what version of html for the browser to render.
### Header Section:

- `<meta>`  tags
for **keyword** and **description**; or more! Like viewport definition for mobile view.

- `<scritp>` tag 
for JS **function** (inline) or JS **files** (external);
live in **head** or **body** (for performance reason).
`document.write('String');`
`<p>always has a blank line before the tag.</p>`

### Body Section:
- Display Content: `<body>` tag

```
<h1> ... <h6>
<sup></sup>, <sub></sub>, <strong></strong>, <em></em>.
```

for **hightlight** `<mark></mark>`

- Hyperlinks: `<a>` tag
Inside attribute, target attribute "_blank" open a new tab in browser.
Link to an e-mail address:
`<a href="mailto:example@example.com?subject=Bug+Report"></a>`


- Image: `<img>` tag
When we want to resize the image, we can just specify only `height` or `wideth`;
Or we can just define them in percentage %(relative measure for the image).

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
`<th>` vanila basic.
Table rows split into three semantic sections: header, body and footer.
`<thead> <tbody> <tfoot>`

table attribute: ` cellspacing="15" cellpadding="0" `

`colspan` & `rowspan`

- Forms
`<input>` type can be **text** amd **checkbox** and **radio** and **submit**;
Dropdown meus:
```
<select>
   <option>/</a>option>
</select>
```

### HTML Layout

```
<div>

Default:
 - creat a new p with a blank line
 - Always occupy the complete width
 - Next <div> start a new p
<table> can position its cells

<section>

HTML5
<header>
<nav>
<aside>
<footer>
```

Use Bootstrap Grid System:



------------------------------------------------------






## CSS (Cascading Style Sheet) 
`07/24/2015`

Cascading = Inheritance.

Why USE CSS: Designed Separate content from presentation. (将内容和展示分隔开。)

Why "Cascading"?
Priority scheme determing which sytle rules apply to element.

In CSS, statement is a rule.
Rule : Selector  +  Declaration Block(property : value)

Selectors are seperated by commas;
Declaration are separated by semicolons;
Properties and value are separated colons;

Three `Primary` kinds of selector
1. By Tag Name.
2. By element ID Name. (Not useful, because it's unique, you can not reuse it. Mostly, element ID is used in jQuery for DOM Manipulation)
3. By element Class Name (Recommended to use)

Selectors can be combine with commas.


Pseudo-class define state: {
    : hover,
    : visited,
    : active,
    : lang 
    **These keywords are reserved. That you can not change it.**
}
Pseudo-element define element {
    : first-line
    ... and more
}

Match relative to element placement: 
Example: p a {...} This will match all `<a>` tag that are inside of `<p>`

`*`  - universal selector selector (avoid or use with care)

`+` use to match the next **sibling**

`>` matches direct child nodes

`[]` matches tag attributes by regular expression.


Colors are set in RGB format(decimal or hex). Safe colors: #112233 (most computers shared the same color, so when doing the UI design, it won't mess up)

Numeric values are specified in: pixels, ems(more `relative pixals`); points, inches, centimeters, millimeters; Percentages; Zero can be used with no unit: {border: 0}

**Browsers have default CSS styles**

- Linking HTML and CSS:
Three ways: **inline**: the CSS styles in the style attribute; **embedded**: in the `<head>` in a `<style>` tag; **external**: CSS rules in separated file(best)


**CSS Cascade(Precedence)**
- Browser Styles
- Normal User styles
- Normal Author styles(inline, embedded, external)
- Important author styles
- Import user styles(!important)

**CSS Specificity** 
inline -> embedded -> external(When applying the CSS rules, this is how the browser check the rules.)

external CSS (class =" c1, c2"):supposed `c1` and `c2` comes from 2 different files, so `c1` has a higher priority.

Backgrounds:
`background-repeat` repeat the smaller images.

