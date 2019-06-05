Customizing the sidebar
=======================

!!! Tip
    You can see the configuration file of any project by clicking the <code><i class="fa fa-wrench"></i></code> icon in the top bar.

Example
-------
This is the configuration file that creates this help section. 

```JSON
{
    "sidebar": {
        "Basic Tutorial": [
            {"pageName": "Getting Started","filePath": "docs/getting-started.md"},
            {"pageName": "Customizing The Sidebar","filePath": "docs/customizing-the-sidebar.md"},
            {"pageName": "Customizing The Public Api","filePath": "docs/customizing-the-public-api.md"}
        ],
        "More Info": [
            {"pageName": "Autodoc Settings","filePath": "docs/autodocSettings-full-list.md"},
            {"pageName": "Building Version Documentation","filePath": "docs/building-version-documentation.md"},
            {"pageName": "Discussions","filePath": "docs/discussions.md"},
            {"pageName": "Markdown Cheat Sheet","filePath": "docs/markdown-cheat-sheet.md"},
            {"pageName": "Configuration Schema","filePath": "docs/schema.json"},
            {"pageName": "Feature Requests","url": "https://github.com/erez-o/doxiz/issues"},
            {"pageName": "Contact Us","filePath": "docs/contact-us.md"}
        ]
    },
    "autodocSettings": []
}
```

The above Json file defines:

1.  A `sidebar` that contains multiple sections, the 1st being "Basic Tutorial". Each section contains multiple pages.

2.  A blank `AutodocSettings`, because this project contains no auto code documentation.


Page Types
----------
There are several page types that can be created:

1. **Documentation page**.

    To add this type of page to your sidebar, you need to supply a `pageName` that defines the page name, and a `filePath` to where your file is in your repository.

    They can be documentation files (markdown, reStructuredTxt, html, asciidoc, text), or they can be source code files, like the above `schema.json`.
    
    For example:
    
        {"pageName": "Customizing The Sidebar","filePath": "docs/customizing-the-sidebar.md"},


2. **API page**

    The auto-documentation creates API pages from your source code, and displays **all** of them under the section `Public API`.
     
    However, not all API pages are as important as others. Therefore, you can highlight some of them, and insert them to additional sections as well.
    
    For example: (see [getting started](https://doxiz.com/getting_started/#configuration-file))
     
        {"apiPath":"my_important_class/my_important_function1"}.
    
    (*) This assumes you have function `my_important_class` inside class `my_important_function1`. Also note the lack of `pageName`, as the name of a public API page is known (in this case, it's "Function my_important_function1").

    !!! tip
        To make things simpler, on every public API page, there's a <code><i class="fa fa-star-o"></i></code> icon that will add the page to the `Important API` section in the json configuration file.

3. **Link page**

    To add this type of page to your sidebar, you need to supply a `pageName` that defines the page name, and a `url` to the full http you wish to link to. 
    
    For example: 
    
        {"pageName": "Contact us","url": "http://example.com/contact-us/"}
        
        
Multi Level Sections
--------------------

The [example](#example) mentioned previously creates a flat single level sections. Multi level sections are supported as well.

Multi-level example:

```JSON
{
    "sidebar": {
        "Flat Section": [
            {"pageName": "Getting Started","filePath": "docs/getting-started.md"},
            {"pageName": "Customizing The Sidebar","filePath": "docs/customizing-the-sidebar.md"},
            {"pageName": "Customizing The Public Api","filePath": "docs/customizing-the-public-api.md"}
        ],
        "Parent Section": [
          {
            "Child Section1": [
                {"pageName": "Autodoc Settings","filePath": "docs/autodocSettings-full-list.md"},
                {"pageName": "Building Version Documentation","filePath": "docs/building-version-documentation.md"}
            ],
            "Child Section2": [
                {"pageName": "","filePath": "docs/child_section2_content.md"},
                {"pageName": "Discussions","filePath": "docs/discussions.md"},
                {"pageName": "Markdown Cheat Sheet","filePath": "docs/markdown-cheat-sheet.md"},
                {"pageName": "Configuration Schema","filePath": "docs/schema.json"},
                {"pageName": "Feature Requests","url": "https://github.com/erez-o/doxiz/issues"},
                {"pageName": "Contact Us","filePath": "docs/contact-us.md"}
            ]
          }
        ]
    },
    "autodocSettings": []
}
```

`Child Section1` and `Child Section2` are `directory pages` and will be presented by an expandable directory icon.


### Flat level example:

![Flat level example](https://raw.githubusercontent.com/erez-o/doxiz/master/images/docs-single_level_sidebar.png)

### Multi level example:

![Multi level example](https://raw.githubusercontent.com/erez-o/doxiz/master/images/docs-multi_level_sidebar.png)

### Adding content to a directory page

The default content of directory pages (for example, `Child Section1` and `Child Section2`) is auto generated. The default content is a simple list of its children pages. 

You can override the auto generated content by supplying the filePath where your content is. This can be done by adding an inner `"pageName":""` or `"pageName":"index"` or `"pageName":"readme"` to the directory. All three options are synonymous in this regard.

In the above example, `Child Section1` will have an auto generated content, while `Child Section2` will have the content of the markdown page located at `"filePath": "docs/child_section2_content.md"`.