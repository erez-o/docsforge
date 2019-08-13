Customizing The Public Api
=========================

!!! Tip
    You can see the configuration file of any project by clicking the <code><i class="fa fa-wrench"></i></code> icon in the top bar.

When you add a new project, The default is to create pages for **any public** function/class/etc... found in your repository.

In some projects, there are too many public API pages, and it can confuse end users. End users mainly want the most used top level public API.

The `autodocSettings` in your Yaml configuration file helps you customize which parts of your public API you wish to display, and which you wish to hide.

There are various customization options.

Exclude or Include Files and Directories
-------------------------------------
You can exclude or include specific files or directories from being auto-documented.

Paths are relative to your repository root directory. You can exclude or include multiple files and directories by separating them with a blank space.

**Examples:**

1.  Writing the following in the `"INPUT"` section:

        autodocSettings:
          Public API:
            ...
            INPUT: "src/public src/myproj/myproj.h",
            ...

    will create auto-documentation **only** for the directory `src/public` and the file `src/myproj/myproj.h`
    

2.  Writing the following in the `"EXCLUDE"` section:

        autodocSettings:
          Public API:
            ...
            EXCLUDE: "tests"
            ...

    will result in the auto-documentation disregarding any source code written in the `tests` directory.
    
3.  If both include and exclude conditions exist, both will be met.

        autodocSettings:
          Public API:
            ...
            INPUT": "src/public src/myproj/myproj.h"
            EXCLUDE: "tests"
            ...

Exclude or Include Specific API Pages
-------------------------------------

!!! tip
    The most consistent way to remove a specific API page, is to change the permission in the code to private.
    
You can exclude or include specific public API pages (functions, classes, namespaces, etc...) from being auto-documented.

A public API page is defined by it's **page_path** - a concatenation of **all** the scopes (functions, classes, namespaces, etc...) that led to the page. 

For example: `api/my_class/my_func`.

You can exclude or include multiple api pages by adding them as a yaml list. 

**Examples:**

1.  Writing the following in the excluded_paths section:

        autodocSettings:
          Public API:
            baseUrl: api
            ...
            excludeApi":
            - "api/my_namespace/my_class/my_func"
            - "api/my_namespace/my_other_class"
            ...

    will exclude `my_func` and `my_other_class` (and all it's methods, see note.).

    !!! note
        Any descendant of an excluded page will be deleted as well. Therefore, if your want to remove a certain class and all its methods, you only need to exclude the class page_path.

    !!! tip
        On every public API page, there's a <code><i class="fa fa-trash-o"></i></code> icon that will add it to the excluded list.


2.  Writing the following condition in the included_paths section:

        autodocSettings:
          Public API:
            baseUrl: api
            ...
            includeApi":
            - "api/my_other_namespace"
            ...

    will create documentation **only** of API pages that are inside the scope `my_other_namespace`. Any other API page will be omitted from the public API.
    
    The use case is if your project has hundreds of API classes/functions, but you wish to document only a small subset that is important for the end users.

3.  If both includeApi and excludeApi conditions exist, both will be met.

        autodocSettings:
          Public API:
            baseUrl: api
            ...
            includeApi":
            - "api/my_other_namespace"
            excludeApi":
            - "api/my_other_namespace/my_class/my_func"
            - "api/my_namespace/my_other_class"
            ...
    
    only `my_other_namespace` will be documented, `my_other_namespace/my_class/my_func` inside it will be excluded, and the exclusion `my_namespace/my_other_class` will be ignored since it's not under `my_other_namespace` which is the only included api. 
    

Additional Customization
------------------------

There are additional configuration parameters that will let you customize which parts of your public API you expose to the end user.
 
To name a few, there are:

*   `documentSingleUnderscore` - Regard names that start with a single underscore (_) as 'private', disabling their documentation.

*   `documentStatic` - Document keyword static as part of the Public API.

*   `documentProtected` - Document keyword protected as part of the Public API.

You can view the full list on [autodoc settings](https://doxiz.com/doxiz/master/autodoc-settings).

Default AutodocSettings Per Language
------------------------------------

We've prepared a list of default autodocSettings per lanuage:

- [Default autodocSettings for C++](https://doxiz.com/doxiz/master/autodoc-settings/#default-configurations-for-c_1)

- [Default autodocSettings for C](https://doxiz.com/doxiz/master/autodoc-settings/#default-configurations-for-c)

- [Default autodocSettings for C#](https://doxiz.com/doxiz/master/autodoc-settings/#default-configurations-for-c_2)

- [Default autodocSettings for Python](https://doxiz.com/doxiz/master/autodoc-settings/#default-configurations-for-python)

- [Default autodocSettings for Java](https://doxiz.com/doxiz/master/autodoc-settings/#default-configurations-for-java)


Multiple Language Projects
--------------------------

Some code projects have multiple languages (for example C++ and Python). You can auto-document each language separately.

For example:

```yaml
autodocSettings:
  Public API C++:
    baseUrl: api-cpp
    language: cpp
    INPUT: src/cpp
    EXCLUDE: tests/cpp examples/cpp
    excludeApi:
    - some_cpp_class
    - some_func
    documentSingleUnderscore: true
    documentStatic: true
    documentProtected: true
  Public API Python:
    baseUrl: api-python
    language: python
    INPUT: src/python
    EXCLUDE: "tests/python examples/python setup.py test.py tests.py"
    includeApi: []
    excludeApi:
    - some_python_class
    documentSingleUnderscore: false
    documentStatic: true
    documentProtected: true
```

Grouping
--------

Some projects consist of relatively separated modules. You can auto-document each module separately and display its public API separately.

For example:

```yaml
autodocSettings:
  Public API Module1:
    baseUrl: api-module1
    language: cpp
    INPUT: src/module1
    EXCLUDE: tests/module1
    includeApi: []
    excludeApi:
    - some_cpp_class
    - some_func
    documentSingleUnderscore: true
    documentStatic: true
    documentProtected: true
  Public API Module2:
    baseUrl: api-module2
    language: cpp
    INPUT: src/module2
    EXCLUDE: "tests/python examples/python setup.py test.py tests.py"
    includeApi: []
    excludeApi:
    - some_cpp_class
    - some_func
    documentSingleUnderscore: false
    documentStatic: true
    documentProtected: true
```
