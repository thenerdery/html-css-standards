# <a href="#formatting"></a>CSS Formatting

## Capitalization

Use camelCase for selector names and lowercase for properties & property values (unless strings).

```css
.mySelector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Name Delimiters

For more information on classes, class members, class extensions and class mixins, read the [methodology](/standards/methodology.md/).

**Class Names**

Use camelCase for class names.

```css
.featurePromo {
    padding: 10px;
    border: 1px solid #bbbbbb;
    background: #ffffff;
}
```

**Sub Components**

Use a hyphen before a class member (sub-component) name, prefixed with the base class name. The class member name is camelCased.

```css
.featurePromo-hd {
    margin-bottom: 10px;
}

.featurePromo-bd {
    position: relative;
    padding: 5px;
}

.featurePromo-ft {
    border-top: 1px solid #000000;
}

.featurePromo-statusMessage {
    padding: 10px;
    border: 1px dotted #ff0000;
}
```

**Extensions**

Use an underscore before a class extension name, prefixed with the base class or sub-component class it extends. The extension name is camelCased.

```css
.featurePromo_primary {
    border-color: #ff0000;
    background: #aa6600;
}

.featurePromo_lastChild {
    border: none;
}

.featurePromo-bd_inset {
    padding: 20px;
}
```

**Mixins**

Use `mix-` followed by the base class, then the rest of the class extension name. The extension name is camelCased.

```css
.hdg {
    font-family: arial, helvetica, sans-serif;
    font-size: 32px;
    font-weight: bold;
    text-transform: uppercase;
    color: #000000;
}

.hdg_1 {
    font-size: 30px;
}

.hdg_2 {
    font-size: 20px;
}

.mix-hdg_brandColor {
    color: #cccccc;
}
```

**States**

Use an underscore between a state class and the class it extends. Prefix the state class name with `is`. The state name is camelCased

```css
.menuItem_isActive {
    font-weight: bold;
    text-decoration: underline;
}
```

**Themes**

Name class theme extensions prefixed with `theme-` followed by the base class, then the rest of the class extension name. The extension name is camelCased

```css
.masthead {
    background: #333333;
}

.theme-masthead_cats {
    background: transparent url("../images/cat-bg.jpg") no-repeat 0 0;
}

