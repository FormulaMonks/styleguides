# CSS Style Guide

This styleguide addresses both the CSS syntax specifics and an actual model
of how to structure the CSS of a web application, in an organized scalable way.

## Syntax

* Use UTF-8.

* Use 2 space indent, no tabs.

* Avoid trailing whitespace.

* Use a line for each selector when using multiple comma-separated selectors.

* Include a space before the opening brace.

* Leave the closing brace on its own line, leaving an empty line afterwards.

* Use one space after `:` for each declaration, and end every declaration with a
  `;`.

* Put every property declaration in a single line, with the exception of single
  declarations.
  ```css
  /* Bad */
  .navTab {
    margin: 20px; padding: 20px;
  }
  /* Good */
  .navTab {
    margin: 20px;
    padding: 20px;
  }
  /* Good */
  .icon--plus { background-position: -4px -28px; }
  .icon--minus { background-position: -4px -58px; }
  ```

* Align vendor prefixed properties with the non-prefixed property.
  ```css
  -webkit-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
     -moz-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
       -o-box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
          box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
  ```

* Use `rgb()` and `rgba()` only to define colors, and don't leave spaces after
  the opening parentheses or before the closing parentheses.

* Use a space after every comma.

* Use a preceding zero for decimal numbers.

* Use double quotes for values in attribute value selectors (e.g.
  `input[type="text"]`).

* Don't specify units for zero values.

* Declare properties in alphabetical order, declaring mixins first if using
  LESS/SASS.

* Don't use `@import`, add an extra `<link>` tag instead.

* Prefer using the shorthand form of properties to declaring their individual
  values separately.
  ```css
  /* Bad */
  .someElement {
    margin-top: 8px;
    margin-right: 7px;
    margin-bottom: 6px;
    margin-left: 5px;
  }
  /* Good */
  .someElement {
    margin: 8px 7px 6px 5px;
  }
  ```

* Try to shorten the `margin` and `padding` when possible to their shorthand
  notation, one-value or two-value form. Don't use its shorter three-value form.

* Place media queries close to the elements they are referring to, don't put
  them all at the end of the document.

* Try to avoid using IDs as part of the selectors.

* Try to avoid nesting as much as possible, don't use more than 3 levels of
  nesting.

* Use `em` instead of `px` or `pt` for `font-size`

* Use unit-less `line-height` values except for when the `line-height` has to
  match the fixed box height, in which case the `line-height` is the elements
  `height` minus 1.

* Prefer selecting elements through class names, instead of element name or
  through attributes.

* Use double quotes for properties that receive strings, like `font-family`
  values and `url("")`.

* Never use any rules with `!important`.

## General

* Don't use class names that specify presentational behavior, instead use class
  names that describe a semantic structure. Grid-like class names (`col-6`,
  `row`) shouldn't never be used.

* Compile your assets with a preprocessor like LESS or SASS into a single file.

* Use a reset file, to avoid browser implementation inconsistencies.

* Use comments to separate a cohesive declaration of rule sets including
  multiple `*`. Each of these comment lines should have 80 characters in size.

* Avoid too long or too short class names.

* Keep the code simple.

* Be consistent.

* Use common sense.

## LESS (or SASS) specifics

* Use mixins for every property declaration that requires vendor prefixes, mixin
  names are prefixed with `m-`.

* Use a mixin for declaring the `font-size` and `line-height` in `px`, to
  transform it into `em`, receiving the context in `px` as an optional
  parameter.

* Avoid nesting selectors as much as possible, unless nesting the selectors is
  your only choice.

## CSS architecture using BEM

