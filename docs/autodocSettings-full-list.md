Auto Documentation Configuration Settings
=========================================

Required Fields
---------------

The following fields are required in every autodoc block:

### title ###

The title as it will appear on the sidebar.

The default value is: "Public API"

### language ###

The programming language for the auto-documentation. 
 
Available values are: c, cpp, csharp, java, python


### baseUrl (optional) ###

The base Url path of every API page in this section. 

Each section should have a different baseUrl to avoid url collision between apis.

By default, it's automatically calculated and equal to the slug of the section title, and if the section title is equal to "Public API", the baseUrl is simply "api" instead of "public-api". 

You can supply a baseUrl to override this default. Sometimes you have to supply an override because slug can produce the same output for different titles because it omits certain characters, for example, slug("C API") is equal to slug("C++ API").

The default value is: `slugify(section title)`  
The default value if `title == "Public API"`: "api"

### Examples ###

1. This is the bare minimum for defining a cpp block:

```yaml
autodocSettings:
  Public API:             # Required "title" for this autodoc block
    language: c           # Required language for this autodoc block
```

2. This is the bare minimum for defining two blocks - one for c and another for c++

```yaml
autodocSettings:
  C API:                  # Required "title" for this autodoc block
    baseUrl: c-api        # Speficially added because slugify(C API) == slugify(C++ API)
    language: c           # Required language for this autodoc block
    
  C++ API:                # Required "title" for this autodoc block
    baseUrl: cpp-api      # Speficially added because slugify(C API) == slugify(C++ API). 
    language: cpp         # Required language for this autodoc block
```


Exclude Include Directories and Files
-------------------------------------

