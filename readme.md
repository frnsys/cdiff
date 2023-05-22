`cdiff` -> "Content Diff"

This is a simple program that compares the text content of two HTML documents and then shows the diff in `nvim`.

It tries to align lines, even if the order is different, so that a direct line-by-line comparison can be made.

Usage:

```
cdiff /path/to/source-of-truth.html /path/to/version-to-update.html
```