The [BEM approach](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
to structure the CSS has been proven to be the most successful in organizing and
working with presentational assets in web applications.

The BEM (Block-Element-Modifier) approach consists in separating every piece of
the UI into components, so that they can be reused throughout the entire
application. These components would naturally derive from a styleguide where
every component is defined separately. It is only through the composition of
these components that the entire pages are built.

It is recommended that each of these components are specified in a different
file and then compiled into a single stylesheet.

The BEM convention used here consists of declaring the component, its
descendants and modifiers as follows:

### Component (Block)

The component name consists of a `camelCase` declaration which is descriptive
according to the structure of the component.

```css
.navMenu {}
```

### Descendants (Element)

The component descendants consist of the child elements of the component. They
are named using `camelCase` as well, and prepended by the component name
separated by a hyphen.

```css
.navMenu-item {}
```

### Modifiers

Modifiers apply when the presentation of the main component or its descendants
changes slightly from its original one. These rules are specified after the
component or descendant specification. The name consists of the component or
descendant name, two hyphens and the `camelCase` modifier name.

```css
.navMenu--secondary {}
.navMenu-item--featured {}
```

### State declarations

State declarations on components or descendants are used to indicate some state
of the element itself. Every state indicator is prepended by `is-`. Common state
declarations used are: `.is-active`, `.is-disabled`, `.is-expanded`.

```css
.navMenu {
  display: none;
}

.navMenu.is-expanded {
  display: block;
}
```

### Javascript classes

Use `js-` prefixed class names for elements that are going to be manipulated
through JavaScript. Examples: `js-tooltip`, `js-dropdown`.

### Folder structure

A typical folder structure to hold this architecture would be:

* On the LESS stylesheets root should be a main file for each CSS file to be
  generated as output. Usually, you could have `application.less`, `admin.less`
  and `mobile.less`.

* Then there's the `components/` folder, where you have every component with one
  file per component, using the component name as the file name. Each of these
  files only contains the component definition, including its descendants and
  modifiers.

* The there's the `shared/` folder, that contains:
  * The `base.less` file, which specifies a few base styles for the entire
    HTML document, treat the base file as if there was a `base` component,
    where you define the `font-size`, `background-color`, etc for the
    document/body.
  * The `mixins.less` file, which specifies all the mixins to be used by the
    components.
  * The `reset.less` file, which sets the base styles for all HTML elements to
    maintain a consistency between the browsers.
  * The `variables.less` file, which holds all the variables to be used by the
    components and mixins.

```
less/
├-- application.less
├-- mobile.less
├-- admin.less
├-- components/
│   ├-- action.less
│   ├-- detailCard.less
│   ├-- formField.less
│   ├-- icon.less
│   ├-- list.less
│   └-- selectMenu.less
└-- shared/
    ├-- base.less
    ├-- mixins.less
    ├-- reset.less
    └-- variables.less

public/ # Output folder
└-- stylesheets/
    ├-- application.css
    ├-- mobile.css
    └-- admin.css
```

### Variables

Variables should be used for everything that could be reused. Use variables for
the following things:

* `z-index`, this should go from the lowest `z-index` value (100) to the
  highest (1000), use them in order of availability and try to avoid reaching
  the highest value.
  ```css
/* z-index definition */
@zIndex-1: 100;
@zIndex-2: 200;
@zIndex-3: 300;
@zIndex-4: 400;
@zIndex-5: 500;
@zIndex-6: 600;
@zIndex-7: 700;
@zIndex-8: 800;
@zIndex-9: 900;
@zIndex-10: 1000;

/* z-index application */
@sidebar--zIndex: @zIndex-1;

@mainHeader--zIndex: @zIndex-2;
@caption--zIndex: @zIndex-2;
@tooltip--zIndex: @zIndex-2;
  ```

* `font-weight`, which should be defined as follows:
  ```css
/* font-weight definition */
@fontWeight-1: 200;
@fontWeight-2: 400;
@fontWeight-3: 700;
@fontWeight-4: 900;

/* font-weight application */
@mainHeader-title--fontWeight: @fontWeight-4;
  ```

* `letter-spacing`, which should be defined as follows:
  ```css
/* letter-spacing definition */
@letterSpacing-tighter: -0.1em
@letterSpacing-tight: -0.04em;
@letterSpacing-normal: -0.02em;
@letterSpacing-loose: 0;
@letterSpacing-looser: 0.02em;

/* letter-spacing application */
@tooltip--letterSpacing: @letterSpacing-tight;
  ```

* Base `font-size`, `line-height`, `font-family`. These are then used on the
  `shared/base.less`.
  ```css
  /* fonts */
  @base--fontSize: 13px;
  @base--lineHeight: 1.4em;
  @base--fontFamily: "Helvetica Neue", "Helvetica", Arial;
  ```

* Colors. Not all colors are supposed to be specified in variables to then be
  used on the components. Usually the colors that are important and define the
  look and feel of the pages are the ones that need to go in the
  `shared/variables.less`. The format for specifying these colors would be
  `<component>[-descendant][-modifier]--<property>`. Some examles would be:
  ```css
  /* colors */
  @base--color: rgb(56, 56, 56);
  @base--backgroundColor: rgb(255, 255, 255);
  @mainHeader--backgroundColor: rgb(42, 52, 64);
  @navMenu-item--color: rgba(0, 0, 0, 0.9);
  @navMenu-item-active--color: rgba(0, 136, 204, 0.9);
  ```
  Things that would not need go in the `shared/variables.less` are for example
  box shadow colors and other neutral colors that wouldn't change regardless of
  the site style.

  Use as few colors as possible, and try to share them in multiple components.
  If necessary, use LESS color transformation functions to reduce the opacity
  of an existing color and to lighten it up.

### Layout

Using a system of grids with classes is the opposite from what you want to
achieve using CSS classes. One of the main purposes of using CSS is to remove
the presentation aspect from the HTML. Classes like `col-3` and `span-4` are
purely presentational, and they violate the purpose of using stylesheets and
separating presentation from the semantic structure.

Every layout of every page can also be abstracted into the sum of multiple
components. Usually these components will consist of some header, sidebar,
content, footer and maybe even secondary headers and a bunch of box groups.

An example of a layout component, would be `.mainHeader`, which could be defined
as follows:

```css
/* components/mainHeader.less */
/* mainHeader *****************************************************************/
.mainHeader {
  height: 80px;
  line-height: 79px;
  background-color: @mainHeader--background-color;
}

.mainHeader-title {
  display: none;
}

.mainHeader-logo {
  float: left;
  max-height: 40px;
  margin: 20px 0;
}

.mainHeader-nav {
  float: right;
}

/* components/contentWrapper.less */
/* contentWrapper *************************************************************/
.contentWrapper {
  max-width: 520px;
  margin: 0 auto;
}
```

```
<header class="mainHeader">
  <div class="contentWrapper">
    <a href="/">
      <h1 class="mainHeader-title">App Name</h1>
      <img class="mainHeader-logo" src="/images/app-logo.png"
           alt="App Logo" />
    </a>
    <nav class="mainHeader-nav">
      <ul class="navMenu">
        <li class="navMenu-item is-active"><a href="/">Home</a></li>
        <li class="navMenu-item"><a href="/overview">Overview</a></li>
      </ul>
    </nav>
  </div>
</header>
```

## Mobile

The mobile approach depends solely on the web application size, and how it is
expected for it to scale.

If the webapp is a small one which will remain this way the responsive design is
the way to go. You deal with this by using media queries and fluid layouts.

If the webapp is a large scale application, then using an adaptive approach by
detecting the agent from the server-side and rendering the necessary data
depending on the device is the best approach. This will reduce the difficulty
needed to be able to take into account multiple devices like the responsive
approach does. This approach consists of building one webapp for the large
screens and a different one for mobile. These two applications would share most
of the components and variables usage, but there will be some differences. This
approach, will most likely reduce the page load time and will accelerate the
development process.

## References

* [@mdo codeguide](http://codeguide.co/#css).

* [BEM approach](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

* [@fat Medium story](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)

* [Responsive vs. Adaptive](http://blog.catchpoint.com/2014/07/16/adaptive-vs-responsive-web-design-quantifying-difference/)
