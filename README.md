# mkdocs-minify-plugin

An MkDocs plugin to minify HTML, JS or CSS files prior to being written to disk.

HTML minification is done using [htmlmin](https://github.com/mankyd/htmlmin).

JS minification is done using [jsmin](https://github.com/tikitu/jsmin/).

CSS minification is done using [csscompressor](https://github.com/sprymix/csscompressor).

## Setup

Install the plugin using pip:

`pip install mkdocs-minify-plugin`

Activate the plugin in `mkdocs.yml`:
```yaml
plugins:
  - search
  - minify:
      minify_html: true
      minify_js: true
      minify_css: true
      htmlmin_opts:
          remove_comments: true
      js_files:
          - my/javascript/dir/file1.js
          - my/javascript/dir/file2.js
      css_files:
          - my/css/dir/file1.css
          - my/css/dir/file2.css
```

> **Note:** If you have no `plugins` entry in your config file yet, you'll likely also want to add the `search` plugin. MkDocs enables it by default if there is no `plugins` entry set, but now you have to enable it explicitly.

## Options

- `minify_html`: Sets whether HTML files should be minified. Defaults to `false`.
- `htmlmin_opts`: Sets runtime htmlmin API options using the [config parameters of htmlmin](https://htmlmin.readthedocs.io/en/latest/reference.html#main-functions)
- `minify_js`: Sets whether JS files should be minified. Defaults to `false`. If set to `true`, you must specificy the JS to be minified files using `js_files` (see below).
- `minify_css`: Sets whether CSS files should be minified. Defaults to `false`. If set to `true`, you must specificy the CSS to be minified files using `css_files` (see below).
- `js_files`: List of JS files to be minified. The plugin will generate minified versions of these files and save them as `.min.js` in the output directory.
- `css_files`: List of CSS files to be minified. The plugin will generate minified versions of these files and save them as `.min.css` in the output directory.

> **Note:** When using `minify_jss` or `minify_css`, you don't have to modify the `extra_javascript` or `extra_css` entries
in your `mkdocs.yml` file. The plugins automatically takes care of that.

More information about plugins in the [MkDocs documentation][mkdocs-plugins].

## See Also

More information about templates [here][mkdocs-template].

More information about blocks [here][mkdocs-block].

[mkdocs-plugins]: https://www.mkdocs.org/user-guide/plugins/
[mkdocs-template]: https://www.mkdocs.org/user-guide/custom-themes/#template-variables
[mkdocs-block]: https://www.mkdocs.org/user-guide/styling-your-docs/#overriding-template-blocks
