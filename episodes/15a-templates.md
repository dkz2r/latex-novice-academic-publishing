---
title: 'Journal Templates'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I adapt my LaTeX document to a specific journal's required format?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Get a journal-specific LaTeX class file (using Biometrika as an example).
- Identify the special commands a journal template provides.
- Migrate content into the template.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

In many scientific fields, LaTeX is the default system for writing and submitting papers to journals. Journals commonly develop their own template to ensure a consistent style across all submitted articles. Templates can look a little overwhelming at first, since the folder usually contains several files. Typically the folder contains a PDF, which serves as an authors guide. A quick read of this PDF goes a long way toward understanding how the template expects your document to be structured.


In this chapter, we will use the Biometrika template as a running example. We will see what is inside a typical template, how it changes commands you already know, and how to migrate a document you have written into that template.

## Workflow

In general, it is advisable to start by exploring the downloaded template folder
and reading the journal's author guide.
Many journals include a PDF inside the folder that is typeset using the template itself.
This guide explains the technical requirements, formatting rules, and which packages are allowed or not allowed.


Never edit the template's core files (`*.cls`, `*.sty`, `*.bst`).
These are maintained by the publisher, and manual changes will likely break compatibility or be overwritten during production.



### Structure of Templates

An example structure of a journal template inside a folder could look like this:

```
journal_template/
├── graphics
│   ├── example.png
│   ├── example1.eps
├── main.tex
├── journal.cls
├── style_file.sty
├── style_file1.sty
├── bib_style_file.bst
├── references.bib
├── other files...
```

- `main.tex`: is the main document where you paste your content.
- `*.cls`: The journal's document class. It defines the layout, fonts, margins, sectioning commands, and journal-specific environments.
- `*.sty`: Additional style packages that extend the class with additional formatting rules, math styles, or author metadata handling.
- `*.bib`: Your bibliography database. Paste your references here using BibTeX or BibLaTeX format.
- `*.bst`: Controls how citations and the reference list are formatted.



::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Migrate your Paper to the Biometrika Template

We provide a basic paper which you can [download](/files/paper.zip) and then use for migrating it into the [Biometrika](/files/Biometrika.zip) template.

::: hint

The Biometrika template uses `BibTeX` instead of `Biber` for the references. You have to change your editor settings (e.g. `Options --> Configure TeXstudio --> Build --> Default Bibliography Tool`) and must use the `BibTeX` citation commands (`\citet{}`, `\citep{}`).

:::

::: hint

You have to remove the comment in front of the `graphics` package to use it. Also make sure that you place your pictures inside the `art` folder.

:::

:::::::::::::::::::::::: solution

The final main `.tex` file can be downloaded [here](/files/biometrika_paper.tex). Please ensure that you place the file in the template folder so that the links to the associated files work correctly.

:::::::::::::::::::::::::::::::::

## Challenge 2: what does the class option `lineno` do?


:::::::::::::::::::::::: solution

The `lineno` class option enables line numbering in the document.
Line numbers are useful during the submission and peer-review process because reviewers can refer to specific lines.

For the camera-ready (final) version of the manuscript, the `lineno` option is typically disabled so that line numbers do not appear in the published document.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- Understanding and working with templates.

::::::::::::::::::::::::::::::::::::::::::::::::

