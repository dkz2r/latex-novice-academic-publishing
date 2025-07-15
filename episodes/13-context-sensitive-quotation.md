---
title: 'Context Sensitive Quotations'
teaching: 25
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions
- How can I semantically markup quotes?
- What is the benefit of referencing the source of the quote to my references list?


::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Learn the differences of common use of quotation mark, text quotes and block
  quotes.
- Adjust quotation marks to locale standards or custom choices.
- Load proper hyphenation for the quotes (foreign) language.


::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

A very handy way of adding quotes to our document is using the package
`csquotes`, which is nevertheless recommended when using the package `biblatex`.

 We can find information about the package on
CTAN: [https://ctan.org/pkg/csquotes](https://ctan.org/pkg/csquotes), including a readme.

We can install the package using the following command in the terminal:

```bash
tlmgr install csquotes
```

We can then load the package in our LaTeX document using the following command:

```latex
\usepackage{csquotes}
```
A common way is to load `csquotes` after having loaded `biblatex`.



## Various Types of Indicating Quotes



## Referencing Source of Quote to BibLaTeX-Entry


## Foreign Language Quotes 


## Adjust Default Settings

::::::::::::::::::::::::::::::::::::: keypoints

- The `csquotes` package allows us to write quotes in a context sensitive way.
- Based on the current language you can adjust quotation marks.

::::::::::::::::::::::::::::::::::::::::::::::::

