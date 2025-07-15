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

you write:

- `\enquote{…}` uses the main quote style.
- `\enquote*{…}` (star form) forces the inner quote style, even if not
  nested.

```latex
According to Smith, \enquote{the population has doubled since 2000 \enquote*{remarkably fast}}.
```


## Text or Block Quotes

For longer quotations you can use:

```latex
\blockquote[see][45]{%
  This is a long quotation that spans
  multiple lines and even paragraphs...
}
```

- The first optional bracket is a prenote (e.g. “see”).
- The second is a postnote (e.g. source or page number).

It will produce an indented block and automatically insert quotation
marks (or omit them, depending on style). There is also the `\textquote`-command
but this is ommitted since `\blockquote` has the greater flexibility.


# Referencing Source of Quote to BibLaTeX-Entry

One of the biggest advantages of using `csquotes` is its interplay with
`biblatex` as a way of referencing sources.


```latex
\blockcquote[⟨prenote⟩][⟨postnote⟩]{⟨key⟩}[⟨punct⟩]{⟨text⟩}⟨tpunct⟩
```

- **⟨prenote⟩**: optional text before the citation (e.g. “see”, “cf.”).
- **⟨postnote⟩**: optional locator such as a page number (e.g. “45–47”).
- **⟨key⟩**: the BibLaTeX entry key (e.g. `doe2020`).
- **⟨punct⟩**: punctuation inserted *inside* the closing quote (e.g. a comma or period).
- **⟨text⟩**: the quoted passage itself.
- **⟨tpunct⟩**: punctuation inserted *after* the closing quote (e.g. a period or question mark).

Here is an example:


```latex
\blockcquote[see][12]{smith2024}{%
  The rapid growth observed over the past decade
  challenges our previous assumptions about population dynamics.%
}
```

This will produce:

> “The rapid growth observed over the past decade
> challenges our previous assumptions about population dynamics.” — see Smith 2024, 12

and automatically add the `smith2024` entry to your bibliography when you run
`\printbibliography`.


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Referencing Sources

- Add a new entry to your `references.bib` for a short article.
- Use `\blockcquote` to insert a two sentence quote with a pre- and
    postnote pointing to the entry you just created.

:::::::::::::::::::::::: solution

## Output



:::::::::::::::::::::::::::::::::


# Foreign Language Quotes

`csquotes` can detect and adjust for foreign passages if you load
`polyglossia` or `babel`. For example:

```latex
\usepackage[ngerman,english]{babel}
\usepackage{csquotes}

% In your document:
\foreignquote{ngerman}{Er ist der Beste.}
```

This switches to German quotes („…“) only for that passage, then returns
to the main language.

You can also nest foreign quotes:

```latex
\enquote{He said, \foreignquote{french}{Je ne sais quoi}, before leaving.}
```
…which might render as: 
> “He said, ‹Je ne sais quoi›, before leaving.”

There is also the command `\foreignblockcquote` that first needs the language as
mandatory argument, for a concrete example:

```latex
\foreignblockcquote{english}[see][11]{smith2024-german}{%
  Das in den letzten zehn Jahren beobachtete rasche Wachstum
  stellt unsere bisherigen Annahmen über die Bevölkerungsdynamik in Frage.%
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

If you prefer guillemets for English, or want space‑padded French
guillemets, configure:

```latex
\SetQuoteStyle{guillemets}
\DeclareQuoteAlias{french}{guillemets}
\MakeOuterQuote{"}  % allow ASCII "…"
```
You can also customize the nesting levels:

```latex
\DeclareQuoteAlias{ngerman}{\glqq}{\grqq}  % primary German quotes
\DeclareQuoteAlias{ngerman*}{\guqq}{\gdqq} % secondary German quotes
```


…and fine-tune spacing:

```latex
\SetBlockThreshold{1} % number of full ines for blockquote
```




::::::::::::::::::::::::::::::::::::: keypoints

- Use `\enquote{…}` for semantic, language-aware inline quotes.
- Use `\blockquote[prenote][postnote]{…}` for automatic block formatting
  and citation.
- Integrate with `biblatex` via `\autocite` inside quotes for full
  bibliographic support.
- Switch quote styles per language with `\foreignquote` or global
  `\SetQuoteStyle`.
- Customize nesting, spacing, and thresholds to match publisher or
  style-guide requirements.

::::::::::::::::::::::::::::::::::::::::::::::::

