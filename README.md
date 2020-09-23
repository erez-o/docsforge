[![Documentation](https://img.shields.io/badge/docs-docsforge-blue)](http://help.docsforge.com/)

DocsForge
=========

[DocsForge](http://docsforge.com/) is a documentation framework that creates and hosts docs for github code projects.

Key features
------------

- **No installation needed**.  
Your docs are built and hosted directly through [DocsForge](http://docsforge.com/).

- **Easy to set up**.  
Takes only a few minutes to get your documentation website up and running. 

- **Multiple docs formats**.  
Support docs in markdown, GitHub flavored commonmark, reStructuredText, AsciiDoc, Man, MediaWiki, ...

- **API code documentation, tailored for C/C++**.  
Supports API documentation in multiple languages (uses and extends doxygen). Supports projects with multiple languages (for example both C++ and python). Documentation pages are scanned to automatically detect api pages and creates links to them.

- **Highly configurable yaml configuration file**.  
Define which markdown files you want to display, define 

- **Docs are updated automatically.**.  
Your docs are rebuilt periodically so your project remains in sync with the docs.

- **Multiple versions**.  
Host docs for multiple interesting branches or versions. For example, `master` and `v1.0`. 

- **Customizable looks**.  
Change themes, add your own css or js.

Screenshots:
------------

For example, the following screenshots are from the [TinyXml2](http://tinyxml2.docsforge.com/) project (version 7.0.1):

### Getting started page:

![Getting started](https://raw.githubusercontent.com/erez-o/docsforge/master/images/tinyxml2-getting_started.png)

<br>

### Man page for class XMLDocument:

![XMLDocument](https://raw.githubusercontent.com/erez-o/docsforge/master/images/tinyxml2-class_xml_document.png)

<br>

### Man page for function OpenElement:

![GetText1](https://raw.githubusercontent.com/erez-o/docsforge/master/images/tinyxml2-open_element_1.png)

<br>

**Page continues...**

![GetText2](https://raw.githubusercontent.com/erez-o/docsforge/master/images/tinyxml2-open_element_2.png)

<br>


Configuration File
------------------

Each project has a YAML configuration file that defines how to build the documentation.

When you add a new project, we create a configuration file to get you started.

An example configuration file:

```yaml
sidebar:
  Basic Tutorial:
  - Getting Started: readme.md
  - Installation: docs/readme.md
  Advanced Tutorial:
  - Frequently Asked Questions: docs/faq.md
  - Advanced Topics: docs/advanced.md
  - Code Example 1: src/my_example.cpp
  - Contact us: http://example.com/contact-us/
  Important API:
  - func1: api/my_class/func1             # Highlight your most used api. 
  - class2: api/class2                    # Highlight your most used api. 
  
autodocSettings:
  Public API:
    baseUrl: api                          # prefix url for all api pages.
    language: cpp                         
    INPUT: include src                    # `src` directory, where the code files are located. 
    EXCLUDE: src/utils                    # exclude `src/utils` from being auto documentation                     
    excludeApi:
    - my_class/my_func                    # exclude `my_class/my_func` from being auto documented
    includeApi:
    - include/publc.h                     # autodocument only elements that are declared in `include/public.h`.
    documentSingleUnderscore: true        # document functions/classes if their names start with `_`
    documentStatic: true                  # document `static` elements 
    documentProtected: true               # document `protected` elements
    extractNonDocComments: false          # If True, extract any code comment that starts with `//`, not only comments that starts with `///`
```

*   `sidebar` - defines the documentation layout - which sections and pages will appear in your sidebar. Pages can either be text files (.txt, .md, .rst, ...) or selected API pages from the auto-documentation. 

*   `autodocSettings` - defines which parts of your public API will be displayed - which source files to document, which to exclude, whether to document names that start with a single underscore, etc...

*   `Important API`   - The full public API can be very large and daunting for new users. Focus users to look into the most used API as was done in `Important API` section. Any auto-generated API page can be added to any section.

To learn more, you can learn how to [customize the sidebar](http://help.docsforge.com/master/customizing-the-public-api), [customize the public api](http://help.docsforge.com/master/customizing-the-public-api), or view the full list of [autodoc settings](http://help.docsforge.com/master/autodoc-settings)


Example projects using docsforge
--------------------------------

- https://drogon.docsforge.com/

    ![drogon](https://raw.githubusercontent.com/erez-o/docsforge/master/images/drogon-main.png)
    
    The configuration file is:
    
    ```yaml
    sidebar:
      Basic Tutorial:
      - Getting Started: README.md
      - License: LICENSE
      Wiki:
      - Overview: wiki/ENG-01-Overview.md
      - Installation: wiki/ENG-02-Installation.md
      - Quick Start: wiki/ENG-03-Quick-Start.md
      - Controller Introduction:
        - index: wiki/ENG-04-0-Controller-Introduction.md
        - Controller HttpSimpleController: wiki/ENG-04-1-Controller-HttpSimpleController.md
        - Controller HttpController: wiki/ENG-04-2-Controller-HttpController.md
        - Controller WebSocketController: wiki/ENG-04-3-Controller-WebSocketController.md
      - Filter: wiki/ENG-05-Filter.md
      - View: wiki/ENG-06-View.md
      - Session: wiki/ENG-07-Session.md
      - Database General:
        - index: wiki/ENG-08-0-Database-General.md
        - DataBase DbClient: wiki/ENG-08-1-DataBase-DbClient.md
        - DataBase Transaction: wiki/ENG-08-2-DataBase-Transaction.md
        - DataBase ORM: wiki/ENG-08-3-DataBase-ORM.md
        - DataBase FastDbClient: wiki/ENG-08-4-DataBase-FastDbClient.md
      - Plugins: wiki/ENG-09-Plugins.md
      - Configuration File: wiki/ENG-10-Configuration-File.md
      - Drogon Ctl Command: wiki/ENG-11-drogon_ctl-Command.md
      - AOP Aspect Oriented Programming: wiki/ENG-12-AOP-Aspect-Oriented-Programming.md
      - Benchmarks: wiki/ENG-13-Benchmarks.md
      - Coz profiling: wiki/ENG-14-Coz.md
      Important API:
      - HttpController: api/drogon/HttpController
      - HttpAppFramework: api/drogon/HttpAppFramework
      - HttpRequest: api/drogon/HttpRequest
      - HttpResponse: api/drogon/HttpResponse
      - HttpClient: api/drogon/HttpClient
      - CacheMap: api/drogon/CacheMap
      - Cookie: api/drogon/Cookie
      - HttpFilter: api/drogon/HttpFilter
      - HttpSimpleController: api/drogon/HttpSimpleController
      - WebSocketClient: api/drogon/WebSocketClient
    
    autodocSettings:
      Public API:
        baseUrl: api
        language: cpp
        INPUT: lib/inc/drogon orm_lib/inc/drogon/orm
        EXCLUDE: test tests examples
        EXCLUDE_PATTERNS: '*/tests/* */test/*'
        EXAMPLE_PATH: ''
        includeApi: []
        excludeApi:
        - drogon/internal
        - trantor
        - Json
        documentSingleUnderscore: true
        documentStatic: true
        documentProtected: true
        extractNonDocComments: false
        extract_namespace_comments: false
        ENABLE_PREPROCESSING: 'YES'
        MACRO_EXPANSION: 'NO'
        EXPAND_ONLY_PREDEF: 'NO'
        PREDEFINED: ''
        SEARCH_INCLUDES: 'YES'
        INCLUDE_PATH: ''
        INCLUDE_FILE_PATTERNS: ''
    
    additionalSettings:
      wiki_repo_path: wiki
    ```

- https://flecs.docsforge.com/

    ![flecs-doc](https://raw.githubusercontent.com/erez-o/docsforge/master/images/flecs-doc-example.png)
    ![flecs-api](https://raw.githubusercontent.com/erez-o/docsforge/master/images/flecs-api-example.png)
    
    The configuration file is: (note two separate autodoc blocks for `C API` and `C++ API`)
    
    ```yaml
    sidebar:
      Documentation:
      - Readme: README.md
      - FAQ: docs/FAQ.md
      - Quickstart: docs/Quickstart.md
      - Manual: docs/Manual.md
      - MigrationGuide: docs/MigrationGuide.md
    
    autodocSettings:
      C API:
        language: c
        INPUT: include/flecs.h
        EXCLUDE_PATTERNS: '*/tests/* */test/* include/flecs/util/*'
        EXAMPLE_PATH: examples
        includeApi: []
        excludeApi: []
        documentSingleUnderscore: true
        documentStatic: false
        documentProtected: true
        extractNonDocComments: false
        sort_by_type: false
        sort_alphabetically: false
        ENABLE_PREPROCESSING: 'YES'
        MACRO_EXPANSION: 'NO'
        EXPAND_ONLY_PREDEF: 'NO'
        PREDEFINED: ''
        SEARCH_INCLUDES: 'YES'
        INCLUDE_PATH: ''
        INCLUDE_FILE_PATTERNS: ''
      C++ API:
        baseUrl: api-cpp
        language: cpp
        INPUT: include/flecs/flecs.hpp
        EXCLUDE: 'test templates'
        EXCLUDE_PATTERNS: '*/tests/* */test/*'
        EXAMPLE_PATH: examples
        includeApi: []
        excludeApi: []
        documentSingleUnderscore: true
        documentStatic: true
        documentProtected: true
        extractNonDocComments: false
        ENABLE_PREPROCESSING: 'YES'
        MACRO_EXPANSION: 'NO'
        EXPAND_ONLY_PREDEF: 'NO'
        PREDEFINED: ''
        SEARCH_INCLUDES: 'YES'
        INCLUDE_PATH: ''
        INCLUDE_FILE_PATTERNS: ''
    
    additionalSettings:
      markdown_fenced_code_tabs: true
    ```

- https://entt.docsforge.com/

    ![EnTT-api](https://raw.githubusercontent.com/erez-o/docsforge/master/images/entt-api.png)

Bugs and feature requests
-------------------------

If you find a bug or have a feature request, please open an issue here.

This project is actively being developed, so any feedback is greatly appreciated.  