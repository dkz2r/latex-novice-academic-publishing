---
title: 'Citations and References'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- bibtex-ext
- siunitx
- cite, cites, parentcite, parentcites, autocite, smartcite

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

-

::::::::::::::::::::::::::::::::::::::::::::::::

## Citations and References

For bibliographic citations, while you can include references sources directly in our document,
usually you will get that information from one or more external files. Such a file is a database
of references, containing the information in a processing-friendly format (which
is called `BibTeX`). Using one or more
reference databases lets you re-use information and avoid manual formatting.

## Reference Databases (BiBTeX)

Reference databases are normally referred to as *BiBTeX* files, and have the extension `.bib`. They
contain one or more entries, one for each reference, and within each are a series of fields.

Create a new file in your project called `sample-references.bib` and add the following content:

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
book. Each entry type starts with a the `@` symbol, followed by the type of the
referencing item (e.g. `article`) and all information appears within a pair of
curly braces `{}`.

The various fields are given in key-value format. Exactly which fields you need to give depends on
the type of entry.

::: callout

You might notice that in the `author` field, each entry is separated by the word `and`. This is
essential: the format of the output needs to know which author is which.

You might also notice that in the article title, some entries are in an extra set of braces. This
is to prevent any case-changing that might be applied to the title.

:::

### The BibTeX Format

Editing BiBTeX files by hand can be difficult and tedious. A number of tools exist to help you
manage your reference files. You can find a list of sugggested tools in the references section.

We're going to cover two different ways to include references in our document: using the `natbib`
package and using the `biblatex` package. For the purposes of this workshop, we'll use `biblatex`,
but feel free to explore `natbib` on your own - an identical example is provided in the `natbib`
tab below.

::: group-tab

### biblatex

When using Overleaf, we just need to make sure that the bibliography file is present in the project
and properly referenced in our document. Check to make sure that your `main.tex` file is in the
same directory as your `sample-references.bib` file.

At the top of our `main.tex` file, we'll add a line to import biblatex:

```latex
\usepackage[style=authoryear]{biblatex}
\addbibresource{sample-references.bib}
```
Do not forget to write the suffix of your referencing file, too (`.bib`).

Then, at the bottom of your `main.tex` file, add the following lines:

```latex
\printbibliography
```

And... nothing? Right, because we haven’t cited anything in our document yet. Let’s add a citation:

```latex
\section{Reference Databases}

One of the best features of LaTeX when writing academic documents is the ability to easily and
confidently \kw{cite references}.

We can cite the article by Thomas (e.g. with `\autocite{Thomas2008}`) and it will show up in the references.

You should see that the citation appears in the text (`(Thomas et al. 2008)`), and the reference
now appears at the end of the document. `\autocite` is a command that automatically chooses the
citation style for you.

Let’s explore some of the other citation commands available in `biblatex`:

- `\cite{key}` or `\cite{key1,key2}`: Cite the reference with the given key.
- `\cites{key1}{key2}{key-n}`: Cite multiple references.
- `\parentcite{key}`: Cite the parent reference of the given key.
- `\autocite{key}`: Automatically choose the citation style.
- `\smartcite{key}`: Automatically choose the citation style, but with more control.
- `footcite{key}`: Cite the reference in a footnote.

```latex
A plain citation looks like this \cite{Graham1995}, while multiple citations look like this
\cites{Graham1995}[see][p. 42]{Thomas2008}. We already used autocite, but we can also use the
similar smartcite \smartcite{Graham1995}. The benefit with smartcite is that you
can setup that e.g. all references should go into a footnote. You can continue
using smartcite when you are *in* a footnote and it will then detect that there
is no need for creating another footnote but behaving like autocite.
```


#### Good to know

If you want to have all entries of your referencing file in your bibliography,
you can either go with `\cite{key1,key2,.....}` for all entries or you type
`\cite{*}`.
This will print all entries first in your text section and puts them into the
bibliography. You can also go with `\nocite{*}` then the reference is only
internally called and put into the bibliography. 



It is always good to tidy up your `.bib`-file and use the fields accordingly. In
case you want to omit certain fields in your bibliography you can do so on the
fly:
```latex 
\AtEveryBibitem{
  \clearfield{url}
  \clearfield{month}
  \clearfield{note}
  \clearfield{isbn}
  \clearname{translator}
  \clearlist{language}
}
```

With this command you will delete the content of the fields in the bibliography.
Note, that there is `\clear*field*`, `\clear*name*` and `\clear*list*`.




### natbib

When using Overleaf, we just need to make sure that the bibliography file is present in the project
and properly referenced in our document. Check to make sure that your `main.tex` file is in the
same directory as your `sample-references.bib` file.

At the top of our `main.tex` file, we'll add a line to import natbib:

```latex
\usepackage{natbib}
\bibliographystyle{plainnat}
```

Then, at the bottom of your `main.tex` file, add the following lines:

```latex
\bibliography{sample-references}
```

And... nothing? Right, because we haven't cited anything in our document yet. Let's add a citation:

```latex
\section{Reference Databases}

