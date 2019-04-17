Doxiz
=========

[Doxiz](http://doxiz.com/) is a website that hosts and creates documentation for your code projects.

It is completely **FREE** of charge for open source projects.
 
It features a customizable manual and automatic code documentation. It also features multiple versioning for each tag or branch.

**It's designed to be simple and automatic, so documenting your project should only take a few minutes.**

Screenshots:
------------

For example, the following screenshots are from the [TinyXml2](http://doxiz.com/tinyxml2/) project (version 7.0.1):

### Getting started page:

![Getting started](https://raw.githubusercontent.com/erez-o/doxiz/master/images/tinyxml2-getting_started.png)

<br>

### Man page for class XMLDocument:

![XMLDocument](https://raw.githubusercontent.com/erez-o/doxiz/master/images/tinyxml2-class_xml_document.png)

<br>

### Man page for function OpenElement:

![GetText1](https://raw.githubusercontent.com/erez-o/doxiz/master/images/tinyxml2-open_element_1.png)

<br>

**Page continues...**

![GetText2](https://raw.githubusercontent.com/erez-o/doxiz/master/images/tinyxml2-open_element_2.png)

<br>


How it works:
------------

When you [add a new project](http://doxiz.com/add-project/choose-host/), you provide a few basic parameters:

*   A url to where your repository is located.

*   The main programming language of your project (github or bitbucket).

*   (Optional) Docs directory where you have manually written documentation files.

*   (Optional) Source code directory that you wish to extract code auto-documentation.

We then link to your repository, extract documentation files that were written manually, and auto-document your source code.

Configuration File
------------------

Each project has a configuration file that defines how to build the documentation. 

When you add a new project, we create a configuration file to get you started.

An example configuration file:

```json
{
    "sidebar": {
        "Basic Tutorial": [
            {"pageName": "Getting Started","filePath": "readme.md"},
            {"pageName": "Installation","filePath": "docs/readme.md"}         
        ],
        "Advanced Tutorial": [
            {"pageName": "Frequently Asked Questions","filePath": "docs/faq.md"},
            {"pageName": "Advanced Topics","filePath": "docs/advanced.md"},
            {"pageName": "Code Example 1","filePath": "src/my_example.cpp"}, 
            {"pageName": "Contact us","url": "http://example.com/contact-us/"}
        ],        
        "Important API": [
            {"apiPath": "api/my_important_class/my_important_function1"},
            {"apiPath": "api/my_important_function2"}
        ]
    },
    "autodocSettings": [
        {
            "sectionName": "Public API",
            "baseUrl": "api",
            "language": "cpp",
            "INPUT": "src",
            "EXCLUDE": "tests examples",
            "excludeApi": ["an_unimportant_public_class", "an_unimportant_public_func"],
            "documentSingleUnderscore": true,
            "documentStatic": true,
            "documentProtected": true
        }
    ]
}
```

*   `sidebar` - defines the documentation layout - which sections and pages will appear in your sidebar. Most pages will be text files (.txt, .md, .rst) or auto-generated API pages. 

*   `autodocSettings` - defines which parts of your public API will be displayed - which source files to document, which to exclude, whether to document names that start with a single underscore, etc...

*   `Important API`   - The full public API can be very large and daunting for new users. Focus users to look into the most used API as was done in `Important API` section. Any auto-generated API page can be added to any section.

To learn more, you can learn how to [customize the sidebar](http://doxiz.com/doxiz/master/customizing-the-public-api), [customize the public api](http://doxiz.com/doxiz/master/customizing-the-public-api), or view the full list of [autodoc settings](http://doxiz.com/doxiz/master/autodoc-settings)


Bugs and feature requests
-------------------------

If you find a bug or have a feature request, please open an issue here.

This project is actively being developed, so any feedback is greatly appreciated.  