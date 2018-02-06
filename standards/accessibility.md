#Accessibility

## Source Order

Use logical source order as assistive devices follow source top to bottom.

```html
<div class="masthead">
    ...
</div>
<div class="navigation">
    ...
</div>
<div class="contentMain">
    ...
</div>
<div class="contentRelated">
    ...
</div>
<div class="footer">
    ...
</div>
```

## JavaScript Content

JavaScript content should be accessible to screen readers. The best option for this is to use a logical source order and keep appended / prepended items near the element that triggers their appearance.

If this isn't an option rely on ARIA techniques instead.

```html
<div class="contentMain">
    <a href="#myModal" class="js-spawn-modal">View Larger Image</a>
    <div class="modal" id="myModal">
        ...
    </div>
</div>
<div class="footer">
    ...
</div>
```

## Page Titles

Include a unique title for each page.

```html
<title>Nerdery Primer: Responsive Design - Blog - The Nerdery</title>
```

## ARIA Roles

**Landmark Roles**

Use landmark ARIA roles on all projects.

The landmark ARIA roles include:

* **banner** - wraps the typical site masthead. Use only once per page.
* **search** - place on a form that performs search.
* **navigation** - place on your navigation container (for in-document and site-wide navigation).
* **main** - place on container that holds the main page content. Use only once per page.
* **complementary** - place on containers that are akin to the `<aside>` HTML5 element.
* **contentinfo** - place on element that contains meta information about the page or content, often the site footer. Use only once per page.

When using HTML5 elements, like `<header>` and `<footer>`, provide progressive enhancement for screen readers by including ARIA landmark roles on these elements as well, even though some screen readers may see this as redundant.

```html
<div class="masthead" role="banner">
    ...
    <form class="search" action="#" method="post" role="search">
        ...
    </form>
    ...
</div>
<div class="navigation" role="navigation">
    ...
</div>
<div class="contentMain" role="main">
    ...
</div>
<div class="contentRelated" role="complementary">
    ...
</div>
<footer class="footer" role="contentinfo">
    ...
</footer>
```

If the project requirements allow, you may combine the use of landmark ARIA roles with HTML5 elements.

```html
<header class="masthead" role="banner">
    ...
    <form class="search" action="#" method="post" role="search">
        ...
    </form>
    ...
</header>
<nav class="navigation" role="navigation">
    ...
</nav>
<main class="contentMain" role="main">
    ...
</main>
<aside class="contentRelated" role="complementary">
    ...
</aside>
<footer class="footer" role="contentinfo">
    ...
</footer>
```

**Resources**

* <http://www.w3.org/1999/xhtml/vocab#XHTMLRoleVocabulary>
* <http://www.paciellogroup.com/blog/2010/10/using-wai-aria-landmark-roles/>

## Skip Links

In order for keyboard users to easily skip to the main content of a site without tabbing through all the previous content, use a "skip to content" link. It is also acceptable to include a "skip to navigation" link if it takes an excessive number of tabs to get focus on the navigation.

It's best practice to bring focusable into view when they are focused.

```html
<body>
    <a href="#page-content" class="isVisuallyHidden">Skip to Content</a>
    <div class="masthead">
        ...
    </div>
    <div id="page-content" class="contentMain">
        ...
    </div>
</body>
```

```css
.isVisuallyHidden:not(:focus):not(:active) {
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

## Alt Attributes

Use `alt` attributes on all images.

If the image is in a link, the alt text should specify the action that will be taken upon clicking the image.

Include any text content that appears in an image in the `alt` attribute.

```html
<!-- DO -->
<a href="index.html"><img src="../images/logo.png" alt="Crispen &amp; Mulberry Home" /></a>

<!-- DO NOT -->
<a href="index.html"><img src="../images/logo.png" alt="Logo" /></a>
```

If a content image contains no useful information or text, include the `alt` attribute but leave the value empty.

Do not describe the image. Never use the phrases "image of" or "picture of" in `alt` values.

```html
<!-- DO -->
<img src="../images/business.jpg" alt="" />

<!-- DO NOT -->
<img src="../images/business.jpg" alt="Picture of two gentlemen shaking hands with a blue sky and tree in the background" />
```

## Longdesc Attributes

Do not rely on the longdesc attribute for consistent accessibility.

Instead, opt for including the content as text on the page or provide a link to the text alternative on the page.

```html
<img src="infographic.jpg" alt="A list of all the presidents with facial hair listed chronologically" />
<a href="presidents-with-facial-hair.html">See the list of presidents who had facial hair while in office.</a>
```

## Tables

Include `thead`, `tbody` and `tfoot` to indicate the table header, table body and table footer.

Declare table header cells and scope them properly.

```html
<table>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Goals</th>
            <th scope="col">Assists</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Evgeni Malkin</td>
            <td>50</td>
            <td>59</td>
        </tr>
        <tr>
            <td>Ilya Kovalchuk</td>
            <td>37</td>
            <td>46</td>
        </tr>
    </tbody>
