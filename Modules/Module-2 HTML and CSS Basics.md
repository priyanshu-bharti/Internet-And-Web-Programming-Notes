# Internet and Web Programming (ITA6003)

## Module 2 : HTML and Static Webpages

- [x] ~~HTML Structure~~
- [x] ~~Legacy HTML Tags~~
- [x] ~~Typography~~
- [x] ~~Special Characters~~
- [x] ~~Lists~~
- [x] ~~Nested Lists~~
- [x] ~~Images~~
- [x] ~~Mail~~
- [x] ~~Forms~~
- [x] ~~Frames~~
- [x] ~~FrameSet~~
- [x] ~~NoFrames~~
- [x] ~~Tables~~
- [x] ~~CSS~~
- [x] ~~Where to Write CSS~~
- [x] ~~Types of CSS and Precedence~~
- [x] ~~Why use CSS~~
- [x] ~~CSS Selectors~~

## HTML Structure

```html
<html>
  <head>
    <title>Title</title>
  </head>
  <body>
    Basic Website
  </body>
</html>
```

## Legacy HTML Tags and Attributes

- **Body Tag Attributes**
  - `Text=“#RRGGBB”` : For changing the color of text in the body.
  - `bgcolor=“#RRGGBB”` : Change the background color of the body.
  - `link=“#RRGGBB”`, `vlink=“#RRGGBB”`, `alink=“#RRGGBB"` : Change the color of the link in the body.
- **Alignment**
  - `<div>` : Represents a division in the document and can contain most other document type.
  - `<span>` : Represent an inline division
  - `<center>` : Center the elements.

## Typography

- `<h1>` to `<h6>` : Heading size 1 to 6
- `<p>` : Paragraph
- `<br>` : Line Break
- `<hr>` : Horizontal Rule
- `<b>` : Bold
- `<u>` : Underline
- `<i>` : Italics
- `<font color="#RRGGBB">` : Change the font properties
- `<pre>` : Reformatted text
- `<em>` : Emphasis
- `<strong>` : Strong Text
- `<tt>` : Teletype text (Monospace font)
- `<cite>` : Represents citation (italics).
- `<strike>` : Strikethrough text
- `<big>` : Places text in Big font
- `<small>` : Places text in small font
- `<sub>` : Places text in subscript position
- `<sup>` : Places text in superscript position

## Links

```html
<a href="address" color="#RRGGBB">Link Text</a>
```

## Special Characters

- These characters are recognized in HTML.
- The value will either be an entity name or an ASCII character number.
- They’re called escape sequences.
- Ampersand: `&amp;`
- Copyright: `&copy;`
- Greater Than: `&gt;`
- Less Than: `&lt;`
- Non-breaking Space: `&nbsp;`
- Quotation Mark: `&quot;`
- Registration Mark: `&reg;`
- Trademark: `&trade;`

## Lists

### Unordered List

- List items starts with a bullet point.
- The kind of marking is changed when the list is nested.

```html
<ul>
  <li>List Item</li>
  <li>List Item</li>
</ul>
```

### Ordered List

```html
<ol type="a">
  <li>List Item</li>
  <li>List Item</li>
</ol>
```

- Type can be:
  - 1 : Arabic Numbers
  - a : Lowercase Alphabets
  - A : Uppercase Alphabets
  - i : Lowercase Roman
  - I : Uppercase Roman

## Nested Lists

```html
<ol type="a">
  <li>List Item</li>
  <ul>
    <li>List Item</li>
    <li>List Item</li>
  </ul>
</ol>
```

## Images

```html
<img
  src="..."
  alt="alternate images"
  width="30"
  height="50"
  align="left"
  hspace="15"
  vspace="45"
/>
```

## Mail

```html
<a href="mailto:email@example.com">Send Email</a>
```

## Forms

- Add the ability to access the information
- All kinds of inputs are placed inside the `<form>` tag.

