Customizing The Public Api
=========================

!!! Tip
    You can see the configuration file of any project by clicking the <code><i class="fa fa-wrench"></i></code> icon in the top bar.

When you add a new project, The default is to create pages for **any public** function/class/etc... found in your repository.

In some projects, there are too many public API pages, and it can confuse end users.

The `autodocSettings` in your Json configuration file helps you to customize which parts of your public API you wish to display, and which you wish to hide.

There are various customization options.

Exclude or Include Files and Directories
-------------------------------------
You can exclude or include specific files or directories from being auto-documented.

Paths are relative to your repository root directory. You can exclude or include multiple files and directories by separating them with a blank space.

**Examples:**

1.  Writing the following in the "INPUT" section:
 
        "autodocSettings": [{
            ...
            "INPUT": "src/public src/myproj/myproj.h",
            ...
        }]

    will create auto-documentation **only** for the directory `src/public` and the file `src/myproj/myproj.h`
    

2.  Writing the following in the "EXCLUDE" section:

        "autodocSettings": [{
            ...
            "EXCLUDE": "tests",
            ...
        }]

    will result in the auto-documentation disregarding any source code written in the `tests` directory.
    
3.  If both include and exclude conditions exist, both will be met.

        "autodocSettings": [{
            ...
            "INPUT": "src/public src/myproj/myproj.h",
            "EXCLUDE": "tests",
            ...
        }]

Exclude or Include Specific API Pages
-------------------------------------

!!! tip
    The most consistent way to remove a specific API page, is to change the permission in the code to private.
    
You can exclude or include specific public API pages (functions, classes, namespaces, etc...) from being auto-documented.

A public API page is defined by it's **page_path** - a concatenation of **all** the scopes (functions, classes, namespaces, etc...) that led to the page. 

For example: `my_class/my_func`.

You can exclude or include multiple api pages by seperating between them with a comma. 

**Examples:**

1.  Writing the following in the excluded_paths section:

        "autodocSettings": [{
            ...
            "excludeApi": ["my_namespace/my_class/my_func", "my_namespace/my_other_class"],
            ...
        }]

    will exclude `my_func` and `my_other_class` (and all it's methods, see note.).

    !!! note
        Any descendant of an excluded page will be deleted as well. Therefore, if your want to remove a certain class and all its methods, you only need to exclude the class page_path.

    !!! tip
        On every public API page, there's a <code><i class="fa fa-trash-o"></i></code> icon that will add it to the excluded list.


2.  Writing the following condition in the included_paths section:

        "autodocSettings": [{
            ...
            "includeApi": ["my_other_namespace"],
            ...
        }]

    will create documentation only of API pages that are inside the scope `my_other_namespace`.

3.  If both includeApi and excludeApi conditions exist, both will be met.

        "autodocSettings": [{
            ...
            "includeApi": ["my_other_namespace"],
            "excludeApi": ["my_namespace/my_other_class", "my_other_namespace/my_class/my_func"],
            ...
        }]
    
    only `my_other_namespace` will be documented, `my_class/my_func` inside it will be excluded, and the exclusion `my_namespace/my_other_class` will be ignored since it's not under `my_other_namespace` in the first place. 
    

Additional Customization
------------------------

There are additional configuration parameters that will let you customize which parts of your public API you expose to the end user.
 
To name a few, there are:

*   `documentSingleUnderscore` - Regard names that start with a single underscore (_) as 'private', disabling their documentation.

*   `documentStatic` - Document keyword static as part of the Public API.

*   `documentProtected` - Document keyword protected as part of the Public API.

You can view the full list on [autodoc settings](http://doxiz.com/doxiz/master/autodoc-settings).


Multiple Language Projects
--------------------------

Some code projects have multiple languages (for example C++ and Python). You can auto-document each language separately.

For example:

```json
{
    "autodocSettings": [
        {
            "sectionName": "Public API C++",
            "baseUrl": "api-cpp",
            "language": "cpp",
            "INPUT": "src/cpp",
            "EXCLUDE": "tests/cpp examples/cpp",
            "excludeApi": ["some_cpp_class", "some_func"],
            "documentSingleUnderscore": true,
            "documentStatic": true,
            "documentProtected": true
        },
        {
            "sectionName": "Public API Python",
            "baseUrl": "api-python",
            "language": "python",
            "INPUT": "src/python",
            "EXCLUDE": "tests/python examples/python setup.py test.py tests.py",
            "includeApi": [],
            "excludeApi": ["some_python_class"],
            "documentSingleUnderscore": false,
            "documentStatic": true,
            "documentProtected": true
        } 
    ]
}
```

Grouping
--------

Some projects consist of relatively separated modules. You can auto-document each module separately and display its public API separately.

For example:

```json
{
    "autodocSettings": [
        {
            "sectionName": "Public API Module1",
            "baseUrl": "api-module1",
            "language": "cpp",
            "INPUT": "src/module1",
            "EXCLUDE": "tests/module1",
            "excludeApi": ["some_cpp_class1", "some_func1"],
            "documentSingleUnderscore": true,
            "documentStatic": true,
            "documentProtected": true
        },
        {
            "sectionName": "Public API Module2",
            "baseUrl": "api-module2",
            "language": "cpp",
            "INPUT": "src/module2",
            "EXCLUDE": "tests/module2",
            "excludeApi": ["some_cpp_class2", "some_func2"],
            "documentSingleUnderscore": true,
            "documentStatic": true,
            "documentProtected": true
        }
    ]
}
```
