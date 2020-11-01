Themes CSS Javascript
==============

Themes
------
There are various color schemes that can be chosen in the <code><i class="fa fa-cog"></i></code> `Edit Project Settings` menu.

The current themes are:

- Dark Blue (dark sidebar, blue top, invisible scrollbar)

- Dark Green (dark sidebar, green top, invisible scrollbar)

- Dark Purple (dark sidebar, purple top, invisible scrollbar)

- White Blue (white sidebar, blue top, visible scrollbar)

- White Green (white sidebar, green top, visible scrollbar)

- White Purple (white sidebar, purple top, visible scrollbar)

<p>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-blue.jpg">
        <img width="200" alt="Dark Blue" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-blue.jpg">
    </a>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-green.jpg">
        <img width="200" alt="Dark Green" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-green.jpg">
    </a>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-purple.jpg">
        <img width="200" alt="Dark Purple" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/dark-purple.jpg">
    </a>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-blue.jpg">
        <img width="200" alt="White Blue" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-blue.jpg">
    </a>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-green.jpg">
        <img width="200" alt="White Green" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-green.jpg">
    </a>
    <a href="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-purple.jpg">
        <img width="200" alt="White Purple" src="https://raw.githubusercontent.com/erez-o/docsforge/master/images/themes/white-purple.jpg">
    </a>
</p>

CSS
---

If you wish to further customize the predefined themes, you can also include an additional html css snippet in the <code><i class="fa fa-cog"></i></code> `Edit Project Settings` menu.

This additional html snippet will be included at the end of the `<head>` section of every page in your project.

Example snippet:

```html
<!-- External css -->
<link rel="stylesheet" href="URL_TO_YOUR_CSS_FILE.min.css">

<!-- Internal css -->
<style>body {color:red}</style>
```

[Jsdelivr](https://github.com/jsdelivr/jsdelivr) provides a free and easy way to serve css/js files from your github repository using the format:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/user/repo@version/filename.min.css">.
```

### CSS Variables ###

docsforge uses css variables to allow easy themeing of your project docs.

Notable css variables:

```css
:root {
    /* The default fallback are currently black sidebar + bluish nabvar/sidebar titles. */

    /* configurable css vars: */
  --left-sidebar-bg: #222d32;                         /* left sidebar background - default= balckish */
  --top-navbar-bg: #3c8dbc;                           /* top navbar background - default=blueish */
  --top-left-navbar-bg: #367ea9;                      /* top left navbar background - default=darker blueish */
  --left-sidebar-width-md: 250px;                     /* width of sidebar in md screens. Maintainers can change if it's too narrow */
  --left-sidebar-width-lg: 320px;                     /* width of sidebar in lg screens. Maintainers can change if it's too narrow */
  --left-sidebar-selected-color: #2badd4;             /* left sidebar selected color. ONLY APPLICABLE TO WHITE THEME (blue by default). */
  --left-sidebar-title-color: var(--top-navbar-bg);   /* left sidebar title colors. ONLY APPLICABLE TO DARK THEME (blue by default). (On white theme, the titles color are the same as the tree.) */
  --link-color: #2badd4;                              /* link color */
}
```

If you wish to add additional variable please open an issue on github. 




Javascript
----------

You can also include an additional html javascript snippet in the <code><i class="fa fa-cog"></i></code> `Edit Project Settings` menu.

This additional html snippet will be included at the end of the `<body>` section of every page in your project.

Example snippet:

```html
<!-- External javascript -->
<script src="URL_TO_YOUR_JS_FILE.min.js"></script>

<!-- Inline javascript -->
<style>body {color:red}</style>
```

[Jsdelivr](https://github.com/jsdelivr/jsdelivr) provides a free and easy way to serve css/js files from your github repository using the format:

```html
<script src="https://cdn.jsdelivr.net/gh/user/repo@version/filename.min.js"></script>
```

### Helpful JS Examples ###

#### accesskey ####

Adding an access key for the search box [#27](https://github.com/erez-o/docsforge/issues/27)

Add the following html snippet:

```js
<script>
  $("#search-in-project").attr("accesskey", "s");      // Activate the search box when pressing "s" on the keyboard
</script>
```
