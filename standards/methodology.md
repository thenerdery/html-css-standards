# Methodology

The following key points and ideas make up the methodology of "how" and "why" we do Front-End Development at the Nerdery the way we do. Most of these topics are touched on in the standards in the form of rules to follow, but they will be covered more in depth in an effort to better explain and stress the importance of our methodology.

## Modularity

Approaching front end code from a modular point of view addresses the goal outlined in our standards. Writing in a modular fashion makes our code more flexible to change and resistant to breakage as sites grow larger. Modular code is more scalable and maintainable - requiring less CSS that can do more.

The goal here is not to avoid repeating a property/value pair, but to identify the patterns that can be abstracted for high reuse and to identify and create modules that are fully encapsulated logical entities that are easy to extend, and extremely portable.

A module, or "object," is the combination of some markup and the associated CSS (and sometimes Javascript). It is portable, in that it does not change based upon context. It contains all of the CSS needed for that object to function, without relying on context or utility type classes.

Objects come in all shapes and sizes. A button is an object. A heading is an object. A masthead is an object. Some classes have sub-components (class members) which are the children markup elements (and the associated CSS) that make up the object. If the objects are carefully written, you can put them together in any number of ways without having to write additional CSS.

Objects are the Lego blocks that are assembled into full blown pages and sites. Writing CSS to be modular means removing contextual dependencies and writing defensive selectors that limit the depth of applicability.

## CSS Selectors

One of the quickest ways to improve the modularity and flexibility of code is to think harder about the selectors you choose. The first step is to eliminate IDs from CSS selection. IDs do nothing that classes can't also do, but instantly limit reuse and flexibility as they cannot appear on a page more than once. They are also difficult to work with due to their high specificity. The ideal selector is a single classname like `.masthead`.

The next step is to avoid contextual selection, especially across unrelated objects. By styling an object based on context, we again reduce flexibility by needlessly tying an object's appearance to some unrelated class farther up the DOM tree. Now we've created a situation where those styles can only be used within that container, whereas had we simply written the object without contextual selection, we would be free to move that module anywhere in our site and it would still function as it should.

Contextual selection introduces complexity and unpredictability into the mix. If the next developer is unaware of a myriad of contextual conditions for an object, imagine the frustration as an object breaks or changes simply by moving it somewhere else in the site. By avoiding contextual selection, we keep our selector specificity low and gain predictable, robust objects.

Contextual selectors also add weight to our selectors, making them more difficult to work with.

```css
/* DO */
.utilNav { }

/* DO NOT */
.masthead .utilNav { }
```

Avoid overqualified selectors. Similar to contextual selectors, overqualification limits flexibility and needlessly increases selector weight.

```css
/* DO */
.utilNav { }

/* DO NOT */
div.utilNav { }
```

Avoid using elements in selectors. Elements are risky for a couple of reasons. First, they limit the markup elements we can apply a given class to - making semantic decisions for us in our CSS. Second, they have a high depth of applicability - meaning the likelihood that something will accidentally receive or collide with those styles goes up.

```css
/* DO */
.utilNav-item { }

/* DO NOT */
.utilNav a span { }
```

By simply avoiding IDs, elements and contextual selection, the potential for reuse and modularity increases dramatically.

One false sense of reuse is the use of stacked selectors. In most cases, stacked selectors are an indication that objects aren't properly being identified and abstracted into objects. If selectors are being stacked, a single class probably should have been used.

```css
/* DO */
.utilNav { }

/* DO NOT */
.newsNav,
.eventsNav,
.legalNav { }
```

## Object Identification

One key to writing modular, object based front end code is getting the granularity right. This usually involves thinking about the items on our pages "inside out" instead of "outside in."

Instead of thinking about creating pages, think about the little bits that combine to make that page. The bits are smaller and generally good at doing one thing - being a button, being a list with top borders on my items, being a container that has space for an image, a heading and some copy, being a grid to lay out major components of a site. With each object doing an excellent job, being free of contextual specificity and elemental restraints - it can be placed into the site at will, in a predictable, flexible fashion.

## Object Members

Objects may consist of a single element.

```html
<a href="#" class="btn">Push Me</a>
```

Or objects may consist of base class and any number of class members (sub-components). We prefix the name of sub-components with the base class name, followed by a hyphen to indicate a sub-component.

```html
<div class="object">
    <div class="object-member"> ... </div>
</div>
```

A very common pattern is for objects to have head, body and foot components.

```html
<div class="featurePanel">
    <div class="featurePanel-hd"> ... </div>
    <div class="featurePanel-bd"> ... </div>
    <div class="featurePanel-ft"> ... </div>
</div>
```

Components are frequently optional, and certainly aren't restricted to head, body and foot items.

```html
<div class="featurePanel">
    <div class="featurePanel-bd"> ... </div>
</div>
```

## Object Extension

We can account for variations on an object by creating an extension to that object. We prefix the name of an extension with the base class name, followed by an underscore to indicate an extension.

```html
<div class="object object_extension"> ... </div>
```

Extending objects is an important habit to get into. Always directly alter the object you want to change, instead of styling it contextually from a different object.

```html
<!-- DO -->
<div class="box">
    <a href="#" class="btn btn_secondary">Go Back</a>
</div>
```

```css
/* DO */
.btn { color: #000000; }
.btn_secondary { color: #999999; }
```

```html
<!-- DO NOT -->
<div class="box">
    <a href="#" class="btn">Go Back</a>
</div>
```

```css
/* DO NOT */
.btn { color: #000000; }
.box .btn { color: #999999; }
```

## Object Mixins

Extensions to an object should follow a single ancestry chain. Two sub-classes of an object should not appear on the same object if they are of a different ancestry chain. For these types of scenarios, we have mixins.

