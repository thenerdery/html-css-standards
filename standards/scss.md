## Folder Structure

The file structure when using SCSS includes 4 folders: base, helpers, landmarks, and modules.

The base folder contains:

* Elements - styles for base element like `<body>` or `<a>`.
* Fonts - `@font-face` rules for embedding fonts for global use
* Reset - common reset styles

The helpers folder contains:

* Utilities - styles for common patterns like `.isVisuallyHidden` and common mixins like `clearfix`
* Variables - all global variables used throughout the site
* Vendor - mixins for vendor prefixes

The landmarks and modules folders contain:

* A folder for each object named after the object
* A file within each folder named after the object that contains relevant styles for the object

Additionally there is a `screen.scss` file that is used to import all SCSS partials for inclusion in a single compiled `screen.css` file.

```diff
└── assets
    └── styles
        ├── base
        |   ├── _elements.scss
        |   ├── _fonts.scss
        |   └── _reset.scss
        ├── helpers
        |   ├── _utils.scss
        |   ├── _vars.scss
        |   └── _vendor.scss
        ├── landmarks
        |   ├── masthead
        |   |   └── _masthead.scss
        |   ├── navPrimary
        |   |   └── _navPrimary.scss
        |   └── footer
        |       └── _footer.scss
        ├── modules
        |   ├── blocks
        |   |   └── _blocks.scss
        |   ├── grid
        |   |   └── _grid.scss
        |   ├── hlist
        |   |   └── _hlist.scss
        |   └── media
        |       └── _media.scss
        └── screen.scss
```

When media queries are introduced into the code the folder structure becomes more complex in order to offer the modularity required to support legacy browsers.

The file structure remains the same, however the following rules apply.

* Each object in the landmarks or modules folder should use the name of the object and the name of the corresponding breakpoint in it's file name separated by a single underscore.
* If a module level variable is needed for multiple breakpoints, add a `_helpers.scss` partial. Use the aforementioned naming convention - the object name followed by `_helpers.scss`

Additionally, instead of compiling everything into a single `screen.css` file, code will be compiled into `modern.css` and `legacy.css` files using the following steps:

* Create a `_screen_breakpoint.scss` file for each breakpoint
* Import partials for each module into the corresponding breakpoint files making sure not to include media queries
* Import all breakpoint partials into `legacy.css`
* Import all breakpoint partials into `modern.css` with each file contained inside the corresponding media queries

Taking these steps provides two production ready CSS files - one of which requires media queries and one that doesn't that can be used to apply a fixed width design for legacy browsers.

```diff
└── assets
    └── styles
        ├── base
        |   ├── _elements.scss
        |   ├── _fonts.scss
        |   └── _reset.scss
        ├── helpers
        |   ├── _utils.scss
        |   ├── _vars.scss
        |   └── _vendor.scss
        ├── landmarks
        |   ├── masthead
        |   |   ├── _masthead_large.scss
        |   |   ├── _masthead_medium.scss
        |   |   └── _masthead_screen.scss
        |   ├── navPrimary
        |   |   ├── _navPrimary_large.scss
        |   |   ├── _navPrimary_medium.scss
        |   |   └── _navPrimary_screen.scss
        |   └── footer
        |       ├── _footer_large.scss
        |       ├── _footer_medium.scss
        |       └── _footer_screen.scss
        ├── modules
        |   ├── blocks
        |   |   ├── _blocks_helpers.scss
        |   |   ├── _blocks_medium.scss
        |   |   └── _blocks_screen.scss
        |   ├── grid
        |   |   └── _grid_medium.scss
        |   ├── hlist
        |   |   ├── _hlist_helpers.scss
        |   |   ├── _hlist_large.scss
        |   |   ├── _hlist_medium.scss
        |   |   ├── _hlist_screen.scss
        |   |   └── _hlist_small.scss
        |   └── media
        |       └── _media_screen.scss
        ├── _screen.scss
        ├── _screen_large.scss
        ├── _screen_medium.scss
        ├── _screen_small.scss
        ├── legacy.scss
        └── modern.scss
```

## Partials

Sass files that are not intended to be compiled independently, should be named with a leading underscore.

```diff
_media.scss
```

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
    width: 1px !important;
    height: 1px !important;
    margin: -1px !important;
    border: 0 !important;
    padding: 0 !important;
    clip-path: inset(100%) !important;
    clip: rect(0 0 0 0) !important;
    overflow: hidden !important;
    position: absolute !important;
    white-space: nowrap !important;
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

## @extend

Do not use `@extend`.

```scss
/* DO */
.message {
    padding: 10px;
    border: 1px solid #cccccc;
}

.message_success { color: #00ff00; }
.message_error { color: #ff0000; }

/* DO NOT*/
.message {
    padding: 10px;
    border: 1px solid #cccccc;
}

.message_success {
    @extend .message;
    color: #00ff00;
}

.message_error {
    @extend .message;
    color: #ff0000;
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

## Other @directives

**@import**

Do not include the file extension when using `@import`.

```scss
@import "_media";
```

**@media**

It is acceptable to use `@media` rules nested in selectors if they are used for small tweaks. Separate stylesheets (`screen`, `screen_small`, `screen_large`, etc) should be used for major breakpoints.

```scss
.exampleObject {
    padding: 10px;
    @media (max-width: 500px) {
        padding: 20px;
    }
}
```

**@function**

Function naming should follow the same naming conventions as mixins.

**@warn**

It is acceptable to use `@warn` in-lieu of TODO comments.

**@debug**

It is acceptable to use `@debug` provided it is not committed to the version control repository.
