---
title: 'tables'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I add tables to a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

-

::::::::::::::::::::::::::::::::::::::::::::::::

## Defining Tables

Tables in LaTeX are set using the `tabular` environment. For our purposes here, we are going to
use the `array` package to create a table, which provides additionl functionality for creating
tables.

```latex
\usepackage{array}
```

In order to create a table, we need to tell latex how may columns we will need and how they should
be aligned.

Available column types are:

| Column Type       | Description   |
|-------------------|---------------|
| `l`               | left-aligned  |
| `c`               | centered      |
| `r`               | right-aligned |
| `p{width}`        | a column with fixed width width; the text will be automatically line wrapped and fully justified |
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

Tables are defined using the `tabular` environment.

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

Vertical merging is not supported in LaTeX. Usually it is sufficient to leave empty rows in the
table to create the impression of vertical merging.

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

Cool, right?****

::::::::::::::::::::::::::::::::::::: keypoints

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

