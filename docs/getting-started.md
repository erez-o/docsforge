Getting Started
===============

[Doxiz](http://doxiz.com/) creates and hosts documentation for your open source projects.

It supports both manual documentation pages, and code auto-documentation to create public API pages.

Adding a New Project
--------------------

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
            "excludeApi": ["some_class1", "some_func2"],
            "documentSingleUnderscore": true,
            "documentStatic": true,
            "documentProtected": true
        }
    ]
}
```

The configuration file has 2 main parts:

*   `sidebar` - defines the documentation layout - which sections and pages will appear in your sidebar. Most pages will be text files (.txt, .md, .rst) or auto-generated API pages. 

*   `autodocSettings` - defines which parts of your public API will be displayed - which source files to document, which to exclude, whether to document names that start with a single underscore, etc...

!!! Tip
    The full public API can be very large and daunting. Focus users to look into the most used API as was done in `Important API` section. Any auto-generated API page can be added to any section.

To learn more, you can learn how to [customize the sidebar](http://doxiz.com/doxiz/master/customizing-the-public-api), [customize the public api](http://doxiz.com/doxiz/master/customizing-the-public-api), or view the full list of [autodoc settings](http://doxiz.com/doxiz/master/autodoc-settings)

Improving your documentation
----------------------------
Anyone reading your documentation can suggest edits and improvements.

Every page in your documentation is linked to your git repo, so any edits will go directly to github or bitbucket.

This includes documentation created from your source code - when you try to edit a public API page, you will be sent to the lines of code that created this documentation. 

Multiple Versions
-----------------
Each project can have several documentation versions, for different release tags or branches of your project. 

You can also define which version is the `latest stable` - the version which the end users should see by default.