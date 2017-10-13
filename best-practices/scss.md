_TODO: Update to CSS Precompiler Best Practices_
# SCSS Best Practices

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

**@warn**

It is acceptable to use `@warn` in-lieu of TODO comments.

**@debug**

It is acceptable to use `@debug` provided it is not committed to the version control repository.
