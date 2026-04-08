---
title: 'Citations and References'
teaching: 20
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I add bibliographic references to my document?
- How do I format my references in LaTeX?
- How do I cite references in my document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn how to use a reference database to manage references in LaTeX documents.
- Explore different ways of citing references in our document.

::::::::::::::::::::::::::::::::::::::::::::::::


## Citations and References

For bibliographic citations, while you can include references sources directly in our document,
usually you will get that information from one or more external files. Such a file is a database
of references, containing the information in a processing-friendly format (which
is called `BibTeX`). Using one or more
reference databases lets you re-use information and avoid manual formatting.

## Settings

TeXstudio offers several backend options for handling `BibTeX` files. For the purposes of this workshop, we’ll use `Biber`. 
Open TeXstudio and go to **Options** > **Configure TeXstudio**. 
In the configuration dialog, select **Build** from the left-hand panel. Under **Default Bibliography Tool**, open the drop-down menu and select `Biber`.

![](fig/12-citations/settings_biber.PNG)

## Reference Databases (BiBTeX)

Reference databases are normally referred to as *BiBTeX* files, and have the extension `.bib`. They
contain one or more entries, one for each reference, and within each are a series of fields.

Create a new file in your project called `sample-references.bib` and add the following content:

```bibtex
@article{Thomas2008,
	author  = {Thomas, Christine M.},
	title   = {The Fascinating World of Penguins},
	journal = {Penguin Chronicles},
	date    = {2008},
	pages   = {7009-7024},
}

@book{Graham1995,
	author    = {Graham, Richard L. and Harris, Lisa A.},
	title     = {The Humble Paperclip},
	subtitle  = {Master of the Modern Office},
	publisher = {Scranton Press},
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

You might notice that in the `author` field, surname and givenname and each entry (author) is separated by the word `and`. This is
essential: the format of the output needs to know which author is which. When
using `biblatex` this applies also to the fields `publisher` and `location`, in
which you can also have many values.

You might also notice that in the article title, some entries are in an extra set of braces. This
is to prevent any case-changing that might be applied to the title.

:::

### The BibTeX Format

Editing BiBTeX files by hand can be difficult and tedious. A number of tools exist to help you
manage your reference files. You can find a list of sugggested tools in the references section.

For the purposes of this workshop, we'll use `biblatex`, but feel free to explore other options (e.g. `natbib`) on your own. 

::: group-tab

### biblatex

Check to make sure that your `main.tex` file is in the same directory as your
`sample-references.bib` file.

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

We can \kw{cite references} from our bibliography.

We can cite the article by Thomas (e.g. with `\textbackslash autocite\{Thomas2008\}`).
```


You should see that the citation appears in the text (`(Thomas et al. 2008)`), and the reference
now appears at the end of the document. \cmd{\textbackslash autocite} is a command that automatically chooses the
citation style for you.

Some additional commands that are available in  `biblatex`:

- `\cite{key}` or `\cite{key1, key2}`: Cite the reference with the given key
- `\usepackage{}\parentcite{key}`: Cite the parent reference of the given key.
- `\autocite{key}`: Automatically choose the citation style.
- `\smartcite{key}`: Automatically choose the citation style, but with more control.
- `\footcite{key}`: Cite the reference in a footnote.

A plain citation looks like this `\cite{Graham1995}`, while multiple citations look like this
`\cites{Graham1995}[see][p. 42]{Thomas2008}`. We already used autocite, but we can also use the
similar smartcite `\smartcite{Graham1995}`. The benefit with smartcite is that you
can setup that e.g. all references should go into a footnote. You can continue
using smartcite when you are *in* a footnote and it will then detect that there
is no need for creating another footnote but behaving like autocite.

Furthermore you can use more commands to get the author, title or the date of
the publication directly into your document:

- `\citeauthor{Graham1995}`: Graham and Harris   
- `\citetitle{Graham1995}`: "The Humble Paperclip"  
- `\citeyear{Graham1995}`: 1995  

The outcome and display depends on your style.


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

:::


::: callout

There are many different bibliography styles available, and you can find a list of them at
[CTAN](https://ctan.org/topic/biblio).
Check if one of those bibligraphy and citation styles meets your requirements.
If you want to finetune an existing one we suggest to take a look at [biblatex-ext](https://texdoc.org/serve/biblatex-ext/0).

:::

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Add another reference, then delete it.

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

## Challenge 2: What's wrong with this?

We have the following reference in our document:

```bibtex
@misc{mikolov2013,
	title         ={Efficient Estimation of Word Representations in Vector Space},
	author        ={Mikolov, Tomas and Chen, Kai and Corrado, Greg and Dean, Jeffrey},
	year          ={2013},
	eprint        ={1301.3781},
	archivePrefix ={arXiv},
	primaryClass  ={cs.CL},
	url           ={https://arxiv.org/abs/1301.3781},
}
```
We are using `biblatex` to manage our references, and we identify this reference in the text like
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

## Challenge 3: What's problem with this?

We inculde the following reference in our document:

```bibtex
@article{bentham2011,
	author = {H. Muller, Rainer and Shegokar, Ranjita and M. Keck, Cornelia},
	title = {20 Years of Lipid Nanoparticles (SLN & NLC): Present State of Development & Industrial Applications}, 
	journal= {Current Drug Discovery Technologies},
	year = {2011},
	volume = {8},
	number = {3},
	pages = {207--227},
	doi = {https://doi.org/10.2174/157016311796799062},
	publisher = {Bentham Science Publishers},
}
```

We are using `biblatex` and cite this reference in the text as follows:

```latex
\autocite{bentham2011} provied a good overview over nanoparticles over the last 20 years.
```

What happens when compiling this document? What is wrong with the reference, and how can it be fixed?

:::::::::::::::::::::::: solution

The issue in this reference is cause by a sepcial character (`&` in the title field). 
In LaTeX the ampersand `&` is reserved for alignment, so it must be escaped (`\&`)in normal text. 


If special characters are not escaped properly, LaTeX produce unexpected output or may fail to compile. 
In some cases, this can also corrupt auxiliary files (such as `.aux` or `.bbl`), preventing the document from rendering as expected.
If problems persist after correcting the reference, a common solution is to delete all intermediate files and recompile the document from scratch. Deleting them forces a clean rebuild. 

Corrected bib entry:

```bibtex
@article{bentham2011,
	author = {H. Muller, Rainer and Shegokar, Ranjita and M. Keck, Cornelia},
	title = {20 Years of Lipid Nanoparticles (SLN \& NLC): Present State of Development \& Industrial Applications}, 
	journal= {Current Drug Discovery Technologies},
	year = {2011},
	volume = {8},
	number = {3},
	pages = {207--227},
	doi = {https://doi.org/10.2174/157016311796799062},
	publisher = {Bentham Science Publishers},
}
```
:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- References are stored in a reference database, seperate from the LaTeX document.
- BiBTeX files are used to store references in a processing-friendly format and have the extension
  `.bib`.
- There are multiple libraries available to manage references in LaTeX documents, including
  `natbib` and `biblatex`.
- We can use the `\cite` command or one of its variants to cite references in our document.

::::::::::::::::::::::::::::::::::::::::::::::::

