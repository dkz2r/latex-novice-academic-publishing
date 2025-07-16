---
title: 'Context Sensitive Quotations'
teaching: 25
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions
- How can I semantically markup quotes so they adapt to language and style?
- What is the benefit of letting `csquotes` integrate with `biblatex` for quoting?
- How do I switch between different quotation styles (e.g. English “…” vs. German „…“)?
- How can I automatically hyphenate and nest quotations correctly in another language?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
By the end of this lesson, learners will be able to:

1. Explain the difference between inline quotes, block quotes, and semantic quoting.
2. Use `\enquote{…}` (and its variants) to produce context‑sensitive quotation marks.
3. Reference a quoted passage with a citation that feeds into the bibliographic list.
4. Switch quote styles to match locale conventions (e.g. German vs. English).
5. Configure `csquotes` to handle nested quotes, foreign‑language quotes, and hyphenation.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Quotations play an essential role in scholarly writing, allowing you to bring in authoritative voices or preserve precise wording. But “dumb” straight ASCII quotes (`"like this"`) don’t adapt to language conventions, and block quotes can be cumbersome to format manually.

The **`csquotes`** package makes all of this automatic:

- It defines semantic commands like `\enquote{…}`, which insert the right opening/closing marks based on the current language (e.g. “English style,” ‹French guillemets›, or „German quotes“).
- It integrates smoothly with `biblatex`, so you can attach a citation to a quote with `\blockquote[prenote][postnote]{…}` and have the entry appear in your bibliography.
- It handles nested quotations, switching automatically to secondary marks (e.g. single quotes) when you nest quotes.
- It can load language-specific hyphenation patterns so that breaking long quoted passages doesn’t lead to poorly shaped lines.

Before we begin, make sure you’ve installed `csquotes`:

```bash
tlmgr install csquotes
```

and that your document preamble loads it (ideally after the package `biblatex`):
```latex
\usepackage{csquotes}
```



# Various Types of Quotation

## Inline Quotes

Instead of typing this by hand:
```latex
“She said, ‘Hello.’”
```
you write:

```latex
\enquote{She said, \enquote*{Hello}.}
```

- `\enquote{…}` uses the main quote style.
- `\enquote*{…}` (star form) forces the inner quote style, even if not
  nested.

Here is a full example.
```latex
According to Charles Hoare, \enquote{Documentation must be regarded 
as \enquote*{an integral part} of the process of design and coding.}
(1973, p. 195)
```


## Text or Block Quotes

For longer quotations you can use:

```latex
\blockquote[see Hoare 1973, p. 195]{%
 Documentation must be regarded as an integral part of the process of design and coding. 
 A good programming language will encourage and assist the programmer to write clear, 
 self-documenting code, and even perhaps to develop and display a pleasant style of writing.%
}
```

- The optional bracket is a postnote (e.g. source or page number).

It will produce an indented block and automatically insert quotation
marks (or omit them, depending on style). There is also the `\textquote`-command
but this is ommitted since `\blockquote` has the greater flexibility.


# Referencing Source of Quote to BibLaTeX-Entry

One of the biggest advantages of using `csquotes` is its interplay with
`biblatex` as a way of referencing sources.
To use this kind of quotes you also need to have the package `biblatex` loaded
in your preamble.


```bibtex
@InCollection{Hoare1973,
  author    = {Charles Antony Richard Hoare},
  title     = {Hints on programming language design},
  editor    = {C. Bunyan},
  booktitle = {Computer Systems Reliability},
  series    = {State of the Art Report},
  number    = {20},
  pages     = {193--216},
  year      = {1973},
  url       = {http://flint.cs.yale.edu/cs428/documentation/HintsPL.pdf},
  urlyear   = {2018},
  comment   = {Documentation must be regarded as an integral part of the process of design and coding. A good programming language will encourage and assist the programmer to write clear, self-documenting code, and even perhaps to develop and display a pleasant style of writing.}
}
```

```latex
\blockcquote[⟨prenote⟩][⟨postnote⟩]{⟨key⟩}[⟨punct⟩]{⟨text⟩}⟨tpunct⟩
```

- **⟨prenote⟩**: optional text before the citation (e.g. “see”, “cf.”).
- **⟨postnote⟩**: optional locator such as a page number (e.g. “193–216”).
- **⟨key⟩**: the BibLaTeX entry key (e.g. `Hoare1973`).
- **⟨punct⟩**: punctuation inserted *inside* the closing quote (e.g. a comma or period).
- **⟨text⟩**: the quoted passage itself.
- **⟨tpunct⟩**: punctuation inserted *after* the closing quote (e.g. a period or question mark).

Here is an example:


