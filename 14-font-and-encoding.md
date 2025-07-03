---
title: 'Fonts and Encodings'
teaching: 5
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions

- How do you write a lesson using R Markdown and `{sandpaper}`?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain how to use markdown with the new lesson template
- Demonstrate how to include pieces of code, figures, and nested challenge blocks

::::::::::::::::::::::::::::::::::::::::::::::::

## documentclass Parameters

In an earlier episode we learned that we can change the font size of the entire document by
changing the `\documentclass` command. For example, we can change the font size to 12pt by using:

```latex
\documentclass[12pt]{article}
```

But we can add other parameters to this command to change the overall layout of the document.
For example, we can set the size of the document to A4 paper by using:

```latex
\documentclass[a4paper]{article}
```

We can also change the entire document to a two-column layout by using:

```latex
\documentclass[twocolumn]{article}
```

And we can of course combine these options:

```latex
\documentclass[a4paper,12pt,twocolumn]{article}
```

## Fonts

We saw earlier that we can create commands of our own in LaTeX, but there is also a `renewcommand`
command that let's us change the definition of an existing command. This might be useful if you
want the definition of a command to change throughout the document, however there are also some
commands that are pre-defined that we can modify with this command.

For Example, we can change the font of the entire document by adding the following line to the
`preamble/custom-commands.tex` file:

```latex
% Change the font of the entire document to a monospace font
\renewcommand{\familydefault}{\ttdefault}
```

When you compile the document you should see something like this:

IMAGE GOES HERE

### More Fonts

Unfortunately, the default LaTeX installation does not come with many fonts. However, there are
additional packages that you can include if you are looking for a specific font. Let's try making
our document look like it's using the `Times New Roman` font. To do this, all we need to do is add
the following import to the `preamble/packages.tex` file:

```latex
\usepackage{tgtermes}
```

::: callout

You can find a large selection of fonts at [The LaTeX Font Catalogue](https://www.tug.org/FontCatalogue/),
complete with examples of how to use them in your document.

:::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1:

We saw how to change the font of the entire document using the `\renewcommand` command. But what if
only want a specific section of the document to be in a different font? What would we have to
modify in the following code to make the text in the first `\section{}` command use a different
font?

```latex
\documentclass{article}

\usepackage{tgtermes}
\usepackage{lipsum}

\begin{document}

\texttt{
\section{My Section}
\lipsum[1]
}


\section{My Other Section}
\lipsum[2]

\end{document}
```

:::::::::::::::::::::::: solution

```latex
\documentclass{article}

\usepackage{tgtermes}
\usepackage{lipsum}

\begin{document}

\section{My Section}
\renewcommand{\familydefault}{\ttdefault}
\lipsum[1]

\section{My Other Section}
\renewcommand{\familydefault}{\rmdefault}
\lipsum[2]

\end{document}
```


:::::::::::::::::::::::::::::::::


## Challenge 2:

:::::::::::::::::::::::: solution

:::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

