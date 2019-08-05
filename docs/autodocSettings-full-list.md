Auto Documentation Configuration Settings
=========================================

Required Fields
---------------

The following fields are required in every autodoc block:

### baseUrl ###

The base Url path of every API page in this section. Especially needed if there are multiple public API sections. Each section should have a different baseUrl to avoid url collision between apis.

The default value is: "api"

### language ###

The programming language for the auto-documentation. 
 
Available values are: c, cpp, csharp, java, python

Exclude Include Directories and Files
-------------------------------------

### INPUT ###

Input directories and files.  

The default value is: ""

### EXCLUDE ###

Exclude directories and files.  

The default value is: ""

### EXCLUDE_PATTERNS ###

Exclude directories and files using a pattern.  

The default value is: ""

### EXAMPLE_PATH ###

The example path  

The default value is: ""

Exclude Include API by name
---------------------------

### includeApi ###

A list of API names to include in the auto-documentation. if this list is not empty, any other apis will not be documented.

The default value is: []

### excludeApi ###

A list of API names to exclude from the auto-documentation.  

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


Extract All Code Comments
------------------------

### extractNonDocComments ###

Extracts all non doc code comments.

If False, only doc comments that start with `///` or `/**` will be extracted.
If True, non doc comments that start with `//` or `/*` will also be extracted.

The default value for C, C++, C#, Java is: true  
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
    The down side is changing `//`to `///` for each and every comment, which is tedious for some maintainers.  
    
    We suggest extracting all comments (`extractNonDocComments=true`). It's not too greedy because only comments which are adjacent to objects will be extracted.  
    Whenever a comment was wrongfully extracted, turning `//` to `////` or more slashes will force it not to be extracted.

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

The following parameters deal with the c preprocessor that works with doxygen. You can see additional details [here](https://www.star.bnl.gov/public/comp/sofi/doxygen/config.html#config_prepro).

### ENABLE_PREPROCESSING ###

If the ENABLE_PREPROCESSING tag is set to YES (the default) doxygen will evaluate all C-preprocessor directives found in the sources and include files.  

The default value is: "YES"

### MACRO_EXPANSION ###

If the MACRO_EXPANSION tag is set to YES (the default) doxygen will expand all macro names in the source code. If set to NO only conditional compilation will be performed. Macro expansion can be done in a controlled way by setting EXPAND_ONLY_PREDEF to YES.  

The default value is: "YES"

### EXPAND_ONLY_PREDEF ###

If the EXPAND_ONLY_PREDEF and MACRO_EXPANSION tags are both set to YES then the macro expansion is limited to the macros specified with the PREDEFINED and EXPAND_AS_DEFINED tags.  

The default value is: "NO"

### SEARCH_INCLUDES ###

If the SEARCH_INCLUDES tag is set to YES (the default) the includes files in the INCLUDE_PATH (see below) will be searched if a #include is found.  

The default value is: "YES"

### INCLUDE_PATH ###

The INCLUDE_PATH tag can be used to specify one or more directories that contain include files that are not input files but should be processed by the preprocessor.  

The default value is: ""

### INCLUDE_FILE_PATTERNS ###

You can use the INCLUDE_FILE_PATTERNS tag to specify one or more wildcard patterns (like *.h and *.hpp ) to filter out the header-files in the directories.  

The default value is: ""

### PREDEFINED ###
 
The PREDEFINED tag can be used to specify one or more macro names that are defined before the preprocessor is started (similar to the -D option of gcc). The argument of the tag is a list of macros of the form: name or name=definition (no spaces). If the definition and the "=" are omitted, "=1" is assumed.  

The default value is: ""

### EXPAND_AS_DEFINED ###

If the MACRO_EXPANSION and EXPAND_ONLY_PREDEF tags are set to YES then this tag can be used to specify a list of macro names that should be expanded. The macro definition that is found in the sources will be used. Use the PREDEFINED tag if you want to use a different macro definition.  

The default value is: ""    

### SKIP_FUNCTION_MACROS ###

If the SKIP_FUNCTION_MACROS tag is set to YES (the default) then doxygen's preprocessor will remove all function-like macros that are alone on a line, have an all uppercase name, and do not end with a semicolon. Such function macros are typically used for boiler-plate code, and will confuse the parser if not removed.  

The default value is: "YES"  
    

Default configurations per language
-----------------------------------

To sum up the above information, we summarize the defaults for each language:

### Default Configurations for C++

In C++ (`["autodocSettings][SectionName]["language"]="cpp"`), the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:
    baseUrl: api
    language: cpp
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

    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.c *.cc *.cxx *.cpp *.c++ *.ii *.ixx *.ipp *.i++ *.inl *.h *.hh *.hxx *.hpp *.h++ *.mm"
    EXTENSION_MAPPING: "c=c C=c cc=c CC=c cxx=c cpp=c c++=c ii=c ixx=c ipp=c i++=c inl=c h=c H=c hh=c HH=c hxx=c hpp=c h++=c mm=c"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'YES'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'YES'
```

### Default Configurations for C

To sum up, In C `["autodocSettings][SectionName]["language"]="c"` , the following parameters have the following default values:

```yaml
autodocSettings:
  PublicAPI:
    baseUrl: api
    language: c
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
  
    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.c *.cc *.cxx *.cpp *.c++ *.ii *.ixx *.ipp *.i++ *.inl *.h *.hh *.hxx *.hpp *.h++ *.mm"
    EXTENSION_MAPPING: "c=c C=c cc=c CC=c cxx=c cpp=c c++=c ii=c ixx=c ipp=c i++=c inl=c h=c H=c hh=c HH=c hxx=c hpp=c h++=c mm=c"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'YES'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'YES'
```

### Default Configurations for C# ###

To sum up, In C# (`["autodocSettings][SectionName]["language"]="csharp"`), the following parameters have the following default values:

```yaml
autodocSettings:
  Public API:
    baseUrl: api
    language: csharp
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
  
    # The following parameters are usually good for 99% of projects. 
    # Don't copy them to your configuration file unless you specifically want to edit them. 
    FILE_PATTERNS: "*.cs"
    EXTENSION_MAPPING: "cs=csharp"
    ENABLE_PREPROCESSING: 'YES'
    MACRO_EXPANSION: 'YES'
    EXPAND_ONLY_PREDEF: 'NO'
    SEARCH_INCLUDES: 'YES'
    INCLUDE_PATH: ''
    INCLUDE_FILE_PATTERNS: ''
    PREDEFINED: ''
    EXPAND_AS_DEFINED: ''
    SKIP_FUNCTION_MACROS: 'YES'
```

### Default Configurations for Java

To sum up, In Java (`["autodocSettings][SectionName]["language"]="java"`), the following parameters have the following default values:

```yaml
autodocSettings:
  Public API:
    baseUrl: api
    language: java
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
  Public API:
    baseUrl: api
    language: python
    INPUT: ""                 # paths to source files and directories to auto document
    EXCLUDE: ""               # paths to exclude , for example "test tests examples setup.py"
    EXCLUDE_PATTERNS: ""      # for example, */tests/* */test/*
    EXAMPLE_PATH: ""          # for example, "examples"
    includeApi: []
    excludeApi: []
    documentSingleUnderscore: false
    documentStatic: true
    documentProtected: true

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

