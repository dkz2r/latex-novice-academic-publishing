---
title: 'Structuring Sources'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How can we make it easier to manage large LaTeX projects?
- How can we reuse parts of our LaTeX document in other documents?
- How can we structure our LaTeX project?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn how to use commands to include other files in your LaTeX document
- Restructure a LaTeX project to use multiple files

::::::::::::::::::::::::::::::::::::::::::::::::

## Project Structure

So far, we've been putting all of our LaTeX code into a single document. This is fine for small
projects, but even with what we have here so far, you might have started to feel like things are
getting a little unwieldy and hard to manage.

One of the great things we can do with LaTeX is break our document up into smaller "sources", which
allows us to work on each part of the document separately. You can imagine this might be helpful
when working on a large document with multiple chapters, where each chapter is a separate file. You
might also find this useful when you intend to reuse parts of your document in other documents,
like title pages, tables of contents, or lists of figures.

This also helps with collaboration, as multiple people can work on different parts of the document
at the same time without having to worry about conflicts.

## Commands

There are two important commands to know when working with multiple sources:

- `\input{filename}`
- `\include{filename}`

The `\input{filename}` command will include the contents of the file `filename.tex` at the point
where the command is called as though it was typed directly into the main document. This can be
useful for things that are not, for example, separate chapters, but rather things like a title
page, a table of contents, or a list of figures.

The `\include{filename}` command will do the same thing, but it will also start a new page before
including the file. This is useful for including separate chapters or sections of your document.
When you use `\include{filename}` you can also use
`\includeonly{filename1,filename2}` in your preamble. This will then only insert
the file mentioned but respect all other files regarding e.g. pagenumber,
references etc.

### Input Example

Let's try out using the `\input{filename}` command. We'll create a new file called
`input_example.tex` in our project directory with the following contents:

```latex
\cmd{Input} is useful for including things as if they were typed directly into the main document.
Things like commands don't have to be defined in the included file, as long as they are defined in
the main document.
```

Then, in our `main.tex` document, let's add the following section:

```latex
\section{Project Structure}

\subsection{Input}

\input{input_example}
```

When we compile our document, we should see the contents of `input_example.tex` included in our
main document.

### Include Example

Let's try out using the `\include{filename}` command. We'll create a new file called
`include_example.tex` in our project directory with the following contents:

```latex
\cmd{Include} is useful for including things as if they were typed directly into the main document,
but it will also start a new page before including the file.
```

Then, in our `main.tex` document, let's add the following section:

```latex
\subsection{Include}

\include{include_example}
```

When we compile our document, we should see the contents of `include_example.tex`, however this
time the content will have included a new page before the content.

::: callout

Another important thing to note about the `\include{filename}` command is that it cannot contain
another `\include{}` command - this will result in an error.

You can, however, use `\input{}` inside an `\include{}` command or an `\input{}` command inside
another `\input{}` command.

:::

## Updating Our Project

Now that we've seen how to use the `\input{filename}` and `\include{filename}` commands, let's
refactor our project to use them. We'll take each section and put it in it's own file, then include
the files in our `main.tex` document. This will main our main document easier to read and manage,
while separating out the content into more manageable pieces.

Let's also organize our files a little bit. Instead of putting everything in the "root" directory
of this project, we'll create a folder called "content" and put our section files in there.

### Separating Our Sections

Let's make files in our "content" directory for each of our sections:

- `content/sections.tex`
- `content/lists.tex`
- `content/graphics.tex`
- `content/tables.tex`
- `content/cross-references.tex`
- `content/mathematics.tex`
- `content/fonts-and-spacing.tex`
- `content/reference-databases.tex`

We'll move the content from each section into the corresponding file.

::: spoiler
`content/sections.tex`

```latex
\section{Sections}

I can add content to my first \kw{section}!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a \kw{subsection} inside my first section.
```
:::

::: spoiler
`content/lists.tex`

```latex
\section{Lists}

There are two types of lists: ordered and unordered.

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

\end{document}
```
:::

::: spoiler
`content/graphics.tex`

```latex
\section{Graphics}

We can include \kw{images} in our document using the \cmd{graphicx} package, which lets us use the
\cmd{includegraphics} command.

\includegraphics{figures/example-image.png}

\subsection{Small Image}

We can pass parameters to the \cmd{includegraphics} command to adjust the appearance of the image.

\includegraphics[height=2cm]{figures/example-image.png}

Other possible options include:

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
  \includegraphics[height=2cm]{figures/example-image.png}
\end{center}

\subsection{Floating Image}

\kw{Floating images} can move around the page as text is added or removed. We can use the
\cmd{figure}environment to create a floating image.

\begin{figure}[ht]
  \centering
  \includegraphics[height=2cm]{figures/example-image.png}
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

\begin{figure}[h]
  \centering
  \includegraphics[height=2cm]{figures/example-image.png}
  \caption{This is a caption for our image.}
\end{figure}
```
:::

::: spoiler
`content/tables.tex`

