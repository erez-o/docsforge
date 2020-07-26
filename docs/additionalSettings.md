Additional Configuration Settings
=========================================

There are several additional settings that can be activated to provide further customization.

To activate them, add `additionalSettings` to your configuration file, as appears in the following example: 

```yaml
additionalSettings:
  autolink: true
  autolink_exclude: []
  wiki_repo_path: false
  markdown_math: false
  markdown_tasklist: false
  markdown_emoji: false
  markdown_tabs: false
  markdown_fenced_code_tabs: false
```

For most projects, the defaults work well, and there's no need to add section `additionalSettings` as the defaults will kick in. There is no need to add a key with a value equal to the default. 

autolink
--------
Scans documentation pages and tries to automatically detect api pages and creates links to them. 

For example, if the method `my_class::my_func` is in your public api, anytime the text `my_class::my_func` is encountered in a documentation page, the text will turn to a link to the `my_class::my_func` API page.

Autolinks are created for the following regular expressions:

- `[a-zA-Z0-9_]+((\.|\:\:)[a-zA-Z0-9_]+)+` - Any reference to 2 or more API pages, for example, `my_namespace::my_class::my_func`, `my_class::my_func`, `my_class.my_func`.

- `[a-zA-Z0-9_]+(\()` - Any reference to an API page that ends with `(`, for example a method `load_function(`.

- `[a-zA-Z0-9_]+(\&lt;)` - For C/C++ - any reference to an API page that ends with `<`, for example a method `load_function<`.

Inside `<pre>` or `<code>` tags, the algorithm is greedier:

- `[a-zA-Z0-9_]+` - Any reference to an API pages, for example `my_class`, `my_function`, etc.

To avoid misdetections, any reference that can point to two different API pages is excluded. For example, if two different classes have a method `get`, we won't create a link if we find `get`, `get(`, or `get<`.

default: true


autolink_exclude
----------------
Excludes the following list of words from being autolinked.

The normal autolinking is intentionally quite greedy, but you can override and exclude word list from this process.

The words are cap sensitive, so excluding the word `my_class` won't exclude the word `my_Class`

default: []

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

Markdown Extensions
-------------------

### markdown_fenced_code_tabs

Multiple consecutive fenced code tabs or `<pre>` tags can be turned to tabs.

#### Simple example

    ```cpp
    float res = calc_cpp(50);
    ```
    ```c
    float res = calc_c(50);
    ```

Turns to:

```cpp
float res = calc_cpp(50);
```
```c
float res = calc_c(50);
```

#### Advanced example

    ```cpp
    ecs_entity_t e = ecs_new_cpp(world, 0);
    ```
    ```c
    ecs_entity_t e = ecs_new_c(world, 0);
    ```
    ```
    ecs_entity_t e = ecs_new_java(world, 0);
    ```
    <pre><code class="cpp tab_name">ecs_entity_t e = ecs_new_java(world, 0);</code></pre>
    
Turns to:

```cpp
ecs_entity_t e = ecs_new_cpp(world, 0);
```
```c
ecs_entity_t e = ecs_new_c(world, 0);
```
```
ecs_entity_t e = ecs_new_java(world, 0);
```
<pre><code class="cpp tab_name">
ecs_entity_t e = ecs_new_java(world, 0);
</code></pre>

!!! note
    If the language is not specified, the tab name defaults to `txt`. 
    
    You can control the tab name by using the raw html `<pre><code class="cpp tab_name">`

default: false

### markdown_tabs

A more general syntax for allowing tabs can be created using this extension.

=== "Markdown"
    ```
    === "Tab 1"
        Markdown **content**.

        Multiple paragraphs.

    === "Tab 2"
        More Markdown **content**.

        - list item a
        - list item b
    ```

=== "Output"
    === "Tab 1"
        Markdown **content**.

        Multiple paragraphs.

    === "Tab 2"
        More Markdown **content**.

        - list item a
        - list item b


As a precaution, even if enabled, tabs will only be activated on tutorial markdown files, and not automatically generated api files.

default: false

### markdown_math

Markdown extra that enables math symbols and equations. 

For example:


=== "Markdown"
    ```markdown
    $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$, \(p(x|y) = \frac{p(y|x)p(x)}{p(y)}\).
    ```

=== "Output"
    $p(x|y) = \frac{p(y|x)p(x)}{p(y)}$, \(p(x|y) = \frac{p(y|x)p(x)}{p(y)}\).


Javascript rendering is later done using <a href="https://www.mathjax.org/" rel="nofollow">MathJax</a>. 

default: false


### markdown_tasklist

Enable github markdown style task list

=== "Markdown"
    ```
    Task List

    - [X] item 1
        * [X] item A
        * [ ] item B
            more text
            + [x] item a
            + [ ] item b
            + [x] item c
        * [X] item C
    - [ ] item 2
    - [ ] item 3
    ```


=== "Output"
    Task List

    - [X] item 1
        * [X] item A
        * [ ] item B
            more text
            + [x] item a
            + [ ] item b
            + [x] item c
        * [X] item C
    - [ ] item 2
    - [ ] item 3

default: false


### markdown_emoji

Enable emojis in markdown. 

=== "Markdown"
    ```markdown
    :smile: :heart: :clap: :cake:
    ```

=== "Output"
    :smile: :heart: :clap: :cake:

See <a href="https://www.webfx.com/tools/emoji-cheat-sheet/" rel="nofollow">cheat sheet codes</a>.

There's a risk of emojis being recognized too often, for example, the code `my_namespace::cake::bake()` will turn to my_namespace::cake::bake() if not in a `<pre>` or `<code>` tag.

As a precaution, even if enabled, emojis will only be activated on tutorial markdown files, and not automatically generated api files.

Emoji is activated by default on discussions.

default: false