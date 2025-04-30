---
title: 'Tables'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I add tables to a LaTeX document?
- How can I format a table in a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create a table in a LaTeX document.
- Customize the appearance of a table in a LaTeX document.
- Add horizontal lines to a table in a LaTeX document.

::::::::::::::::::::::::::::::::::::::::::::::::

## Defining Tables

Tables in LaTeX are set using the `tabular` environment. For our purposes here, we are going to
use the `array` package to create a table, which provides additional functionality for creating
tables. We'll add this to the preamble of our document:

```latex
\usepackage{array}
```

::: callout

As we start to add more and more packages to our preamble, it can get a bit unwieldy. For now,
let's just keep them alphabetized to make it keep things organized. Our imports should now look
like this:

```latex
\usepackage{array}
\usepackage[margin=1in]{geometry}
\usepackage{graphicx}
\usepackage{xcolor}
```

:::

In order to create a table, we need to tell latex how many columns we will need and how they should
be aligned.

Available column types are:

| Column Type       | Description   |
|-------------------|---------------|
| `l`               | left-aligned  |
| `c`               | centered      |
| `r`               | right-aligned |
| `p{width}`        | a column with fixed width; the text will be automatically line wrapped and fully justified |
| `m{width}`        | like p, but vertically centered compared to the rest of the row |
| `b{width}`        | like p, but bottom aligned |
| `w{align}{width}` | prints the contents with a fixed width, silently overprinting if things get larger. (You can choose the horizontal alignment using l, c, or r.) |
| `W{align}{width}` | like w, but this will issue an overfull box warning if things get too wide. |

::: callout

The columns l, c and r will have the natural width of the widest entry in the column. Each column
must be declared, so if you want a table with three centered columns, you would use `ccc` as the
column declaration.

:::


There are also a few other preamble-tokens that are available. These don't define a column, but
can be useful as well:

| Token | Description |
| Token     | Description                                                                                          |
|-----------|------------------------------------------------------------------------------------------------------|
| `{num}{string}` | repeats string for num times in the preamble. With this you can define multiple identical columns. |
| `>{decl}` | this will put decl before the contents of every cell in the following column (this is useful, e.g., to set a different font for this column) |
| `<{decl}` | this will put decl after the contents of each cell in the previous column                             |
| `|`       | add a vertical rule                                                                                  |
| `@{decl}` | replace the space between two columns with decl                                                      |
| `!{decl}` | add decl in the center of the existing space                                                         |

## Creating a Table

Now that we have the array package loaded and we know how to define columns, we can create a table
using the `tabular` environment.

```latex
\section{Tables}

\kw{Tables} are defined using the \cmd{tabular} environment.

\begin{tabular}{lll}
  Fruit  & Quantity & Price \\
  Apple  & 5        & 1.50  \\
  Banana & 6        & 2.00  \\
  Orange & 4        & 1.20  \\
\end{tabular}
```

This will create a table with three columns, all left-aligned. The values of each row are separated
by `&` and the rows are separated by `\\`. We do now yet have any horizontal lines in the table, so
it will look like this:

IMAGE HERE

::: callout

Note that the `&` and `\\` characters are aligned in our example. This isn't strictly necessary in
LaTeX, but it makes the code much easier to read.

:::

::: callout

If your table has many columns, it may get cumbersome to write out the column definitions every
time. In this case you can make things easier by using `*{num}{string}` to repeat the string `num`
times. For example, in our table above, we can instead write:

```latex
\begin{tabular}{*{3}{l}}
  Fruit  & Quantity & Price \\
  Apple  & 5        & 1.50  \\
  Banana & 6        & 2.00  \\
  Orange & 4        & 1.20  \\
\end{tabular}
```

:::

### Adding Horizontal Lines

We're going to introduce another package here: `booktabs`. This package provides a few commands
that make it easier to create professional looking tables. To use it, add the following to your
preamble:

```latex
\usepackage{booktabs}
```

`booktabs` provides three commands for creating horizontal lines in your table:

- `\toprule`: creates a line at the top of the table
- `\midrule`: creates a line in the middle of the table
- `\bottomrule`: creates a line at the bottom of the table

Horizontal lines make tables easier to read and understand, and they can be used to separate the
header from the body of the table, and the body from the footer. We can insert these commands into
our table to add horizontal lines:

```latex
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
```

::: callout

A general recommendation is to use lines sparsely in your tables, and vertical lines should be
avoided.