```latex
\blockcquote[see][195]{Hoare1973}{Documentation must be regarded as an integral part of the process of design and coding. A good programming language will encourage and assist the programmer to write clear, self-documenting code, and even perhaps to develop and display a pleasant style of writing.}
```

This will produce (with default settings for `biblatex`):


> Documentation must be regarded as an integral part of the process
> of design and coding. A good programming language will encourage
> and assist the programmer to write clear, self-documenting code,
> and even perhaps to develop and display a pleasant style of writing.
> [see 1, p. 195]

and automatically add the `Hoare1973` entry to your bibliography when you run
`\printbibliography`.


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Referencing Sources

- Add a new entry to your `references.bib` for a short article.
- Use `\textcquote` and `\blockcquote` to insert a two sentence quote with a pre- and
    postnote pointing to the entry you just created.
Do you see a difference when you use `\textcquote` or `\blockcquote`?

:::::::::::::::::::::::: solution

## Output

With default settings, quotes written with `\blockcquote` will be displayed in
the same way as `\textcquote`. As soon as the text is longer than three complete
lines of text, then the whole quote is indented and set as a block.


:::::::::::::::::::::::::::::::::


# Foreign Language Quotes

`csquotes` can detect and adjust for foreign passages if you load
`polyglossia` or `babel`. For example:

```latex
\usepackage[ngerman,english]{babel}
\usepackage[autostyle]{csquotes}

% In your document:
\foreignquote{german}{Er ist der Beste.}
```

This switches to German quotes („…“) only for that passage, then returns
to the main language.

You can also nest foreign quotes:

```latex
\enquote{He said, \foreignquote{french}{Je ne sais quoi}, before leaving.}
```
…which might render as (setting in your preamble `\usepackage[autostyle,french=guillemets]{csquotes}`):
> “He said, « Je ne sais quoi », before leaving.”

There is also the command `\foreignblockcquote` that first needs the language as
mandatory argument, for a concrete example:

```latex
\foreignblockcquote{german}[vgl.][195 (eigene Übersetzung)]{Hoare1973}{%
Die Dokumentation muss als integraler Bestandteil des Entwurfs- und Kodierungsprozesses betrachtet werden. Eine gute Programmiersprache wird den Programmierer ermutigen und unterstützen, klaren, selbstdokumentierenden Code zu schreiben und vielleicht sogar einen angenehmen Schreibstil zu entwickeln und zu pflegen.%
}
```

# Auxiliary Commands


When quoting text in a formal way, any changes applied to the quoted material—such as omissions, insertions, or deletions—should be explicitly marked. The `csquotes` package provides three auxiliary commands for this purpose:

- `\textelp{}` / `\textelp{⟨text⟩}` / `\textelp*{⟨text⟩}`  
  Prints an ellipsis to indicate omitted material. With an argument, it also shows inserted text in brackets. The starred form reverses insertion order. 
- `\textins{⟨text⟩}` / `\textins*{⟨text⟩}`  
  Marks added text in square brackets. The starred variant is intended for small modifications (e.g. capitalization). 
- `\textdel{⟨text⟩}`  
  Indicates deletion by printing empty brackets; the omitted text itself is not displayed. 


```latex
She said, “To be, or not to be\textelp{} that is the question.”
He corrected it to “To be, or not to be\textelp{ indeed}\textelp*{ indeed}.”
Old form: “colour” → “colou\textdel{r}”
Insersion: “The quick \textins{brown} fox.”
```


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Auxiliary Commands

- Take the sentence: “The quick brown fox jumps over the lazy dog.”
- Omit the word “brown” using `\textelp{}` and show the result.
- Insert the word “agile” before “fox” using `\textins{}`.
- Delete the “s” in “jumps” using `\textdel{}`.

:::::::::::::::::::::::: solution

## Output



:::::::::::::::::::::::::::::::::::::


# Adjust Default Settings

Change the amount of lines you want to have for a block quote:

```latex
\SetBlockThreshold{0} % number of full ines for blockquote, 0= all quotes are like blockquote
```

Adjust the appearance of a deleted word.
```latex
\renewcommand{\mktextdel}[1]{[\textellipsis]}
```

Define the way of a source is displayed after the blockquote:

```latex
\renewcommand{\mkcitation}[1]{\footnote{#1}}
\renewcommand{\mkccitation}[1]{\footnote{#1}}
```
This will put the references in a footnote.

::::::::::::::::::::::::::::::::::::: keypoints

- Use `\enquote{…}` for semantic, language-aware inline quotes.
- Use `\blockquote{…}` for automatic block formatting
  and citation.
- Integrate with `biblatex` inside quotes for full
  bibliographic support.
- Switch quote styles per language with `\foreign(c)quote`.
- Customize nesting, spacing, and thresholds to match publisher or
  style-guide requirements.

::::::::::::::::::::::::::::::::::::::::::::::::

