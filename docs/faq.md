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

## Add a shield icon

Shield icon links are quite popular in github repositories.

If you want to add a docs shield to your repo:

[![Documentation](https://img.shields.io/badge/docs-docsforge-blue)](http://docsforge.com/<YOUR_PROJECT_NAME>/)

Add the following code snippet:

`[![Documentation](https://img.shields.io/badge/docs-docsforge-blue)](http://docsforge.com/<YOUR_PROJECT_NAME>/)`