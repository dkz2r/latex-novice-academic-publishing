---
title: 'Adding Cross References'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How can I ensure that numbers in my document are automatically updated?
- How can I refer to numbered elements in my document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Insert a cross-reference in a LaTeX document.
- Refer to a cross-referenced element in a LaTeX document.

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

We can \kw{refer} to the section with the \cmd{ref} command, like this: \ref{sec:cross-references}.
We can likewise refer to the table like this: \ref{tab:cross-reference-commands}.
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
the benefit is that if the table number changes because we've added or removed sections before it,
the reference will update automatically.

There are packages that can provide more advanced cross-referencing capabilities, such as the
`cleveref` package, which can automatically detect the type of element being referenced and insert
the appropriate name. For more details about this, refer to the references section.

:::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: What's wrong with this code?

Here's a section from a larger document. Why might the references not be working as expected? (This
is a tiny but common issue!)

```latex
\section{Findings}
\label{sec:findings}

\begin{table}[ht]
  \centering
  \begin{tabular}{lll}
    \toprule
    Color & Pre-treatment & Post-treatment \\
    \midrule
    Blue  & 30\% & 35\% \\
    Green & 15\% & 55\% \\
    Red   & 10\% & 12\% \\
    \bottomrule
  \end{tabular}
  \caption{Findings from the survey.}
  \label{tab:findings}
\end{table}

As shown in \ref{tab:findings} post-treatment values are higher...

```

The document compiles without error, but the reference text has an issue. What is it?

:::::::::::::::::::::::: solution

The `\ref{}` command is correctly written, but the `\ref{}` command only returns the number of the
label it is referring to. In this case, it will return the number of the table, not the name of the
table. To fix this, you can write "As shown in Table \ref{tab:findings}..."

:::::::::::::::::::::::::::::::::


## Challenge 2: Where does the reference go?

We mentioned that the `\label{}` command should always come after the numbered element you want to
refer to. What do you think would happen if we put the `\label{}` command before the numbered
element? For example:

```latex
\documentclass{article}

\usepackage{lipsum}

\begin{document}

\section{Introduction}
\label{sec:intro}
\lipsum[1]

\label{sec:methods}
\section{Methodology}
\lipsum[2]

\section{Findings}
As indicated in Section \ref{sec:methods}, \lipsum[3][2]

\end{document}
```

*The `\lipsum` package is a nice way of quickly generating large amounts of placeholder text -
great if you just want to get an idea of how your document will look!*

Before you run the code, think about what will happen. What do you expect the output to be?
Run the code and see if your expectations were correct. Why or why not?

:::::::::::::::::::::::: solution

You might have expected the output to be either "As indicated in Section 2, ..." or "As indicated
in Section ???", but it actually returns "As indicated in Section 1, ...". This is because the
`\label{}` command marks the section number **immediately preceding** it. In this case, the
`\label{}` command is placed before the `\section{Methodology}` command, so it marks the section
number of the previous section, which is the `Introduction` section. The fact that the
`Introduction` section already has a label does not matter.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- The `\label{}` command marks a spot in the document.
- The `\ref{}` command refers to a marked spot in the document.

::::::::::::::::::::::::::::::::::::::::::::::::

::: spoiler

After this episode, here is what our LaTeX document looks like:

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}

\usepackage{array}
\usepackage{booktabs}
\usepackage[margin=1in]{geometry}
\usepackage{graphicx}
\usepackage{xcolor}

