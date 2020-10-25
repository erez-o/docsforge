Customizing the sidebar
=======================

!!! Tip
    You can see the configuration file of any project by clicking the <code><i class="fa fa-wrench"></i></code> icon in the top bar.

Example
-------
This is the configuration file that creates this help section. 

```yaml
sidebar:
  Basic Tutorial:
  - Getting Started: docs/getting-started.md
  - Customizing The Sidebar: docs/customizing-the-sidebar.md
  - Customizing The Public Api: docs/customizing-the-public-api.md
  - Discussions: docs/discussions.md
  - Themes and CSS: docs/themes-and-css.md
  More Info:
  - Autodoc Settings: docs/autodocSettings-full-list.md
  - Building Version Documentation: docs/building-version-documentation.md
  - Markdown Cheat Sheet: docs/markdown-cheat-sheet.md
  - Configuration Schema: docs/schema.json
  - Changelog: docs/changelog.md
  - Contact Us: docs/contact-us.md
  - Feature Requests: https://github.com/erez-o/docsforge/issues
autodocSettings: {}
```

The above yaml configuration file defines:

1.  A `sidebar` that contains two sections - "Basic Tutorial" and "More Info". Each section contains multiple pages.

2.  A blank `AutodocSettings`, because this project contains no auto code documentation.


Page Types
----------
To add pages to sections, you need to supply a simple `key: value`. `key` is the name of the page, and `value` is how to retrieve its data.

There are several page types that can be created:

### Doc page from your repo

To add a documentation page to your sidebar, you need to supply a `key` that defines the page name, and a `value` that defines that file path to where your file is in your repository.

File path can be a documentation file (markdown, reStructuredTxt, html, asciidoc, text), or a source code file, like the above `schema.json`.

For example:

```yaml
Customizing The Sidebar: docs/customizing-the-sidebar.md
```


### API page

The auto-documentation creates API pages from your source code, and displays **all** of them under the section `Public API`.
 
However, not all API pages are as important as others. Therefore, you can highlight some of them, and insert them to additional sections as well.

For example: (see [getting started](https://help.docsforge.com/getting-started/#configuration-file))

```yaml
my_important_function1: api/my_important_class/my_important_function1
```

(*) This assumes you have function `my_important_class` inside class `my_important_function1`, and `baseUrl: api` in your `autodocSettings`.

!!! tip
    To make things simpler, on every public API page, there's a <code><i class="fa fa-star-o"></i></code> icon that will add the page to the `Important API` section in the yaml configuration file.

### Link page

To add this type of page to your sidebar, you need to supply a `key` that defines the page name, and a `value` to the to the full url you wish to link to. 

For example: 

```yaml
Contact us: http://example.com/contact-us/
```
        
### Doc page from a different repo

To add a documentation page to your sidebar, you need to supply a `key` that defines the page name, and a `value` that defines that file path to where the **raw** file is.

For example, a markdown file from a regular repository:
    
```yaml
My page: https://raw.githubusercontent.com/<username>/<reponame>/master/<filename>.md
```
    
For example, from a wiki repository:
    
```yaml
My page: https://raw.githubusercontent.com/wiki/<username>/<reponame>/<filename>.md
```
        
        
Multi Level Sections
--------------------

The [example](#example) mentioned previously creates a flat single level sections. Multi level sections are supported as well.

Multi-level example:

```yaml
sidebar:
  Flat Section:
  - Getting Started: docs/getting-started.md
  - Customizing The Sidebar: docs/customizing-the-sidebar.md
  - Customizing The Public Api: docs/customizing-the-public-api.md
  Parent Section:
  - Child Section1:
    - Autodoc Settings: docs/autodocSettings-full-list.md
    - Building Version Documentation: docs/building-version-documentation.md
    Child Section2:
    - index: docs/child_section2_content.md
    - Discussions: docs/discussions.md
    - Markdown Cheat Sheet: docs/markdown-cheat-sheet.md
    - Configuration Schema: docs/schema.json
    - Feature Requests: https://github.com/erez-o/docsforge/issues
    - Contact Us: docs/contact-us.md
autodocSettings: {}
```

`Child Section1` and `Child Section2` are `directory pages` and will be presented by an expandable directory icon.


### Flat level example:

![Flat level example](https://raw.githubusercontent.com/erez-o/docsforge/master/images/docs-single_level_sidebar.png)

### Multi level example:

![Multi level example](https://raw.githubusercontent.com/erez-o/docsforge/master/images/docs-multi_level_sidebar.png)

### Adding content to a directory page

The default content of directory pages (for example, `Child Section1` and `Child Section2`) is auto generated. The default content is a simple list of its children pages. 

You can override the auto generated content by supplying the filePath where your content is. This can be done by adding an inner `key` page name `index`,`readme` or blank `` to the directory. All three options are synonymous in this regard.

In the above example, `Child Section1` will have an auto generated content, while `Child Section2` will have the content of the markdown page located at `docs/child_section2_content.md`.