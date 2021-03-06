# Frequently Asked Questions

## Broken image links and relative links

DocsForge tries to resolve any relative links or image links found in your markdown files automatically. 
However, there are always edge cases where this automatic process fails.
In such cases you can either file an issue or change the link to an absolute url and the automatic process won't touch it.

### Broken image links

DocsForge doesn't store images locally. The automatic process changes any relative image links to absolute external url.
If it fails, note the following:

- Github advises users to use the following format to create absolute image links:
    
    For example, instead of linking to `filename.png`, use:
    
    `https://raw.githubusercontent.com/user/repository/branch/filename`.
    
    inside a markdown file it would look like:
    
    `![alt text](https://raw.githubusercontent.com/user/repository/branch/filename)`
    
    If the file is inside a wiki repository, it should be accessed in the following way:
    
    `https://raw.githubusercontent.com/wiki/user/repository/filename`


## Your sidebar section Public API has 0 pages

If you get this error message, something is wrong with your configuration file.

Possible reasons:

-   No source files were read.  

    Check that your `INPUT`, `EXCLUDE`, `includeAPI`, `excludeAPI` fields don't result in an empty file list being fed to the autodoc engine.

-   The source files are empty due to `#ifdef`. 

    For example, consider a file `my_file.h` with the following content:

    ```cpp
    #ifdef MY_DEFINE
    #define MY_DEFINE 10
    
    ... lines of code
    
    #endif
    ``` 
    
    If `MY_DEFINE` is not defined in any of the files being fed to the autodoc, all the above lines of code will be skipped.
    
    Solutions:
    
    1.  If possible, change your code so that `ifdef` doesn't wrap any lines of codes.
    
        ```cpp
        #ifdef MY_DEFINE
        #define MY_DEFINE 10
        #endif
        
        ... Lines of code
        
        ```
        
    2.  If `MY_DEFINE` is defined in another file `my_other_file.h` add it to the `INPUT` key (so it can be read in the autodoc stage) and to `excludeAPI` (to exclude it from being documented)
    
        ```yaml
        autodocSettings:
          PublicAPI:
            ...
            INPUT: 'my_file.h my_other_file.h'
            excludeApi: [my_other_file.h]
            ENABLE_PREPROCESSING: 'YES'     #default value for C/C++
            
        ```
        
    3.  Use the `PREDEFINED` key to add the definition of to define `MY_DEFINE` for the autodoc stage.
    
        ```yaml
        autodocSettings:
          PublicAPI:
            ...
            INPUT: 'my_file.h'
            excludeApi: []                  #default value for C/C++
            ENABLE_PREPROCESSING: 'YES'     #default value for C/C++
            PREDEFINED:
            - MY_DEFINE=10
        ```
        
    4.  Disable `ENABLE_PREPROCESSING` to stop doxygen from evaluating any C-preprocessor directives.
    
        ```yaml
        autodocSettings:
          PublicAPI:
            ...
            INPUT: 'my_file.h'
            excludeApi: []                  #default value for C/C++
            ENABLE_PREPROCESSING: 'NO'
            PREDEFINED:''                   #default value for C/C++
        ```


## Add a shield icon

Shield icon links are quite popular in github repositories.

If you want to add a docs shield to your repo:

[![Documentation](https://img.shields.io/badge/docs-docsforge-blue)](http://<YOUR_PROJECT_SUBDOMAIN>.docsforge.com/)

Add the following code snippet:

```
[![Documentation](https://img.shields.io/badge/docs-docsforge-blue)](http://<YOUR_PROJECT_SUBDOMAIN>.docsforge.com/)
```


## Configuration file from repo ##

For each version, the configuration file can either be read from your repository, or read from our database.

Choose whichever is more convenient for you.

When you choose to take the configuration file from your repository, you supply a `raw url` where the file can be reached.

For example, if your project is in github, and your `docsforge.yaml` file is located at the root of the repository, it is accessible at https://raw.githubusercontent.com/user/repository/branch/docsforge.yaml

Taking the file from the raw url is by far the fastest approach, especially if you're building the docs of your older `version 3.5.1` and you want to use the latest configuration file from your `master` branch.

The drawback is that it can take some time for github and other providers to update the raw urls.

!!! note
    When you push a commit to github, it can take some time for github to clear the cache and update the raw urls.
    
    To be on the safe side, you can access the url and check that it has been updated before rebuilding your docs.
   

## Doxygen Preprocessor ##

TODO: Elaborate on this topic. 

Read [doxygen's explanation](https://www.doxygen.nl/manual/preprocessing.html) on how to use the preprocessor.

Read [comment on stackoverflow](https://stackoverflow.com/questions/3435225/c-meta-programming-doxygen-documentation) on real life example. 

### C++ Macros not read correctly ###

### Documenting SFINAE ###