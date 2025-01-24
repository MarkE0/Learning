# CSS Fundamentals

## Referencing Style Definitions
Styles can be applied:
- **Inline**: Directly in the HTML element `<div style="color: red;">` although this can make things more difficult to maintain.
- **Embedded**: Using the `<script>` tag inside the `<head>` section, styles can be defined.
- **External**: Generally, it's best to define all CSS styles in a separate file that is referenced..

**Priority in execution**: Inline > Embedded > External

```html
<head>
    <link rel="stylesheet" href="styles/mystyles.css"> <!-- Referencing an EXTERNAL style Sheet -->

    <style>
        .embedded-style { /* Defining an EMBEDDED style sheet */
            color: blue;
        }
    </style>
</head>

<body>
    <div style="color: red;">Div using the inline Style.</div>                                       <!-- Defining & using an INLINE style -->
    <p  class="embedded-style">Paragraph using the embedded Style.</p>                               <!-- Using the EMBEDDED style from HEAD -->
    <h1 class="external-style">Heading with external style.</h1>                                     <!-- Using the EXTERNAL style -->
    <h1 class="external-style" style="color: yellowgreen;">External style overridden by Inline.</h1> <!-- Inline overrules external -->
</body>
```

`styles/mystyles.css`:
```css
/* External styles */
.external-style {
    font-size: 24px;
    font-weight: bold;
    color: blueviolet;
}
```


## Rule Sets
- Fundamental construct in CSS, consisting of:
  - **Selector**: The HTML element to be styled (see below).
  - **Declaration Block**: Contains one or more (semicolon separated) declarations, of the form `property: value;`


### Selectors

Selectors are patterns used to select the elements to be styled.

```css
/* Element Selector. Recognised HTML tags. */
p {
    color: blue;
}

/* Grouping Selectors. Comma separated list to apply same rules to multiple elements. */
th, td {
    color: blue;
}

/* Class Selector. Defined new class. Used with class="myClass" (no dot in front). Case sensitive. */
.myClass {
  font-size: 26px;
}

/* ID Selector. Unique ID for style to apply to single element only. */
#myID {
  background-color: yellow;
}

/* Descendant Selector. Apply to <p> elements inside the container. */
.container p {
  font-weight: bold;
}

/* Pseudoclass Selectors. Apply to specific part of element, e.g. link new / visited. */
a:link {
    color: white;
}
a:visited {
    color: grey;
}
a:hover {
    color: yellow;
}
/* MEP/TODO: Another example: 
.container p:first-child::first-letter { . . }*/

.container > div:nth-of-type(2) {
    flex: 2;                    /* For the nth (e.g. 2nd) div, grow at twice the rate of surrounding div (see flex below).  */
}

/* Attribute Selectors. Apply where a tag hsa an attribute */
img[title="one day ago"] { .. } /* Apply where the attribute matches exactly */
img[src~="day"] { .. }          /* Apply where the attribute has a word matching */
img[src|="day"] { .. }          /* Apply where the attribute is an exact match, or exactly matches up to a hyphen */
img[src^="day"] { .. }          /* Apply where the attribute starts with the value */
img[src$="day"] { .. }          /* Apply where the attribute ends with the value */
img[src*="day"] { .. }          /* Apply where the attribute contains the value anywhere in it */

/* The Universal Selector. Apply to all elements on the page. */
* {
  color: #333;
}
```

Sample use of above in HTML:
```html
<body>
    <p>This is the Element Selector</p>
    <p class="myClass">This is the Class Selector</p>  <!-- Specify a class to use. Note: This is case sensitive. -->
    <p id="myID">This is the ID Selector</p>           <!-- ID is used once generally, as opposed to a class which would be used many times -->
    <div class="container">                            <!-- A descendant selector allows for an alternative set of styles within a section of the webpage -->
        <p>This is the Descendant Selector</p>
    </div>
    <a href="https://www.microsoft.com">Microsoft</a>  <!-- A link will use the a:hover (etc) Pseudoclass Selectors -->

</body>
```

**Note**: The order can be important on selectors, e.g. Visited should be listed *before* Hover, otherwise Visited would take precedence when hovering over, and nothing would change.





## Style Declarations

```css
.font {
    color: red;                     /* Font colour. Can use a colour name, or hex number. */
    background-color: #f0f0f0;      /* Hex colours must use "#" and be either 6 or 3 digits (e.g. #1166bb = #16b) */

    font-family: Arial, sans-serif; /* Try Arial, and if not available try sans-serif (without curly bits in font). Careful: Fonts may not be available */
    font-size: 2em;                 /* Set font size as pixels or "em" which is a multiplier of the original size, e.g. 1.5 times the normal size. */
    font-weight: bold;              /* Weight/bold */
    line-height: 1.6;               /* Specify the height of text lines, as a multiple of a single line. e.g. 1.5 */
}
```

