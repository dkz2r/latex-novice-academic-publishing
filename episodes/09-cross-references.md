---
title: 'Adding Cross References'
teaching: 10
exercises: 15
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
  \toprule
  Command & Description \\
  \midrule
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

::: caution

When you hit compile, you may notice that the `\ref{}` command does not return the correct
references and instead shows question marks (??). This is because LaTeX needs to compile the
document twice. Once to gather all the labels and references, and a second time to resolve them.
If you see question marks, just compile the document again, and it should work correctly.

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

`cleveref` allows the format of cross-references to be formatted automatically, so that the "type"
of the referenced element (e.g., figure, table, section) is included in the reference text. The
`\cref` command is used to create these references.

:::

::: callout

If you want the references to be clickable in the PDF, you can use the `hyperref` package:

```latex
\usepackage{hyperref}
```

This package automatically makes all references clickable, allowing you to jump to the referenced
element in the PDF document. However be aware that this can sometimes cause issues with other
packages, so it's best to load it last in your preamble.

:::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Add a figure, then reference it.

In your LaTeX document, include the image `example-image.PNG` and cross-reference it in the text.
Make sure the figure has a caption and is labeled and centered properly. Use the
`\includegraphics` command to add the image and wrap it in a `figure` environment.
Then, refer to it in the text using the `\ref` command.

You may find the following LaTeX template helpful.

```latex
\documentclass{article}
\usepackage{graphicx}

\begin{document}

\section{Cross-referencing Figures}



\end{document}
```


:::::::::::::::::::::::: solution

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

```latex
\documentclass{article}
\usepackage{graphicx}


\begin{document}

\section{Cross-referencing Figures}

Here is an example of a figure in the document. We will refer to it later in the text.

\begin{figure}[ht]
  \centering
  \includegraphics[height=4cm]{example-image.PNG}
  \caption{This is an example figure.}
  \label{fig:example-image}
\end{figure}

In the text, we can refer to the figure using its label: Figure \ref{fig:example-image}.

\end{document}
```

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


## Challenge 3: What's wrong with this code?

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

The document compiles without error, but the reference text has an issue. What is it? Why does this
happen?

:::::::::::::::::::::::: solution

The `\ref{}` command is correctly written, but the `\ref{}` command only returns the number of the
label it is referring to. In this case, it will return the number of the table, not the name of the
table. To fix this, you can write "As shown in Table \ref{tab:findings}..."

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- The `\label{}` command marks a spot in the document.
- The `\ref{}` command refers to a marked spot in the document.

::::::::::::::::::::::::::::::::::::::::::::::::

::: spoiler

After this episode, [here is what our LaTeX document looks like](files/document_state/ep-08.tex).

:::
