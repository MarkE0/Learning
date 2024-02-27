# HTML & CSS

<!-- "Entry level cert in html and css" -->

## Rules
- Keywords are placed in **angular brackets**: `<` and `>`.
- Keywords may be in uppercase, lowercase, or a mixture of both, although **lower case is recommended**.
- Closing tags (e.g. "`</title>`") do not have parameters.
- Anything in angular brackets not recognised by the browser is ignored.
- Some element parameters (e.g. "align") are deprecated, so this type of styling should instead be set in CSS
  - VSCode can assist in identifying deprecated items, and provide a hover-over tip.


## Basic Format
```html
<html>
    <head>
        <title>Test</title>
    </head>

    <body>
        Hello World!
    </body>
</html>
```

## Initial tags
```html
<!DOCTYPE html>                     All HTML documents must start with this declaration. Not case sensitive.
          html                      Here html refers to HTML5.

<html lang="en"> </html>            Root of the HTML document. All elements (excl. DOCTYPE) should fall within the <html> tags.
      lang="en"                     Always declare the language of the webpage to assist search engines and browsers.
                                      See links below for Language Codes.
```


## Head Section
```html
<head> </head>                      Container for meta data, title, embedded CSS styles.

<meta charset="UTF-8">              Metadata is information about the page. Used by browsers, search engines, and web services.
      charset="UTF-8"               Specifies the character encoding for the page.
      name="description"            Name/type of data. Here it is the page description. Paired with a "content" tag.
        content="Page description"
      name="keywords"               Keyword for search engines, e.g. content="HTML, CSS, JavaScript".
      name="viewport"               Viewport is the users visible area of a webpage. Accessing on phone, browers, etc.
        content=".., .."              Comma separated list of values:
            width=device-width          Sets page width following the width of screen on the display device.
            initial-scale=1.0           Set the initial zoom of the page when loaded the first time.

<title>My Page</title>              Page title to display in title/tab bar or bookmark. 
                                      Having a different title on every page helps with SEO.

<link rel="stylesheet" href="1.css"> Reference an external CSS style sheet.

<style> </style>                    If using Embedded styles, they should be defined in the head. Appear AFTER meta tags.
                                      See also CSS notes.
```


## Body Section

### Semantic Tags
Non-semantic elements:
- Examples: `<div>` and `<span>`
- Don’t provide any inherent meaning.

Semantic elements:
- **Clearly describe their meaning** to both browser and developer. 
- Help **structure a web page** by defining different parts of its content.
- **Improve accessibility**.
- Makes HTML code **more meaningful** and **easier to understand** for both developers and search engines.

```html
<header>  </header>                 A header section within a document. Can contain other tags, such as <h1>, <p>, etc.

<footer>  </footer>                 A footer section. Can contain other tags, such as <h1>, <p>, etc.

<nav>     </nav>                    Represents a navigation menu. Use it for site navigation links, such as <ul> or a <table>:
                                        <nav>
                                            <ul>
                                                <li><a href="/">Home</a></li> |
                                                <li><a href="/about">About</a></li>
                                                <!-- More navigation items -->
                                            </ul>
                                        </nav>

<article> </article>                Specifies independent, self-contained content. An article should make sense on its own and can 
                                     be distributed independently from the rest of the website. Use it for blog posts, forum threads, 
                                     or news articles. May typically contain <h1>, <p>, etc tags.

<section> </section>                Defines a thematic grouping of content with a heading. It can represent chapters, introduction, 
                                     or other related sections. May typically contain <h1>, <p>, etc tags.

<details> </details>                Defines additional details that can be opened (display content) or closed (default) on demand.

  <summary> </summary>              Defines *visible* heading for <details> element which can be clicked to view/hide the details.
                                        Note: Must be the first child element within <details>.

<main>    </main>                   Defines the main content of a document. There should be only one <main> per page.

<figure>  </figure>                 Specifies self-contained content (e.g. images/diagrams/code). May contain <img> for example.

  <figcaption> </figcaption>        Defines a caption for the <figure> element.
```


### General Tags
```html
<div>     </div>                    Division. Contains any other elements. Useful for applying specific styles. Causes line break.

<a href> COME BACK TO <!-- ! TODO -->

<p>       </p>                      Paragraph.
     style="text-align:right"         Specify alignment via style ("align" keyword is deprecated).

<span>    </span>                   Can define a section of a line, without getting line breaks (unlike a div which will break).
```


### Lists
```html
<ul>      </ul>                     Unordered (bulleted) list.

<ol>      </ol>                     Ordered (numbered) list.

  <li>List item 1</li>              List items are enclosed in <li> tags, and appear within <ul> or <ol> sections.
```


### Tables
```html
<table  > </table>                  Open a table. Tables very useful for controlling page layout. Use CSS to style.
    width="100%"                      Define the width of the table relative to the browser window.
    border="0"                        DEPRECATED. Define the border. Use CSS to do this instead.
    align="center"                    DEPRECATED. Alignment. Use CSS instead.

  <tr>    </tr>                     Open a table row.

    <th>Header 1</th>               Define a table header column (inside row).

    <td>Data 1</td>                 Define a table data/cell (inside a row). Use a different row to the header.
      colspan="2"                     Let the cell span two cells (compared to other rows).
      style="color: red;"             Apply CSS styling directly to a cell. (External CSS preferrable.)
```


