# Changelog

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
