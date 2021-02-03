# Search Engines #

## Default search engine ##

The default search in project engine is sufficient for most projects.

The default search index includes **only** headings (h1-h6) of your documentation pages and all the APIs of your public API section.

However, it does not support full text search of all the pages inner content.

There are other search providers that provide full text search that might suit your needs better.

## Algolia ##

Algolia provides free search service for open source projects.

As of Feb 2021, the following needs to be done to integrate Algolia:

1) You first need to join at https://docsearch.algolia.com/ and follow the guideline at https://docsearch.algolia.com/docs/dropdown

2) Go to your project settings.

3) Uncheck "Use Default project search".

4) Add the following CSS snippet:

```css
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/docsearch.js@v2.6.3/dist/cdn/docsearch.min.css"
/>
```

5) Add the following JS snippet:

Once your Algolia DocSearch index is ready, set up, and filled with the right data, you can integrate it by adding the following snippet: 

```js
<script src="https://cdn.jsdelivr.net/npm/docsearch.js@v2.6.3/dist/cdn/docsearch.min.js"></script>
<script>
  docsearch({
    // Your apiKey and indexName will be given to you once algolia creates a config for your project
    apiKey: '<API_KEY>',
    indexName: '<INDEX_NAME>',
    inputSelector: '#search-in-project',
    // Set debug to true to inspect the dropdown
    debug: false,
  });
</script>
```

If you're eager to test Algolia DocSearch but don't have any credentials of your own yet, you can try the following test project:

```js
<script src="https://cdn.jsdelivr.net/npm/docsearch.js@v2.6.3/dist/cdn/docsearch.min.js"></script>
<script>
  docsearch({
    apiKey: '25626fae796133dc1e734c6bcaaeac3c',
    indexName: 'docsearch',
    inputSelector: '#search-in-project',
    debug: false,
  });
</script>
```