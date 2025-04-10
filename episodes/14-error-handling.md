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

Way back in [Episode 2 - Document Structure](02-document-structure.html), we saw some error
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

