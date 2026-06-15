# CSS Selectors — Deep, Brutal, Understanding-First Notes

---

# What is a Selector?

A **selector** tells CSS:

> "Which HTML elements should receive these styles?"

Without selectors, CSS would not know where to apply rules.

Basic syntax:

```css
selector {
    property: value;
}
```

Example:

```css
h1 {
    color: red;
}
```

Meaning:

```text
Find all <h1> elements
↓
Apply color:red
```

---

# Why Do Selectors Exist?

Imagine a webpage with:

```html
100 headings
50 buttons
200 paragraphs
```

Without selectors:

```text
You cannot target specific elements.
```

Selectors solve this problem by allowing CSS to:

- Target specific elements
- Target groups of elements
- Target based on relationships
- Target based on attributes
- Target based on state (hover, focus)
- Target based on position

---

# Categories of CSS Selectors

```text
CSS Selectors
│
├─ Basic Selectors
│
├─ Combinator Selectors
│
├─ Attribute Selectors
│
├─ Pseudo-Class Selectors
│
├─ Pseudo-Element Selectors
│
└─ Universal Selector
```

---

# 1. Element Selector

## What is it?

Targets HTML tags directly.

Syntax:

```css
tagname {
}
```

Example:

```css
p {
    color: blue;
}
```

HTML:

```html
<p>First</p>
<p>Second</p>
```

Output:

```text
Both paragraphs become blue.
```

---

## Use When

✔ Styling all elements of same type.

Example:

```css
body {
    font-family: Arial;
}

h1 {
    color: navy;
}
```

---

## Avoid When

❌ Need specific targeting.

Bad:

```css
button {
    color:red;
}
```

when only one button should change.

---

# 2. ID Selector

## What is it?

Targets an element using its unique ID.

Syntax:

```css
#idname {
}
```

Example:

```css
#header {
    color: red;
}
```

HTML:

```html
<h1 id="header">Welcome</h1>
```

---

## Rules

HTML:

```html
id="header"
```

CSS:

```css
#header
```

IDs should be:

```text
Unique
```

per page.

---

## Use When

✔ One specific element.

Example:

```html
<section id="hero">
```

---

## Avoid When

❌ Reusable styling.

Bad:

```html
id="card"
id="card"
id="card"
```

---

# 3. Class Selector

## What is it?

Targets elements sharing the same class.

Syntax:

```css
.classname {
}
```

Example:

```css
.note {
    color: green;
}
```

HTML:

```html
<p class="note">A</p>
<p class="note">B</p>
```

Output:

```text
Both become green.
```

---

## Use When

✔ Reusable styles.

Examples:

```css
.card
.btn
.error
.success
```

---

## Real Projects

Most styling uses classes.

Example:

```html
<button class="btn btn-primary">
```

---

# 4. Universal Selector

## What is it?

Targets EVERYTHING.

Syntax:

```css
* {
}
```

Example:

```css
* {
    margin: 0;
    padding: 0;
}
```

---

## Use When

CSS reset.

---

## Avoid When

Heavy styling.

Bad:

```css
* {
    color:red;
}
```

May hurt readability.

---

# 5. Group Selector

## What is it?

Targets multiple selectors.

Syntax:

```css
selector1,
selector2 {
}
```

Example:

```css
h1,
h2,
h3 {
    color: blue;
}
```

---

## Use When

Repeated styles exist.

Bad:

```css
h1{color:red;}
h2{color:red;}
h3{color:red;}
```

Good:

```css
h1,h2,h3{
    color:red;
}
```

---

# COMBINATOR SELECTORS

---

# 6. Descendant Selector (Space)

## What is it?

Targets descendants.

Syntax:

```css
ancestor descendant
```

Example:

```css
div p {
    color:red;
}
```

HTML:

```html
<div>
    <p>A</p>

    <section>
        <p>B</p>
    </section>
</div>
```

Output:

```text
A → Red
B → Red
```

Because both are inside div.

---

## Meaning

```text
Inside anywhere
```

---

# 7. Child Selector (>)

## What is it?

Targets direct children only.

Syntax:

```css
parent > child
```

Example:

```css
div > p {
    color:red;
}
```

HTML:

```html
<div>
    <p>A</p>

    <section>
        <p>B</p>
    </section>
</div>
```

Output:

```text
A → Red
B → Not affected
```

---

## Meaning

```text
Immediate child only
```

---

# Descendant vs Child

Descendant:

```css
div p
```

```text
Any level deep.
```

Child:

```css
div > p
```

```text
Only one level down.
```

---

# 8. Adjacent Sibling Selector (+)

## What is it?

Targets next sibling.

Syntax:

```css
A + B
```

Example:

```css
h1 + p {
    color:red;
}
```

HTML:

```html
<h1>Title</h1>

<p>First</p>

<p>Second</p>
```

