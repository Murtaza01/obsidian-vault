The preamble provides the basic configuration and style of your
document.

# documentclass

documentclass is what the document will be, there is many types:

* book
* article
* letter
* report

When picking one, there is a slight change in the style of your document
that will adjust to the corresponding type, it will also inclue additional
commands that you can use. There is another types that are not native to 
latex:

* scrartcl
* scrrprt
* scrbook

These change the fonts and the style a bit.

# maketitle

You can make a title inside your document by using the `\maketitle` which
goes only inside the document, however you need 3 **mandatory** commands:

```
\title{}
\author{}
\date{}
```

If date is not set the current date will be set.
