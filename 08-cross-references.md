---
title: 'Adding Cross References'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- 

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- 

::::::::::::::::::::::::::::::::::::::::::::::::

## Cross References

When writing a document of any length, you'll often want to refer to numbered elements such as 
figures, tables, equations, or sections. LaTeX provides a way to automatically number these elements
and refer to them in your text.

### Label and Ref

To have LaTex remember a specific spot in your document, you have to use the `\label{}` command to 
mark it, and the `\ref{}` command to refer to it. For example:

```latex	
\section{Cross References}
\label{sec:cross-references}

\subsection{Material for the Introduction}

In this section, we introduce two new concepts:

\begin{tabular}{cp{9cm}}
  Command & Description \\
  \toprule
  \kw{label} & Marks a spot in the document \\
  \kw{ref} & Refers to a marked spot in the document \\
  \bottomrule
\label{tab:cross-reference-commands}
\end{tabular}

We can refer to the section with the \kw{ref} command, like this: \ref{sec:cross-references}. We 
can likewise refer to the table like this: \ref{tab:cross-reference-commands}.
```

::: callout

The `sec` and `tab` prefixes in the `\label{}` command are not required, but they help to identify
the type of element being labeled. This is especially useful when you have many labels in your
document.

:::

The label command always refers to the previous numbered entry: a section, a table, a figure, etc.
This means that the `\label{}` command should always come *after* the numbered element you want to
refer to.

::: callout

Note that the `ref` command does not insert the section or table name, but rather the number 
associated with it. We would still write "Refer to Table \ref{tab:cross-reference-commands}", but
the benefit is that if the table number changes, the reference will update automatically.

:::


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

