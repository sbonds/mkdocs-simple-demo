# mkdocs simple demo

This exists to demonstrate aspects of mkdocs, such as bugs, in a way where the whole process is easy to understand and reproduce.

## Demo: nested unordered lists

* This is an unordered list item
* This is another item
  * This should appear indented UNDER "This is another item"
* This is yet another item and should be at the original indent level

### GitHub rendering

Shows the third bullet indented:

![Nested unordered list rendered by GitHub](2019-06-19-13-51-17.png)

### mkdocs rendering

(Using GitHub version as of June 29 2019)

Shows all unordered list items at the same indent level.

![Nested unordered list rendered by mkdocs](2019-06-19-13-52-21.png)

HTML as created:

```html
<h1 id="mkdocs-simple-demo">mkdocs simple demo</h1>
<p>This exists to demonstrate aspects of mkdocs, such as bugs, in a way where the whole process is easy to understand and reproduce.</p>
<h2 id="demo-nested-unordered-lists">Demo: nested unordered lists</h2>
<ul>
<li>This is an unordered list item</li>
<li>This is another item</li>
<li>This should appear indented UNDER "This is another item"</li>
<li>This is yet another item and should be at the original indent level</li>
</ul>
```

### Solution: upstream fix or use custom extension

Lots of good discussion and detail was found in [mkdocs issue 545](https://github.com/mkdocs/mkdocs/issues/545)

#### FIXED via `mdx_truly_sane_lists`

This was added to `mkdocs.yml`:

```YAML
markdown_extensions:
- mdx_truly_sane_lists
```

And an appropriate `pip` command was added to the Travis CI "install" section to load the extension.

That results in this GitHub-compatible behavior:

![Truly Sane Lists extension renders as expected](2019-06-19-14-41-20.png)

## Demo: nested unordered lists with Markdown-spec spacing (4 spaces)

* This is an unordered list item
* This is another item
    * This should appear indented UNDER "This is another item"
* This is yet another item and should be at the original indent level

## Test .NET directory

* [dotNet](./dotNet/index.md)

The .NET directory itself gets excluded due to the defaults for `exclude_docs`: [exclude_docs in 1.6.0 docs](https://github.com/mkdocs/mkdocs/blob/1.6.0/docs/user-guide/configuration.md#exclude_docs)

This was new in 1.5 so I'm not clear how .NET gets skipped in 1.4.1, which is the version I was using when I noticed the problem.

* [.NET](./dotNet/index.md)

Using `[.NET](./dotNet/index.md)` generates this warning:

```text
WARNING -  Doc file 'index.md' contains a link './dotNET/index.md', but the target 'dotNET/index.md' is not found among
           documentation files.
DEBUG   -  Reading: doc file with horrible characters +=%#'~^.md
DEBUG   -  Reading: doc file with spaces.md
DEBUG   -  Reading: dotNet/index.md
```

## Test .NET directory under a different name

Copied the contents of the dotNet directory to a new directory by another name:

* [.NET](./notTheName/index.md)

* [Not .NET](./notDotNet/index.md)

Maybe it's something odd that's Windows-specific since I'm doing all my rendering on Windows currently.
