---
title: 'The Structure of a Document'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How are LaTeX documents structured?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Identify the different kinds of section commands in LaTeX.
- Create a list within a LaTeX document.

::::::::::::::::::::::::::::::::::::::::::::::::

## Sections

In a word processor, you might use headings to organize your document.In LaTeX, we'll use the
section commands:

- `\section{...}`
- `\subsection{...}`

LaTeX will handle all of the numbering, formatting, vertical spacing, fonts, and so on in order to
keep these elements consistent throughout your document. Let's add sections to our document.

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}


% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here
Hello World!

This is my first LaTeX document.

% The section command automatically numbers and formats the section heading.
\section{Sections}

I can add content to my first section!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a subsection inside my first section.

\section{Second Section}

And this text will go into another section.

\end{document}
```

You should have something that looks like this:

![](fig/03-logical-structure/sections.PNG){alt='Our document with sections added.'}

::: callout

There are many different section commands in LaTeX, including `\subsubsection{...}`,
`\paragraph{...}`, `\chapter{...}`, and more. Each of these commands will create a new section
heading with a different level of indentation and numbering.

Some of these commands are only available in certain document classes, so be sure to check the
documentation for the class you are using.

:::

## Lists

In LaTeX, as in markdown, there are two types of lists: ordered and unordered. They are both
defined with `\begin{...}` and `\end{...}` commands, as we saw with the document body. Let's add
an ordered list to our document.

We'll replace our "Second Section" with on for "Lists" and add an ordered list:

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}


% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here
Hello World!

This is my first LaTeX document.

% The section command automatically numbers and formats the section heading.
\section{Sections}

I can add content to my first section!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a subsection inside my first section.

\section{Lists}

There are two types of lists: ordered and unordered.

\subsection{Ordered}

Ordered lists have a number or letter associated with each item.

\begin{enumerate}
  \item Item 1
  \item Item 2
  \item Item 3
\end{enumerate}

\end{document}
```

When you compile this document, you should see something like this in the preview pane:

![](fig/03-logical-structure/enumerated-list.PNG){alt='Our document with an enumerated list.'}

::: callout

Note that the `\item` commands do not need to be enclosed in braces. These commands do not take
any arguments, so they can be used as standalone commands. The text that follows the `\item`
command will be treated as the content of the list item.

:::

Adding an unordered list is just as easy. We can use the exact same syntax, but replace the
`enumerate` environment with `itemize`.

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}


% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here
Hello World!

This is my first LaTeX document.

% The section command automatically numbers and formats the section heading.
\section{Sections}

I can add content to my first section!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a subsection inside my first section.

\section{Lists}

There are two types of lists: ordered and unordered.

\subsection{Ordered}

Ordered lists do not have numbers or letters associated with each item.

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

![](fig/03-logical-structure/itemized-list.PNG){alt='Our document with an unordered list.'}

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: What needs to change?

We have the following in our LaTeX document:

```latex
\documentclass{article}

\begin{document}

\begin{enumerate}
  \item Banana Bread
  \item Carrot Muffins
  \item Apple Cake
\end{enumerate}

\end{document}
```

How would we modify this to change this ordered list to an unordered list?

:::::::::::::::::::::::: solution

## Answer

You would need to change the `enumerate` environment to `itemize`:

```latex
\documentclass{article}

\begin{document}

\begin{itemize}
  \item Banana Bread
  \item Carrot Muffins
  \item Apple Cake
\end{itemize}

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Can you do it?

We would like to have the following appear in our LaTeX document:

- Apples
  1. Gala
  2. Fuji
  3. Granny Smith
- Bananas
- Oranges

How would you write this in LaTeX?

:::::::::::::::::::::::: solution

## Answer

```latex
\documentclass{article}

\begin{document}

\begin{itemize}
  \item Apples
  \begin{enumerate}
    \item Gala
    \item Fuji
    \item Granny Smith
  \end{enumerate}
  \item Bananas
  \item Oranges
\end{itemize}

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- LaTeX documents are structured using section commands.
- There are many different section commands in LaTeX, including `\subsubsection{...}`, `\paragraph{...}`, `\chapter{...}`, and more.
- Lists in LaTeX are created using the `enumerate` and `itemize` environments.

::::::::::::::::::::::::::::::::::::::::::::::::


::: spoiler

After this episode, here is what our LaTeX document looks like:

```latex
% This command tells LaTeX what kind of document we are creating (article).
\documentclass{article}


% Everything before the \begin{document} command is called the preamble.
\begin{document} % The document body starts here
Hello World!

This is my first LaTeX document.

% The section command automatically numbers and formats the section heading.
\section{Sections}

I can add content to my first section!

% The subsection command does the same thing, but for sections within sections.
\subsection{Subsection}

I can put a subsection inside my first section.

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
