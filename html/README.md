# HTML Style Guide

## Formatting

* Use UTF-8.

* Use 2 space indent, no tabs.

* Keep lines fewer than 80 characters.

* Avoid trailing whitespace.

* When a single tag takes more than one line, align the first letter of each
  attribute to the first letter of the first attribute. Leave a blank line after
  the tag end.

```
<!-- _ represent spaces -->
<a class="verLongClassName"
___id="very-long-id-attribute"
___href="/very/long/path">

__Link
</a>
  ```

* Encode HTML special characters with the `&` notation.

## Syntax

* Use double quotes on all attributes.

* Don't omit optional closing tags.

* Use `<!DOCTYPE html>` at the beggining of the page.

* Use the language attribute on the `html` tag, like so: `<html lang="en-us">`.

* Use the `X-UA-Compatible` meta tag [for IE compatibility](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).

* Use the `charset` meta tag with `UTF-8` as its value.

* Don't specify a `type` for stylesheet `link` tags and javascript `script`
  tags.

* Write the HTML attributes in this particular order:
  1. `class`
  2. `id`, `name`
  3. `data-*`
  4. `src`, `for`, `type`, `href`, `value`
  5. `title`, `alt`
  6. `aria-*`, `role`

  Classes make for great reusable components, so they come first. IDs are more
  specific and should be used sparingly (e.g., for in-page bookmarks), so they
  come second.

* Use a value for all attributes, including `checked` and `selected`.

* Never use `<br>` tags.

* Every form input that has text attached should utilize a `<label>` tag. When
  the tag wraps the input (usually with checkboxes/radiobuttons), there's no
  need for a `for` attribute.

* Use trailing slashes in self-closing tags, like `<img>` and `<input>`.

* Don't set `tabindex` manually, rely on the browser.

* For tables, use the `<caption>`, `<thead>`, `<tfoot>` (optional), `<tbody>`
  and `<th>` tags.

* Use the `scope` attribute on `<th>` tags to specify the scope.

* Try to avoid using `colspan` and `rowspan` on tables.

* Use the `alt` attribute with a meaningful text for all `<img>`.

* Don't use `<img>` tags for presentational purposes.

* Use `<em>` tags to emphasize text, avoid using `<strong>`.

* Try to avoid using the `<iframe>` tag, but if you do, add a meaningful `title`
  attribute to it.

* Don't use HTML5 deprecated tags like `<i>`, `<b>` and `<font>`.

* Put stylesheets at the bottom of the `<head>` and scripts at the bottom of the
  `<body>`, unless you can't avoid it.

* Include a single `<h1>` tag on every page.

* Don't leave empty `<a>` tags, add text and hide it with CSS.

* `<div>` and `<span>` have no semantic meaning, don't use them to separate
  semantic content.

## General

* Avoid using comments.

* HTML documents should be readable without a stylesheet.

* Always take accessibility into account.

* Use links to convey navigational actions and buttons to convey modifying
  server-side actions.

* Write as little HTML as possible.

* Keep the code simple.

* Be consistent.

* Use common sense.

## Sample
```html
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <title>Organization | Overview</title>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=Edge" />

    <link href="/stylesheets/application.css" media="screen" rel="stylesheet" />
    <link href="/assets/images/favicon.png" rel="shortcut icon" type="image/png" />
  </head>
  <body>
    <header class="mainHeader">
      <a href="/"><img src="logo.png" alt="Company Logo" /></a>
      <hgroup>
        <h1>Overview</h1>
        <h2>We code</h2>
      </hgroup>
      <nav class="navMenu">
        <ul>
          <li>
            <a class="navMenu-item" href="/">Home</a>
          </li>
          <li>
            <a class="navMenu-item is-active" href="/overview">Overview</a>
          </li>
        </ul>
      </nav>
    </header>
    <section class="veryVeryLongClassName"
             id="very-very-very-long-id-attribute-name">

      <header><h2>Explanation<h2></header>
      <p>This is the explanation...</p>
    </section>

    <script src="/javascripts/application.js"></script>
  </body>
</html>
```

## References

* [@mdo codeguide](http://codeguide.co/#html)

* [WebAIM](http://webaim.org/standards/508/checklist)
