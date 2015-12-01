# <a href="#formatting"></a>HTML Formatting

## Output

All html formatting standards are written with source files in mind. If you're using a build process, templates, or partials, the source files (not the build files) are the ones that need to follow the outlined standards.

## Closing Tags

All elements should be closed via a tag pair or self closing declaration.

```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
```

```html
<input type="text" />
```

## Indentation

Use 4 spaces for indenting.

Place block, list and table elements on a new line and indent the new line 4 additional spaces.

```html
<div>
    <ul>
        <li><a href="page.html">Link</a></li>
        <li><a href="page.html">Link</a></li>
    </ul>
</div>
```

When using templating logic to generate markup, indent each new line 4 additional space.

```html
{{#if}}
    <div>
        ...
    </div>
{{/if}}
```

## Trailing Whitespace

Remove all trailing whitespace.

## Capitalization

Use only lowercase.

This applies to element names, attributes, and attribute values (unless strings).

```html
<img src="felix.png" alt="Felix, a cat, wrestles with his yarn playfully" />
```

## Quotes

Use double quotes around attribute values.

```html
<input type="text" />
```
## Boolean Attributes

Boolean attributes should not have a value.

```html
<input type="text" disabled />
```

## Comments & Grouping

Use standard HTML comments to indicate the beginning and end of large sections of code.

```html
<!-- Main Content -->
<div>
    ...
</div>
<!-- // End Main Content -->
```

## TODO Comments

Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.

```html
<!-- TODO - Review content styles -->
<div>
    ...
</div>
```
# <a href="#bestpractices"></a>HTML Best Practices

## W3C Validation

* Write valid code.
* Remaining errors and warnings should be intentional.

**Resources**

* <http://validator.w3.org/>

## Doctypes

Use the HTML5 doctype.

```html
<!doctype html>
```

**Resources**

* <http://www.alistapart.com/articles/doctype/>
* <https://css-tricks.com/snippets/html/the-common-doctypes/>
* <http://en.wikipedia.org/wiki/Document_type_declaration>


## Encoding

Use UTF-8 encoding. This meta tag should always be the very first element inside of the document's `<head>` element.

```html
<meta charset="utf-8" />
```

If you end up working in code that does not use an HTML5 doctype, use the meta tag associated with the proper doctype.

```html
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
```
## HTML5 Usage

Not all projects warrant the use of HTML5 elements, but when they do, use HTML5 elements and attributes that progressively enhance modern browsers.

**Use**

- `<div data-controller="exampleDataController"></div>`
- `<input type="email" placeholder="example@domain.com" />`
- `<input type="search" />`
- `<input type="tel" />`
- `<input type="url" />`
- `<input type="text" required />`
- `<article></article>`
- `<aside></aside>`
- `<figure></figure>`
- `<footer></footer>`
- `<header></header>`
- `<mark></mark>`
- `<nav></nav>`
- `<section></section>`
- `<time></time>`
- `<small>&copy; 2015 The Nerdery</small>`

**Use with Caution**

- `<audio></audio>`
- `<canvas></canvas>`
- `<video></video>`
- `<figcaption></figcaption>`
- `<keygen></keygen>`
- `<main></main>`
- `<meter></meter>`
- `<progress></progress>`
- `<output></output>`

**Do Not Use**

- `<datalist></datalist>`
- `<dialog></dialog>`
- `<details></details>`
- `<summary></summary>`
- `<menu></menu>`
- `<menuitem></menuitem>`
- `<hgroup></hgroup>`
- `<wbr>`
- `<bdi>`

**Special Consideration**

Entirely new elements like `<video>` should use appropriate markup based fallbacks so the content is still accessible even if the browser can't render it.

