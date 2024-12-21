---
title: 'Document Structure in LaTeX'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- What is the basic structure of a LaTeX document?
- How do I see what my LaTeX document looks like when it's rendered?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Become familiar with the basic structure of a LaTeX document.
- Use Overleaf to render a LaTeX document into a PDF.
- Identify how to add special characters to a LaTeX document.

::::::::::::::::::::::::::::::::::::::::::::::::

## Editing the Document
We can edit the `main.tex` file by clicking on it in the *File Navigator*. This will open the file
in the text editor. Let's edit some of the provided code to create our first LaTeX document.


```latex
\documentclass{article}

\begin{document}
Hello World!

This is my first LaTeX document.
\end{document}
```

::: callout

Errors happen! Check that you have entered each line in the text file exactly as written above.
Sometimes seemingly small input changes give large changes in the result, including causing a
document to not work. If you are stuck, try erasing the document and copying it fresh from the
lines above.

:::

## Looking at our document

Our first document shows us the basics. LaTeX documents are a mixture of text and commands.

- *Commands* start with a backslash `\` and sometimes have arguments in curly braces `{}`.
- *Text* is what you want to appear in the document and requires no special formatting.

Let's look at the commands we've used so far:

- `\documentclass{article}`: This command tells LaTeX what kind of document we are creating. (We
  might also use this command to instruct LaTeX to use a specific font size, paper size, or other
  document settings.)
- `\begin{document}` and `\end{document}`: These commands mark the beginning and end of the
  document body. These commands are required in every LaTeX document and create the document body.

::: callout

You can have multiple \begin{...} and \end{...} pairs in a single LaTeX document, but
you must have exactly as many \begin{...} commands as \end{...} commands.

:::

Everything before the `\begin{document}` command is called the *preamble*. The preamble is where
you set up the document, including the document class, title, author, and any other settings you
want to apply to the entire document.

## Rendering the Document

In your Overleaf project, click the green *Recompile* button to render the document. This will
generate a preview of the document in the right-hand pane.

::: callout

There are many shortcut keyboard commands that you can use to speed up your work in Overleaf. When
we want to render the document, we can use `Ctrl + S` or `Ctrl + Enter` (Windows) or `Cmd + S` or
`Cmd + Enter` (Mac). This will save the document and render it in one step.

:::

## Paragraphs

Note that we have an empty line between our two lines of text. This is important in LaTeX, as this
indicates a new paragraph. Let's try removing the empty line and recompiling the document to see
what happens.

## Special Characters

You've probably noticed by now that the characters `\`, `{`, and `}` are special characters in
LaTeX. There are others though, such as `$`, `%`, `&`, `#` and `^`. These characters tend to be
much less common in text, but you can use them by "excaping" them with a backslash. For example,

- `\%` produces `%`
- `\&` produces `&`
- `\#` produces `#`
- `\^` produces `^`

and so on.












### Let's make this document a bit more interesting
Now we're going to add in some dummy text to get a sense of what a more-complete document would
look like.

We'll do this using the `lipsum` package, which provides sample text blocks from a common
placeholder text.

> ## Lorem Ipsum
>
> Lorem Ipsum is a common piece of placeholder text used in publishing and graphic design. It is
> often used to demonstrate the visual form of a document without relying on meaningful content.
>
> The text itself comes from the first-century BC work *De finibus bonorum et malorum* by Marcus
> Tullius Cicero.
{: .callout}

We'll need to add a new `\usepackage{}` command, with the argument `lipsum`, to the metadata
section. Then we can add the `\lipsum` commands to the document body:


```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{lipsum}

\title{Irish Fairy Tales}
\author{James Stephens}

\begin{document}

\maketitle

\section{Introduction}
\lipsum

\end{document}
```

When we recompile the document, we'll see that the `\lipsum` command has added some dummy text to
the document body below the section heading.

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: What's wrong with this document?

There is an error in the following LaTeX document. Can you find it?

```latex
\documentclass{article}

\title{My First LaTeX Document}

I've created a new LaTeX document.

But there's an issue with it that's preventing it from rendering correctly.

Can you find and fix the error?

\end{document}
```

:::::::::::::::::::::::: solution

## Answer

Each section of a LaTeX document must be enclosed in a pair of `\begin{...}` and `\end{...}`. This
document is missing the `\begin{document}` command.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Displaying Special characters.

How would I display the following text in a LaTeX document?

```
5 is greater than 3 & 2 is less than 4. This is 100% true.
```

:::::::::::::::::::::::: solution

## Answer

We need to use escapes before each of the special characters. The following LaTeX code will display
the text correctly:

```latex
5 is greater than 3 \& 2 is less than 4. This is 100\% true.
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- We can use Overleaf to edit and render LaTeX documents.
- LaTeX documents are a mixture of text and commands.
- Commands start with a backslash `\` and sometimes have arguments in curly braces `{}`.

::::::::::::::::::::::::::::::::::::::::::::::::

::: spoiler

After this episode, here is what our LaTeX document looks like:

```latex
\documentclass{article}

\begin{document}
Hello World!

This is my first LaTeX document.
\end{document}
```

:::
