# Complete CSS Notes - From Introduction to Mastery

## Table of Contents
1. [Introduction to CSS](#introduction-to-css)
2. [Why CSS?](#why-css)
3. [CSS Declaration Methods](#css-declaration-methods)
4. [CSS Structure](#css-structure)
5. [Selectors](#selectors)
6. [CSS Box Model](#css-box-model)
7. [Text Properties](#text-properties)
8. [Font Properties](#font-properties)
9. [Background Properties](#background-properties)
10. [CSS Values and Units](#css-values-and-units)
11. [Color Units](#color-units)
12. [CSS Position](#css-position)
13. [Flexbox](#flexbox)
14. [CSS Grid](#css-grid)
15. [Transitions](#transitions)
16. [Transforms](#transforms)
17. [Animations](#animations)
18. [Border Properties](#border-properties)
19. [Z-Index](#z-index)
20. [Overflow](#overflow)
21. [Opacity](#opacity)

---

## Introduction to CSS

**CSS (Cascading Style Sheets)** is a stylesheet language used to describe the presentation and design of HTML documents. CSS controls the layout, colors, fonts, and overall visual appearance of web pages.

**Key Points:**
- CSS separates content (HTML) from presentation (styling)
- Makes websites visually appealing and user-friendly
- Current version: CSS3 (with ongoing updates)

---

## Why CSS?

CSS is essential for modern web development for several reasons:

1. **Separation of Concerns** - Keeps HTML clean by separating structure from style
2. **Reusability** - Write once, apply to multiple elements
3. **Consistency** - Maintain uniform design across entire website
4. **Maintainability** - Easy to update styles in one place
5. **Performance** - Reduces code redundancy and page load time
6. **Responsive Design** - Create layouts that adapt to different screen sizes
7. **Cross-browser Compatibility** - Ensures consistent appearance across browsers

---

## CSS Declaration Methods

CSS can be applied to HTML in three ways:

### 1. Inline CSS
Styles applied directly to HTML elements using the `style` attribute.

```html
<p style="color: blue; font-size: 16px;">This is inline CSS</p>
```

**Pros:** Quick for single elements  
**Cons:** Not reusable, hard to maintain, mixes content with presentation

### 2. Internal CSS
Styles defined within the `<style>` tag in the HTML document's `<head>` section.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <p>This is internal CSS</p>
</body>
</html>
```

**Pros:** Affects entire page, better than inline  
**Cons:** Not reusable across multiple pages

### 3. External CSS (Best Practice)
Styles defined in a separate `.css` file and linked to HTML.

**style.css:**
```css
p {
    color: blue;
    font-size: 16px;
}
```

**index.html:**
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <p>This is external CSS</p>
</body>
</html>
```

**Pros:** Reusable, maintainable, separates concerns completely  
**Cons:** Requires additional HTTP request

---

## CSS Structure

CSS follows a specific syntax structure:

```css
selector {
    property: value;
    property: value;
}
```

**Example:**
```css
h1 {
    color: red;
    font-size: 24px;
    text-align: center;
}
```

**Components:**
- **Selector:** Targets HTML element(s)
- **Property:** The style attribute you want to change
- **Value:** The setting for the property
- **Declaration:** Property-value pair
- **Declaration Block:** All declarations within curly braces `{}`

---

## Selectors

Selectors are patterns used to select and style HTML elements.

### 1. Universal Selector
Selects all elements on the page.

```css
* {
    margin: 0;
    padding: 0;
}
```

### 2. Element Selector
Selects all elements of a specific type.

```css
p {
    color: blue;
}
```

### 3. Class Selector
Selects elements with a specific class (use `.` prefix).

```css
.button {
    background-color: green;
    color: white;
}
```

```html
<button class="button">Click Me</button>
```

### 4. ID Selector
Selects a single element with a specific ID (use `#` prefix).

```css
#header {
    background-color: navy;
}
```

```html
<div id="header">Header Content</div>
```

### 5. Descendant Selector
Selects elements nested inside other elements.

```css
div p {
    color: red;
}
```

### 6. Child Selector
Selects direct children only.

```css
div > p {
    color: blue;
}
```

### 7. Attribute Selector
Selects elements with specific attributes.

```css
input[type="text"] {
    border: 1px solid gray;
}
```

### 8. Pseudo-class Selector
Selects elements in a specific state.

```css
a:hover {
    color: red;
}

button:active {
    background-color: darkblue;
}

input:focus {
    border-color: blue;
}
```

### 9. Pseudo-element Selector
Styles specific parts of elements.

```css
p::first-line {
    font-weight: bold;
}

p::before {
    content: "→ ";
}
```

### 10. Group Selector
Applies same styles to multiple selectors.

```css
h1, h2, h3 {
    color: navy;
    font-family: Arial;
}
```

---

## CSS Box Model

The CSS box model describes how elements are rendered as rectangular boxes.

**Components (from inside to outside):**

1. **Content** - The actual content (text, images, etc.)
2. **Padding** - Space between content and border
3. **Border** - Edge around the padding
4. **Margin** - Space outside the border

```css
.box {
    width: 300px;
    height: 200px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```

**Box Model Properties:**

```css
/* Padding (inside spacing) */
padding: 10px;                    /* All sides */
padding: 10px 20px;               /* Top/Bottom Left/Right */
padding: 10px 20px 15px 25px;    /* Top Right Bottom Left */
padding-top: 10px;
padding-right: 20px;
padding-bottom: 15px;
padding-left: 25px;

/* Margin (outside spacing) */
margin: 10px;                     /* All sides */
margin: 10px auto;                /* Top/Bottom auto centers horizontally */
margin-top: 10px;
margin-right: 20px;
margin-bottom: 15px;
margin-left: 25px;

/* Border */
border: 2px solid black;
border-width: 2px;
border-style: solid;
border-color: black;
```

**Box-sizing Property:**

```css
/* Default - width/height applies to content only */
box-sizing: content-box;

/* Better - width/height includes padding and border */
box-sizing: border-box;
```

**Visual Representation:**
```
┌─────────────────────────── Margin ────────────────────────────┐
│                                                                 │
│  ┌────────────────────── Border ───────────────────────────┐  │
│  │                                                           │  │
│  │  ┌──────────────── Padding ────────────────┐           │  │
│  │  │                                           │           │  │
│  │  │  ┌────────── Content ─────────┐         │           │  │
│  │  │  │                             │         │           │  │
│  │  │  │      Text/Images            │         │           │  │
│  │  │  │                             │         │           │  │
│  │  │  └─────────────────────────────┘         │           │  │
│  │  │                                           │           │  │
│  │  └───────────────────────────────────────────┘           │  │
│  │                                                           │  │
│  └───────────────────────────────────────────────────────────┘  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Text Properties

Properties that control the appearance of text content.

```css
/* Text Alignment */
text-align: left;        /* left, right, center, justify */

/* Text Decoration */
text-decoration: none;   /* none, underline, overline, line-through */

/* Text Transformation */
text-transform: uppercase;   /* uppercase, lowercase, capitalize */

/* Text Indentation */
text-indent: 50px;

/* Letter Spacing */
letter-spacing: 2px;

/* Word Spacing */
word-spacing: 5px;

/* Line Height */
line-height: 1.6;

/* Text Shadow */
text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
/* horizontal vertical blur color */

/* White Space */
white-space: nowrap;     /* nowrap, pre, pre-wrap */

/* Text Overflow */
text-overflow: ellipsis;
overflow: hidden;
white-space: nowrap;
```

**Example:**
```css
.paragraph {
    text-align: justify;
    line-height: 1.8;
    letter-spacing: 1px;
    text-indent: 30px;
}

.heading {
    text-transform: uppercase;
    text-shadow: 3px 3px 5px gray;
}
```

---

## Font Properties

Properties that control font appearance.

```css
/* Font Family */
font-family: Arial, Helvetica, sans-serif;

/* Font Size */
font-size: 16px;

/* Font Weight */
font-weight: bold;       /* normal, bold, bolder, lighter, 100-900 */

/* Font Style */
font-style: italic;      /* normal, italic, oblique */

/* Font Variant */
font-variant: small-caps;

/* Shorthand Font Property */
font: italic bold 16px/1.5 Arial, sans-serif;
/* style weight size/line-height family */
```

**Web Fonts (Google Fonts Example):**

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

```css
body {
    font-family: 'Roboto', sans-serif;
}
```

**Example:**
```css
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.6;
}

h1 {
    font-size: 2.5rem;
    font-weight: 700;
}
```

---

## Background Properties

Properties that control element backgrounds.

```css
/* Background Color */
background-color: lightblue;

/* Background Image */
background-image: url('image.jpg');

/* Background Repeat */
background-repeat: no-repeat;    /* repeat, repeat-x, repeat-y, no-repeat */

/* Background Position */
background-position: center;     /* top, bottom, left, right, center */
background-position: 50% 50%;

/* Background Size */
background-size: cover;          /* auto, cover, contain, or specific values */
background-size: 100% 100%;

/* Background Attachment */
background-attachment: fixed;    /* scroll, fixed */

/* Shorthand Background */
background: url('image.jpg') no-repeat center center/cover;
/* image repeat position/size */

/* Multiple Backgrounds */
background-image: url('img1.jpg'), url('img2.jpg');
background-position: left top, right bottom;
```

**Gradient Backgrounds:**

```css
/* Linear Gradient */
background: linear-gradient(to right, red, blue);
background: linear-gradient(45deg, #ff0000, #0000ff);

/* Radial Gradient */
background: radial-gradient(circle, red, blue);
```

**Example:**
```css
.hero-section {
    background-image: url('hero-bg.jpg');
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
}

.gradient-box {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

---

## CSS Values and Units

### Most Frequently Used Units

#### 1. Absolute Units

**px (Pixels)** - Fixed unit, most commonly used
```css
width: 300px;
font-size: 16px;
```

#### 2. Relative Units

**% (Percentage)** - Relative to parent element
```css
width: 50%;          /* 50% of parent's width */
font-size: 120%;     /* 120% of parent's font size */
```

**vh (Viewport Height)** - Relative to viewport height
```css
height: 100vh;       /* 100% of viewport height */
margin-top: 10vh;    /* 10% of viewport height */
```

**vw (Viewport Width)** - Relative to viewport width
```css
width: 50vw;         /* 50% of viewport width */
font-size: 5vw;      /* 5% of viewport width */
```

#### 3. Other Important Units

**em** - Relative to parent element's font size
```css
font-size: 2em;      /* 2 times parent's font size */
padding: 1.5em;
```

**rem** - Relative to root element's font size
```css
font-size: 1.5rem;   /* 1.5 times root font size */
margin: 2rem;
```

**Comparison Example:**
```css
html {
    font-size: 16px;     /* Root font size */
}

.container {
    width: 80%;          /* 80% of parent */
    height: 100vh;       /* Full viewport height */
    padding: 2rem;       /* 32px (16 × 2) */
    font-size: 1.25rem;  /* 20px (16 × 1.25) */
}

.box {
    width: 300px;        /* Fixed 300 pixels */
    max-width: 90vw;     /* 90% of viewport width */
}
```

---

## Color Units

CSS supports multiple ways to define colors:

### 1. RGB (Red Green Blue)
```css
color: rgb(255, 0, 0);           /* Red */
color: rgb(0, 255, 0);           /* Green */
color: rgb(0, 0, 255);           /* Blue */
color: rgb(255, 255, 255);       /* White */
```

### 2. RGBA (RGB with Alpha/Opacity)
```css
background-color: rgba(255, 0, 0, 0.5);      /* 50% transparent red */
background-color: rgba(0, 0, 0, 0.8);        /* 80% transparent black */
background-color: rgba(255, 255, 255, 0.3);  /* 30% transparent white */
```

### 3. Hexadecimal (Hexa Code)
```css
color: #ffffff;      /* White */
color: #000000;      /* Black */
color: #ff0000;      /* Red */
color: #00ff00;      /* Green */
color: #0000ff;      /* Blue */
color: #fff;         /* Shorthand for #ffffff */
```

### 4. Color Keywords
```css
color: red;
color: blue;
color: green;
color: orange;
color: yellow;
color: purple;
color: pink;
color: brown;
color: gray;
color: black;
color: white;
```

### 5. HSL (Hue Saturation Lightness)
```css
color: hsl(0, 100%, 50%);        /* Red */
color: hsl(120, 100%, 50%);      /* Green */
color: hsl(240, 100%, 50%);      /* Blue */

/* HSLA with alpha */
color: hsla(0, 100%, 50%, 0.5);  /* 50% transparent red */
```

**Example Usage:**
```css
.button {
    background-color: #3498db;              /* Hex */
    color: rgb(255, 255, 255);              /* RGB */
    border: 2px solid rgba(0, 0, 0, 0.2);   /* RGBA */
}

.alert {
    background-color: rgba(255, 0, 0, 0.1); /* Light red background */
    color: red;                              /* Keyword */
}
```

---

## CSS Position

The `position` property specifies how an element is positioned in the document.

### 1. Static (Default)
Elements positioned according to normal document flow.

```css
.element {
    position: static;
}
```

### 2. Relative
Positioned relative to its normal position.

```css
.element {
    position: relative;
    top: 20px;       /* Moves 20px down from normal position */
    left: 30px;      /* Moves 30px right from normal position */
}
```

### 3. Absolute
Positioned relative to nearest positioned ancestor (or viewport if none).

```css
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 0;
    right: 0;        /* Positioned at top-right of parent */
}
```

### 4. Fixed
Positioned relative to the viewport (stays in place during scroll).

```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
}
```

### 5. Sticky
Toggles between relative and fixed based on scroll position.

```css
.header {
    position: sticky;
    top: 0;          /* Sticks when scrolled to top */
}
```

**Position Properties:**
- `top`, `right`, `bottom`, `left` - Offset from respective edges
- Only work with positioned elements (not static)

**Example:**
```css
.container {
    position: relative;
    height: 400px;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
    background-color: red;
    color: white;
}

.footer {
    position: fixed;
    bottom: 0;
    width: 100%;
}
```

---

## Flexbox

**Flexbox** is a one-dimensional layout method for arranging items in rows or columns.

### Container Properties (Parent)

```css
.container {
    display: flex;  /* or inline-flex */
}
```

#### flex-direction
Defines the main axis direction.

```css
flex-direction: row;             /* Default: left to right */
flex-direction: row-reverse;     /* right to left */
flex-direction: column;          /* top to bottom */
flex-direction: column-reverse;  /* bottom to top */
```

#### justify-content
Aligns items along the main axis.

```css
justify-content: flex-start;     /* Default: start of container */
justify-content: flex-end;       /* end of container */
justify-content: center;         /* center of container */
justify-content: space-between;  /* equal space between items */
justify-content: space-around;   /* equal space around items */
justify-content: space-evenly;   /* equal space everywhere */
```

#### align-items
Aligns items along the cross axis.

```css
align-items: stretch;      /* Default: stretch to fill */
align-items: flex-start;   /* start of cross axis */
align-items: flex-end;     /* end of cross axis */
align-items: center;       /* center of cross axis */
align-items: baseline;     /* align baselines */
```

#### flex-wrap
Controls wrapping of flex items.

```css
flex-wrap: nowrap;         /* Default: single line */
flex-wrap: wrap;           /* wrap to multiple lines */
flex-wrap: wrap-reverse;   /* wrap in reverse */
```

#### align-content
Aligns flex lines (works with wrap).

```css
align-content: flex-start;
align-content: flex-end;
align-content: center;
align-content: space-between;
align-content: space-around;
```

#### gap
Space between flex items.

```css
gap: 20px;                 /* gap between items */
row-gap: 20px;
column-gap: 10px;
```

### Item Properties (Children)

#### flex-grow
Defines ability to grow.

```css
.item {
    flex-grow: 1;          /* can grow to fill space */
}
```

#### flex-shrink
Defines ability to shrink.

```css
.item {
    flex-shrink: 1;        /* can shrink if needed */
}
```

#### flex-basis
Defines default size before growing/shrinking.

```css
.item {
    flex-basis: 200px;
}
```

#### flex (shorthand)
```css
.item {
    flex: 1;               /* flex-grow flex-shrink flex-basis */
    flex: 1 1 200px;
}
```

#### align-self
Override align-items for individual item.

```css
.item {
    align-self: flex-end;
}
```

#### order
Changes visual order of items.

```css
.item {
    order: 2;              /* default is 0 */
}
```

**Practical Example:**

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
}

.card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.card {
    flex: 1 1 300px;       /* grow, shrink, basis */
    max-width: 400px;
}
```

---

## CSS Grid

**CSS Grid** is a two-dimensional layout system for rows and columns.

### Container Properties (Parent)

```css
.container {
    display: grid;  /* or inline-grid */
}
```

#### grid-template-columns
Defines column structure.

```css
grid-template-columns: 200px 200px 200px;           /* 3 fixed columns */
grid-template-columns: 1fr 1fr 1fr;                  /* 3 equal columns */
grid-template-columns: 1fr 2fr 1fr;                  /* middle column 2x */
grid-template-columns: repeat(3, 1fr);               /* repeat pattern */
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));  /* responsive */
```

#### grid-template-rows
Defines row structure.

```css
grid-template-rows: 100px 200px 100px;
grid-template-rows: repeat(3, 1fr);
```

#### gap (grid-gap)
Space between grid items.

```css
gap: 20px;                     /* row and column gap */
row-gap: 20px;
column-gap: 10px;
```

#### grid-template-areas
Named grid areas.

```css
.container {
    grid-template-areas:
        "header header header"
        "sidebar main main"
        "footer footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

#### justify-items
Aligns items horizontally within cells.

```css
justify-items: start;
justify-items: end;
justify-items: center;
justify-items: stretch;        /* default */
```

#### align-items
Aligns items vertically within cells.

```css
align-items: start;
align-items: end;
align-items: center;
align-items: stretch;          /* default */
```

#### justify-content
Aligns entire grid horizontally within container.

```css
justify-content: start;
justify-content: end;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
```

#### align-content
Aligns entire grid vertically within container.

```css
align-content: start;
align-content: end;
align-content: center;
align-content: space-between;
align-content: space-around;
align-content: space-evenly;
```

### Item Properties (Children)

#### grid-column
Defines column span.

```css
.item {
    grid-column: 1 / 3;        /* spans from column 1 to 3 */
    grid-column: span 2;       /* spans 2 columns */
}
```

#### grid-row
Defines row span.

```css
.item {
    grid-row: 1 / 3;           /* spans from row 1 to 3 */
    grid-row: span 2;          /* spans 2 rows */
}
```

#### grid-area
Shorthand for grid position.

```css
.item {
    grid-area: 1 / 1 / 3 / 3;  /* row-start / col-start / row-end / col-end */
}
```

#### justify-self & align-self
Override container alignment for individual items.

```css
.item {
    justify-self: center;
    align-self: end;
}
```

**Practical Example:**

```css
/* Simple 3-column grid */
.gallery {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

/* Responsive grid */
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
}

/* Complex layout */
.layout {
    display: grid;
    grid-template-columns: 250px 1fr;
    grid-template-rows: 80px 1fr 60px;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    gap: 20px;
    height: 100vh;
}
```

---

## Transitions

**Transitions** create smooth animations when CSS properties change.

### Basic Syntax

```css
.element {
    transition: property duration timing-function delay;
}
```

### transition-property
Specifies which property to animate.

```css
transition-property: all;              /* all properties */
transition-property: background-color; /* specific property */
transition-property: width, height;    /* multiple properties */
```

### transition-duration
How long the transition takes.

```css
transition-duration: 0.3s;             /* 300 milliseconds */
transition-duration: 1s;               /* 1 second */
```

### transition-timing-function
Speed curve of transition.

```css
transition-timing-function: ease;          /* default: slow-fast-slow */
transition-timing-function: linear;        /* constant speed */
transition-timing-function: ease-in;       /* slow start */
transition-timing-function: ease-out;      /* slow end */
transition-timing-function: ease-in-out;   /* slow start and end */
transition-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);  /* custom */
```

### transition-delay
Delay before transition starts.

```css
transition-delay: 0s;                  /* no delay */
transition-delay: 0.5s;                /* 500ms delay */
```

### Shorthand

```css
.button {
    transition: all 0.3s ease 0s;
    /* property duration timing-function delay */
}

/* Multiple transitions */
.box {
    transition: 
        width 0.3s ease,
        height 0.3s ease 0.1s,
        background-color 0.5s ease;
}
```

**Practical Examples:**

```css
.button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    transition: background-color 0.3s ease;
}

.button:hover {
    background-color: darkblue;
}

.card {
    transform: scale(1);
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}

.menu {
    height: 0;
    overflow: hidden;
    transition: height 0.5s ease-in-out;
}

.menu.open {
    height: 300px;
}
```

---

## Transforms

**Transforms** modify the coordinate space of elements without affecting document flow.

### 2D Transforms

#### translate()
Moves element from its current position.

```css
transform: translate(50px, 100px);     /* x, y */
transform: translateX(50px);           /* horizontal only */
transform: translateY(100px);          /* vertical only */
```

#### rotate()
Rotates element around a point.

```css
transform: rotate(45deg);              /* clockwise 45 degrees */
transform: rotate(-45deg);             /* counter-clockwise */
```

#### scale()
Changes element size.

```css
transform: scale(1.5);                 /* 150% size */
transform: scale(2, 0.5);              /* width 2x, height 0.5x */
transform: scaleX(2);                  /* width only */
transform: scaleY(0.5);                /* height only */
```

#### skew()
Skews element along axes.

```css
transform: skew(20deg, 10deg);         /* x, y */
transform: skewX(20deg);               /* horizontal only */
transform: skewY(10deg);               /* vertical only */
```

### 3D Transforms

```css
transform: rotateX(45deg);             /* rotate around X axis */
transform: rotateY(45deg);             /* rotate around Y axis */
transform: rotateZ(45deg);             /* rotate around Z axis (same as rotate) */
transform: translateZ(100px);          /* move along Z axis */
transform: perspective(500px);         /* set perspective */
```

## Animations

**Animations** allow elements to gradually change from one style to another using keyframes.

### Creating Keyframes

Define animation sequence using `@keyframes`.
```css
@keyframes slide-in {
  from {
    transform: translateX(-100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

/* Using percentages for multiple steps */
@keyframes bounce {
  0% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
  100% { transform: translateY(0); }
}
```

### Animation Properties

#### animation-name
Specifies the keyframe name to use.
```css
animation-name: slide-in;
```

#### animation-duration
Sets how long animation takes to complete.
```css
animation-duration: 2s;                /* 2 seconds */
animation-duration: 500ms;             /* 500 milliseconds */
```

#### animation-timing-function
Controls animation speed curve.
```css
animation-timing-function: ease;       /* default, slow start/end */
animation-timing-function: linear;     /* constant speed */
animation-timing-function: ease-in;    /* slow start */
animation-timing-function: ease-out;   /* slow end */
animation-timing-function: ease-in-out; /* slow start and end */
```

#### animation-delay
Specifies delay before animation starts.
```css
animation-delay: 1s;                   /* start after 1 second */
animation-delay: -0.5s;                /* start halfway through */
```

#### animation-iteration-count
Number of times animation repeats.
```css
animation-iteration-count: 3;          /* repeat 3 times */
animation-iteration-count: infinite;   /* loop forever */
```

#### animation-direction
Sets animation play direction.
```css
animation-direction: normal;           /* forward (default) */
animation-direction: reverse;          /* backward */
animation-direction: alternate;        /* forward then backward */
animation-direction: alternate-reverse; /* backward then forward */
```

#### animation-fill-mode
Defines styles before/after animation.
```css
animation-fill-mode: none;             /* no styles applied */
animation-fill-mode: forwards;         /* keep end state */
animation-fill-mode: backwards;        /* apply start state during delay */
animation-fill-mode: both;             /* both forwards and backwards */
```

#### animation-play-state
Controls whether animation is running or paused.
```css
animation-play-state: running;         /* default */
animation-play-state: paused;          /* pause animation */
```

### Animation Shorthand
```css
animation: name duration timing-function delay iteration-count direction fill-mode;

/* Examples */
animation: slide-in 2s ease-in-out 0.5s infinite alternate;
animation: bounce 1s linear infinite;
animation: fade-in 0.3s ease-out forwards;
```

### Multiple Animations

Apply multiple animations separated by commas.
```css
animation: slide-in 1s ease-out, fade-in 0.5s ease-in;
```

---

## Border Properties

**Border properties** control the border around elements.

### border-width
Sets border thickness.
```css
border-width: 5px;                     /* all sides */
border-width: 2px 4px;                 /* top/bottom left/right */
border-width: 1px 2px 3px 4px;         /* top right bottom left */

/* Individual sides */
border-top-width: 5px;
border-right-width: 3px;
border-bottom-width: 5px;
border-left-width: 3px;

/* Keywords */
border-width: thin;                    /* browser default thin */
border-width: medium;                  /* default value */
border-width: thick;                   /* browser default thick */
```

### border-style
Defines border line style.
```css
border-style: solid;                   /* solid line */
border-style: dashed;                  /* dashed line */
border-style: dotted;                  /* dotted line */
border-style: double;                  /* double line */
border-style: groove;                  /* 3D grooved */
border-style: ridge;                   /* 3D ridged */
border-style: inset;                   /* 3D inset */
border-style: outset;                  /* 3D outset */
border-style: none;                    /* no border */
border-style: hidden;                  /* hidden border */

/* Individual sides */
border-top-style: solid;
border-right-style: dashed;
border-bottom-style: dotted;
border-left-style: double;
```

### border-color
Sets border color.
```css
border-color: red;                     /* all sides */
border-color: red blue;                /* top/bottom left/right */
border-color: red blue green yellow;   /* top right bottom left */

/* Individual sides */
border-top-color: red;
border-right-color: blue;
border-bottom-color: green;
border-left-color: yellow;
```

### Border Shorthand
```css
border: width style color;

/* Examples */
border: 2px solid black;
border: 5px dashed #ff0000;
border: thin dotted blue;

/* Individual sides */
border-top: 2px solid red;
border-right: 3px dashed blue;
border-bottom: 1px dotted green;
border-left: 4px solid yellow;
```

### border-radius
Creates rounded corners.
```css
border-radius: 10px;                   /* all corners */
border-radius: 10px 20px;              /* top-left/bottom-right top-right/bottom-left */
border-radius: 10px 20px 30px 40px;    /* top-left top-right bottom-right bottom-left */

/* Individual corners */
border-top-left-radius: 10px;
border-top-right-radius: 20px;
border-bottom-right-radius: 30px;
border-bottom-left-radius: 40px;

/* Elliptical corners */
border-radius: 50px / 25px;            /* horizontal / vertical */

/* Circle */
border-radius: 50%;
```

### border-image
Uses image as border.
```css
border-image: source slice width outset repeat;

/* Example */
border-image: url('border.png') 30 stretch;
border-image: url('border.png') 30 round;
```

---

## Z-Index

**Z-index** controls the stacking order of positioned elements (overlapping).

### Basic Usage
```css
z-index: 1;                            /* positive value */
z-index: -1;                           /* negative value */
z-index: 0;                            /* default */
z-index: 999;                          /* high priority */
z-index: auto;                         /* stack order from parent */
```

### Requirements

- Element must have `position` value other than `static`
- Works with: `relative`, `absolute`, `fixed`, `sticky`
```css
.element {
  position: relative;
  z-index: 10;                         /* will work */
}

.static-element {
  z-index: 10;                         /* won't work without position */
}
```

### Stacking Context

Elements with higher z-index appear in front of elements with lower z-index.
```css
.background {
  position: relative;
  z-index: 1;                          /* bottom layer */
}

.middle {
  position: absolute;
  z-index: 5;                          /* middle layer */
}

.foreground {
  position: fixed;
  z-index: 10;                         /* top layer */
}
```

### Stacking Context Rules

- Parent with lower z-index cannot have children appear above elements with higher z-index
- Z-index only works within the same stacking context
- Creating new stacking context: `position` + `z-index`, `opacity` < 1, `transform`, `filter`, etc.
```css
.parent {
  position: relative;
  z-index: 1;
}

.child {
  position: absolute;
  z-index: 999;                        /* still below elements with parent z-index > 1 */
}
```

---

## Overflow

**Overflow** controls what happens when content is too large for its container.

### overflow Property
```css
overflow: visible;                     /* default, content not clipped */
overflow: hidden;                      /* clip content, no scrollbar */
overflow: scroll;                      /* always show scrollbars */
overflow: auto;                        /* scrollbar only when needed */
```

### overflow-x and overflow-y

Control overflow separately for horizontal and vertical axes.
```css
overflow-x: hidden;                    /* hide horizontal overflow */
overflow-y: scroll;                    /* vertical scrollbar */

overflow-x: auto;
overflow-y: visible;
```

### Text Overflow

Handle text that overflows its container.
```css
.text-clip {
  overflow: hidden;
  text-overflow: clip;                 /* cut off text (default) */
}

.text-ellipsis {
  overflow: hidden;
  white-space: nowrap;                 /* prevent wrapping */
  text-overflow: ellipsis;             /* show ... */
}
```

### Scrollbar Styling
```css
/* Webkit browsers (Chrome, Safari) */
::-webkit-scrollbar {
  width: 10px;                         /* scrollbar width */
}

::-webkit-scrollbar-track {
  background: #f1f1f1;                 /* track color */
}

::-webkit-scrollbar-thumb {
  background: #888;                    /* handle color */
}

::-webkit-scrollbar-thumb:hover {
  background: #555;                    /* handle hover color */
}
```

### overflow-wrap

Control word breaking.
```css
overflow-wrap: normal;                 /* break at normal points */
overflow-wrap: break-word;             /* break long words */
overflow-wrap: anywhere;               /* break anywhere if needed */
```

---

## Opacity

**Opacity** controls the transparency level of an element.

### Basic Usage
```css
opacity: 1;                            /* fully opaque (default) */
opacity: 0.5;                          /* 50% transparent */
opacity: 0;                            /* fully transparent */
```

### Value Range

- Accepts values from `0.0` to `1.0`
- `0` = completely transparent (invisible)
- `1` = completely opaque (solid)
- `0.5` = 50% transparent
```css
.transparent {
  opacity: 0.3;                        /* 30% opaque, 70% transparent */
}

.semi-transparent {
  opacity: 0.7;                        /* 70% opaque, 30% transparent */
}

.invisible {
  opacity: 0;                          /* invisible but still in layout */
}
```

### Opacity vs Visibility vs Display
```css
/* Opacity: transparent but takes space, events still work */
.fade-out {
  opacity: 0;
}

/* Visibility: invisible, takes space, no events */
.hidden {
  visibility: hidden;
}

/* Display: removed from layout completely */
.removed {
  display: none;
}
```

### Opacity with Hover Effects
```css
.image {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.image:hover {
  opacity: 0.7;                        /* semi-transparent on hover */
}
```

### Opacity vs RGBA
```css
/* Opacity affects entire element including children */
.parent {
  opacity: 0.5;                        /* children also 50% transparent */
}

/* RGBA affects only background, not children */
.parent-rgba {
  background-color: rgba(0, 0, 0, 0.5); /* only background 50% transparent */
}
```

### Performance Note

- Opacity creates new stacking context
- Can trigger GPU acceleration
- Generally good for transitions and animations
```css
.fade-transition {
  opacity: 1;
  transition: opacity 0.3s ease;
  will-change: opacity;                /* hint for optimization */
}
```

## Media Queries

**Media Queries** allow you to apply CSS styles based on device characteristics like screen size, resolution, and orientation.

### Basic Syntax
```css
@media media-type and (condition) {
  /* CSS rules */
}
```

### Media Types
```css
@media screen { }                      /* computer screens, tablets, phones */
@media print { }                       /* printers and print preview */
@media all { }                         /* all devices (default) */
@media speech { }                      /* screen readers */
```

### Common Breakpoints
```css
/* Mobile First Approach */
/* Mobile devices (default styles) */
.container {
  width: 100%;
}

/* Tablets */
@media (min-width: 768px) {
  .container {
    width: 750px;
  }
}

/* Desktops */
@media (min-width: 1024px) {
  .container {
    width: 960px;
  }
}

/* Large screens */
@media (min-width: 1280px) {
  .container {
    width: 1200px;
  }
}
```

### Width and Height

#### min-width and max-width
```css
@media (min-width: 768px) { }          /* 768px and above */
@media (max-width: 767px) { }          /* 767px and below */
@media (min-width: 768px) and (max-width: 1023px) { } /* between 768px and 1023px */
```

#### min-height and max-height
```css
@media (min-height: 600px) { }         /* height 600px and above */
@media (max-height: 599px) { }         /* height 599px and below */
```

### Orientation
```css
@media (orientation: portrait) {       /* height > width */
  .sidebar {
    width: 100%;
  }
}

@media (orientation: landscape) {      /* width > height */
  .sidebar {
    width: 30%;
  }
}
```

### Resolution
```css
@media (min-resolution: 2dppx) { }     /* high DPI screens (Retina) */
@media (min-resolution: 300dpi) { }    /* 300 dots per inch */
@media (-webkit-min-device-pixel-ratio: 2) { } /* Webkit browsers */
```

### Aspect Ratio
```css
@media (aspect-ratio: 16/9) { }        /* exact aspect ratio */
@media (min-aspect-ratio: 16/9) { }    /* minimum aspect ratio */
@media (max-aspect-ratio: 4/3) { }     /* maximum aspect ratio */
```

### Logical Operators

#### and
Combines multiple conditions (all must be true).
```css
@media (min-width: 768px) and (max-width: 1023px) {
  /* applies only between 768px and 1023px */
}

@media screen and (min-width: 768px) and (orientation: landscape) {
  /* screen, at least 768px wide, and landscape */
}
```

#### or (comma)
Separates multiple queries (any can be true).
```css
@media (min-width: 768px), (orientation: landscape) {
  /* applies if width >= 768px OR landscape orientation */
}

@media screen, print {
  /* applies to both screen and print */
}
```

#### not
Negates entire query.
```css
@media not screen and (color) {
  /* applies to non-color screens */
}

@media not (min-width: 768px) {
  /* applies when width < 768px */
}
```

#### only
Prevents older browsers from applying styles.
```css
@media only screen and (min-width: 768px) {
  /* ignored by older browsers */
}
```

### Common Patterns

#### Mobile First

Start with mobile styles, add complexity for larger screens.
```css
/* Base mobile styles */
.nav {
  flex-direction: column;
}

/* Tablet and up */
@media (min-width: 768px) {
  .nav {
    flex-direction: row;
  }
}
```

#### Desktop First

Start with desktop styles, simplify for smaller screens.
```css
/* Base desktop styles */
.nav {
  flex-direction: row;
}

/* Tablet and below */
@media (max-width: 767px) {
  .nav {
    flex-direction: column;
  }
}
```

### Breakpoint Examples
```css
/* Extra small devices (phones, less than 576px) */
@media (max-width: 575.98px) {
  .container {
    padding: 10px;
  }
}

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) {
  .container {
    padding: 15px;
  }
}

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) {
  .container {
    padding: 30px;
  }
}

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) {
  .container {
    padding: 40px;
  }
}
```

### Dark Mode
```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #ffffff;
  }
}

@media (prefers-color-scheme: light) {
  body {
    background-color: #ffffff;
    color: #000000;
  }
}
```

### Reduced Motion
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}

@media (prefers-reduced-motion: no-preference) {
  .element {
    transition: all 0.3s ease;
  }
}
```

### Hover Capability
```css
@media (hover: hover) {                /* device can hover (mouse) */
  .button:hover {
    background-color: blue;
  }
}

@media (hover: none) {                 /* device cannot hover (touch) */
  .button:active {
    background-color: blue;
  }
}
```

### Pointer Precision
```css
@media (pointer: fine) {               /* precise pointer (mouse) */
  .target {
    width: 20px;
    height: 20px;
  }
}

@media (pointer: coarse) {             /* less precise (touchscreen) */
  .target {
    width: 44px;                       /* larger touch target */
    height: 44px;
  }
}
```

### Nesting Media Queries
```css
.container {
  width: 100%;
}

@media (min-width: 768px) {
  .container {
    width: 750px;
    
    @media (min-width: 1024px) {       /* nested query */
      width: 960px;
    }
  }
}
```

### Print Styles
```css
@media print {
  /* Hide elements when printing */
  .no-print {
    display: none;
  }
  
  /* Optimize for print */
  body {
    font-size: 12pt;
    color: black;
    background: white;
  }
  
  /* Add page breaks */
  .page-break {
    page-break-before: always;
  }
}
```

### Best Practices
```css
/* Use relative units */
@media (min-width: 48em) {             /* 768px / 16px = 48em */
  /* styles */
}

/* Avoid device-specific breakpoints */
/* ❌ Bad */
@media (width: 375px) { }              /* iPhone specific */

/* ✅ Good */
@media (min-width: 320px) and (max-width: 480px) { }

/* Test in between breakpoints */
@media (min-width: 768px) and (max-width: 1023px) {
  /* styles for tablets */
}
```

