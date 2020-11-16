Source Browser Configuration Settings
=========================================

Source browsing can be enabled by adding the key `source_browser`.

Any files and folders in the `input` field will be recursively included.

Source browsing allows users to browse the source code files with helpful links to the various API documentation pages.

For example:

```yaml
source_browser:
  title: 'Source Browser'                         # section title
  base_url: 'source'                              # base url
  input: 'src include'                            # incldue these directories
  exclude: 'include/private'                      # exclude this directory
  filename_extensions: '.cpp .h'                  # include only these filename extension
  filename_extensions_exclude: '.txt .md'         # exclude these filename extension
```

## source_browser ##

If `source_browser:` does not exist in your configuration file, source browsing will be deactivated.

To activate, `source_browser:` with at least one key (`input`, `title`, etc.) must exist in your configuration file.

## title ##

The section title of the source browser.

The default value is: "Source Browser"

## base_url ##

The base url path of every page in this section. 

Each section should have a different base url to avoid url collision between other pages and sections.

The default value is: "source"


## input ##

The input tag is used to specify the files and/or directories that you wish to add to the source browsing. 

You may enter file names like `myfile.cpp` or directories like `src/myproject`. Separate the files or directories with spaces.

Note that relative paths are relative to the root of your repository.

The order of the files/folders is disregarded. All files and folders will be sorted alphabetically while conserving folders first before files.

If this tag is empty, all the source files in your repository are scanned.

The default value is: ""


## exclude ##

The exclude tag can be used to specify files and/or directories that should be excluded from the input source files.

Note that relative paths are relative to the root of your repository.

If this tag is empty, no files/folders will be excluded.

The default value is: ""


## filename_extensions ##

The filename_extensions tag can be used to include only extensions in this list. 

For example, `filename_extensions: '.cpp .h'` will exclude any files that don't end in either `.cpp` or `.h`.

If this tag is empty, all filename extensions will be included.

The default is different for every code language of the autodoc settings: 


=== "C/C++"
    ```
    FILE_PATTERNS: ".c .cc .cxx .cpp .c++ .ii .ixx .ipp .i++ .inl .h .hh .hxx .hpp .h++ .mm .tpp"
    ```


=== "C#"
    ```
    FILE_PATTERNS: ".cs"
    ```


=== "Python"
    ```
    FILE_PATTERNS: ".py .pyw"
    ```


=== "Java"
    ```
    FILE_PATTERNS: ".java"
    ```

If a project has several autodoc blocks with **different languages**, the default `filename_extensions` will be a union of them.

For example, the default `filename_extensions` of a project that has both C and Python autodoc blocks, will be:

```
FILE_PATTERNS: ".c .cc .cxx .cpp .c++ .ii .ixx .ipp .i++ .inl .h .hh .hxx .hpp .h++ .mm .tpp .py .pyw"
```

## filename_extensions_exclude ##

The filename_extensions_exclude tag can be used to exclude extensions in this list. 

For example, `filename_extensions_exclude: '.md .txt'` will exclude any files that end in either `.md` or `.txt`.

If this tag is empty, all filename extensions will be included.

The default value is: ""