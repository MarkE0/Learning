# HTML & CSS

<!-- "Entry level cert in html and css" -->

## Rules
- Keywords are placed in angular brackets: `<` and `>`.
- Keywords may be in uppercase, lowercase, or a mixture of both.
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
- Help structure a web page by defining different parts of its content.
- **Improves accessibility**.
- Makes HTML code **more meaningful** and **easier to understand** for both developers and search engines.

```html
<header>  </header>                 A header section within a document. Can contain other tags, such as <h1>, <p>, etc.
<footer>  </footer>                 A footer section. Can contain other tags, such as <h1>, <p>, etc.
<nav>     </nav>                    Represents a navigation menu. Use it for site navigation links, such as <ul> or a <table>:
                                        <nav>
                                            <ul>
                                                <li><a href="/">Home</a></li>
                                                <li><a href="/about">About</a></li>
                                                <!-- More navigation items -->
                                            </ul>
                                        </nav>
<article> </article>                Specifies independent, self-contained content. An article should make sense on its own and can 
                                    be distributed independently from the rest of the website. Use it for blog posts, forum threads, 
                                    or news articles. May typically contain <h1>, <p>, etc tags.
<section> </section>                Defines a thematic grouping of content with a heading. It can represent chapters, introduction, 
                                    or other related sections. May typically contain <h1>, <p>, etc tags.
<details> </details>                <!-- TODO -->
<summary> </summary>                <!-- TODO -->
<main>    </main>                   Defines the main content of a document. There should be only one <main> per page.
<figure>  </figure>                 <!-- TODO -->
    <figcaption> </figcaption>      See also bootstrap..
```
