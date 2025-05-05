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

## Updating Our Project

Now that we've seen how to use the `\input{filename}` and `\include{filename}` commands, let's
refactor our project to use them. We'll take each section and put it in it's own file, then include
the files in our `main.tex` document. This will main our main document easier to read and manage,
while separating out the content into more manageable pieces.

Let's also organize our files a little bit. Instead of putting everything in the "root" directory
of this project, we'll create a folder called "content" and put our section files in there.

### Separating Our Sections

Let's make files in our "content" directory for each of our sections:

- `sections.tex`
- `lists.tex`
- `graphics.tex`
- `tables.tex`
- `cross-references.tex`
- `math.tex`
- `text-and-spacing.tex`

We'll move the content from each section into the corresponding file.

::: spoiler
`sections.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`lists.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`graphics.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`tables.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`cross-references.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`math.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`text-and-spacing.tex`

```latex
TO BE ADDED LATER
```
:::

Then, in our `main.tex` document, we'll include each of these files using the `\input{filename}`:

```latex
\input{content/sections}
\input{content/lists}
\input{content/graphics}
\input{content/tables}
\input{content/cross-references}
\input{content/math}
\input{content/text-and-spacing}
```

::: callout

Note that the `\input{filename}` command does not require the `.tex` extension. LaTeX will assume
that the file is a `.tex` file if no extension is provided.

:::

When we compile our document, we should see the same content as before, but now we can make changes
in our content files, and the changes will be reflected in our main document.

### Other Files

While we're at it, let's also create files for our packages, commands, and title page. We'll also
put these into their own directory called "includes":

- `packages.tex`
- `custom-commands.tex`
- `titlepage.tex`

::: spoiler
`packages.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`custom-commands.tex`

```latex
TO BE ADDED LATER
```
:::

::: spoiler
`titlepage.tex`

```latex
TO BE ADDED LATER
```
:::

### Our New main.tex

Our `main.tex` document should now look like this:

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}

\input{includes/packages}

\input{includes/custom-commands}

% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here

\input{includes/titlepage}

Hello World!

This is my first \kw{LaTeX} document.

\input{content/sections}
\input{content/lists}
\input{content/graphics}
\input{content/tables}
\input{content/cross-references}
\input{content/math}
\input{content/text-and-spacing}

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

