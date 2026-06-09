# AMA Questions and Answers

## What is span in CSS Grid?

**Answer:** Span is used to make a grid item occupy multiple rows or columns.

```css
.item {
    grid-column: span 2;
}
```

---

## Difference Between Class and ID

**Answer:**

* Class can be used on multiple elements.
* ID should be unique for a single element.

```html
<div class="box">Class Example</div>
<div id="header">ID Example</div>
```

---

## What is the Use of z-index?

**Answer:** z-index controls the stacking order of overlapping elements.

```css
.box1 {
    z-index: 1;
}

.box2 {
    z-index: 2;
}
```

---

## Difference Between width and min-width

**Answer:**

* width sets the exact width.
* min-width sets the minimum width an element can shrink to.

```css
.box {
    width: 300px;
    min-width: 150px;
}
```

---

## Use of Media Queries

**Answer:** Media queries make websites responsive on different screen sizes.

```css
@media (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```

---

## What is Title Tag in Head?

**Answer:** The title tag defines the webpage title shown in the browser tab.

```html
<head>
    <title>My Website</title>
</head>
```

---

## Purpose of alt Attribute in Image

**Answer:** It provides alternative text when the image cannot be displayed and improves accessibility.

```html
<img src="logo.png" alt="Company Logo">
```

---

## Can We Use Multiple Header Tags?

**Answer:** Yes, HTML5 allows multiple `<header>` tags for different sections of a webpage.

```html
<header>Main Header</header>

<section>
    <header>Section Header</header>
</section>
```

---

## Difference Between Absolute and Relative Position

**Answer:**

* Relative positions an element relative to its normal position.
* Absolute positions an element relative to the nearest positioned ancestor.

```css
.relative {
    position: relative;
}

.absolute {
    position: absolute;
}
```

---

## What is Border and Border Values?

**Answer:** Border is a line surrounding an element. It consists of width, style, and color.

```css
.box {
    border: 2px solid black;
}
```

### Border Styles

* solid
* dashed
* dotted
* double
* groove

---

## What is flex-wrap?

**Answer:** flex-wrap determines whether flex items stay on one line or move to multiple lines.

```css
.container {
    display: flex;
    flex-wrap: wrap;
}
```

---

## Some Table Attributes

| Attribute   | Purpose              |
| ----------- | -------------------- |
| border      | Adds border to table |
| cellpadding | Space inside cells   |
| cellspacing | Space between cells  |
| colspan     | Merge columns        |
| rowspan     | Merge rows           |

```html
<table border="1">
    <tr>
        <td colspan="2">Merged Cell</td>
    </tr>
</table>
```

---

## Difference Between Padding and Margin

**Answer:**

* Padding is space inside the border.
* Margin is space outside the border.

```css
.box {
    padding: 20px;
    margin: 20px;
}
```

---

## Difference Between Background and Background-Color

**Answer:**

* background-color sets only the color.
* background is a shorthand property that can set color, image, position, repeat, etc.

```css
.box1 {
    background-color: yellow;
}

.box2 {
    background: yellow url(image.jpg) no-repeat center;
}
```

---

## Why Do We Use the Head Tag in HTML?

**Answer:** The head tag contains metadata, title, CSS links, JavaScript links, and SEO-related information.

```html
<head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css">
</head>
```

---