One of the best features of LaTeX when writing academic documents is the ability to easily and
confidently \kw{cite references}.

We can cite the article by Thomas \citep{Thomas2008} and it will show up in the references.
```

You should see that the citation appears in the text (`(Thomas et al. 2008)`), and the reference
now appears at the end of the document. `\citep` is a command that automatically chooses the
citation style for you.

Let's explore some of the other citation commands available in `natbib`:

- `\citet{key}`: Cite the reference with the given key in a textual context.
- `\citep{key}`: Cite the reference with the given key in a parenthetical context.
- `\citealt{key}`: Cite the reference with the given key without any parentheses.
- `\citeauthor{key}`: Cite the author of the reference.
- `\citeyear{key}`: Cite the year of the reference.

```latex
A plain citation looks like this \citep{Graham1995}, while multiple citations look like this
\citep{Graham1995,Thomas2008}. We already used \citep, but we can also use \citet{Graham1995}, which
gives us a textual citation, or \citealt{Thomas2008}, which gives us a citation without parentheses.
```



:::


::: callout

There are many different bibliography styles available, and you can find a list of them at
[CTAN](https://ctan.org/topic/biblio).
Check if one of those bibligraphy and citation styles meets your requirements.
If you want to finetune an existing one we suggest to take a look at [biblatex-ext](https://texdoc.org/serve/biblatex-ext/0).

:::

::: callout



:::

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Try out the other example?

Go back up to the `natbib` tab and try out the example there. What differences do you notice?

:::::::::::::::::::::::: solution

## Answer

The `natbib` package is a bit more manual than `biblatex`. You have to specify the bibliography
style and the bibliography file separately, and the citation commands are a bit more manual.
This isn't necessarily a bad thing, as it gives you more control over the output. There's no wrong
answer, just personal preference.

:::::::::::::::::::::::::::::::::


## Challenge 2: Add another reference, then delete it.

Try adding the following reference to your `sample-references.bib` file:

```bibtex
@book{Huff1954,
  author    = {Huff, Darrell},
  title     = {How to Lie with Statistics},
  publisher = {W. W. Norton \& Company},
  year      = {1954},
}
```

Then, add a citation to this reference in your document. Try a couple different styles of citation
commands. Then, once you have it working, delete the reference and re-compile your document. What
happens?

:::::::::::::::::::::::: solution

You might expect removing the reference to either error or remove the citation from the text, but
it doesn't - instead we get a placeholder in the text and a warning in the log. A missing reference
is not so critical an error that we can't render the document, but we should probably fix it.

:::::::::::::::::::::::::::::::::

## Challenge 3: What's wrong with this?

We have the following reference in our document:

```bibtex
@misc{mikolov2013,
      title={Efficient Estimation of Word Representations in Vector Space},
      author={Tomas Mikolov and Kai Chen and Greg Corrado and Jeffrey Dean},
      year={2013},
      eprint={1301.3781},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/1301.3781},
}
```
We are using biblatex to manage our references, and we identify this reference in the text like
this:

```latex
The Word2Vec algorithm \autocite{mikolov} is a popular method for generating word embeddings.
```

When we compile our document, we see the following error:

```output
The Word2Vec algorithm (mikolov) is a popular method for generating word embeddings.
```

What's wrong with this reference? How can we fix it?

:::::::::::::::::::::::: solution

We are referencing the key `mikolov` in our document, but the key in our BiBTeX file is
`mikolov2013`. We need to update our citation command to `\autocite{mikolov2013}`. Note that LaTeX
still compiles the document, but it gives us a warning that the reference is missing and uses the
key as a placeholder. You might use this to temporarily mark a reference that you haven't added yet,
just be sure to clear all of your warnings before finializing your document.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

-

::::::::::::::::::::::::::::::::::::::::::::::::