% Highlight Keywords using \kw{}
\newcommand{\kw}[1]{\textcolor{blue}{\textbf{#1}}}

% Italics for commands with \cmd{}
\newcommand{\cmd}[1]{\textit{#1}}

% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here
Hello World!

This is my first \kw{LaTeX} document.

% The section command automatically numbers and formats the section heading.
\section{Sections}

I can add content to my first \kw{section}!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a \kw{subsection} inside my first section.

\section{Lists}

There are two types of \kw{lists}: \kw{ordered} and \kw{unordered}.

\subsection{Ordered}

Ordered lists do not have numbers associated with each item.

\begin{enumerate}
  \item Item 1
  \item Item 2
  \item Item 3
\end{enumerate}

\subsection{Unordered}

Unordered lists are just a series of items preceded by a marker.

\begin{itemize}
  \item Item 1
  \item Item 2
  \item Item 3
\end{itemize}

\section{Graphics}

We can include \kw{images} in our document using the \cmd{graphicx} package, which lets us use the
\cmd{includegraphics} command.

\includegraphics{example-image.PNG}

\subsection{Small Image}

We can pass parameters to the \cmd{includegraphics} command to adjust the appearance of the image.

\includegraphics[height=4cm]{example-image.PNG}

\begin{itemize}
  \item width: the width of the image
  \item scale: the scaling factor of the image
  \item angle: the angle of rotation of the image
  \item clip: whether to clip the image to its bounding box
  \item trim: trim the image by a specified amount
  \item draft: display a box instead of the image
\end{itemize}

\subsection{Centered Image}

By placing the \cmd{includegraphics} command inside a center environment, we can center the
image on the page.

\begin{center}
  \includegraphics[height=2cm]{example-image.PNG}
\end{center}

\subsection{Floating Image}

\kw{Floating images} can move around the page as text is added or removed. We can use the
\cmd{figure}environment to create a floating image.

\begin{figure}[ht]
  \centering
  \includegraphics[height=2cm]{example-image.PNG}
\end{figure}

Control the position of a floating image by passing paratmeters to the \cmd{figure} environment:

\begin{itemize}
  \item h: Place the float "here" (where it appears in the code)
  \item t: Place the float at the "top" of the page
  \item b: Place the float at the "bottom" of the page
  \item p: Place the float on a "page" by itself
\end{itemize}

\subsection{Caption}

We can add a \kw{caption} to our floating image by using the \cmd{caption} command inside of the
\cmd{figure} environment.

\begin{figure}[ht]
  \centering
  \includegraphics[height=2cm]{example-image.PNG}
  \caption{This is a caption for our image.}
\end{figure}

\section{Tables}

\kw{Tables} are defined using the \cmd{tabular} environment.

\begin{tabular}{lll}
  Fruit  & Quantity & Price \\
  Apple  & 5        & 1.50  \\
  Banana & 6        & 2.00  \\
  Orange & 4        & 1.20  \\
\end{tabular}

\subsection{Tables with Horizontal Lines}

We can use the \cmd{toprule}, \cmd{midrule}, and \cmd{bottomrule} commands from the \cmd{booktabs}
package to create horizontal lines in our table.

\begin{tabular}{*{3}{l}}
  \toprule
  Fruit  & Quantity & Price \\
  \midrule
  Apple  & 5        & 1.50  \\
  Banana & 6        & 2.00  \\
  Orange & 4        & 1.20  \\
  \bottomrule
\end{tabular}

\subsection{Partial Horizontal Lines}

\begin{tabular}{*{3}{l}}
  \toprule
  Fruit  & Quantity &  Price \\
  \midrule
  Apple  & 5        &  1.50  \\
  Banana & 6        &  2.00  \\
  Orange & 4        &  1.20  \\
  \cmidrule{3-3}
  Total & 15        & 28.20  \\
  \bottomrule
\end{tabular}

\subsection{Merging Cells}

\begin{tabular}{*{3}{l}}
  \toprule
  \multicolumn{3}{c}{Overall Inventory} \\
  Fruit  & Quantity &  Price  \\
  \midrule
  Apple  & 5        &  1.50   \\
  Banana & 6        &  2.00   \\
  Orange & 4        &  1.20   \\
  \midrule
  \multicolumn{2}{c}{Summary} \\
  Total & 15        & 28.20   \\
  \bottomrule
\end{tabular}

\section{Cross References}
\label{sec:cross-references}

\subsection{Material for the Introduction}

In this section, we introduce two new concepts:

\begin{tabular}{cp{9cm}}
  Command & Description \\
  \toprule
  \cmd{label} & Marks a spot in the document \\
  \cmd{ref} & Refers to a marked spot in the document \\
  \bottomrule
\label{tab:cross-reference-commands}
\end{tabular}

We can \kw{refer} to the section with the \cmd{ref} command, like this: \ref{sec:cross-references}.
We can likewise refer to the table like this: \ref{tab:cross-reference-commands}.

\end{document}
```

:::
