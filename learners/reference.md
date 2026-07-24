---
title: 'Reference'
---

## Glossary

### [Introduction to the LaTeX Workflow](episodes/01-introduction-to-the-latex-workflow.md)

- LaTeX source files use the `.tex` extension.
- Documents are compiled (e.g., with `LuaLaTeX`) to produce output such as PDFs.
- You can write LaTeX in editors like [TeXstudio](https://www.texstudio.org) or online platforms, e.g., [Overleaf](https://www.overleaf.com).


### [Basic LaTeX Document Components](episodes/02-basic-latex-document-components.md)

- LaTeX commands begin with a backslash `\`.  
- Every document must declare a document class using `\documentclass{...}` (common options: `article`, `report`, `book`).  
- Environments are defined using `\begin{...}` and `\end{...}` and must always be properly paired.  
- The **body** of the document is enclosed between: `\begin{document}` and `\end{document}`.
- Everything before `\begin{document}` is called the **preamble**.
- Comments are created using `%`, everything following this symbol on the same line is ignored by the compiler.
- A new paragraph is created by leaving a blank line or by using `\par`.
- Special characters in LaTeX include: `\`, `{`, `}`, `$`, `%`, `&`, `#`, `^`. 
  - To display these characters in text, escape them with a backslash (e.g. `\#`). he exception is `\` itself, which can be produced using `\textbackslash`.

### [Error Handling](episodes/03-error-handling.md)

- Errors are often cascading, one initial error can trigger many others. Always fix the first error first.
- The error `! Undefined control sequence` indicates an unknown or misspelled command.
- Messages like `l.2` indicate the line number where LaTeX detected the error.
- Types of messages:
  - `Error`: prevents the document from compiling
  - `Warning`: may affect output but compilation continues
  - `Information`: additional helpful details

### [The Structure of a Document](episodes/04-the-structure-of-a-document.md)

- `\section{...}` & `\subsection{...}` create a new (sub-) section,  which is automatically numbered.
  - The starred variants `\section*{...}` & `\subsection*{...}` is used for unnumbered headings, which are also excluded from the table of content.
- Similarly, `\paragraph{...}`, `\chapter{...}`, and other sectioning commands work like `\section{...}`. Which commands are available typically depends on the document class.
- A table of contents can be generated with `\tableofcontents`, placed wherever you want it to appear in the document.

- Unordered list (`itemize`):
  
```latex
\begin{itemize}
  \item ...
  \item ...
\end{itemize}
```

- Ordered list (`enumerate`):

```latex
\begin{enumerate}
  \item ...
  \item ...
\end{enumerate}
  ```
  - Custom bullet symbols can be specified using the optional argument `\item[...]` (e.g., `\item[(a)]` to label an item with `(a)`).

### [Using Document Classes](episodes/05-using-document-classes.md)

- Document classes set global options `\documentclass[<options>]{<class>}`
  - e.g.`\documentclass[12pt]{article}`, `\documentclass[a4paper]{article}`, `\documentclass[a4paper,12pt,twocolumn]{article}`.
- Standard classes are: `article`, `report`, `book`, `letter` and `slides`.

- Modern (function-rich) classes:
  - AMS classes: `amsbook`, `amsart` and `amsproc`.
  - `beamer` for creating (modern) presentations with support for themes, overlays, and animations.
  - `KOMA-Script` (`scrartcl`, `scrreprt`, `scrbook`, `scrlttr2`) modern, highly customizable replacements for standard classes.
  - `memoir` a flexible class for books, reports, and articles, with many built-in formatting tools.
  
### [Extending LaTeX](episodes/06-extending-latex.md)

- New packages are loaded in the **preamble** using `\usepackage{<package_name>}`, e.g. `geometry`, `booktabs` or `xcolor`. The package is applied during the next compilation.
  - If a package is not installed, use `tlmgr install <package_name>` in the terminal to install it.
  - All installed packages can be updated at once with `tlmgr update --self --all`.
- Many packages accept additional options inside square brackets: `\usepackage[<options>]{<package_name>}`.
  - For example, `\usepackage[width = 6cm]{geometry}` sets the text block width to six cm.
  
- Custom commands can be defined using: `\newcommand{<\command_name>}[<number_of_arguments>][<default_value_first_argument>]{<definition>}`.
  - If a command with this name already exists, use `\renewcommand` instead, which has the same syntax.
  - This allows document-wide formatting changes from a single definition.

### [Fonts, Formatting and Spacing](episodes/07-fonts,-formatting-and-spacing.md)

- To change the font for the entire document use `\renewcommand{\familydefautl}{<font>}`
- The packages `tgtermes` or `fontspec` can be used for font management. Note that `fontspec` requires `LuaLaTeX` or `XeLaTeX`.
  - With `fontspec`, you can set fonts using `\setmainfont{...}`, `\setsansfont{...}` and `\setmonofont{...}`.
- With `\lipsum` from the `lipsum` package placeholder text can be generated. 
- The package `parskip` helps controlling spaces between paragraphs. `\usepackage[parfill]{parskip}` removes the indentation and adds spacing between paragraphs.
  - With KOMA-Scripts this option is also available in the class options, e.g.  `\documentclass[parskip=full]{scrbook}` 
- A global option can also be change in the document class `\documentclass[parskip=full]{scrbook}`.
- `\\` forces a new line. 
- Explicit spacing commands:
  - `\.` for a "dot" space.
  - `\:` for a "colon" space.
  - `\;` for a "thick" space.
  - `\!` for a "negative" space.
  - `\,` for a "thin" space.
  - `\hspace{1cm}` for a horizontal space.
  - `\vspace{1cm}` for a vertical space.
  - `\vfill` for fill the remaining space on a page.
- Explicit text formatting commands:
  - Bold: `\textbf{...}`,  italic `\textit{...}`, roman text `\textrm{...}`, san serif text `\textsf{...}`, typewriter text `\texttt{...}`, small caps text `\textsc{...}`.
- Font sizes are: `\huge`, `\large`, `\normalsize`, `\small` and `\footnotesize`.
  - For custom sizes, use: `{\fontsize{14}{16}\selectfont <text>}`, where $14$ is the font size and $16$ the line spacing.
- Text alignment: `\centering`, `\raggedright` and `\raggedleft`.

- Create a title page using the `titlepage` environment: `\begin{titlepage} \centering ... \vfill \end{titlepage}`.

### [Using Graphics](episodes/08-using-graphics.md)

- The `graphicx` package enables working with `jpeg`, `png`, `svg`, `pdf` and `eps` file formats.
- Use `\graphicspath{{<folder>/}}` to specify a default folder where LaTeX will search for images.
- Use `\includegraphics[<options>]{<file_name>}` to include graphics in your document. Available options include `height`, `width`, `scale`, `angle`, `clip`, `trim` and `draft` among others.
  - The width can be set relative to the line width using `\linewidth`, e.g. ``\includegraphics[width=0.5\linewidth]{<file_name>}`.
- Centering environment `\begin{center}...\end{center}`.
- Floating figure environment `\begin{figure}...\end{figure}`.
  - Control position:
    - `h`: "here".
    - `t`: top of the page.
    - `b`: bottom of the page.
    - `p`: on an own page.
    - `ht`: combination of the first two.
  - `\centering` to center the image inside the environment.
- Add a caption below an image with `\caption{...}`.
- A list of all Graphics can be generated with `\listoffigures`, if they have a caption.

### [Tables](episodes/09-tables.md)

- New content coming up soon!

### [Adding Cross References](episodes/10-adding-cross-references.md)

- Use `\label{<label_name>}` to mark an element and reference it with `\ref{<label_name>}`. 
  - To keep references organized, use the following prefixes `before the`for the label names: `fig:` (figures), `tab:`  (tables) and `sec:` (Section).
- `cleveref` provides advanced cross-referencing capabilities. Use `\cref{<label_name>}` instead of `\ref{<label_name>}` to automatically add the reference type before the number in the text. 
- With the `hyperref` package you can make the references linked by clicking.
  - Recommendation: load `hyperref` last in your preamble as it could lead to issues with other packages. But `cleveref` should be loaded after hyperref.

### [Mathematics](episodes/11-mathematics.md)


- The `amsmath` package extends the mathematical expression support.
- Inline math mode with `$...$` or `\(...\)`.
- Display math mode, rebders centered on own line, with `$$...$$` or `\[...\]`.
- Math symbols & expressions:
  - Superscript and subscript: `x^{<expression>}`, `x_{<expression>}` .
  - Greek letters: `\alpha`, `\beta`, ...
  - Operators: `\times`, `\sin`, `\log`, `\sum`, `\int`, `\sqrt{expression} ...
  - Fractions: `\frac{numerator}{denominator}`.
  - Brackets: `()`, `\{ \}` (need backslash since else used as LaTeX-Operator), `[]`, `\big`, `\left(... \right)`, `\langle`, ...
- Math environment with numbered equations `\begin{equation} ... \end{equation}`, refereed by `\ref{eq:...}` (`eq` not obligated). Wrap in a `figure` environment to add a caption.
- Aligned math environment `\begin{align} ... \end{align}`, `&` as an anchor point for alignement.
  - Writing `align*` ignores numbering.

- The `siunitx` package provides consistent formatting of numbers and units.
- Write scientific with units, e.g. `\qty{934.54}{\m}`.
- Number formatting:
  - `\num{...}` (a numbers), `\numlist{...}` (list of numbers), `\numproduct{...}` (product of numbers).
- Unit parsing:
  - `\qty{9.81}{\metre\per\second\squared}`, `\qty[per-mode = symbol]{1}{kilo\gram\metre\per\second\squared}`, ...
- Uncertainties, lists and ranges:
  - `\qty{1.23(4)}{\metre}`, `\qtylist{0.13;0.67;0.80}{\milli\metre}`, `\qtyrange{20}{25}{\celsius}`, ...
- Decimal-aligned columns in tables:
  - `\begin{tabular}{S[table-format=3.2] c}`

### [Citations and References](episodes/12-citations-and-references.md)

- Use the `biblatex` package for citation and reference management: `\usepackage[<option>]{biblatex}`.
  - Common options include the citation style and sorting method, e.g.: `\usepackage[style=authoryear, sorting=nyt, backend=biber]{biblatex}`
- `biblatex` requires a bibliography backend to process and sort entries. The recommended backend is `Biber`. You may need to configure your LaTeX editor.
- References are usually stored in a BibTeX file (`.bib`). Each entry follows this format: `@<type>{<cite_key>, <key> = {<value>}, ...}`
  - Common entry types: `article`, `book`, `online`, `misc`, `manual`, `proceedings`, ...
  - Common fields: `author`, `title`, `journal`, `date`, `pages`, `publisher`, ...
- Link your `.bib` file in the preamble with `\addbibresource{<file_name>.bib}`.
- Citing a reference with `\cite{<cite_key>}`
  - Granular citation commands allow you to reference specific parts of a citation: `\citeauthor{<cite_key>}`, `citetitle{<cite_key>}` and `\citeyear{<cite_key>}` we can control apparence in the document
- Smart citation commands automatically adapt the citation style: `\autocite{}` and `\smartcite{}`.


### [Context Sensitive Quotations](episodes/13-context-sensitive-quotations.md)

- New content coming up soon!

### [Structuring Sources](episodes/14-structuring-sources.md)

- Use `\input{<filename>}` or `\include{<filename>}` to insert content from external `.tex` files into your main document. `input` includes your content directly, while `include` start a new page before inserting the content.
- Use  `\includeonly{<filename>}` in the preamble  to restrict which files are compiled.  
- The following commands help organize the structure of a document and automatically adjust formatting such as page numbering: `\frontmatter`, `\mainmatter`, `\backmatter`, and `\appendix`.

### [Loading and Manipulating Data](episodes/15-loading-and-manipulation-data.md)

- New content coming up soon!

### [Documentation and Finding Help](episodes/16-documentation-and-finding-help.md)

- 
