# Changelog

## 3.4.21 (6th Dec 2020)

- Fixed private function overlaods [#37](https://github.com/erez-o/docsforge/issues/37).

- Overload badge changed to lowercase.

- Created infrastructure for LLVM, Incomplete. See [#40](https://github.com/erez-o/docsforge/issues/40) and doxygen issue [#8202](https://github.com/doxygen/doxygen/issues/8202)

- Added `clean-css` for css minification. Improved deployment of minified css and javascript.

- Improved javascript scrollspy.

- Improved "add new project" form.

## 3.4.20 (22nd Nov 2020)

- Fixed download configuration bug [#42](https://github.com/erez-o/docsforge/issues/42) 

- Improved correction of code body starting position.

- Fixed bug where public api was not correctly disaplyed [#41](https://github.com/erez-o/docsforge/issues/41). Issue was related to API objects having the same name in the same scope.

- Added `Overload` badge to overload functions. If multiple different (non empty) brief exists, display each on a separate row. See  [#37](https://github.com/erez-o/docsforge/issues/37)

- Improved `extractNonDocComments` - removed line separators if exist.

- Improved css. 

## 3.4.19 (18th Nov 2020)

- Improved discussions.

- "Mentioned in" is now disabled for namespaces / packages / modules.

- Improved support for anonymous enums. 

## 3.4.18 (16th Nov 2020)

- Fixed source browsing bug - source file names with uppercase were causing broken links. Disabled slugification of source browsing files.

- Improved autolinking - Added dash (`-`).

- Improved css.

- Improved add new project form.

- Added terser for javascript minification. Improved deployment of minified css and javascript.
 
## 3.4.17 (10th Nov 2020)

- Added code source browsing. See [#36](https://github.com/erez-o/docsforge/issues/36)

- Improved `extractNonDocComments` - when true, it disregards the first non-doc multiline comment (`/*`, not `/**`) or multi lines of normal comments (`//`, not `///`).

- Fixed `/pre` and `/post` titles were rendered incorrectly. Need to display `Precondition` and `Postcondition` instead. see [#31](https://github.com/erez-o/docsforge/issues/31)

- Removed colons that were inconsistently added on several special key titles (`Exceptions`, `Parameters`, `Template Parameters`) . See end of [#34](https://github.com/erez-o/docsforge/issues/34#issuecomment-722439919)

- Improved css and javascript. [highlightjs-line-numbers.js](https://github.com/wcoder/highlightjs-line-numbers.js/) was added for source browsing.

## 3.4.16 (1st Nov 2020)

- `css` and `javascript` html snippets can now be added by project maintainers.

- Added css variables to allow easier theming by project maintainers. Dropped support for IE11. See [#26](https://github.com/erez-o/docsforge/issues/26)

- Added `FORCE_LOCAL_INCLUDES` to the `autodocSettings` section in the YAML configuration file. See [#21](https://github.com/erez-o/docsforge/issues/21)

- Added doxygen's `MARKDOWN_SUPPORT` to the `autodocSettings` section in the YAML configuration file. See [#22](https://github.com/erez-o/docsforge/issues/22)

- Improved handling of unicode special charachters, e.g. `em dash`. See [#30](https://github.com/erez-o/docsforge/issues/30)

- Bugfix - code comment with special doxygen command `\par` with a title wasn't parsed correctly. See [#24](https://github.com/erez-o/docsforge/issues/24), [#25](https://github.com/erez-o/docsforge/issues/25)

- Improved collapsing sidebar speed on mobile.

## 3.4.15 (25th Oct 2020)

- Added `scrollspy` javascript implementation to documentation & api pages.

- Improved build behaviour if `separate_defines: true`.

- Various javascript improvements in handling of sidebar tree. Improved back/forward behaviour. 

- Added github stargazers & forks. 

- `font-awsome` updated to 4.7.0. 

- Added css fix for reStructuredText adding `.system-message` errors in created html.

- Added link to cfg used from repo if exists. 

- Removed "download version/package" button from top header. Not helpful - people will prefer cloning or downloading directly from github.

- Enums / Typedefs / Variables inside classes are now also `split_by_file=True`. Same as the public api page.

## 3.4.14 (8th Oct 2020)

- Added an option to read `docsforge.yaml` configuration from the repository if the user chooses it. Until now configuration files had to be managed locally on `docsforge.com` 

- Added `.tpp` as a valid c++ file extension. Default values of `FILE_PATTERNS` and `EXTENSION_MAPPING` now include `.tpp`.

- Added additional words to the list of common words excluded from autolinking (most popular additions: `min`, `max`, `bool`,...)

- Nameless groups are now disregarded.

- Added `DISTRIBUTE_GROUP_DOC` to the `autodocSettings` section in the YAML configuration file.

## 3.4.13 (27th Sep 2020)

- Improve validation tests for yaml configuration files.

- Improved "mentioned in"

- Improved `sort_by_declaration`.

## 3.4.12 (21th Sep 2020)

- Improved "show more"/"Show less".

- Added internal tests. Improved internal logs. General css improvements.

## 3.4.11 (10th Sep 2020)

- Added online markdown editor for discussions.
 
- `markdown_commonmark_gfm: true` is now the default.

- Added Javascript "show more"/"Show less" for table cells that are too high.

- Added configurable `separate_defines` to allow defines to be displayed on a separate page.

- Added configurable `extract_namespace_comments` to optionally disregard code comments relating to namespaces (modules and packages for python).

- General css improvements.

## 3.4.10 (19th Aug 2020)

- Added `markdown_commonmark_gfm` - optional flag to render markdown using github commonmark renderer, thanks to https://github.com/github/cmark-gfm.

- Improved spam filter.

- Improved include/exclude api logic.

- Internal: disabled `FILE_PATTERNS += " *.md *.txt *.rst"`

- Various fixes and css improvements. 


## 3.4.9 (5th Aug 2020)

- Enums are now displayed as separate pages.

- Standardized table rows of defines/typedefs/variables to be the same as function/clases/etc. Needed for allowing sorting different types by order of appearance. 

- Added configurable sorting options : `sort_by_type` and `sort_alphabetically`.

- Added grouping types with a user defined name, read from `@defgroup` and `@name` as a code comment.

- Disabled tweakable `display_enums_on_sidebar`, `display_defines_on_sidebar`, `display_variables_on_sidebar`, `display_typedefs_on_sidebar`. They will all be displayed by default on the sidebar if sort by type.

- Improved js, css.

## 3.4.8 (26th Jul 2020)

- Updated doxygen to latest.

- Major internal change to allow sorting by order of code appearance in the next update.

- Improved discussions spam filter

- Disabled sending emails to collaborators when builds are complete.

- `baseUrl` is optional and not required.

- Several markdown extensions will now be handled by `pymdown-extensions`. Added `markdown_tabs`

- Improved js, css, bug fixes.

## 3.4.7 (12th Jul 2020)

- Added `display_enums_on_sidebar`, `display_defines_on_sidebar`, `display_variables_on_sidebar`, `display_typedefs_on_sidebar`.

- Enums / Defines / Typedefs / Variables are now displayed as groups.

- Added section variables.

- Added single character words to autolink excluded list.

- Added `star_mentioned` and `star_list` to `autodocSettings`.

- Allowed viewing `subdomain.docsforge.com` without redirection.

- Improved logs, js, css, bug fixes.


## 3.4.6 (29th Jun 2020)

- Improved inheritance field.

- Improved syntax for `typedef` and `using`.

- Improved algorithm for suggesting important api section for the first time.

- Discussions can now be turned off by project maintainer.

- Improved css. 

## 3.4.5 (23rd Jun 2020)

- Added support for multiple configuration files per project. This allows different versions to be totally isolated and use alternate configuration files.

- Improved `includeApi`, `excludeApi` - can now filter according to file. Filter also applies to defines/enums/typedefs

- Added optional project browser tab icon.

- Login goes through `www.docsforge.com` and not through `subdomain.docsforge.com`. Fixed google sign in. 

- Improved css on mobile. 

## 3.4.4 (15th Jun 2020)

- Added support for `markdown_fenced_code_tabs`.

- Added theme `clean blue`.

- Added word `meta` to common english words excluded from autolinking.

- Improved spam filter for discussions.

- Several messages in build log are now mute.

- Various bug fixes.

## 3.4.3 (9th Jun 2020)

- Changed `ENABLE_PREPROCESSING` to `YES` by default for C, C++ and C#. 

- Revised and default autodocSettings are printed in a freshly created configuration file.

- Improved css, js, and various bug fixes.


## 3.4.2 (20th May 2020)

- Default autodocSettings are not printed in a freshly created configuration file.

- Various bug fixes.

## 3.4.1 (17th May 2020)

- Changed domain to `www.docsforge.com`

- Various bug fixes.


## 3.4.0 (1st May 2020)

- Seperate subdomian per project. Allows to setup any custom domain like `example.com` by pointing your CNAME. 

- Various bug fixes.

## 3.3.13 (8th Apr 2020)

- Added doxygen warnings to build log.

- Extended sidebar headings (h1-h6).

- Various bug fixes.

## 3.3.12 (19th Mar 2020)

- Multiple fields in yaml configuration file can now be a list of strings. For example, `INPUT`, `PREDEFINED`, etc.

- Trying to automatically search and read `doxyfile.in` when adding a new project.

- Various bug fixes.

## 3.3.11 (4th Mar 2020)

- Added support for `.mediawiki` files using Pandoc.

- Improved title tag, 302 redirects, spam filter, various bug fixes.

## 3.3.10 (20th Feb 2020)

- If multiple api sections, autolinking on each api section uses combined api links from all api sections. Before, autolinking for each api section was done only with api of said section. 

- Improved yaml editing and validations.

- Improved source section.

- Various improvements and fixes. 

## 3.3.9 (13th Feb 2020)

- Improved autolinks.

- Synopsis section is created for classes even if not template.  

## 3.3.8 (9th Feb 2020)

- Various CSS & Javascript improvements

- Added template and virtual keywords when occurs.

- Support for groupings.

- Bugfix - autolinks wrongfully detected folders. 

## 3.3.7 (3rd Feb 2020)

- Various improvements to autolinks.

## 3.3.6 (31st Jan 2020)

- Updated 3rd party packages.

- Improved enum tables css.

- Improved celery maintenance flow.

- Improved "Mentioned in".

- Improved sidebar javascript.

## 3.3.5 (27th Jan 2020)

- Improved sorting of funtcions/classes/namespaces/etc. 

  - First, sort by type : Namespaces/Packages are displayed first, Modules second, Classes/Structures/Unions/Interfaces third, Functions/Properties fourth (constructors/destructors first amongst them). 

  - Second, sort alphabetically, currently not user customizable not to add too many parameters for the users.
  
- Improved autolinks and markdown.

- Improved build speed.

- Fixed rare cases of wrongfully created pages for private apis. 

## 3.3.4 (19th Jan 2020)

- Minor bug fix

## 3.3.3 (19th Jan 2020)

- Enums/Defines/Typedefs/Variables are only read if their scopes are from files/namespaces/packages/modules. They are now searchable.

- Improved autolinks and "mentioned in".

- Improved user experience of sidebar.

- Various fixes

## 3.3.2 (12th Jan 2020)

- Added "Mentioned in" section to api pages. For every api page we look at all the doc pages it was mentioned in, and list them.

- Improved autolinking of api pages to reduce false detection.

- Added support for reading `man` pages (using pandoc)

- `extractNonDocComments` default changed to `false`

- Various fixes

## 3.3.1 (5th Jan 2020)

- Improved 404 pages (added relative search results)

- Added optional per project table of 301 redirects

- Improved build summary sent in emails. 

- Improved emails to admins.

- Improved loggings.

- Bug fix PREDEFINED multiline.

## 3.3.0 (1st Jan 2020)

- Added display of Defines, Typedefs, Enums of files in the public api section. Added search and autolinking of these objects.

- Improved autolinking.

## 3.2.5 (28th Dec 2019)

- Improved display of members (variables, enums, typedefs, events, properties) section. Only public members are displayed. Non public are not part of the common public API and should not be generally used by native users.

## 3.2.4 (23th Dec 2019)

- Improved 404 pages of project pages.

## 3.2.3 (19th Dec 2019)

- Various css and javascript changes.

## 3.2.2 (16th Dec 2019)

- Improved `autolink` of API pages. Made algorithm greedier in `<code>` and `<pre>` tags.

- Added `TYPEDEF_HIDES_STRUCT`, which favors using the typedef name instead of the struct name. Activated by default on C/C++.


## 3.2.1 (14th Dec 2019)

- Added on option for project maintainers to download docs. Helpful for tracking changes offline (changes caused by changing the yaml file or changes in your project repositroy).

- Added a report on API documentation coverage - methods, classes, etc don't have description. Report can be seen inside project build log.

- Various minor bug fixes.

## 3.2.0 (11th Dec 2019)

- Added automatic mapping of relative links and images found in markdown pages. 

    - Solves broken links and the need for manual changes.

    - Mapping is done only for markdown pages that appear in the sidebar section of the yaml configuration file. 
    
    - Also relevant for github wiki pages.

## 3.1.20 (9th Dec 2019)

- Various fixes

## 3.1.19 (8th Dec 2019)

- Added Google Analytics

## 3.1.18 (6th Dec 2019)

- Improved meta description tag for API pages. Non API pages are created without a meta description tag.

## 3.1.17 (1st Dec 2019)

- Removed meta description tag.

## 3.1.16 (26th Nov 2019)

- Improved readability of yaml configuration file.

## 3.1.15 (24th Nov 2019)

- Updated highlight.js to fix yaml support

- Added support for emojis in markdown

## 3.1.14 (13th Nov 2019)

- Improved logging

## 3.1.13 (5th Nov 2019)

- Added periodic creation of docs.

## 3.1.12 (27th Sep 2019)

- Added discussion spam filter.

- Added printing of git commit hash to log file.

## 3.1.11 (14th Aug 2019)

- Bug fixes.

## 3.1.10 (13th Aug 2019)

- Improved member documentation if `extractNonDocComments=true`.

- Improved next / prev page.

- Added a few more license options.

- Changed serveral default keys in cfg (ENABLE_PREPROCESSING, MACRO_EXPANSION, ...)

- Allowing support for non ascii characters in cfg and sidebar.

- Sidebar namespace/classes/functions are more sorted.

## 3.1.9 (5th Aug 2019)

- Source files that are too big (> 1MB) will now appear without syntax highlighting.

## 3.1.8 (4th Aug 2019)

- Added `extractNonDocComments`, an option to extract all code comments even if they do not start with `///` or `/**`

## 3.1.7 (1st Aug 2019)

- Improved linkifying, upgraded Bleach.

- Improved css for plaintext files.

## 3.1.6 (25th Jul 2019)

- Public API pages now have a summary of their childes.

- Dark theme sidebar is now always visible. 

- Improved extra project css.

## 3.1.5 (23rd Jul 2019)

- Important APIs are now created automatically if new project. Done by scanning project markdown pages for references to apis similar to `autolink`.

- Improved css and javascript

- Internal: multi process testing.


## 3.1.4 (14th Jul 2019)

- Improved css (star icons for highlighted apis).

- Highlighted apis are now highlighted inside nested namespace / classes / functions.

## 3.1.3 (11th Jul 2019)

- `additionalSettings` added to yaml file:

    - `autolink` - create autolinks from written markdown pages to api pages.
  
    - `wiki_repo_path` - allows copying and adding pages from project github wiki to sidebar.

- Improved page search - can now search for terms with `::` and `.`, for example, `namespace::class` in C++ or `class.method` in python

- Improved markdown support.

## 3.1.2 (19th Jun 2019)

- Minor css modification.

## 3.1.1 (17th Jun 2019)

- Brief descriptions appended to detailed description start if not too similar.

- Maximum allowed project tags incrased to 10.

## 3.1.0 (16th Jun 2019)

- Project configuration file changed from JSON to YAML to improve editing and readability.

- Docs edited to reflect change.

- Improved displayed build log.

- Updated highlight.js to 9.15.8.

- Internal: Improved update scripts.

## 3.0.13 (6th Jun 2019)

- Fixed javascript sidebar bug on ipad.

- Improved css of themes.

- Changed Public API sections to internal directories

- Internal: Improved testing, added prettify_json for testing, improved update scripts.

## 3.0.12 (31th May 2019)

- Improved performance of sidebar, initial data fetched without ajax.

- Changed sidebar jstree data from HTML to JSON.

- When creating a new project, added to default sidebar pages like `changelog`, `license`, ... if exists in repository. 

## 3.0.11 (27th May 2019)

- Added option to see task position in queue when in PENDING.

## 3.0.0 (13th Apr 2019)

- Initial release