Mixins are a type of class extension that do not create a sub-class, but rather can be added to (mixed with) any super or sub-class of object. If a type of object has many variations that cannot be elegantly defined into discrete sub-classes, mixins may be the best solution. Mixins are generally an undesirable way to write CSS and should only be used when that is the best option availabe - usually when a design lacks consistency. Often it is better to create more base classes than to try and shoehorn everything into a single object with a lot of mixins.

We indicate an object mixin by prefixing the name with "mix-" and the base class name.

```html
<div class="object mix-object_extension"> ... </div>
```

```html
<h1 class="hdg hdg_h1"> ... </h1>
<h1 class="hdg hdg_h1 mix-hdg_cap"> ... </h1>
<h1 class="hdg hdg_h2"> ... </h1>
<h1 class="hdg hdg_h2 mix-hdg_cap"> ... </h1>
```

```css
.hdg {
    font-family: arial, helvetica, sans-serif;
    font-weight: bold;
}

.hdg_h1 { font-size: 30px; }
.hdg_h2 { font-size: 20px; }

.mix-hdg_cap { text-transform: uppercase; }
```

## Object States

States are special class extensions that represent the various states an object may be in - often used in conjunction with Javascript. States are indicated with the "is" prefix before the extension name.

```html
<div class="object object_isState"> ... </div>
```

```html
<a href="#" class="navItem navItem_isActive"> ... </a>
```

```css
.navItem {
    color: #ffffff;
    background: #000000;
}

.navItem_isActive {
    color: #000000;
    background: #ffffff;
}
```

## All Together Now

With these naming conventions, intention and structure become clear just from reading a class from right to left. Underscore means extends, hyphen indicates a class member (sub-component).

A selector this deep is rare, but it illustrates the point:

```css
.cta-bd_highlight-status { }
```

Right to left, this tells us we're dealing with: The status element which is a sub-component (-) of the highlight extension (_) of bd which is a sub-component of the cta base object. From this alone we can extrapolate the ancestry of our selector as well as part of the markup structure this object has:

```html
<div class="cta">
    <div class="cta-bd cta-bd_highlight">
        <div class="cta-bd-status cta-bd_hightlight-status"> ... </div>
    </div>
</div>
```

## Depth of Applicability

Carefully written objects limit their depth of applicability. A selector with a high depth of applicability casts too wide a net and can result in unexpected results. By writing defensive selectors from the start, we eliminate that risk. An object's depth of applicability should extend only to the known components of that module. For instance, if we started an object that is used on a product listing page:

```html
<ul class="listing">
    <li> ... </li>
    <li> ... </li>
    <li> ... </li>
    <li> ... </li>
</ul>
```

One might be tempted to style the list like this:

```css
.listing li {
    border-top: 1px solid #000000;
    padding-top:10px;
    margin-top: 10px;
}
```

This selector is not defensive enough - any number of things could go inside of .listing, including other lists, which means we'd then have to override our listing styles and make sure our overrides appear later in the CSS source file. We would improve the depth of applicability by utilizing a child combinator selector:

```css
.listing > li {
    border-top: 1px solid #000000;
    padding-top: 10px;
    margin-top: 10px;
}
```

That accomplishes the goal of limiting the depth at which that style will be applied. By making a small change in our selector, we have ensured that these styles will not collide with any of the other modules it may house. We can even take this a step further by removing the element from the selector completely, which would allow us to use this object's styles with more than one kind of markup element:

```css
.listing > * {
    border-top: 1px solid #000000;
    padding-top: 10px;
    margin-top: 10px;
}
```

Alternatively, we can just name member we wish to style and use its classname as the selector:

```html
<ul class="listing">
    <li class="listing-item"> ... </li>
    <li class="listing-item"> ... </li>
    <li class="listing-item"> ... </li>
    <li class="listing-item"> ... </li>
</ul>
```

```css
.listing-item {
    border-top: 1px solid #000000;
    padding-top: 10px;
    margin-top: 10px;
}
```

## Keeping Objects Separate in the DOM

The classes that make up separate objects should not be combined in the DOM - this leads to unpredictable results and breaks object encapsulation. Keep objects separate, both in CSS and in the DOM.

```html
<!-- DO -->
<div class="grid">
    <div class="grid-col grid-col_1of2">
        <div class="someModule"> ... </div>
    </div>
</div>

<!-- DO NOT -->
<div class="grid">
    <div class="someModule grid-col grid-col_1of2">
        ...
    </div>
</div>
```

## Separation of Concerns

By separating certain concerns amongst our objects, we end up with a more flexible set of objects. The rules of thumb are:

- Separate layout styles from container styles
- Separate content styles from container styles

By having layout be its own class of object, separate from container objects, we dramatically increase the number of layouts we can achieve while increasing the flexibility of where and how we can use our container objects. All while writing less CSS as containers no longer need lots of width and float rules, only to be overridden in other contexts. This works to simplify the code and results in more predictable results.

Similarly, by separating our content styles from our container styles, we increase the flexibility and predictability of our content - as we can put any object into any other object and it won't suddenly change.

Attempting to separate your objects into these three duties results in code that is easier to work with, flexible to change, resistant to breakage, scalable and maintainable.

## Resources

- [http://smacss.com/](http://smacss.com/)
- [http://coding.smashingmagazine.com/2012/04/20/decoupling-html-from-css/](http://coding.smashingmagazine.com/2012/04/20/decoupling-html-from-css/)
- [http://coding.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/](http://coding.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)
- [http://www.vanseodesign.com/css/smacss-introduction/](http://www.vanseodesign.com/css/smacss-introduction/)