```latex
\section{Tables}

\kw{Tables} are defined using the \cmd{tabular} environment.

\input{tables/basic-table}

\subsection{Tables with Horizontal Lines}

We can use the \cmd{\textbackslash toprule}, \cmd{\textbackslash midrule}, and
\cmd{\textbackslash bottomrule} commands from the \cmd{booktabs} package to create horizontal
lines in our table.

\input{tables/table-with-horizontal-lines}

\subsection{Partial Horizontal Lines}

The \cmd{\textbackslash cmidrule} command can be used to create partial horizontal lines in a
table. The command accepts the arguments {number-number}, where the first number is the column to
start the line and last number is the column to end the line.

\input{tables/table-with-partial-horizontal-lines}

\subsection{Merging Cells}

Merge cells horizontally using the \cmd{\textbackslash multicolumn} command. This command takes
three arguments:

\begin{itemize}
  \item The number of cells which should be merged
  \item The alignment of the merged cell (l, c, or r)
  \item The contents of the merged cell
\end{itemize}

\input{tables/table-with-merged-cells}
```
:::

::: spoiler
`content/cross-references.tex`

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
:::

::: spoiler
`content/mathematics.tex`

```latex
\section{Mathematics}

There are two kinds of math mode in LaTeX: inline and display. Inline math mode is marked with
a pair of dollar signs, whereas display math mode is marked with a pair of square brackets.

\subsection{Inline Math Mode}

The Pythagorean theorem is $a^2 + b^2 = c^2$.

\subsection{Display Math Mode}

The Fourier Transform is defined as:

\[
\hat{f}(\xi) = \int_{-\infty}^\infty f(x) e^{-2\pi i \xi x} \, dx
\]

Where:
\begin{itemize}
  \item \( f(x) \) is the function we are transforming,
  \item \( \hat{f}(\xi) \) is the Fourier Transform of \( f(x) \),
  \item \( \xi \) is the frequency variable,
  \item \( i \) is the imaginary unit.
\end{itemize}

\subsection{Math in Environments}

The quadratic formula is:

\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\label{eq:quadratic}
\end{equation}

This will allow us to refer to the equation later in the document with \cmd{ref} like this:
Refer to Equation \ref{eq:quadratic}.

\subsection{The `amsmath` Package}

Solve the following recurrence for $ n,k\geq 0 $:
\[
Q_{n,0} = 1   \quad Q_{0,k} = [k=0];
\]

\[
Q_{n,k} = Q_{n-1,k}+Q_{n-1,k-1}+\binom{n}{k}, \quad\text{for $n$, $k>0$.}
\]
```
:::

::: spoiler
`content/fonts-and-spacing.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`content/reference-databases.tex`

```latex
\section{Reference Databases}

One of the best features of LaTeX when writing academic documents is the ability to easily and
confidently \kw{cite references}.

We can cite the article by Thomas (e.g. with `\textbackslash autocite\{Thomas2008\}`) and it will show up in the references.

You should see that the citation appears in the text (`(Thomas et al. 2008)`), and the reference
now appears at the end of the document. \cmd{\textbackslash autocite} is a command that automatically chooses the
citation style for you.

Some additional commands that are available in  `biblatex`:

\begin{itemize}
    \item `\textbackslash cite\{key\}` or `\textbackslash cite\{key1, key2\}`: Cite the reference with the given key
    \item `\textbackslash cites\{key1\}\{key2\}\{key-n\}`: Cite multiple references.
    \item `\textbackslash usepackage\{\}\textbackslash parentcite\{key\}`: Cite the parent reference of the given key.
    \item `\textbackslash autocite\{key\}`: Automatically choose the citation style.
    \item `\textbackslash smartcite\{key\}`: Automatically choose the citation style, but with more control.
    \item `\textbackslash footcite\{key\}`: Cite the reference in a footnote.
\end{itemize}