!!! note
    The following keys allows control over which files and directories you wish to auto document.
    
    For more examples, see [here](https://help.docsforge.com/master/customizing-the-public-api/#exclude-or-include-files-and-directories)
    
### INPUT ###

The INPUT tag is used to specify the files and/or directories that you wish to auto-document. 

You may enter file names like `myfile.cpp` or directories like `src/myproject`. Separate the files or directories with spaces.

Note that relative paths are relative to the root of your repository.

If this tag is empty, all the source files in your repository are scanned.

The default value is: ""

### EXCLUDE ###

The EXCLUDE tag can be used to specify files and/or directories that should be excluded from the INPUT source files. This way you can easily exclude a subdirectory from a directory tree whose root is specified with the INPUT tag. 

Note that relative paths are relative to the root of your repository.

The default value is: ""

### EXCLUDE_PATTERNS ###

If the value of the INPUT tag contains directories, you can use the EXCLUDE_PATTERNS tag to specify one or more wildcard patterns to exclude certain files from those directories. 

Note that the wildcards are matched against the file with absolute path, so to exclude all test directories for example use the pattern `*/test/*`

The default value is: ""

### EXAMPLE_PATH ###

The EXAMPLE_PATH tag can be used to specify one or more files or directories that contain example code fragments that are included (see the <a href="http://www.doxygen.nl/manual/commands.html#cmdinclude">\include</a> command).

The default value is: ""

Exclude or Include only Specific API Pages
-------------------

!!! note
    The following keys allow control over which pages to display or omit from the public api.
    
    For example, in C/C++ it's common to document only public APIs that appear in `include/public_file.h`, gather their implementations from the `src` directory, but not to document any additional internal APIs that appear in the `src` directory. 
    
    ```cpp
    INPUT: 'include/public_file.h src'
    includeApi: include/public_file.h
    ```
    
    For more examples, see [here](https://help.docsforge.com/master/customizing-the-public-api/#exclude-or-include-specific-api-pages)

### excludeApi ###

The excludeApi tag is used to exclude a list of APIs from being auto-docmented.

If the list is not empty, the specified apis and their descendents will not be documented.

For example, by writing:

    excludeApi:  
    -  my_namespace/my_class/my_func  
    -  my_namespace/my_other_class

You exclude `my_namespace/my_class/my_func`, `my_namespace/my_other_class` and all their descendants from being documented.

This essentially is a way to treat these objects as private objects without changing the source code.

If this key is empty, no API will be excluded.

The default value is: []

### includeApi ###

The includeApi tag is used to limit the auto-documentation to a specified list of API names or files.

This tag is useful if your source code contains hundreds of classes, but only several of them should be displayed in your public api.

If the list is not empty, **only the specified APIs will be documented**. Any other API will be omitted from being documented.

For example, by writing:

    includeApi:  
    -  file: my_dir/my_file.h  

Only APIs that appear in `my_dir/my_file.h` will be documented.

For example, by writing:

    includeApi:  
    -  api: my_namespace/my_class  
    -  api: my_namespace/my_other_class

Only `my_namespace::my_class`, `my_namespace::my_other_class` and any APIs within their scope will be documented.

You can also mix, for example, by writing:

    includeApi:  
    -  api: my_namespace  
    -  file: my_dir/my_file.h  

Only `my_namespace` (and any APIs within their scope) **OR** APIs that appear in file `my_dir/my_file.h` will be documented. 

You can also define both conditions, for example, by writing: 

    includeApi:  
    -  api: my_namespace  
       file: my_dir/my_file.h  

Only `my_namespace` (and any APIs within their scope) **AND** that is declared in file `my_dir/my_file.h` will be documented. 

Caution: Use lighly if the only condition is `api` such as a specific namespace, as it will filter any defines and scopeless entities such as free functions, typedefs, free enums etc.

If this key is an empty list all apis will be documented.

The default value is: []



Exclude Private Protected Static
--------------------------------

### documentSingleUnderscore ###

Handles names that start with a single underscore (`_`) as `private`, disabling their documentation and appearance in the public API.

If False, objects like `_myfunction`, `_myclass`, etc, will be regarded as private and will not be documented.

This is a common python convention but appears in other languages as well.

The default for python is: true  
The default for other languages: false

### documentStatic ###

Document keyword static as part of the Public API.

If False, objects like `static myfunction()` will be regarded as private, disabling their documentation and appearance in the public API.

The default for C is: false  
The default for other languages: true

### documentProtected ###


Document keyword protected as part of the Public API.

If False, objects with permission level "protected" will not be documented not appear as part of the public API.

The default value is: true


Display defines on separate pages
---------------------------------

### separate_defines ###

Disaply defines on separate pages.

If False, defines don't have a seperate page, and the defines full info (synopsis and full description) appears on the defines table summary.

If True, each define appears on a separate dedicated api page (as done for functions and classes), and only the define's brief description and synopsis appears on the defines summary table.

The default value is: false

Extract Code Comments
------------------------

### extractNonDocComments ###

Extracts all non doc code comments.

If False, only doc comments that start with `///` or `/**` will be extracted.

If True, non doc comments that start with `//` or `/*` will also be extracted.

The default value for C, C++, C#, Java is: false  
For Python this value is not relevant and has no effect.

!!! note
    Doxygen and Javadoc have two different comment types - doc comments and non doc comments (also named implementation comments).  
    Non Doc comments are internal, while Doc comments explain the public API and we want to display them in the extracted documentation.
    
        // Note the difference between /* and /**
        
        /*
         * Here is an implementation code comment that is for internal use and should not be extracted.
         */
         
        /**
         * Here is a doc code comment that explains this object and should be extracted. 
         */     
    
    For additionl info, see http://www.doxygen.nl/manual/docblocks.html
    
!!! tip
    Some projects prefer `extractNonDocComments=false` which gives more control over which comments are extracted and which are not.  
    The downside is changing `//`to `///` for every comment you wish to extract, which can be tedious for some maintainers.  
    
    On the other hand, extracting all comments (`extractNonDocComments=true`) can extract comments that are aimed to be for internal use only.  
    If you prefer `extractNonDocComments=true`, and wish to stop a certain comment from being extracted, turning `//` to `////` will stop it from being extracted.

### extract_namespace_comments ###

Extracts code comments of namespaces (packages and modules in python).

If False, code comments related to namespace will be disregarded.

Useful if namespace code comments don't describe the namespace but something else.

For example, consider the following common mistake:

```cpp
/**
 *
 *  myfile.h
 *  myemail@gmail.com
 *
 *  Copyright 2018, myname.  All rights reserved.
 *  Use of this source code is governed by a MIT license
 *  that can be found in the License file.
 *
 */
 
namespace my_namespace{
    ... Some code

}
```

The programmer intended for `my_namespace` to have no code comment, but since the file comment is the preceding comment for `my_namespace`, it's taken as its comment.

The way to fix it is to add a `/file` doxygen tag (instead of `myfile.h` write `/file myfile.h`). Alternatively, turn the file comment to a non extracted code comment (`//` or `/*`) instead of an extracted code comment (`///` or `/**`).

A dirty fix is to use `extract_namespace_comments` to disregard any comments related to namespace.

The default value is: true

Source File Types
-----------------

### FILE_PATTERNS ###

determines which source file extensions are read.
 
The default is different for every language. See [default configurations per language](#default-configurations-per-language).
    
### EXTENSION_MAPPING ###

determines the language the file extension is read as.

The default is different for every language. See [default configurations per language](#default-configurations-per-language).


PreProcessing
-------------

!!! note
    This section is relevant only for languages c, c++, c#.
    
    The following parameters deal with the c preprocessor that works with doxygen. You can see additional details [here](http://www.doxygen.nl/manual/preprocessing.html).


### ENABLE_PREPROCESSING ###

If the ENABLE_PREPROCESSING tag is set to "YES", doxygen will evaluate all C-preprocessor directives found in the sources and include files.  

The default for C, C++ and C# is: "YES"  
The default for other languages: "NO"

Note: the values true/false can also be used instead of "YES"/"NO".

### MACRO_EXPANSION ###

If the MACRO_EXPANSION tag is set to "YES", doxygen will expand all macro names in the source code. If set to NO only conditional compilation will be performed. Macro expansion can be done in a controlled way by setting EXPAND_ONLY_PREDEF to YES.  

The default value is: "NO"

Note: the values true/false can also be used instead of "YES"/"NO".

### SKIP_FUNCTION_MACROS ###

If the SKIP_FUNCTION_MACROS tag is set to "YES", doxygen's preprocessor will remove all function-like macros that are alone on a line, have an all uppercase name, and do not end with a semicolon. Such function macros are typically used for boiler-plate code, and will confuse the parser if not removed.  

The default value is: "NO"

Note: the values true/false can also be used instead of "YES"/"NO". 

### EXPAND_ONLY_PREDEF ###

If the EXPAND_ONLY_PREDEF and MACRO_EXPANSION tags are both set to "YES" then the macro expansion is limited to the macros specified with the PREDEFINED and EXPAND_AS_DEFINED tags.  

The default value is: "NO"

Note: the values true/false can also be used instead of "YES"/"NO".

### PREDEFINED ###
 
The PREDEFINED tag can be used to specify one or more macro names that are defined before the preprocessor is started (similar to the -D option of gcc). The argument of the tag is a list of macros of the form: name or name=definition (no spaces). If the definition and the "=" are omitted, "=1" is assumed.  

The default value is: ""

### EXPAND_AS_DEFINED ###

If the MACRO_EXPANSION and EXPAND_ONLY_PREDEF tags are set to "YES" then this tag can be used to specify a list of macro names that should be expanded. The macro definition that is found in the sources will be used. Use the PREDEFINED tag if you want to use a different macro definition.  

The default value is: ""   


### SEARCH_INCLUDES ###

If the SEARCH_INCLUDES tag is set to "YES" the includes files in the INCLUDE_PATH (see below) will be searched if a #include is found.  

The default value is: "YES"

Note: the values true/false can also be used instead of "YES"/"NO".

### INCLUDE_PATH ###

The INCLUDE_PATH tag can be used to specify one or more directories that contain include files that are not input files but should be processed by the preprocessor.  

The default value is: ""

### INCLUDE_FILE_PATTERNS ###

You can use the INCLUDE_FILE_PATTERNS tag to specify one or more wildcard patterns (like *.h and *.hpp ) to filter out the header-files in the directories.  

The default value is: "" 
    

Configuration Options
---------------------

### TYPEDEF_HIDES_STRUCT ###

When TYPEDEF_HIDES_STRUCT tag is enabled, a typedef of a struct, union, or enum is documented as struct, union, or enum with the name of the typedef. So typedef struct TypeS {} TypeT, will appear in the documentation as a struct with name TypeT. When disabled the typedef will appear as a member of a file, namespace, or class. And the struct will be named TypeS. This can typically be useful for C code in case the coding convention dictates that all compound types are typedef'ed and only the typedef is referenced, never the tag name.

The default for C and C++ is: "YES"  
The default for other languages: "NO"

Starring API pages
---------------------

Adding a star icon on selected API pages is a helpful visual tip for users that these API are more important than others. 

### star_mentioned ###

When true, any API page mentioned in the tutorial pages will have a star icon on it.

The default is: true

### star_list ###

When list is not empty, any API page on this list will have a star icon on it.

For example, by writing:

    star_list:  
    -  my_namespace/my_class  
    -  my_namespace/my_other_class

These two api pages will be starred.

The default is: []


Sort nested API children
---------------------

APIs hierarchy is displayed according to the scope. 

For example, if your namespace `my_namespace` has multiple types (classes/functions/enums/ etc...) inside its scope - they will be all be displayed below it as its children.

You can configure the order of these children.

The sorting order is: `sort_by_group` >  `sort_by_type` > `sort_alphabetically`.

### sort_by_group ###

`sort_by_group` is not a configurable option, but it's worth explaining it here next to `sort_by_type` and `sort_alphabetically` which are configurable.
 
You can add user defined groups directly in the code. 

For example, by adding `@defgroup` before C1,C2,func1 (and closing with `/** @} */`):

```cpp
/** @defgroup group1 The First Group
 *  This is a detailed description (optional)
 *  @{
 */
 
class C1 {};
class C2 {};
void func1() {}
 
/** @} */
```

You will group C1,C2,func1 into a group called "The First Group". A group can also have an optional detailed description.

If groups are found, they are always sorted first (`sort_by_group` >  `sort_by_type` > `sort_alphabetically`).

The resulting output in a live project can be seen in the following picture:

![grouping](https://raw.githubusercontent.com/erez-o/docsforge/master/images/group_output_example.png)

(*) Notice the output after the user defined the groups 'Events', 'Nodes', etc... 

For more in depth examples, you can read the manual about the grouping mechanism in [doxygen](https://www.doxygen.nl/manual/grouping.html)

### sort_by_type ###

If true, sort nested API children according to types. The sorting order is:

1.  Namespaces (C/C++) or Packages (python)

2.  Modules (Python)

3.  Classes, Structures, Unions, Interfaces

4.  Constructors

5.  Destructors

6.  Other Functions or Properties (python)

7.  Enums

8.  Defines

9.  Typedefs

10. Variables

If true, Enums, Defines, Typedefs and Variables will also be grouped. For example, all enums will be under a group named "Enums". 
The reasoning is that they are usually of lesser importance relative to classes and functions, and it's important not to cloud the user with too much information.

The default is: true

### sort_alphabetically ###

If true, sort nested children alphabetically.

If false, sort according to order of appearance - sorts by declaration filename, then by line number.

The default is: true


Default configurations per language
-----------------------------------

To sum up the above information, we summarize the defaults for each language:

### Default Configurations for C++

In C++ (`["autodocSettings][SectionName]["language"]="cpp"`), the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:                  # Required "title" for this autodoc block
    language: cpp             # Required language for this autodoc block
    
    INPUT: ""                 # paths to source files and directories to auto document, for example, "src include"
    EXCLUDE: ""               # paths to exclude , for example "test tests examples"
    EXCLUDE_PATTERNS: ''      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: true
    documentStatic: true
    documentProtected: true
    extractNonDocComments: true
    star_mentioned: true
    star_list: []
    sort_by_type: true
    sort_alphabetically: true

    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.c *.cc *.cxx *.cpp *.c++ *.ii *.ixx *.ipp *.i++ *.inl *.h *.hh *.hxx *.hpp *.h++ *.mm"
    EXTENSION_MAPPING: "c=c C=c cc=c CC=c cxx=c cpp=c c++=c ii=c ixx=c ipp=c i++=c inl=c h=c H=c hh=c HH=c hxx=c hpp=c h++=c mm=c"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'NO'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'NO'
    TYPEDEF_HIDES_STRUCT: 'YES'
```

### Default Configurations for C

To sum up, In C `["autodocSettings][SectionName]["language"]="c"` , the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:                  # Required "title" for this autodoc block
    language: c               # Required language for this autodoc block
    
    INPUT: ""                 # paths to source files and directories to auto document, for example, "src include"
    EXCLUDE: ""               # paths to exclude , for example "test tests examples"
    EXCLUDE_PATTERNS: ""      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: true
    documentStatic: false
    documentProtected: true
    extractNonDocComments: true
    star_mentioned: true
    star_list: []
    sort_by_type: true
    sort_alphabetically: true
  
    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.c *.cc *.cxx *.cpp *.c++ *.ii *.ixx *.ipp *.i++ *.inl *.h *.hh *.hxx *.hpp *.h++ *.mm"
    EXTENSION_MAPPING: "c=c C=c cc=c CC=c cxx=c cpp=c c++=c ii=c ixx=c ipp=c i++=c inl=c h=c H=c hh=c HH=c hxx=c hpp=c h++=c mm=c"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'NO'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'NO'
    TYPEDEF_HIDES_STRUCT: 'YES'
```

### Default Configurations for C# ###

To sum up, In C# (`["autodocSettings][SectionName]["language"]="csharp"`), the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:                  # Required "title" for this autodoc block
    language: csharp          # Required language for this autodoc block
    
    INPUT: ""                 # paths to source files and directories to auto document
    EXCLUDE: ""               # paths to exclude , for example "test tests examples"
    EXCLUDE_PATTERNS: ""      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: true
    documentStatic: true
    documentProtected: true
    extractNonDocComments: true
    star_mentioned: true
    star_list: []
    sort_by_type: true
    sort_alphabetically: true
  
    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.cs"
    EXTENSION_MAPPING: "cs=csharp"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'NO'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'NO'
```

### Default Configurations for Java

To sum up, In Java (`["autodocSettings][SectionName]["language"]="java"`), the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:                  # Required "title" for this autodoc block
    language: java            # Required language for this autodoc block
    
    INPUT: ""                 # paths to source files and directories to auto document
    EXCLUDE: ""               # paths to exclude , for example "test tests examples"
    EXCLUDE_PATTERNS: ""      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: true
    documentStatic: true
    documentProtected: true
    extractNonDocComments: true
    star_mentioned: true
    star_list: []
    sort_by_type: true
    sort_alphabetically: true
  
    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.java"
    EXTENSION_MAPPING: "java=java"
```

The keys `MACRO_EXPANSION`, `EXPAND_ONLY_PREDEF`, `SEARCH_INCLUDES`, `INCLUDE_PATH`, `INCLUDE_FILE_PATTERNS`, `PREDEFINED`, `EXPAND_AS_DEFINED` and `SKIP_FUNCTION_MACROS` are not relevant for this language. 

### Default Configurations for Python

To sum up, In Python (`["autodocSettings][Section]["language"]="python"`), the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:                  # Required "title" for this autodoc block
    language: python          # Required language for this autodoc block

    INPUT: ""                 # paths to source files and directories to auto document
    EXCLUDE: ""               # paths to exclude , for example "test tests examples setup.py"
    EXCLUDE_PATTERNS: ""      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: false
    documentStatic: true
    documentProtected: true
    star_mentioned: true
    star_list: []
    sort_by_type: true
    sort_alphabetically: true

    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.py *.pyw"
    EXTENSION_MAPPING: "py=python pyw=python"
```

The keys `MACRO_EXPANSION`, `EXPAND_ONLY_PREDEF`, `SEARCH_INCLUDES`, `INCLUDE_PATH`, `INCLUDE_FILE_PATTERNS`, `PREDEFINED`, `EXPAND_AS_DEFINED` and `SKIP_FUNCTION_MACROS` are not relevant for this language. 

Overriding the default configuration
------------------------------------

If you wish to override any of the default values, simply add the `key:diff_value` to your yaml configuration file. 

For example, if your language is C++ and you wish to stop documenting single underscores, add `"documentSingleUnderscore":false` to your autodocSettings.

