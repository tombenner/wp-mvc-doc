WP MVC Doc
==========
Documentation for [WP MVC](https://github.com/tombenner/wp-mvc)

Description
-----------

This documentation can be viewed [here](http://wpmvc.org).  It runs on [JDoc](https://github.com/tombenner/jdoc).

Usage
-----

### Local Development

Install [Jekyll](http://jekyllrb.com/), which is required by JDoc.

Clone the repo recursively:

```bash
git clone --recursive git://github.com/tombenner/wp-mvc-doc
```

And run Jekyll to build the site and start serving it:

```bash
jekyll serve
```

You may need to modify the `baseurl` value in `_config.yml`.

### Deployment

[wpmvc.org](http://wpmvc.org) points to the this repo's GitHub Pages instance, so to deploy, you'll want create the static site, update the `gh-pages` branch with it, then push:

First, run Jekyll to create the static site in the `_site` directory:

```bash
jekyll serve
```

Copy the contents of the `_site` directory, check out the `gh-pages` branch, then past the contents of the `_site` directory into the repo's root directory. Commit and push to master.