```html
<form action="action.php" method="GET" target="frame.html">
  <input type="text|email|password|number" value="" required></input>
  <textarea value="" rows="30" cols="30"></textarea>
  <select selected="optionName" multiple>
    <option value="internalValue">Option Text to show</option>
  </select>
    <fieldset id="group">
        <input type="radio" name="commonName">
        <input type="radio" name="commonName">
        <input type="radio" name="commonName">
    </fieldset>
  <label for="c1">Checkbox</label>
	<input type="checkbox" checked required id="c1"></input>
  <input type="submit" value="ButtonText" required></input>
  <input type="reset" value="ButtonText" required></input>
	<input type="image" src="address.jpg">
</form>
```

## Frames

- Framed page is made off multiple HTML pages.
- One HTML page defines how to break the html into parts
- Each part has an HTML document.

## FrameSet

```html
<html>
  <head>
    <title>HTML Frames</title>
  </head>
  <frameset cols|rows="25%,50%,25%">
    <frame name="left" src="address" />
    <frame name="center" src="address" />
    <frame name="right" src="address" />
    <noframes>
      <body>
        Your browser does not support frames.
      </body>
    </noframes>
  </frameset>
</html>
```

- `noframes`: would only display the text if the browser doesn’t support frames.

## Tables
```html
<table>
  <caption>
    Some Caption
  </caption>
  <tr>
    <th rowspan="2" colspan="2">Heading</th>
    <th>Heading</th>
  </tr>
  <tr>
    <td>Cell</td>
    <td>Cell</td>
  </tr>
</table>
```

## CSS

- Stands for Cascaded Style Sheets
- Separates the structure of the page from the design

```html
<link type="text/css" href="style.css" />
```

## Where to Write CSS

- Could be:
  - Inline
  - External
  - Internal
  - Imported

## Types of CSS and Precedence

The Precedence is as follows (from highest to lowest):

1. Inline
2. Internal
3. External
4. Browser

## Why use CSS

- The design of webpages can be separated from the content
- Fast page downloads
- Shorter Development time
- Easy to write
- Greater control of the website and object placement.
- Improvement in accessibility
- Better search engine rankings

## CSS Selectors

### Simple Selectors

```css
/* Attribute Selector */
p {
  ...;
}

/* Class Selector */
.className {
  ...;
}

/* ID name Selector */
#idName {
  ...;
}

/* Universal Selector */
* {
  ...;
}
```

### Combinator Selector

```css
/* Group Selector */
h1,
h2,
p {
  ...;
}

/* Direct Child Selector */
p > span {
  ...;
}

/* Descendant Selector */
p span {
  ...;
}

/* Sibling Selector */
p > span {
  ...;
}

/* Adjacent Sibling Selector */
p + span {
  ...;
}

/* General Sibling Selector */
p ~ span {
  ...;
}
```

### Pseudo-class Selector

```css
/* ----- ANCHOR TAG PSEUDO CLASS SELECTOR ----- */
/* unvisited link */
a:link {
  color: #ff0000;
}
/* visited link */
a:visited {
  color: #00ff00;
}
/* mouse over link */
a:hover {
  color: #ff00ff;
}
/* selected link */
a:active {
  color: #0000ff;
}

/* ----- HOVER PSEUDO CLASS ----- */
div:hover {
  background-color: blue;
}
```

### Pseudo-elements Selector

```css
/* First Child */
ul:first-child {
  color: blue;
}

/* Last Child */
ul:last-child {
  color: blue;
}
```

## CSS Properties

```css
/* Background Properties */
div {
  background: color;
  background: url("address");
}

/* Text Properties */
div {
  color: color;
  text-align: "left|center|right|justify";
  text-decoration: "none|underline|overline|line-through|blink";
  text-indent: 20px;
}

/* Font Properties */
div {
  font-style: "normal|italics";
  font-variant: "normal|small-caps";
  font-weight: "normal|bold|bolder|lighter|100-900";
  font-size: 16pt;
  font-family: "Arial", sans-serif;
}

/* Insets */
div {
  margin: 20px;
  margin-top: 20px;
  margin-bottom: 20px;
  margin-left: 20px;
  margin-right: 20px;
  padding: 20px;
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 20px;
  padding-right: 20px;
}

/* Table Stylings */
table, th, td {
  border: 1px solid black;
  border-spacing: 2px;
  border-style: "solid|dashed|dotted|double|groove|inset|outset|none|hidden";
  border-collapse: "collapse|separate";
}
```
