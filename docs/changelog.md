# Changelog

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