</table>
```

## Form Labels

All form controls, except `<button>`, require a corresponding `<label>`, even if the label is hidden from view.

The `for` attribute is required on all labels.

```html
<label for="name">Name:</label>
<input type="text" id="name" />
```

If possible, it is preferable to wrap inputs with the corresponding label.

```html
<label for="professionDoctor">Doctor <input type="radio" name="profession" id="professionDoctor" /></label>
<label for="professionLawyer">Lawyer <input type="radio" name="profession" id="professionLawyer" /></label>
<label for="professionOther">Other <input type="radio" name="profession" id="professionOther" /></label>
```

## Form Button Values

Form input buttons require a `value` attribute.

```html
<input type="submit" value="Submit" />
```

```html
<input type="reset" value="Reset" />
```

Image type inputs require an `alt` attribute.

```html
<input type="image" src="button.png" alt="Submit" />
```

Button elements require a value between the opening and closing tags.

```html
<button type="submit">Submit</button>
```

## Form Placeholder Text

Use placeholder text to provide a hint to the user.

Whenever possible, do not use `placeholder` text as a replacement for a `<label>`. When necessary, opt for visually hiding the label instead.

```html
<label for="email" class="isVisuallyHidden">Email</label>
<input type="email" id="email" placeholder="user@domain.com" />
```

## Form Grouped Controls

Use a `fieldset` to logically group form controls.

If form labels don't clearly identify what information is being collected, use a `legend` to label the group.

Keep legend text short as it is read by screen readers before each input in the fieldset.

```html
<fieldset>
    <legend>Profession</legend>
    <label for="professionDoctor">Doctor <input type="radio" name="profession" id="professionDoctor" /></label>
<label for="professionLawyer">Lawyer <input type="radio" name="profession" id="professionLawyer" /></label>
<label for="professionOther">Other <input type="radio" name="profession" id="professionOther" /></label>
</fieldset>
```

## Form Validation

Form inputs that have validation requirements - like required fields, or an expected email format - should be clearly labeled in an accessible manner indicating the requirement. They should also include the `aria-required` attribute with the value set to `true`.

Form validation and submission should be accessible to both the mouse and keyboard.

All form inputs that are validated client side should also be validated in the same manner on the server side.

If a field returns as invalid, it should include the `aria-invalid` attribute with the value set to the proper value (`true`, `false`, `grammar`, `spelling`).

```html
<form action="#" method="post">
    <ul>
        <li>
            <label for="formUsername">Username <span class="required">*</span></label>
            <input type="input" id="formUsername" required aria-required="true" />
        </li>
        <li>
            <label for="formEmail">Email Address <span class="required">*</span></label>
            <input type="email" id="formEmail" required aria-required="true" />
        </li>
        <li>
            <label for="formPassword">Password <span class="required">*</span></label>
            <input type="password" id="formPassword" required aria-required="true" aria-describedby="password-requirements" />
            <span id="password-requirements">Use 6-20 characters, at least 1 uppercase letter and 1 number.</span>
        </li>
        <li>
            <input type="submit" value="Sign Up" />
        </li>
    </ul>
</form>
```

**Resources**

* <http://alistapart.com/article/aria-and-progressive-enhancement>
* <http://www.deque.com/blog/accessible-client-side-form-validation-html5-wai-aria/>
* <https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-invalid_attribute>
* <http://webaim.org/techniques/formvalidation/>

## Hiding Content

When hiding content on a page, choose the appropriate method.

Using `display: none;` or `visibility: hidden;` will hide content from a screen reader.

If content is meant to be available to a screen reader but not to a sighted user, hide the content by using a utility class.

```html
<h2 class="isVisuallyHidden">Featured Articles</h2>
```

```css
.isVisuallyHidden {
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

**Resources**

* <http://snook.ca/archives/html_and_css/hiding-content-for-accessibility>
* <http://webaim.org/techniques/css/invisiblecontent/>

## Focus Styles

Include `:focus` styles to ensure proper keyboard accessibility. Keep in mind, `:focus` is included in `reset.css`, so it will need to be intentionally styled to fit your project requirements.

**Resources**

* <http://24ways.org/2009/dont-lose-your-focus>

## Tabindex

A site should be navigable via keyboard. Write markup that is semantic and supports a logical tab index. Modifying the `tabindex` should be a last resort.

## Magnification

Web pages should remain usable and understandable when the text is magnified via the browser's magnification feature. This includes "pinch zooming" on touch devices. The page may not remain aesthetically pleasing, but it should remain understandable and usable.
