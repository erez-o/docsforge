Building Version Documentation
==============================

Documentation for any of your project's versions is created during the build process. 

You can view the build log for each version.

For example, the build log for this project is:

```
[0s] ====== BEGIN ====== BUILDING VERSION DOCS ======
[0s] version_name: master, repo: https://github.com/erez-o/doxiz, initiated by: erez
[0s] Cloning git : git clone --depth 1 --branch master https://github.com/erez-o/doxiz .
[1s] Finished cloning, Response: 0 - OK
[1s] Git clone finished, stage 1/6
[1s] Saving JSON configuration file
[1s] Creating Non API pages, stage 5/6.
[1s] Json configuration file - content is not in markdown format. using syntax highlighting "json". See "section":"More Info", "pageName":"Configuration Schema", "filePath":"Docs/schema.json".
[1s] Your sidebar contains 10 documentation (non API) pages.
[1s] Replaced old docs with new docs.
[1s] ======  END  ====== 

[1s] Build status : SUCCESS
[1s] Build time: 1.927906 seconds

[1s] Cleaning up
```

The build log intentionally is quite verbose, so you can see what's going on under the hood. 

Warnings and Exceptions
-----------------------

Warnings and exceptions are highlighted, to help identify problems that occurred during the build.

Warnings are intended for the project maintainer, as it will help guide you how to fix things.

If your build failed, or if your log reports any exception, please [file an issue on github](https://github.com/erez-o/doxiz/issues) and link to the problematic build log.