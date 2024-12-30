---
title: 'Using Document Classes'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- What is a LaTeX Document class?
- How does a document class affect the layout of a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

-

::::::::::::::::::::::::::::::::::::::::::::::::

## What is a Document Class?

A document class sets up the general layout of the document, including (but not limited to):

- design (margins, fonts, spacing, etc)
- availability of chapters
- title page layout

Document classes can also add new commands and environments to the document.

::: callout

Document classes can also set global options that apply to the document as a whole.

These options are set in square brackets after the document class name, for example:

```latex
\documentclass[12pt]{article}
```

:::

## The Base Document Classes

LaTeX comes with a set of standard document classes:

- `article`: a short document without chapters
- `report`: a longer document with chapters, intended for single sided printing
- `book`: a longer document with chapters, intended for double sided printing, as well as other
   features like front and back matter
- `letter`: a short document with no sections
- `slides`: a document for creating slide presentations

### Options for the Article Class

### Writing a Letter

So far we've been using the `article` document class. Let's try using the `letter` document class
to write a letter.

::: callout

We've been working in "main.tex" so far, but we can create as many files in this project as we
want. Let's create a new file called "letter.tex" and write our letter there.

:::

```latex
\documentclass{letter}

\begin{document}

\begin{letter}{Some Address\\Some Street\\Some City}

\opening{Dear Sir or Madam,}

The text goes Here

\closing{Yours,}

\end{letter}

\end{document}
```

::: callout

Note the `\\` used to create line breaks in the address - we'll get back to line breaking in a bit.

:::

## Creating a Presentation

The `slides` document class was developed for making physical slides in the mid-1980s, and so
doesn't have any of the features we might use in modern presentations

## Function-rich Classes

The core classes included with base LaTeX are very stable, but this means they are also somewhat
conservative in terms of features. Over time, third parties have developed a number of more
powerful classes that add new features and functionality to LaTeX documents.

These include:

- `amsbook`, `amsart`, and `amsproc`: classes for documents that use the American Mathematical
  Society's style
- `beamer`: a class for creating slide presentations
- `KOMA-Script`: a set of classes that provide a more modern look and feel to LaTeX documents by
                 providing parallel classes to the base classes
- `memoir`: a class that provides a lot of functionality for creating books, reports, and articles

These classes have lots of customization options that we can explore

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Can you do it?

What is the output of this command?

```r
paste("This", "new", "lesson", "looks", "good")
```

:::::::::::::::::::::::: solution

## Output

```output
[1] "This new lesson looks good"
```

:::::::::::::::::::::::::::::::::


## Challenge 2: how do you nest solutions within challenge blocks?

:::::::::::::::::::::::: solution

You can add a line with at least three colons and a `solution` tag.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

## Figures

You can include figures generated from R Markdown:

```{r pyramid, fig.alt = "pie chart illusion of a pyramid", fig.cap = "Sun arise each and every morning"}
pie(
  c(Sky = 78, "Sunny side of pyramid" = 17, "Shady side of pyramid" = 5),
  init.angle = 315,
  col = c("deepskyblue", "yellow", "yellow3"),
  border = FALSE
)
```
Or you can use pandoc markdown for static figures with the following syntax:

`![optional caption that appears below the figure](figure url){alt='alt text for
accessibility purposes'}`

![You belong in The Carpentries!](https://raw.githubusercontent.com/carpentries/logo/master/Badge_Carpentries.svg){alt='Blue Carpentries hex person logo with no text.'}

## Math

One of our episodes contains $\LaTeX$ equations when describing how to create
dynamic reports with {knitr}, so we now use mathjax to describe this:

`$\alpha = \dfrac{1}{(1 - \beta)^2}$` becomes: $\alpha = \dfrac{1}{(1 - \beta)^2}$

Cool, right?

::::::::::::::::::::::::::::::::::::: keypoints

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

::: spoiler

After this episode, here is what our LaTeX document looks like:

```latex
\documentclass{article}

\begin{document}
Hello World!

This is my first LaTeX document.

\section{Sections}

I can add content to my first section!

\subsection{Subsection}

I can put a subsection inside my first section.

\section{Lists}

There are two types of lists: ordered and unordered

\subsection{Ordered}

\begin{enumerate}
  \item Item 1
  \item Item 2
  \item Item 3
\end{enumerate}

\subsection{Unordered}

\begin{itemize}
  \item Item 1
  \item Item 2
  \item Item 3
\end{itemize}

\end{document}
```

:::