For websafe fonts, see [w3schools](https://www.w3schools.com/cssref/css_websafe_fonts.php). Here are a few example:

- Arial (sans-serif)
- Verdana (sans-serif)
- Tahoma (sans-serif)
- Times New Roman (serif)
- Courier New (monospace)

```css
.marginPadding {
    margin: 0;                      /* Margin is the space oOUTSIDE an element, between it and the parent container.
                                       Non-zero values should use "px". Set to zero on body element to remove outer spaces. */
    margin: 20px auto;              /* Shorthand example to set top and bottom to 20px, left & right auto (center) element */
    margin-left: auto;              /* Can specify each side. Use "auto" on left and right, to centre/center an element. */
    padding: 0;                     /* Padding is the space INSIDE an element, between it and some content. */
}

.general {
    border: 1px dashed;             /* Short hand for below border stylings. */
    border-width: 1px;              /* Thickness of border. Can be px or word (e.g. "thin"). Can have each different. */
    border-style: dashed;           /* Type of line for borders: dotted, solid, dashed, double. Can have each different. */
    border-color                    /* Colour of border. */
    border-radius: 5px;             /* Round the corners of an element (e.g. div or img) by pixels or percentage. */

    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Shadow around an element, e.g. a div tag. Values represent: horizontal offset,
                                                vertical offset, blur (width-ish), colour. Other optional definitions available. */
    box-sizing: border-box;         /* Calculate box width, with margin considered on the inside. Useful if calculating size for
                                       boxes beside eachother: Width 200px + Margin 10px + Padding 10px = Total width 200px. */
    list-style-type: none;          /* Don't use bullet points. */
}

.positioning {
    float: left;                    /* Position an element (e.g. img) on the left or right. Text will float around it. */

    position: static;               /* Default. Display in expected place, as per html definition. Will not act as anchor for children. */

    position: relative;             /* Move the element 20 pixels to the left of where it would otherwise appear in normal layout. Anchor. */
      left: -20px;

    position: absolute;             /* Position relative to parent (if an anchor - not static) */
      top: 5px;                       /* Can position based on top, left, right, bottom. */
      left: 5px;

    position: fixed;                /* Position relative to the viewport, not the parent. e.g. the browser window itself. */
      bottom: 10px;                   /* Place 10 pixels up/out from the  the bottom right. Won't move with scrolling. */
      right: 10px;/* */
}

.layout {
    max-width: 800px;               /* Set a maximum width. Will cause line to wrap when reached. */
    height: 100vh;                  /* Height of element. Can use percent (of parent), px, vh, etc.
                                       "vh" is the percentage of the Vertical Height of the window. (See also "vw" for width.) */
    width: 80%;                     /* Width of element. Similar to height. */
    overflow: hidden;               /* Specify what happen when content can't fit inside above defined height.
                                       "visible" (default) spills out, "clip"/"hidden" shortens, "scroll"/"auto" scrolls. */

    text-align: center;             /* Horizontal alignment of text in an element. */

    display: inline;                /* Display behaviour of an element. Default is "inline". "block" will break the line
                                       before and after. "none" will omit the element completely. */
}

.visibility {
    visibility: hidden;             /* An element can be "visible" or "hidden". When hidden, it still takes up the expected space. */
}

.cursor {
    cursor: pointer;                /* Style the cursor as a pointer, grab, etc. */
}
```

## Flex and Media Queries
https://www.w3schools.com/css/css3_flexbox_container.asp
```css
.flex-parent {
    display: flex;                  /* Responsive grid using Flex container. Block type, but can also specify inline type. */
    flex-wrap: wrap;                /* Specify if flexible items should wrap or not. */
    justify-content: space-around;  /* Child spacing: center, space-around (centre evenly), flex-start/end, space-between. */
}

.flex-child {
    flex: 1;                        /* Shorthand for the below */
    flex-grow: 1;                   /* Specify how an element grows in relation to others in the same container. */
    flex-shrink: 1;                 /* Similar to above. */
    flex-basis: 100px;              /* Initial length of a flexible element. */
    width: 70%;                     /* Specify some property which may then change on window resize. */
}
```

### Breakpoints
```css
@media (max-width: 768px) {         /* Media Query for responsiveness - Apply this when viewport width below 768px. */
    .flex-child {
        flex: 1 0 100%;             /* Adjust column size on smaller screen. */
        width: 100%;                /* The property adjust (from 70% above) to a new value on window resize. */
    }
}


@media (min-width: 576px) {
.container {
    width: 80%;                     /* Adjusting container width at a specific breakpoint - 576px */
}
}

@media (min-width: 992px) {
.container {
    width: 70%;                     /* Adjusting container width at a different breakpoint - 992px  */
}
}
```

### Print and Screen
```css
@media print {                      /* Specify how printing is handled.. */
    .nonPrintElement {
        display: none;              /* ..in this case, hide elements using this class when printing. */
    }
}

@media screen and (min-width: 768px) { .. } /* When on a screen display with width more than 768px.. */
```


## Images, Audio, Video

```css
img {
  object-fit: cover;                /* Define how an image or video should fit into it's parent/container
                                        fill (may stretch), cover (fill, no stretch), contain (fit, no fill) */
}
```