Output:

```text
First → Red
Second → Normal
```

---

## Meaning

```text
Immediately after
```

---

# 9. General Sibling Selector (~)

## What is it?

Targets all later siblings.

Syntax:

```css
A ~ B
```

Example:

```css
h1 ~ p {
    color:red;
}
```

HTML:

```html
<h1>Title</h1>

<p>One</p>

<p>Two</p>

<p>Three</p>
```

Output:

```text
All paragraphs become red.
```

---

## Meaning

```text
All following siblings
```

---

# ATTRIBUTE SELECTORS

---

# 10. Attribute Selector

Targets elements having an attribute.

Syntax:

```css
[attribute]
```

Example:

```css
[target] {
    color:red;
}
```

HTML:

```html
<a target="_blank">Link</a>
```

---

# 11. Exact Value Selector

Syntax:

```css
[attr="value"]
```

Example:

```css
input[type="text"] {
    border:2px solid blue;
}
```

---

# 12. Starts With

Syntax:

```css
[attr^="value"]
```

Example:

```css
a[href^="https"] {
    color:green;
}
```

Targets:

```text
https://...
```

---

# 13. Ends With

Syntax:

```css
[attr$="value"]
```

Example:

```css
img[src$=".png"] {
    border:1px solid black;
}
```

---

# 14. Contains

Syntax:

```css
[attr*="value"]
```

Example:

```css
a[href*="google"] {
    color:red;
}
```

---

# PSEUDO-CLASS SELECTORS

Pseudo-classes target STATES.

---

# 15. :hover

Mouse over.

```css
button:hover {
    background:red;
}
```

---

# 16. :focus

Element selected.

```css
input:focus {
    border:2px solid blue;
}
```

Useful for forms.

---

# 17. :active

While clicking.

```css
button:active {
    transform:scale(0.95);
}
```

---

# 18. :visited

Visited links.

```css
a:visited {
    color:purple;
}
```

---

# 19. :link

Unvisited links.

```css
a:link {
    color:blue;
}
```

---

# 20. :first-child

Targets first child.

Example:

```css
li:first-child {
    color:red;
}
```

---

# 21. :last-child

Targets last child.

```css
li:last-child {
    color:green;
}
```

---

# 22. :nth-child()

Targets position.

Example:

```css
li:nth-child(2) {
    color:red;
}
```

Second item.

Odd:

```css
li:nth-child(odd)
```

Even:

```css
li:nth-child(even)
```

---

# 23. :not()

Negation.

Example:

```css
p:not(.special){
    color:red;
}
```

Means:

```text
All paragraphs except .special
```

---

# PSEUDO-ELEMENT SELECTORS

Target PARTS of elements.

---

# 24. ::before

Insert content before.

```css
p::before{
    content:"★ ";
}
```

---

# 25. ::after

Insert content after.

```css
p::after{
    content:" ✓";
}
```

---

# 26. ::first-letter

First letter.

```css
p::first-letter{
    font-size:40px;
}
```

---

# 27. ::first-line

First line.

```css
p::first-line{
    font-weight:bold;
}
```

---

# 28. ::selection

Selected text.

```css
::selection{
    background:yellow;
}
```

---

# Selector Specificity (Interview Favorite)

Priority:

```text
Inline Style
↓
ID Selector
↓
Class / Attribute / Pseudo-class
↓
Element / Pseudo-element
↓
Universal Selector
```

Example:

```css
#box { color:red; }

.note { color:green; }

p { color:blue; }
```

HTML:

```html
<p id="box" class="note">
Hello
</p>
```

Output:

```text
Red
```

ID wins.

---

# Real Project Usage

Most Common:

```text
.class
.class:hover
input:focus
button:hover
:nth-child()
::before
::after
parent > child
```

Rare:

```text
~
$
^
*
```

Used when needed.

---

# Interview Questions

## Difference between ID and Class?

```text
ID → Unique
Class → Reusable
```

---

## Difference between Descendant and Child?

```css
div p
```

Any depth.

```css
div > p
```

Direct child only.

---

## Difference between Pseudo-Class and Pseudo-Element?

Pseudo-Class:

```css
:hover
:focus
:first-child
```

Targets state.

Pseudo-Element:

```css
::before
::after
::first-letter
```

Targets part of element.

---

# Selector Mental Model

```text
Selectors answer ONE question:

"WHO should receive this style?"

Basic Selectors
↓
Choose elements

Combinators
↓
Choose relationships

Attributes
↓
Choose properties

Pseudo-Classes
↓
Choose states

Pseudo-Elements
↓
Choose parts of elements
```

# One-Line Summary

> CSS selectors are the targeting system of CSS that allow you to precisely decide which elements, states, relationships, attributes, or portions of a webpage should receive styles.
