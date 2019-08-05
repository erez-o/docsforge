# Changelog

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