:::

### Partial Horizontal Lines

Another useful feature of `booktabs` is the ability to create partial horizontal lines with the
`\cmidrule` command. This command accepts the arguments {number-number}, where the first number is
the column to start the line and the second number is the column to end the line.

```latex
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

```

### Merging Cells

We can merge cells horizontally using the `\multicolumn` command. This command takes three
arguments:

- The number of cells which should be merged
- The alignment of the merged cell (l, c, or r)
- The contents of the merged cell

```latex
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
```

::: callout

Vertical merging is supported in LaTeX by using the `multirow` package which has the `\multirow` command equipped with it.
It is similarly structured as `\multicolumn` by using three arguments:

- The number of rows which should be merged
- The width of the column (i.e. 4em)
- The contents of the merged rows.

You can find an example in the challenges below.

:::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Can you do it?

Try to make the following table in LaTeX:

| Make | Model | Year |
|------|-------|------|
| Volkswagen | Golf | 84,282 |
| Fiat | 500 | 52,337 |
| Opel | Corsa | 50,191 |
| Mini | Mini | 40,142 |
| Volkswagen | Passat | 39,261 |


:::::::::::::::::::::::: solution

## Answer

```latex
\begin{tabular}{lll}
  \toprule
  Make        & Model & Year  \\
  \midrule
  Volkswagen  & Golf  & 84,282 \\
  Fiat        & 500   & 52,337 \\
  Opel        & Corsa & 50,191 \\
  Mini        & Mini  & 40,142 \\
  Volkswagen  & Passat& 39,261 \\
  \bottomrule
\end{tabular}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::: challenge

## Challenge 3: Merging rows.

Consider the following LaTeX code that creates a table using the command `\multirow`. 
Can you guess how this table will look like? 
How many columns will it have? 
How many rows?
Are any rows or columns combined?


```latex

\documentclass{article}

\usepackage{booktabs}
\usepackage{multirow}

\begin{document}

\begin{tabular}{*{4}{l}}
  \toprule
    & Food & Quantity &  Price  \\
  \midrule
  \multirow{3}{4em}{Fruit} & Apple  & 5  &  1.50   \\
  & Banana & 6        &  2.00   \\
  & Orange & 4        &  1.20   \\
  \midrule
  \multirow{2}{4em}{Cheese} & Brie & 2 & 3.30 \\
   & Asiago   & 3 & 2.90   \\
  \bottomrule
\end{tabular}

\end{document}
```

:::::::::::::::::::::::: solution

The table will have 4 columns where the first column does not have a column name. 
The table will have 6 rows. 
The first row is the column name row. 
Rows 2 to 4 are merged for "Fruit". 
Rows 5 and 6 are merged for "Cheese". 



:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge


## Challenge 4: Adding merged rows to your table.

Consider again the LaTeX code for the table in challenge 3. 
Add four more rows to this table that contain information about the following four sorts of bread: 

- Brioche, 3, 3.00
- Bagel, 2, 3.50
- Matzah, 4, 3.60
- Naan, 2, 3.40

Use `\multirow` to subsume those bread types under the category "Bread".


:::::::::::::::::::::::: solution

```latex
\documentclass{article}

\usepackage{booktabs}
\usepackage{multirow}

\begin{document}

\begin{tabular}{*{4}{l}}
  \toprule
    & Food & Quantity &  Price  \\
  \midrule
  \multirow{3}{4em}{Fruit} & Apple  & 5  &  1.50   \\
  & Banana & 6        &  2.00   \\
  & Orange & 4        &  1.20   \\
  \midrule
  \multirow{2}{4em}{Cheese} & Brie & 2 & 3.30 \\
   & Asiago   & 3 & 2.90   \\
   \midrule
  \multirow{4}{4em}{Bread} & Brioche & 3 & 3.00 \\
  & Bagel & 2 & 3.50 \\
  & Matzah & 4 & 3.60 \\
  & Naan & 2 & 3.40 \\
  \bottomrule
\end{tabular}

\end{document}
```


:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::




::::::::::::::::::::::::::::::::::::: keypoints

- Tables in LaTeX are created using the `tabular` environment.
- The `array` package provides additional functionality for creating tables.
- The `booktabs` package provides commands for creating horizontal lines in tables.
- The `\multicolumn` command can be used to merge cells in a table.
- The `\multirow` command in the `multirow` package can be used to merge rows in a table.

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

\end{document}
```

:::
