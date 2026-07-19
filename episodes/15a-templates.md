---
title: 'Using a Journal Template'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I adapt a LaTeX document to a specific journal's required format?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Get a journal-specific LaTeX class file (using Biometrika as an example).
- Identify the special commands a journal template provides. 
- Migrate content into the template.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

In many scientific fields, LaTeX is the default system for writing and submitting papers to journals. Journals commonly develop their own template to ensure a consistent style across all submitted articles. Templates can look a little overwhelming at first, since the folder usually contains several files. Typically the folder contains a PDF, which serves as an author guide. A quick read of this PDF goes a long way toward understanding how the template expects your document to be structured.


In this chapter, we will use the Biometrika template as a running example. We will see what is inside a typical template, how it changes commands you already know, and how to migrate a document you've written into that template.


## Structure of Templates



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

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Bringing your content into the journal template

:::::::::::::::::::::::: solution

```
\begin{tabular}{rlr}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- The `datatool` package allows us to load and manipulate data in LaTeX documents.


::::::::::::::::::::::::::::::::::::::::::::::::

