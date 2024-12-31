---
title: 'Citations and References'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- bibtex-ext
- siunitx

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- 

::::::::::::::::::::::::::::::::::::::::::::::::

## Citations and References

For bibliographic citations, while you can include references sources directly in our document, 
usually you will get that information from one or more external files. Such a file is a database
of references, containing the information in a processing-friendly format. Using one or more
reference databases lets you re-use information and avoid manual formatting.

## Reference Databases (BiBTeX)

Reference databases are normally referred to as *BiBTeX* files, and have the extension `.bib`. They
contain one or more entries, one for each reference, and within each are a series of fields.

Create a new file in your project called `references.bib` and add the following content:

```bibtex
@article{Thomas2008,
  author  = {Thomas, Christine M. and Liu, Tianbiao and Hall, Michael B.
             and Darensbourg, Marcetta Y.},
  title   = {Series of Mixed Valent {Fe(II)Fe(I)} Complexes That Model the
             {H(OX)} State of [{FeFe}]Hydrogenase: Redox Properties,
             Density-Functional Theory Investigation, and Reactivity with
             Extrinsic {CO}},
  journal = {Inorg. Chem.},
  year    = {2008},
  volume  = {47},
  number  = {15},
  pages   = {7009-7024},
  doi     = {10.1021/ic800654a},
}
@book{Graham1995,
  author    = {Ronald L. Graham and Donald E. Knuth and Oren Patashnik},
  title     = {Concrete Mathematics},
  publisher = {Addison-Wesley},
  year      = {1995},
}
```

This is an example of a BiBTeX file that contains a reference for an article and another for a 
book. Each entry type starts with a the `@` symbol, and all information appears within a pair of
curly braces `{}`.

The various fields are given in key-value format. Exactly which fields you need to give depends on 
the type of entry. 

::: callout

You might notice that in the `author` field, each entry is separated by the word `and`. This is
essential: the format of the output needs to know which author is which. 

You might also notice that in the article title, some entries are in an extra set of braces. This
is to prevent any case-changing that might be applied to the title.

:::

### BibTeX Format



Editing BiBTeX files by hand can be tedious, a number of tools exist to help you manage your 
reference files. 

### Transferring Information from the Database to the Document

When using Overleaf, we just need to make sure that the bibliography file is present in the project 
and properly referenced in our document. Check to make sure that your `main.tex` file is in the 
same directory as your `references.bib` file. Then, at the bottom of your `main.tex` file, add the
following lines:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

The first lines tells LaTeX how to format the references, and the second line tells LaTeX where to
find the references.

::: callout 

There are many different bibliography styles available, and you can find a list of them at
[CTAN](https://ctan.org/topic/biblio).

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

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

Cool, right?

::::::::::::::::::::::::::::::::::::: keypoints 

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

