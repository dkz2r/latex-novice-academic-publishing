---
title: 'Documentation and Finding Help'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- Where can I find help for writing LaTeX documents?
- How do I find out what commands a package provides?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn how to find help for LaTeX documents

::::::::::::::::::::::::::::::::::::::::::::::::

## CTAN (The Comprehensive TeX Archive Network)

A large number of LaTeX packages are available on [CTAN](https://ctan.org/). CTAN contains
packages and related documentation for many widely used LaTeX packages. You can search the archive
for specific strings, or browse by category.

![](fig/15-docum)entation-and-help/ctan-screenshot.PNG){alt='CTAN page for the geometry package.'}
Project pages

Individual package pages often contain links to detailed documentation, including PDF manuals and
example files. Additional you can find links to the package's source code, and information about
the author(s) and ratings from other users.

## Texdoc

[Texdoc](texdoc.org) provides a modern interface for looking up package documentation. Much like
CTAN, you can search for packages and view their documentation.

::: callout

Texdoc is also available as a command line tool, which queries the same database of information,
but allows you to search for packages and documentation from the command line.

:::

## Other Resources

As with any language there are many other resources that you can make use of. The Stack Exchange
for LaTeX is a great place to ask questions and find answers to common problems.

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Find it in the documentation!

We have the geometry package loaded in our document, and we know we want to use to to set the
margins of the document, but we want to set them to 2cm on the left and right, and 4cm on the top
and bottom. We also want to set the per size to A4. Can you find the documentation for the command
and see how to do this?

:::::::::::::::::::::::: solution

Section 5.1 describes how to set the page size, and section 5.4 describes how to set the margins.

```latex
\documentclass[a4paper, left=2cm, right=2cm, top=4cm, bottom=4cm]{geometry}
```

or

```latex
\documentclass{article}

\usepackage[a4paper, left=2cm, right=2cm, top=4cm, bottom=4cm]{geometry}
```

:::::::::::::::::::::::::::::::::


## Challenge 2: Find a specific package.

We have a very particular document we want to create - we are talking about specific positions on
a chess board and we want to render these directly in the document. Can you find a package that
will help us do this? Can you make a simple chess board using this package?

:::::::::::::::::::::::: solution

Searching either CTAN or Texdoc for "chess" will return a number of packages. We'll use the
`chessboard` package for our example. To make a simple chess board, we can use the `chessboard`
command:

```latex
\documentclass{article}

\usepackage{chessboard}

\begin{document}

\chessboard[setpieces={Kd1, Qd8}]

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- CTAN is a large archive of LaTeX packages and documentation
- Texdoc is a website & command line tool for searching LaTeX documentation

::::::::::::::::::::::::::::::::::::::::::::::::