### Forms
- Can interweave a table into a form, to assist with **aligning fields** as required.
```html
<form>      </form>                 Open a form.
  action="[URL]"                      Where to send data when submitted. E.g. "http://localhost:3000/submit".
  method="post"                       Method to use. GET: Get webpage, POST: Send data.
  name="text"                         Name of the form.
  autocomplete="on"                   Allow (or disallow) autocompleting fields on the form.

  <label >  </label>                A label to be used for a form field. Can appear before or after input element.
    for="username"                    Expclicitly associate the label with the field by name. Makes label clickable.

  <input >                          Input field on form. Can be one of many different types. No closing tag.
    type="text"                       Type of input - text / email / password / etc.
    id="username"                     Unique identifier for the field.
    name="username"                   Field name submitted to server. e.g. username: Bob
    maxlength="20"                    Max length of field input. See also minlength.
    placeholder="Username"            Placeholder (ghost) text.
    required                          Field must be filled out before submitting.
    autofocus                         Specify that the field should get focus when page loads.

    type="checkbox"                   Check box type. Specifying the <label> after can make easier to use.
      value="yes"                       Default to checked.

    type="radio"                      Radio buttons - select only one from the associated "name" fields.
      name="gender"                     Name used for submission but also for grouping radio fields.
      value="male"                      Value to be sent back on submission.
    
  <select >     </select>           Dropdown selection.
    id="country"                      Identifier.
    name="country"                    Name for submission

    <option >USA</option>             Options inside the <select>. Use text inside <option> tags for displaying in dropdown.
        value="usa"                     Value to return if option chosen in dropdown.

  <textarea >   </textarea>         Text area.
    id="message"                      ID.
    name="message"                    Name for submission.
    rows="4"                          Size - number of rows.
    cols="50">                        Size - number of columns.

  <button >Submit</button>          Button on form, e.g. Submit.
    type="submit"                     Type of button - submit / button / reset.
```


### Multimedia
```html
<img >                              Embed and image in a webpage.
  src="images/car.png"                Source of the image, i.e. directory and name.
  alt="A picture of a car"            Text alternative for accessibility. Shows if image not displayed.
  title="My first car"                A title for the image. Shown when mouse hovers over the image.
  usemap="#map"                       Specify a map to use for applying links.

<map >      </map>                  Define a map.
  name="map"                          The name of the map. Used in the reference tag "usemap" of an img.

  <area >                           Defines areas inside an image which will be hyperlinked.
    shape="rect"                      Shape - rectangle.
    coords="40,70,380,440"            Coordinate from top-left to bottom-right - x1,y1,x2,y2.
    href="location1.html"             Link to go to.
    alt="Location 1"                  Alt text for area. Required when using href.

    shape="circle"                    Shape - circle.
    coords="100,100,50"               Circle location and radius - x,y,radius.

    shape="poly"                      Shape - polygon.
    coords="200,200,250,250,200,300"  Polygon coordinates - x1,y1,x2,y2,..,xn,yn.


<picture>                           More flexible way to specify image reourses, e.g. responsive to width of window.
  <source  >                        Source for the parent (<picture>) element.
    srcset="images/p800.jpg"          Srcset specifies an image source.
    media="(min-width: 800px)"        Media query defined as CSS. min-width means image will only display screen if larger than 800.
    alt="Alternative text"            Alt text to show if image not displayed.
    title="Title for image"           Title text for mouse hover over.

  <source srcset="images/p600.jpg"  
       media="(min-width: 600px)">    If screen larger than 600px, display this image (priority over above).

  <img src="images/default.jpeg">     If neither of the above apply (less than 600px) display a default image.
</picture>
```



### Script / No Script
Using JavaScript directly in the body:
```html
<script> /* Javascript to log to console - seen in browser: right click > Inspect page */
    document.addEventListener('DOMContentLoaded', function() {
        console.log('DOM is loaded');
    })
</script>
```

Handling when a browser doesn't support JavaScript, or has it disabled.
```html
<noscript>
Browser does not support JavaScript!
</noscript>
```



## CSS Fundamentals

### Styles
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


### Selectors

Selectors are patterns used to select the elements you want to style.

```css
/* Element Selector. Recognised HTML tags. */
p {
    color: blue;
}

/* Multiple elements. Comma separated list. */
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

/* Pseudoclass Selector. Apply to states, e.g. link new / visited. */
a:link {
    color: white;
}
a:visited {
    color: grey;
}
a:hover {
    color: yellow;
}
```

Sample use of above:
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





### Style Definitions (some)

ADD MORE..

```css
body {
    font-family: Arial, sans-serif; /* Try Arial, and if not available try sans-serif (without curly bits in font). Careful: Fonts may not be available */
    line-height: 1.6;               /* What is this? */
    
    margin: 0;                      /* Top, left, right - may be better to use px */
    padding: 0;                     /* Padding body of page (may need px?)*/

    color: red;                     /* Can use a colour name */
    background-color: #f0f0f0;      /* Hex colours must use "#" and be either 6 or 3 digits (e.g. #1166bb = #16b) */
}

.container {                        /* If starting with a dot, it is a Class. Body is not a class. */
    width: 80%;                     /* Percentage of parent (whole page) */
    margin: 20px auto;              /* Margin is outside - between it and the parent container */
    background-color: #fff;         /* Set a different background colour to the body of the page */
    padding: 20px;                  /* Happens inside the container/box */
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Shadow around an element, e.g. a div tag */
}
```






## JavaScript
```javascript
<script> /* Javascript to log to console - seen in browser: right click > Inspect page */
    document.addEventListener('DOMContentLoaded', function() {
        console.log('DOM is loaded');
    })
</script>
```