```html
<video width="640" height="360" controls>
    <source src="cats.mp4" type="video/mp4" />
    <source src="cats.ogv" type="video/ogg" />
    <object width="640" height="360" type="application/x-shockwave-flash" data="cats.swf">
        <param name="movie" value="cats.swf" />
        <param name="flashvars" value="controlbar=over&amp;image=cats.jpg&amp;file=cats.mp4" />
        <img src="cats.jpg" width="640" height="360" alt="Download the video below" />
        <a href="cats.mp4">Download cats mp4 file</a>
        <a href="cats.OGV">Download cats ogv file</a>
    </object>
</video>
```

**Resources**

* <https://status.modern.ie/>
* <http://caniuse.com/>


## HTML5 Form Validation

By default, many HTML5 form inputs include validation that is provided by the browser. Error messages are on by default, though in many cases the browser implemented messages are not what a designer wants. In order to remove validation (and thereby the messages) use the `novalidate` attribute on the containing form.

```html
<form action="#" method="post" novalidate>
    <label for="email">Email address:</label>
    <input type="email" placeholder="example@domain.com" id="email" />
    <button type="submit" id="submit">Submit</button>
</form>
```

**Resources**

* <http://diveintohtml5.info/forms.html#validation>


## Optional Tags

Include tags deemed optional in HTML5 (`<html>`, `<head>`, `<body>`)

```html
<!doctype html>
<html>
    <head>
        <title> ... </title>
    </head>
    <body>
        <p> ... </p>
    </body>
</html>
```

## Type Attributes

**HTML5 Doctype**

When working with the HTML5 doctype, omit `type` attributes for stylesheets and scripts.

```html
<link rel="stylesheet" href="screen.css" />
<script src="global.js" />
```

**Legacy Doctypes**

When working with legacy doctypes older than HTML5, include `type` attributes for stylesheets and scripts.

```html
<link rel="stylesheet" href="screen.css" type="text/css" />
<script src="global.js" type="text/javascript" />
```

## Protocol

Whenever possible, omit the protocol portion (`http:`, `https:`) from URLs.

```html
<link rel="stylesheet" href="//www.nerdery.com/assets/styles/screen.css" />
<a href="//www.nerdery.com/">The Nerdery</a>
```

## HTML Entities

Use the appropriate HTML entity names or numbers for special and reserved characters.

```html
&copy; 2012-2015 Crispin &amp; Mulberry &#8482;
```
## Semantic Markup

Write clean semantic markup that clearly reinforces the meaning of the page content.

```html
<nav>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About Us</a></li>
        <li><a href="#">Resources</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

```html
<div>
    <small>&copy; 2012 The Nerdery</small>
