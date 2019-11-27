Additional Configuration Settings
=========================================

There are several additional settings that can be activated to provide further customization.

To activate them, add `additionalSettings` to your configuration file, as appears in the following example: 

```yaml
additionalSettings:
  autolink: true
  markdown_math: false
  markdown_tasklist: false
  markdown_emoji: false
  wiki_repo_path: false
```

For most projects, the defaults work well, and there's no need to add section `additionalSettings` as the defaults will kick in. There is no need to add a key with a value equal to the default. 

autolink
--------
Scans documentation pages and tries to automatically detect api pages and creates links to them. 

For example, if the method `my_class::my_func` is in your public api, anytime the text `my_class::my_func` is encountered in a documentation page, the text will turn to a link to the `my_class::my_func` page.

The algorithm is not too greedy and favors misdetections to creating false alarms.

default: true


markdown_math
-------------
Markdown extra that enables math symbols and equations. 

Javascript rendering is later done using <a href="https://www.mathjax.org/" rel="nofollow">MathJax</a>. 

default: false


markdown_tasklist
-------------
Enable github markdown style task list

default: false


markdown_emoji
-------------
Enable emojis in markdown. See <a href="https://www.webfx.com/tools/emoji-cheat-sheet/" rel="nofollow">cheat sheet codes</a>.

There's a risk of emojis being recognized too often, for example, the code `std::thread::hardware_concurrency` will turn to `std:🧵:hardware_concurrency`.

As a precaution, even if enabled, emojis will only be searched on markdown files, and not automatically generated api files.

default: false


wiki_repo_path
--------------
Github projects can have a separate wiki repository, located at `https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.wiki.git`. 

Most projects don't have a separate wiki repository, and usually favor creating a `docs` folder in the main repository. By default, the wiki repository will not be cloned.

If you wish to copy wiki pages to your sidebar, you need to enable the key `wiki_repo_path`, with value = subdirectory relative to your root repository. 
We will then clone your wiki repository to the chosen subdirectory. 
The chosen subdirectory must not already exist in your repository.
If you wish to enable wiki pages, it's customary to use `wiki_repo_path: wiki`.

For example:

```yaml
sidebar:
  Basic Tutorial:
  - Getting Started: docs/getting-started.md
  - Customizing The Sidebar: wiki/customizing-the-sidebar.md
  - Customizing The Public Api: wiki/customizing-the-public-api.md
additionalSettings:
  wiki_repo_path: wiki
```

Notice that the pages `Customizing The Sidebar` and `Customizing The Public Api` will be taken from your wiki repository, while `Getting Started` will be taken from your docs directory inside your project repository.

default: false