A plain citation looks like this \cite{Graham1995}, while multiple citations look like this
\cites{Graham1995}[see][p. 42]{Thomas2008}. We already used autocite, but we can also use the
similar smartcite \smartcite{Graham1995}. The benefit with smartcite is that you
can setup that e.g. all references should go into a footnote. You can continue
using smartcite when you are *in* a footnote and it will then detect that there
is no need for creating another footnote but behaving like autocite.
```
:::

Then, in our `main.tex` document, we'll include each of these files using the `\input{filename}`:

```latex
\include{content/sections}
\include{content/lists}
\include{content/graphics}
\include{content/tables}
\include{content/cross-references}
\include{content/mathematics}
\include{content/fonts-and-spacing}
\include{content/reference-databases}
```

::: callout

Note that the `\include{filename}` command does not require the `.tex` extension. LaTeX will assume
that the file is a `.tex` file if no extension is provided.

This is also true for someof the other commands we've seen, such as `\includegraphics{}`. It is
personal preference whether you include the extension or not.

:::

When we compile our document, we should see the same content as before, but now we can make changes
in our content files, and the changes will be reflected in our main document.

### Other Files

While we're at it, let's also create files for our packages, commands, and title page. We'll also
put these into their own directory called "preamble":

- `preamble/packages.tex`
- `preamble/custom-commands.tex`
- `preamble/titlepage.tex`

::: spoiler
`preamble/packages.tex`

```latex
\usepackage{amsmath}
\usepackage{array}
\usepackage[style=authoryear]{biblatex}
\usepackage{booktabs}
\usepackage[margin=1in]{geometry}
\usepackage{graphicx}
\usepackage{lipsum}
\usepackage[parfill]{parskip}
\usepackage{xcolor}
```
:::

::: spoiler
`preamble/custom-commands.tex`

```latex
% Highlight Keywords using the \kw{} command
\newcommand{\kw}[1]{\textcolor{blue}{\textbf{#1}}}
% Italicise LaTeX commands
\newcommand{\cmd}[1]{\textit{#1}}
```
:::

::: spoiler
`preamble/titlepage.tex`

```latex
\begin{titlepage}
    \centering

    \huge
    \textbf{My Example Document}

    \vspace{1cm}
    \normalsize
    \textit{An example of a LaTeX document}

    \vfill
    January 1, 2000
\end{titlepage}
```
:::

### Our New main.tex

Our `main.tex` document should now look like this:

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}

\input{preamble/packages}

\input{preamble/custom-commands}

\addbibresource{sample-references.bib}

% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here

\include{content/titlepage}

Hello World!

This is my first \kw{LaTeX} document.

\include{content/sections}
\include{content/lists}
\include{content/graphics}
\include{content/tables}
\include{content/cross-references}
\include{content/mathematics}
\include{content/fonts-and-spacing}
\include{content/reference-databases}

\printbibliography

\end{document}
```

::: callout

Note that we still need to put the content in the appropriate order. For example, you can't add
`\input{includes/packages}` at the end of the document, as it needs to be included before the
document starts.

:::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Refactor Your Document with Multiple Files

Refactor the following LaTeX document to use multiple files.

```latex
% This is the main document: main.tex

\documentclass{article}


\begin{document}

\begin{titlepage}
    \centering
    \huge
    \textbf{My Custom LaTeX Title Page}

    \vspace{1cm} % Space between title and subtitle
    \normalsize
    \textit{A Sample Document with Custom Formatting}

    \vfill % Fill remaining space
    \large
    January 1, 2025
\end{titlepage}


\section{Tables}

\begin{tabular}{lll}
  Fruit  & Quantity & Price \\
  Apple  & 5        & 1.50  \\
  Banana & 6        & 2.00  \\
  Orange & 4        & 1.20  \\
\end{tabular}

\section{Graphics}

\begin{figure}[ht]
  \centering
  \includegraphics[height=2cm]{example-image.PNG}
  \caption{This is a caption for our image.}
\end{figure}


\end{document}
```

- Separate the content into different files for the sections by `tables.tex` and `graphics.tex`.
- Organize the file for the titlepage in a folder named "includes" and name the file `titlepage.tex`.
- Organize the files for tables and graphics in a folder named "content".
- Use the `\input` command to include the titlepage and the content in your `main.tex` document.


:::::::::::::::::::::::: solution

## Output

```latex
% This is the main document: main.tex

\documentclass{article}


\begin{document}

% Include title page
\input{includes/titlepage}

% Include content from different files in the "content" folder
\input{content/sections}
\input{content/lists}
\input{content/graphics}
\input{content/tables}
\input{content/cross-references}
\input{content/math}
\input{content/text-and-spacing}

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Why did we do this?

In our `content/tables.tex` file, we have a bunch of `\input{}` commands for the tables instead of
writing the tables directly in the file. Why did we do this? What is the benefit of doing this?

:::::::::::::::::::::::: solution

Using an `\input` command inserts the table contents directly into the document as though it was
typed, which means that we can reuse the same table in multiple documents without having to copy
paste it. For example, if we were making a presentation in LaTeX, we could use the same table
in our presentation. This means that if we make a change to the table, it will be reflected in
all of the documents in which we use it.

(This reflects the programming principle of "Don't Repeat Yourself" (DRY)!)

:::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 3: Restructuring a larger document?

Let's make a new project called "structuring-sources". Add the following files to your project:

- `main.tex` (copy the contents from [this file](files/12-structuring-sources/main.tex))
- `references.bib` (copy the contents from [this file](files/12-structuring-sources/references.bib))

How might we use `\input{}` and `\include{}` to break our project up into smaller files?

:::::::::::::::::::::::: solution

## Output

There isn't a specific correct answer for this challenge, but one idea might be something that
looks like this:

```
├── main.tex
├── preamble.tex
├── refereces.bib
├── content/
│   ├── introduction.tex
│   ├── model_architecture.tex
│   ├── model_results.tex
│   └── conclusion.tex
├── tables/
    └── model_results.tex
```

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- LaTeX projects can contain many files that reference each other
- The `\input{filename}` and `\include{filename}` commands allow you to include the contents of other files in your document
- The `\frontmatter`, `\mainmatter`, `\backmatter`, and `\appendix` commands help structure your document

::::::::::::::::::::::::::::::::::::::::::::::::

