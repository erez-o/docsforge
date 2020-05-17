Markdown
========

Markdown is the language used in DocsForge pages and discussions.
It follows [John Gruber’s Markdown](http://daringfireball.net/projects/markdown/) and some extentions from [Github flavored markdown](https://help.github.com/articles/github-flavored-markdown/).
The package used to render markdown is [Python-Markdown](https://pypi.python.org/pypi/Markdown).

This page covers the following topics:

[TOC]

Paragraph and Line breaks
-------------------------
1.  **A single line break does not create a new paragraph:**
         
        paragraph one
        paragraph two

    **Result:**

    paragraph one
    paragraph two

2.  **Two line breaks to create new paragraph:**

        paragraph one

        paragraph two

    **Result:**

    paragraph one

    paragraph two

3.  **To force a line break (`<br>`), end a line with two or more spaces, then type return.**

        paragraph one
        paragraph two

    **Result:**

    paragraph one  
    paragraph two

Bold and Italic
--------
You can make a text bold or italic.
```
*this text will be italic*
**this text will be bold**
```
Emphasize using `*` or `_`. Single asterisks/underscore for Italic, double asterisks/underscore for Bold

Headings
---------
Create headings by adding 1-6 hashes (`#`) at the beginning and ending of a line. In DocsForge, you should use up till H2 because the page main title is kept seperate from the markdown content. If you do use H1, it will be rendered the same as H2.
```
## This is an H2 (the largest heading you should use) ##
### This is an H3 ###
###### This is an H6 (the smallest heading) ######

This is also H2
---------------
```

Lists
------
### Unordered lists
```
*   Item 1
*   Item 2
*   Item 3
```
### Ordered lists
```
1.   Item 1
2.   Item 2
3.   Item 3
```

Links
------
```
This is [an example](http://example.com/) inline link. 
```
**Result:** 
This is [an example](http://example.com/) inline link.

Auto-linking is supported:
```
http://example.com/
```
**Result:**  
http://example.com/

Images
------
Image syntax is very much like the link syntax:

1.  Inline (title is optional)

        ![alt text](http://path/to/img.jpg "Title")

2.  Reference style (title is optional)

        ![alt text][id]

        [id]: /path/to/img.jpg "Title"

Code
----
### Single line code
To indicate a span of code, wrap it with backtick quotes (`). For example:

    Use the `printf()` function.
   
**Result:** Use the `printf()` function.

### Multiline code
To insert a multiline code, either indent it by 4 spaces, or wrap the entire snippet in 3 backtick quotes (```) common in [GitHub](https://help.github.com/articles/github-flavored-markdown/#fenced-code-blocks).

Syntax highlighting is done by highlight.js. 

If you wish to actiate syntax highlighting on a block of code, you must use the (```) option, and add your selected language.

    ```python
    x = 0
    x = x + 1
    print x
    ```

**Result:**

```python
x = 0
x = x + 1
    print x
```


Definition list
----------------
Definition lists are defined using the syntax established in [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/#def-list).
```
Apple
:   Pomaceous fruit of plants of the genus Malus in
    the family Rosaceae.

Orange
:   The fruit of an evergreen tree of the genus Citrus.
```

**Result:**

Apple
:   Pomaceous fruit of plants of the genus Malus in
    the family Rosaceae.

Orange
:   The fruit of an evergreen tree of the genus Citrus.

Tables
------
Tables are defined using the syntax established in [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/#def-list).
```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell
```

Admonition
----------
Admonitions provide important bulletings boxes for the reader. For example:
```
!!! note
    You should note that the title will be automatically capitalized.

!!! note "Optional Title"
    Example with optional title.

!!! hint
    Use hints to provide helpful tips. The keywords `hint` and `tip` render the same.
    
    Remember - two line breaks for additional paragraphs

!!! warning
    You are about to do something dangerous.

!!! danger
    Do not try this at home!

```
**Result:**

!!! note
    You should note that the title will be automatically capitalized.

!!! note "Optional Title"
    Example with optional title.

!!! hint
    Use hints to provide helpful tips. The keywords `hint` and `tip` render the same.
    
    Remember - two line breaks for additional paragraphs

!!! warning
    You are about to do something dangerous.

!!! danger
    Do not try this at home!

Accepted words are `note`, `warning`, `danger`, `hint`, and `tip`.

Table of contents
-----------------
You can display the table of contents (created automatically from all your headings), by adding the keyword `[TOC]` in the position you want it to be spanned.

The table of contents in the beginning of this page was created using it.

Horizontal Rules
----------------
You can produce a horizontal rule tag (`<hr/>`) by placing three or more hyphens, asterisks, or underscores on a line by themselves.
```
*********
```
**Result**:

*********

Using Raw HTML
--------------
You can insert raw html directly in your markdown content. Some tags will be sanitized and escaped. 

For example:

```html
<p>An HTML paragraph with an <script>evil</script></p>

```

**Result:**

<p>An HTML paragraph with an <script>evil</script></p>


ReStructuredText
----------------
ReStructuredText (or RST) is a markup language similar to markdown. ReStructuredText is transformed to html using [docutils](https://pypi.org/project/docutils/). 

You can also use [pandoc](http://pandoc.org/try/?text=&from=rst&to=markdown_github) to convert files from RST to markdown.