.theme-masthead_wolfPack {
    background: transparent url("../images/3-wolves-bg.jpg") no-repeat 0 0;
}
```

## Brackets

Place the opening curly-bracket of each rule block on the same line as the last selector.

Place the closing curly-bracket of each rule block on its own line after the final property of the rule block.

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Indentation

Use 4 spaces for indenting.

Indent each property in a rule block 4 spaces.

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Property Whitespace

Put each property on its own line.

Follow each property with a colon and a single space.

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Semi-colons

Follow each property value with a semi-colon.

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Trailing Whitespace

Remove all trailing whitespace.

## Rule Block Separation

Separate each rule block by an empty line.

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}

.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Property Order

CSS properties should be grouped by commonality (display, then box-model, then positioning, then background/color, then typography, then misc/etc).

```css
.selector {
    display: block;
    width: 400px;
    height: 222px;
    padding: 4px;
    margin: 2px;
    position: absolute;
    top: 22px;
    left: -12px;
    color: #ffffff;
    font: 12/1.2 normal Helvetica, Arial, san-serif;
    text-transform: uppercase;
    text-indent: 0;
}
```

## Vendor Prefixes

Include vendor prefixes for all properties that have had a vendor prefix in the past.

It is not necessary to include vendor prefixes for specific rendering engines if it never existed.

Include the W3C standard property after the vender prefixed properties.

```css
.selector {
    -webkit-border-radius: 6px;
    -moz-border-radius: 6px;
    border-radius: 6px;
}
```

```css
.selector {
    -webkit-transform: rotate(40deg);
    -moz-transform: rotate(80deg);
    -ms-transform: rotate(40deg);
    -o-transform: rotate(40deg);
    transform: rotate(40deg);
}
```

**Resources**

* <http://caniuse.com/>

## Multi-Value Properties

Format multi-value properties by starting a new line for each value and indenting each line 4 spaces.

```css
.selector {
    background: transparent url("space.png") repeat-x 0 0;
    background:
        transparent url("stars-1.png") repeat-x -130% 0,
        transparent url("stars-2.png") repeat-x 40% 0;
}
```

## Single Properties

It is acceptable to put rule blocks with a single property on a single line.

Include a space after the opening bracket and before the closing bracket.

```css
.selector { background-position: 0 -100px; }
```

No line break is required between rule blocks when the selectors are part of the same object and the properties match.

```css
.icn_twitter { background-position: 0 -100px; }
.icn_facebook { background-position: 0 -200px; }
.icn_youtube { background-position: 0 -300px; }
```

## Quotes

Use double quotes.

**File Paths and Data URIs**

Use double quotes for file paths and data URIs.

```css
.selector {
    background-image: url("background.png");
}
```

**Font Family**

Use double quotes for font names unless they are system fonts that don't require them.

```css
.selector {
    font-family: "LeagueGothic", Helvetica, Arial, sans-serif;
}
```

**Generated Content**

Use double quotes around generated content values.

```css
.selector:before {
    content: "Chapter:";
    display: inline;
}
```

**Attribute Selectors**

Use double quotes around values in attribute selectors.

```css
input[type="text"] {
    color: #ff0000;
}
```

## Multiple Selectors

Separate multiple selectors in the same rule block with a comma and place each selector on a new line.

```css
.navItem:focus,
.navItem:active {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

## Comments & Grouping

Group related rule blocks by base object using the standardized section comment style.

```css
/* ---------------------------------------------------------------------
Box
------------------------------------------------------------------------ */

.box {
    padding: 20px;
    background-color: #cccccc;
}
```

If a section requires additional subsets of comments, a single line comment is acceptable.

If a property / value pair needs additional clarity or is not self-documenting, add comments on the same line immediately following the value.

```css
/* ---------------------------------------------------------------------
Horizontal List
------------------------------------------------------------------------ */
.hList {
    overflow: hidden;
    *zoom: 1; /* ie6-7 float clearing */
}

.hList > * { float: left; }

/* horizontal spacing extensions */
.hList_tight > * + * { margin-left: 8px; }
.hList_std > * + * { margin-left: 16px; }
.hList_loose > * + * { margin-left: 24px; }

/* adds vertical pipes between list elements */
.hList_divided > * + * {
    margin-left: 12px;
    padding-left: 12px;
    border-left: 1px solid;
}
```

```css
.carousel {
    position: relative; /* A positioning reference for .carousel-nav */
}

.carousel-nav {
    position: absolute; /* Positioned against .carousel base class */
    right: 20px;
    bottom: 20px;
    z-index: 10; /* Pull navigation on top of .carousel-slides */
}
```

## Hexadecimal Notation

Always use six character and lowercase hexadecimal notation.

```css
.selector {
    background-color: #ff0000;
}
```

## TODO Comments

Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.

```css
/* TODO - Review content styles */
.selector {
    color: #ff0000;
}
```

## Table of Contents

Do not include a table of contents in the CSS.

```css
/* DO NOT */
/* ---------------------------------------------------------------------
Table of Contents

1 - Masthead
2 - Utility Classes
3 - Grid
4 - Media Object
5 - Icons

------------------------------------------------------------------------ */
```

# <a href="#bestpractices"></a>CSS Best Practices

## Encoding

Do not declare a `@charset` in the CSS.

```css
/* DO NOT */
@charset "UTF-8";

.selector {
    color: #ff0000;
}
```

## Browser Reset

```css
/* ------------------------------------------------
RESET CSS (thanks Eric Meyer)
------------------------------------------------ */
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font-weight: inherit;
    font-style: inherit;
    font-family: inherit;
    vertical-align: baseline;
}

body {
    line-height: 1;
}

ol, ul {
    list-style: none;
}

blockquote, q {
    quotes: none;
}

blockquote:before, blockquote:after,
q:before, q:after {
    content: '';
    content: none;
}

table {
    border-collapse: collapse;
    border-spacing: 0;
}

:focus {
    outline-width: 0;
}

html {
    overflow-y: scroll; /* Always show a vertical scrollbar, even when there is no scrolling */
}

html {
    -webkit-text-size-adjust: 100%;
    -ms-text-size-adjust: 100%;
}

/* ------------------------------------------------
 HTML5 Element Reset
------------------------------------------------ */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section, main {
    display: block;
}

audio, canvas, video, progress, picture {
    display: inline-block;
}

template {
    display: none;
}

/* ------------------------------------------------
 Form Reset Styles
------------------------------------------------ */
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration,
input[type="search"]::-webkit-search-results-button,
input[type="search"]::-webkit-search-results-decoration {
    -webkit-appearance: none;
}

input[type="search"] {
    -webkit-appearance: none;
    -webkit-box-sizing: content-box;
    -moz-box-sizing: content-box;
    box-sizing: content-box;
}

textarea {
    overflow: auto;
    vertical-align: top;
    resize: vertical;
}

::-moz-focus-inner {
    border: 0;
    padding: 0;
}
```

**Do not** use normalize.css or a universal selector reset.

## Classes & IDs

**Do not** use `id` for styling purposes

Acceptable uses for `id` include:

* JavaScript selection - prefix these with `js-` to indicate they are for JavaScript only
* Assigning form labels to inputs
* Jump links between sections of a page

```html
<div class="carousel" id="js-carousel"> ... </div>
```

```html
<label for="firstName">First Name</label>
<input type="text" id="firstName" class="input input_txt" />
```

```html
<a href="#mainContent">Skip to Main Content</a>

...

<div class="content" id="mainContent"> ... </div>
```

**Resources**

* <http://www.stubbornella.org/content/2011/04/28/our-best-practices-are-killing-us/>
* <http://screwlewse.com/2010/07/dont-use-id-selectors-in-css/>
* <http://oli.jp/2011/ids/>

## Contextual Selectors

Avoid cross module contextual selection.

```css
/* DO NOT */
.box .hdg { }
```

If a single module can make use of a contextual selector (as the markup structure is known), be sure to apply it with the proper depth of applicability.

```css
.list > li { }
```

## Selector Specificity

Keep selector specificity as low as possible, opting for a single class as the best selector.

```css
.box {
    padding: 20px;
    background-color: #cccccc;
}
```

**Resources**

* <http://www.w3.org/TR/css3-selectors/#specificity>
* <http://www.stuffandnonsense.co.uk/archives/css_specificity_wars.html>
* <http://css-tricks.com/specifics-on-css-specificity/>
* <http://www.standardista.com/css3/css-specificity/>

## Separation of Concerns

Using the [outlined methodology](/standards/methodology.md/), separate layout styles from container styles and content styles from container styles.

**Resources**

* <https://smacss.com/>
* <http://www.smashingmagazine.com/2012/04/20/decoupling-html-from-css/>
* <http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/>
* <http://www.vanseodesign.com/css/smacss-introduction/>

## Naming Conventions

**Name Quality**

Class names should be specific enough so that you can comprehend the name without context, but generic enough for reuse throughout the code base.

```css
.wrapper { }
.masthead { }
.globalFooter { }
.cta { }
.btn { }
.box { }
.icn { }
```

**Numerical/Enumerated Naming**

Do not use numbers, letters, the greek alphabet, or any other sequential naming convention.

```css
/* DO NOT */
.box1 { }
.box2 { }
.box3 { }
```

There are a few notable exceptions:

* Heading tags: `.hdg_1`, `.hdg_2`, etc. are appropriate as they indicate hierarchy.
* Vertical rhythm classes: `.vr_2x`, `.vr_3x`, etc. are appropriate as they indicate a ratio.

## Class Chaining

Avoid chaining classes.

```css
/* DO */
.btn_primary { }

/* DO NOT */
.btn.primary { }
```

An exception to this rule is chaining state classes, as they are often applied via JavaScript and chaining classes in this way provides an appropriate level of reuse.

```css
.btn.isActive { }
```

## Body / Page Classes

Avoid using body / page classes. This includes classes on the `<html>` or `<body>` element, or page-based classes on wrapper `<div>`s.

The exception to this rule is when leveraging Modernizr or other feature detection to add classes to the `<html>` element, allowing for feature based fallbacks in CSS.

```html
<html class="no-js">
...
</html>
```

```css
.carouselItem {
    float: left;
    margin: 0 10px;
}

/* Stack carousel items if no JS */
.no-js .carouselItem {
    float: none;
    margin: 0 0 20px;
}
```

## Shorthand

Use of shorthand is encouraged unless setting a single value.

When using shorthand, be explicit and define all values.

```css
.selector {
    margin: 12px 0 16px 0;
}
```

```css
.selector {
    font: italic small-caps normal 13px/1.6 Arial, Helvetica, sans-serif;
}
```

## Browser Hacks

Browser hacks are an acceptable alternate means of including browser specific code.

Browser specific code should not be needed in most cases - but should be used to handle known browsers bugs such as emulating inline-block in IE7.

If a hack is included, a comment is required to explain the reasoning.

```css
.selector {
    display: inline-block;
    *display: inline; /* ie6-7 emulate inline-block */
    *zoom: 1; /* ie6-7 emulate inline-block */
}
```

If you need to include a large amount of code targeted at a specific browser, instead utilize conditional comments that allow for inclusion of browser specific stylesheets. Keep in mind that this technique hinders your ability to utilize the cascade.

```html
<!--[if IE 9]><link href="ie9.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 8]><link href="ie8.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 7]><link href="ie7.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 6]><link href="ie6.css" rel="stylesheet" /><![endif]-->
```

**Resources**

* <http://browserhacks.com/>

## Multiple Stylesheets

All CSS should be placed in the same stylesheet with the following exceptions:

* Browser specific stylesheets
* Media specific stylesheets (print)
* Breakpoint specific stylesheets (width media queries)
* Area specific stylesheets (standard site, admin area)

```html
<link href="screen.css" rel="stylesheet" media="screen" />
<link href="print.css" rel="stylesheet" media="print" />
```

Do not use `@import` to include stylesheets. All stylesheets should be linked in the head of your document.

```css
/* DO NOT */
@import url("layout.css");
@import url("typography.css");
```

IE conditional stylesheets should use `lte` declarations, with the exception of IE9.

```html
<!-- DO -->
<!--[if IE 9]><link href="ie9.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 8]><link href="ie8.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 7]><link href="ie7.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 6]><link href="ie6.css" rel="stylesheet" /><![endif]-->

<!-- DO NOT -->
<!--[if lte IE 9]><link href="ie9.css" rel="stylesheet" /><![endif]-->
<!--[if IE 8]><link href="ie8.css" rel="stylesheet" /><![endif]-->
<!--[if IE 7]><link href="ie7.css" rel="stylesheet" /><![endif]-->
```

## Units

The recommended unit for font-sizes is pixels.

```css
.selector {
    font-size: 12px;
}
```

The recommended units for setting box model related properties are pixels and percentages.

```css
.box {
    width: 25%;
    margin-bottom: 10px;
}
```

When building RWD websites and web applications, alternative units of measurement may be more appropriate, but should be chosen with care to do what's best for the project while striving to maintain our [goals](/README.md#goals).

## Line-Height

Declare line-height values as unit-less. Unit-less line heights act as a multiplier to the text size for a given element. Always leave a comment explaining the math.

```css
.selector {
    font-size: 12px
    line-height: 1.25; /* 15px / 12px = 1.25 */
}
```

**Resources**

* <http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/>
* <https://developer.mozilla.org/en-US/docs/Web/CSS/line-height>

## Color Values

Use hexadecimal notation for color values. RGBA is acceptable if opacity is needed, but be sure to provide a fallback for browsers that don't support RGBA.

```css
.selector {
    color: #ff0000;
}

.selector {
    color: #ff0000; /* fallback for non-rgba browsers */
    color: rgba(255, 0, 0, 0.8);
}
```

## Clearing Floats

All floats should be cleared using the micro clearfix syntax.

```html
<ul class="hList">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

```css
.hList:before,
.hList:after {
    content: " ";
    display: table;
}

.hList:after {
    clear: both;
}

.hList > li {
    float: left;
}
```

**Resources**

* <http://nicolasgallagher.com/micro-clearfix-hack/>
* <https://css-tricks.com/all-about-floats/>

## Sprites

Use sprites whenever possible to improve performance by reducing http requests. Use multiple sprites that are categorized appropriately (nav-sprite, icon-sprite, etc.) as opposed to using a single super sprite for the entire site.

![JPG Example](/standards/_images/sprite-icon.png)

**Resources**

* <http://alistapart.com/article/sprites>
* <https://css-tricks.com/css-sprites/>

## Image Replacement

When using background images that include text, it's important that there is a text equivalent in the markup itself so that the text is accessible. Use a suitable image replacement technique to keep the text hidden from view.

```html
<a href="/home/" class="nav-home">Home</a>
```

```css
.nav-home {
    background-image: url("nav-home.png"); /* image for display of nav home button */
    background-repeat: no-repeat;
    background-color: transparent;
    border: 0;
    overflow: hidden;
}

.nav-home:before {
    content: " ";
    display: block;
    width: 0;
    height: 100%;
}
```

**Resources**

* <https://css-tricks.com/css-image-replacement/>
* <https://css-tricks.com/examples/ImageReplacement/>

## Font Embedding

Use `@font-face` to embed custom fonts.

Font services like TypeKit or the Google Font API may be used. If embedding from a third party site is required, opt to use a CSS method over one that requires JavaScript.

**Do not use FAUST, SIFR or Cufon.**

```css
@font-face {
    font-family: 'GiantHeadOTRegular';
    src: url('../fonts/giant-head/giant-head-regular-ot-webfont.eot');
    src: url('../fonts/giant-head/giant-head-regular-ot-webfont.eot?#iefix') format('embedded-opentype'),
         url('../fonts/giant-head/giant-head-regular-ot-webfont.woff') format('woff'),
         url('../fonts/giant-head/giant-head-regular-ot-webfont.ttf') format('truetype'),
         url('../fonts/giant-head/giant-head-regular-ot-webfont.svg#GiantHeadOTRegular') format('svg');
    font-weight: normal;
    font-style: normal;
}
```

**Resources**

* <http://www.fontsquirrel.com/>
* <https://typekit.com/>
* <http://www.google.com/fonts/>
* <http://www.fontspring.com/blog/further-hardening-of-the-bulletproof-syntax>

## Font Stacks

Choose font stacks with care, being mindful to ensure all bases are covered. Good font stacks generally have 2-4 font fallbacks declared and set the browser default serif or sans-serif last in the stack.

```css
.selector {
    font-family: "LeagueGothic", Helvetica, Arial, sans-serif;
}
```

**Resources**

* <http://nicewebtype.com/notes/2009/04/23/css-font-stacks/>
* <http://www.cssfontstack.com/>

## Positioning

Do not use absolute positioning to layout the main sections of a page.

Do not use relative positioning to "shim" elements around the page to achieve pixel perfection.

Do use positioning contexts when necessary to achieve a flexible and robust object. When using positioning in CSS, leave a comment describing the context.

```html
<div class="carousel">
    <ul class="carousel-slides">
        ...
    </ul>
    <ul class="carousel-nav">
        ...
    </ul>
</div>
```

```css
.carousel {
    position: relative; /* A positioning reference for .carousel-nav */
}

.carousel-nav {
    position: absolute; /* Positioned against .carousel base class */
    right: 20px;
    bottom: 20px;
}
```

## Document Flow

Take advantage of the natural document flow when spacing content by using *only* margin bottom on content elements so they can easily be interchanged while keeping a predictable document flow and avoiding margin collapsing issues.

Additionally use padding on containers to keep a consistent "edge".

```html
<div class="box">
    <div class="userContent">
        <h2>All About Cats</h2>
        <p> ... </p>
        <p> ... </p>
        <h3> Nocturnal Habits</h3>
        <p> ... </p>
        <p> ... </p>
    </div>
</div>
```

```css
.box {
    padding: 20px;
    background: #ffffff;
}

.userContent h2 {
    font-size: 24px;
    color: #333333;
    margin-bottom: 12px;
}

.userContent h3 {
    font-size: 20px;
    color: #333333;
    margin-bottom: 12px;
}

.userContent p {
    font-size: 12px;
    margin-bottom: 12px;
}
```

When dealing with inter-modular spacing, consider using a vertical rhythm object to provide predictable document flow.

## W3C Validation

Write valid code. Remaining errors & warnings should be intentional.

**Resources**

* <http://jigsaw.w3.org/css-validator/>
* <http://csslint.net/>