</div>
```

When generic containers are needed, use `<div>` for block level elements and `<span>` for inline elements.

**Resources**

* <http://en.wikipedia.org/wiki/Semantic_Web>
* <http://vimeo.com/38594726>
* <http://microformats.org/wiki/posh>

## Document Outline

Craft a proper document outline by using appropriate heading levels in a linear fashion.

When necessary, use headings that are hidden in an accessible way to enhance the document outline.

Note that the outline algorithm has changed in HTML5 with the use of new sectioning elements (nav, article, section and aside), allowing the creation of a document outline without using headings in a linear, hierarchical fashion. **Do not do this**. Craft an outline that is complete and accurate from a pre-HTML5 point of view.

### HTML4

```html
<h1>The Nerdery</h1>
<h2 class="isVisuallyHidden">Featured Content</h2>
<h3>Nerdery Primer</h3>
<h3>Best Place To Work</h3>
<h3>Overnight Website Challenge</h3>
<h2>A developer-driven interactive production shop</h2>
<h3 class="isVisuallyHidden">Statistics</h3>
<h3>What Makes Us Different</h3>
<h4>Partnership-Based Method</h4>
<h4>Technology Agnosticism</h4>
<h4>Size & Scale</h4>
<h4>Methodical & Transparent</h4>
```

**Resources**

* <http://html5doctor.com/outlines/>
* <http://www.456bereastreet.com/archive/201205/make_sure_your_html5_document_outline_is_backwards_compatible/>
* <http://html5forwebdesigners.com/semantics/index.html#sectioning_content>
* <http://webaim.org/projects/screenreadersurvey/#headings>
* <http://www.paciellogroup.com/blog/2013/10/html5-document-outline/>
* <http://www.w3.org/TR/html5/sections.html#headings-and-sections>

## Microdata, Microformats and RDFa

Microdata, microformats and RDFa are all approaches to marking up certain types of data in a machine readable way. Search engines and devices/browsers can leverage this increased semantics in various useful ways. While most search engines currently support all three, Google and the WHATWG are putting their weight behind microdata and this is our preferred method of implementing rich data.

### When to use

Here are some examples of places where we can use microdata:

- Creative Work
- Event
- Person
- Place
- Organization
- Product
- Review
- Rating

Get to know the various types of data that will benefit from this type of markup and leverage this increased semantics whenever possible.

```html
<div itemscope itemtype="http://schema.org/Product">
    <h2 itemprop="name">Strawberry Champagne Vinaigrette</h2>
    <a href="/shop-our-products/strawberry-champagne-vinaigrette" itemprop="url">
        <img src="/media/images/products/strawberry-champagne-vinaigrette.jpg" alt="" itemprop="image" />
    </a>
    <div>
        Item: <span itemprop="sku">753604</span>
    </div>
    <div itemprop="description">
        Drizzle this sweet, gorgeous ruby dressing over salads or grilled meats. Limited time.
    </div>
    <div itemprop="aggregateRating" itemscope itemtype="http://schema.org/AggregateRating">
        <div>
            <span itemprop="ratingValue">3</span> stars
        </div>
        <div>
            <span itemprop="reviewCount">4</span> reviews
        </div>
    </div>
    <div itemprop="offers" itemscope itemtype="http://schema.org/Offer">
        <span itemprop="price">$8.99</span>
    </div>
</div>
```

**Resources**

* <http://schema.org/docs/gs.html>
* <https://developers.google.com/structured-data/rich-snippets/?hl=en&rd=1>
* <http://schema.org/docs/faq.html?hl=en&rd=1>
* <https://developers.google.com/structured-data/?hl=en&rd=1>
* <http://microformats.org/get-started>
* <http://html5doctor.com/microformats/>

## Image Formats

Know image formats well and choose the best format for each scenario. The goal is the best image quality at the smallest file size.

**Resources**

* <http://en.wikipedia.org/wiki/JPEG>
* <http://en.wikipedia.org/wiki/Portable_Network_Graphics>
* <http://en.wikipedia.org/wiki/GIF>

## Image Usage

Consider options carefully when choosing whether or not images will be included as inline images or background images. If an image is considered to be content or if a content editor would want to change the image, it should be inline in the markup as an `<img>` element. If an image is used to enhance the visual aesthetics of the interface and supplies no extra meaning to the markup it should be a CSS background image.

## Table Usage

Tables should be reserved for tabular data and never used to achieve page layout.

To make tables semantic and accessible, always:

* Use `<thead>`, `<tbody>` and `<tfoot>` to differentiate between the table header, table body, and table footer
* Use `<tr>` to separate table rows
* Use `<th>` for table headers and `<td>` for table data
* Include a proper scope on the `<th>`


```html
<table>
    <thead>
        <tr>
            <th scope="col">Year</th>
            <th scope="col">Make</th>
            <th scope="col">Model</th>
            <th scope="col">Color</th>
            <th scope="col">Horsepower</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>2000</td>
            <td>Toyota</td>
            <td>Matrix</td>
            <td>Silver</td>
            <td>140hp</td>
        </tr>
        <tr>
            <td>2007</td>
            <td>BMW</td>
            <td>328xi</td>
            <td>Jet Black</td>
            <td>255hp</td>
        </tr>
    </tbody>
</table>
```