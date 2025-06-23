---
title: 'Fonts and Spacing'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How can we set paragraph spacing in LaTeX?
- How can we customize text formatting in LaTeX?
- How can we align text in LaTeX?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Add custom spacing between paragraphs in LaTeX.
- Create a title page with custom text formatting.

::::::::::::::::::::::::::::::::::::::::::::::::

## Paragraph Spacing

A common style in LaTeX is to have no indents for paragraphs, but to incorporate a blank line
between them. We can achieve this using the `parskip` package.

We're going to use another package here just to show off some commands without having to write a
lot of text: the `lipsum` package. This package provides the `\lipsum` command, which generates
"Lorem Ipsum" text.

```latex
\usepackage{lipsum}
```

::: callout

Lorem Ipsum is a common piece of placeholder text used in publishing and graphic design. It is
often used to demonstrate the visual form of a document without relying on meaningful content.

The text itself comes from the first-century BC work *De finibus bonorum et malorum* by Marcus
Tullius Cicero.

:::

In our document, we can now use a blank line to separate paragraphs:

```latex
\section{Fonts and Spacing}

% Generate some "Lorem Ipsum" text
% The parameters mean "include paragraphs 1 thru 2" from the "Lorem Ipsum" text
\lipsum[1-2]
```

Compile the document and take a look at our section. You should see that our first paragraph has no
indent, and there is no blank line between it and the following paragraph. The second paragraph
does have an indent. This is the default behavior in LaTeX.

Now let's add our package:

```latex
\usepackage[parfill]{parskip}
```

Keep an eye on the preview pane as you compile the document. You should see that the first
paragraph now has a blank line between it and the second paragraph, and there is no indent on the
first line of the second paragraph.

## Forcing a New Line

Most of the time, you should not force a new line in your document; you almost certainly want to
use a new paragraph or `parskip` instead. However, there are a *few* places where you might want
to force a new line:

- At the end of table rows
- Inside a `center` environment
- In poetry (the `verse` environment)

To force a new line, we can use the `\\` command.

## Adding Explicit Space

We can insert a thin space (about half the normal thickness) use the `\,` command.

::: callout

In math mode, there are also other commands:

- `\.` for a "dot" space
- `\:` for a "colon" space
- `\;` for a "thick" space
- `\!` for a "negative" space
- `\,` for a "thin" space

:::

Very rarely, for example when creating a title page, you might want to add explicit horizontal or
vertical space. We can do this using the `\hspace` and `\vspace` commands:

```latex
\hspace{1cm} % 1cm of horizontal space
\vspace{1cm} % 1cm of vertical space
```

We can also use the `\vfill` command to fill the remaining space on a page. This is useful for
centering content vertically on a page.

## Explicit Text Formatting

We've touched on this in previous episodes, but we can also use the following commands to format
text explicitly:

- `\textbf{}` for bold text
- `\textit{}` for italic text
- `\textrm{}` for roman text
- `\textsf{}` for sans serif text
- `\texttt{}` for typewriter text
- `\textsc{}` for small caps text

We can set the font size in the same way. All sizes are relative to the base font size:

- `\huge` for huge text
- `\large` for large text
- `\normalsize` for normal text
- `\small` for small text
- `\footnotesize` for footnote text

## Text Alignment

We can align text using the following commands:

- `\centering` to center text
- `\raggedright` to left-align text
- `\raggedleft` to right-align text



## Creating a Title Page

Using all of this, let's create a simple title page for our document. We'll put this just after
the `\begin{document}` command, and enclose everything in a `titlepage` environment:

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

::: callout

The `titlepage` environment is a special environment that LaTeX uses to create a title page. It
sets some simple formating rules, like removing multiple columns and resetting the page number.
It also prevents styling rules we add like `centering` from affecting the rest of the document.

:::



:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Create a Title Page with Custom Formatting

Using the content covered, create a title page with custom formatting. Your title page should have:

- A centered title "My Custom LaTeX Title Page" in large, bold text.
- A centered subtitle "A Sample Document with Custom Formatting" in italic text, smaller than the title.
- The date centered at the bottom of the page.

You can use the commands `\vspace` and `\vfill` to make fill blank space between the items and may find the following LaTeX template helpful:

```latex
\documentclass{article}

\begin{document}

\begin{titlepage}
    



\end{titlepage}

\end{document}
```



:::::::::::::::::::::::: solution

## Output

```latex
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

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Adjust Paragraph Spacing in Your Document

Create a LaTeX document with the following:

- Use the `parskip` package to adjust the paragraph spacing.
- Generate some text using the `lipsum` package.
- Ensure that paragraphs are separated by a blank line (without indentation).

:::::::::::::::::::::::: solution

```latex
\documentclass{article}
\usepackage{lipsum}  % To generate sample text
\usepackage[parfill]{parskip}  % Adds space between paragraphs without indentation

\begin{document}

\section{Paragraph Spacing Example}

% Generating Lorem Ipsum text with the lipsum package
\lipsum[1-2]

\end{document}
````

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- Use the `parskip` package to add space between paragraphs
- Force a new line with `\\`
- Add explicit space with `\hspace` and `\vspace`
- Format text explicitly with `\textbf`, `\textit`, etc.
- Align text with `\centering`, `\raggedright`, and `\raggedleft`

::::::::::::::::::::::::::::::::::::::::::::::::

