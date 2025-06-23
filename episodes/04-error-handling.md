---
title: 'Error Handling'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- What do I do when I get an error message?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand how to interpret error messages in LaTeX
- Learn how to fix common errors in LaTeX documents

::::::::::::::::::::::::::::::::::::::::::::::::

## Error Handling

Error messages in LaTeX can often be difficult to understand, especially if you're new to the
language. However there are a few common errors that we can learn to recognize and fix, and a few
techniques we can use to debug our documents based on the error messages we receive.

## Anatomy of an Error Message

In [Episode 2 - Document Structure](02-document-structure.html), we saw some error
messages - let's take a closer look at one of them and see what it tells us.

Let's re-introduce the issue: we'll change the `\documentclass` command in `main.tex` to
`\documnetclass`...

![](/fig/14-error-handling/so-many-errors.PNG){alt='A whole bunch of errors.'}

Ok, that's a lot of errors! Let's look at the very first one in the list:

![](/fig/14-error-handling/error-unidentified-control-sequence.PNG){alt='Error: Unidentified control sequence.'}

In the red bar at the top, we have both the name of the error message ("Unidentified control
sequence") and the file and line number where the error occurred (`main.tex, 2`). This gives us a
great starting point to identify the issue. Now let's look at the contents of the message:

```
The compiler is having trouble understanding a command you have used. Check that the command is
spelled correctly. If the command is part of a package, make sure you have included the package in
your preamble using \usepackage{...}.
```

This is Overleaf's way of trying to make a more helpful version of the error message than LaTeX
itself. We can see the actual error message from LaTeX just below:

```
l.2 \documnetclass
                  {article}
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.
```

Of course, we know what the error was, so we can just fix it by changing `\documnetclass` back to
`\documentclass`.

::: callout

In general, the first error message in the list is the most useful one to look at. The other error
messages are often just a result of the first error cascading down the document, so fixing the first
one will often fix the rest of them too.

:::

## Errors vs Warnings vs Information

Not all messages are equal! LaTeX has three different types of messages:

- `Error`: This is a serious issue that will prevent your document from compiling. You need to fix
  this before you can continue.
- `Warning`: This is a less serious issue that may not prevent your document from compiling, but it
  may cause issues with the output. You should still try to fix this, but it may not be critical.
- `Information`: This is just a message that provides additional information about the document. You
  can usually ignore this.

In Overleaf, error messages are shown in red, warnings are shown in yellow, and information
messages in blue.

## Fixing a Common Error

This time, instead of introducing an error into our document, let's create a new file called
`my-error-example.tex` and add the following code:

```latex
\documentclass{article}

\begin{document}

\section{Introduction}
\label{sec:intro}

Hello there!

This document intentionally contains a very common latex error in the following section. Use the
error message to try to identify and fix the error.

\section{A section with an error}
\label{sec:error}

As mentioned in section \ref{sec:intro}, this document contains an error.

We have a list of items in our store:

\begin{itemize}
  \item Camera
  \item Printer (out of stock)
  \item Cellphone
\end

Our Current Inventory:

\begin{tabular}{|l|l|}
  \hline
  Item & Quantity \\
  \hline
  Camera & 5 \\
  Printer & 0 \\
  Cellphone & 10 \\
  \hline
\end{tabular}

\end{document}
```




## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Identify the error

Take a look at the following LaTeX excerpt:

```latex
\documentclass{article}

\begin{document}

My Amazing Content: $\alpha = \fraction{1}{(1 - \beta)^2}$

\end{document}
```

Attempting to compile this document results in the following error message:

```
! Undefined control sequence.
l.4 $\alpha = \fraction
                       {1}{(1 - \beta)^2}$
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.
```

Without running the code, can you identify the issue?

:::::::::::::::::::::::: solution

The error message indicates that the command `\fraction` is not defined. The correct command
should be `\frac`.

:::::::::::::::::::::::::::::::::


## Challenge 2: Identify the error

Here's another LaTeX excerpt:

```latex
\documentclass{article}

\usepackage{booktab}

\begin{document}

More Amazing Content!

\end{document}
```

The following error message appears when you try to compile this document:

```
! LaTeX Error: File `booktab.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)
```

Why is this error occurring? What is the solution?

:::::::::::::::::::::::: solution

The error message indicates that the package `booktab` is not found. The correct package name
should be `booktabs`

:::::::::::::::::::::::::::::::::

# Challenge 3: Why do I get this warning?

The following code generates a warning message:

```latex
\documentclass{article}

\usepackage{graphicx}
\begin{document}

\section{Adding a rotated image}

We can rotate an image by setting the "angle" parameter:

\includegraphics[scale=2, angle=45]{figures/example-image.png}
\end{document}
```

The text of the warning message is:

```
Overfull \hbox (390.7431pt too wide) in paragraph at lines 10--11
[][]
 []

[1

{/usr/local/texlive/2024/texmf-var/fonts/map/pdftex/updmap/pdftex.map}]
Overfull \vbox (170.7431pt too high) has occurred while \output is active []

[2 <./figures/example-image.png>] (./output.aux)
```

The document compiles successfully, but the warning message won't go away. Why is this
happening? How can you fix it?

:::::::::::::::::::::::: solution

The message is indicating that the image is too wide for the page, which is causing an "overfull
hbox" (overfull horizontal box) error. This is a common issue when including images in LaTeX.
The warning will not prevent the document from compiling, but it may point to something we should
take a look at, in this case, an image that flows off the page.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

