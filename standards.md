# HTML and CSS Standards

_TODO: Add standards introduction_

# Shared Standards

## Indentation

Use 4 spaces for indenting.

```html
<div>
    <ul>
        <li><a href="page.html">Link</a></li>
        <li><a href="page.html">Link</a></li>
    </ul>
</div>
```

```css
.selector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
}
```

When using logical blocks, or other control structures, indent each new line by 4 additional spaces.

```html
{{#if}}
    <div>
        ...
    </div>
{{/if}}
```

```scss
.selector {
    padding: 0 5%;
    @media (max-width: 960px) {
        padding: 0 10%;
    }
}
```

## Trailing Whitespace

Remove all trailing whitespace.

# CSS Standards

## Capitalization

Use camelCase for selector names and lowercase for properties & property values (unless strings).

```css
.mySelector {
    color: #ff0000;
    font-family: Times, "Times New Roman", serif;
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

## Name Delimiters

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

## @directives

**@import**

Do not include the file extension when using `@import`.

```css
@import "_media";
```

**@media**

It is acceptable to use `@media` rules nested in selectors if they are used for small tweaks. Separate stylesheets (`screen`, `screen_small`, `screen_large`, etc) should be used for major breakpoints.

```css
.exampleObject {
    padding: 10px;
    @media (max-width: 500px) {
        padding: 20px;
    }
}
```
_TODO: Update to not be SCSS specific_
## Variables

**Global Variables**

Variables defined outside of ruleset are considered to be global and are used for setting values used across multiple modules, such as brand colors.

Define all global variables in the global `helpers/_vars.scss` partial.

Write global variables using uppercase letters delimited by underscores.

```scss
$BRAND_COLOR_RED: #ff0000;

.nav a {
    color: $BRAND_COLOR_RED;
}
```

**Module Variables**

Module variables are defined outside a ruleset and are intended for use only with a single module.

If the variable is used only in a single file, define it at the top of the file above all rulesets.

If the variable is used by more than one file in the module, define it in a module level `_module_helpers.scss` partial.

To prevent variable collisions, module variables should be prefixed with the base object name separated by a single dash.

```scss
$example-SPACING_UNIT: 10px;

.example-hd {
    margin-bottom: $example-SPACING_UNIT;
}

.example-bd {
    margin-bottom: $example-SPACING_UNIT;
}
```

**Private Variables**

Private variables are defined inside a single ruleset and are intended for use only within that ruleset.

Write private variables using uppercase letters delimited by underscores, and preceded by a single underscore.

```scss
.exampleObject {
    $_SIZE: 200px;
    $_OFFSET: -($_SIZE / 2); // Pull the object half its size to center it.
    position: absolute;
    top: 50%;
    left: 50%;
    height: $_SIZE;
    width: $_SIZE;
    margin-top: $_OFFSET;
    margin-left: $_OFFSET;
}
```

# CSS Precompiler Standards
_TODO: Update examples to be compiler agnostic_
## Silent Comments

Silent comments should be used when the comment is irrelevant to the output.

```scss
//----------------------------------------------------------------------
// Micro Clearfix Mixin
//----------------------------------------------------------------------
@mixin clearfix() {
    &:before,
    &:after {
        content: " ";
        display: table;
    }

    &:after {
        clear: both;
    }
}
```

## Operators

Operators should always be surrounded by a single space.

Use of operators should always be accompanied by a comment.

```scss
.exampleObject {
    $_SIZE: 100px;
    $_PULL: -($_SIZE / 2); /* Pull the object half its size to center it. */
    position: absolute;
    top: 50%;
    left: 50%;
    height: $_SIZE;
    margin-top: $_PULL;
    margin-left: $_PULL;
}
```

## Nesting

Avoid nesting selectors.

```scss
/* DO */
.hList {
   @include clearfix();
}

.hList > li {
    float: left;
}

/* DO NOT */
.hList {
    @include clearfix();

    > li {
        float: left;
    }
}
```

Also avoid nesting pseudo classes & pseudo elements.

```scss
/* DO */
.nav a {
    color: #ffffff;
}

.nav a:hover {
    color: #00ff00;
}

/* DO NOT */
.nav a {
    color: #ffffff;

    &:hover {
        color: #00ff00;
    }
}
```

There are a few scenarios where nesting is acceptable. These includes things like sandboxing an entire stylesheet to avoid conflicting selectors, wrapping a WYSIWYG stylesheet, and nesting media queries to make a small change that's not at a minor breakpoint.

When nesting is appropriate, all selectors should be indented one level deeper than the parent selector.

```scss
.exampleObject {
    padding: 10px;
    @media (max-width: 500px) {
        padding: 20px;
    }
}
```

## Mixins

Use mixins to define styles that can be reused throughout the site to avoid repeating common code blocks. Mixins can be used at both the global and module level. Mixins used by a single module should be prefixed with the module name, and defined in the appropriate location.

Mixin definitions should always include the parenthesis.

Provide default arguments when their absence could cause a compilation error, otherwise, avoid using default arguments in favor of optional arguments.

```scss
@mixin isVisuallyHidden() {
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    border: 0;
    position: absolute;
    clip: rect(0 0 0 0);
    overflow: hidden;
}
```

If a mixin is used to produce vendor prefixes of a single property, it should mimic the W3C naming and syntax.

```scss
@mixin transition($transition) {
    -webkit-transition: $transition;
    -moz-transition: $transition;
    -o-transition: $transition;
    transition: $transition;
}
```

## @control directives

`@if`, `@each`, `@while`, `@for`

Flow control directives should never use the single line syntax.

Curly braces should be formatted identically to selectors.

```scss
.exampleObject {
    @if 1 + 1 == 2 {
        border: 1px solid;
    }
}
```

**@function**

Function naming should follow the same naming conventions as mixins.

# HTML Standards

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