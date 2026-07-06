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

- Change fonts with the `\renewcommand{}{}`.
- For fonts use the packages `tgtermes` and `fontspec`. Second requires XeLaTeX or LuaLaTeX.
- Second one can use the calls `\setmainfont{Arial}`, `\setsansfont{}` and `\setmonofont`.
- Write dummy-text ("lorem lpsum" text) with `\lipsum` (`\usepackage{lipsum}`).
- `\usepackage[parfill]{parskip}` can be used to add no indent and a space between paragraphs.
- A global option can also be change in the document class `\documentclass[parskip=full]{scrbook}`.
- To force a new line use `\\`.
- Spacing can be changed the following ways:
  - `\.` for a "dot" space.
  - `\:` for a "colon" space.
  - `\;` for a "thick" space.
  - `\!` for a "negative" space.
  - `\,` for a "thin" space.
  - `\hspace{1cm}` for a horizontal space.
  - `\vspace{1cm}` for a vertical space.
  - `\vfill` for fill the remaining space on a page.
  
- Some text formatting commands:
  - Bold: `\textbf{...}`,  italic `\textit{...}`, roman text `\textrm{...}`, san serif text `\textsf{...}`, typewriter text `\texttt{...}`, small caps text `\textsc{...}`.
  
- Font sizes are: `\huge`, `\large`, `\normalsize`, `\small` and `\footnotesize`.
  - Customize with: `{\fontsize{14}{16}\selectfont text}`.
  
- Text alignment: `\centering`, `\raggedright` and `\raggedleft`.

- Create a title page with `\begin{titlepage} \centering ... \vfill \end{titlepage}`.

### [Using Graphics](episodes/08-using-graphics.md)

- With the package `graphicx` we can add jpeg, png, svg, pdf and eps.
- Use `\graphicspath{{folder1/folder2}}` to tell LaTeX to search in folder1 for folder2 and for images.
- With `\includegraphics[options]{name}` you can add the graphic. Possible options are height, width, scale, angle, clip, trim, draft.
  - The width can be handled with `\linewidth`, `width=0.5\linewidth`.
- Centered environment `\begin{center}...\end{center}`.
- Figure environment `\begin{figure}...\end{figure}` combined with `\centering`.
  - Control position:
    - `h`: "here".
    - `t`: top of the page.
    - `b`: bottom of the page.
    - `p`: on an own page.
    - `ht`: combination of the first two.
- Wrapfigure environment `\begin{wrapfigure}[lineheight]{position}{width}...\end{wrapfigure}`.
- Caption for graphic `\caption{...}`, after including it.
- All figures/graphics with a caption can be listed with `\listoffigures`.

### [Tables](episodes/09-tables.md)

- New content coming up soon!

### [Adding Cross References](episodes/10-adding-cross-references.md)

- Label with `\label{text}` and the reference it with `\ref{text}`. For identification you can use `fig:`, `tab:` or `sec:` before the text to make clear that you reference a figure or table.
- For advanced cross-referencing capabilities use the package `cleveref`, then `\cref` adds the reference text like figure or table.
- With the `hyperref` package you can make the references linked by clicking.

### [Mathematics](episodes/11-mathematics.md)

- Use the `amsmath` package to create mathematical expressions.
- Use pairs `$...$` or `\(...\)` to mark inline math mode.
- Use `$$...$$` or `\[...\]` for display math mode (own paragraph that is centered).
- Some special math symbols:
  - Superscript and subscript: `x^{expression}`, `x_{expression}` .
  - Greek letters: `\alpha`, `\beta`, ...
  - Operators: `\times`, `\sin`, `\log`, `\sum`, `\int`, `\sqrt{expression} ...
  - Fractions: `\frac{numerator}{denominator}`.
  - Brackets: `()`, `\{ \}` (need backslash since else used as LaTeX-Operator), `[]`, `\big`, `\left(... \right)`, `\langle`, ...
- Numbered math environment `\begin{equation} ... \end{equation}`, refered by `\ref{eq:...}` ("eq" not obligatory again).
  - Add figure environment around it to add a caption.
- Aligned math environment `\begin{align} ... \end{align}`, lines up similar to table by using "`&`".
  - Writing `align*` ignores numbering.
- Use the `siunitx` package to write scientific numbers.
- Write scientific with units: `\qty{934.54}{\m}`.
- Locale and digit grouping:
  - `\num{...}`, `\numlist{...}`, `\numproduct{...}`, ...
- Unit parsing:
  - `\qty{9.81}{\metre\per\second\squared}`, `\qty[per-mode = symbol]{1}{kilo\gram\metre\per\second\squared}`, ...
- Uncertainties, lists and ranges:
  - `\qty{1.23(4)}{\metre}`, `\qtylist{0.13;0.67;0.80}{\milli\metre}`, `\qtyrange{20}{25}{\celsius}`, ...
- Algin numbers by decimal marker in tables:
  - `\begin{tabular}{S[table-format=3.2] c}`

### [Citations and References](episodes/12-citations-and-references.md)

- Label with `\label{text}` and the reference it with `\ref{text}`. For identification you can use `fig:`, `tab:` or `sec:` before the text to make clear that you reference a figure or table.
- For advanced cross-referencing capabilities use the package `cleveref`, then `\cref` adds the reference text like figure or table.
- With the `hyperref` package you can make the references linked by clicking.

### [Context Sensitive Quotations](episodes/13-context-sensitive-quotations.md)

- 

### [Structuring Sources](episodes/14-structuring-sources.md)

- 

### [Loading and Manipulating Data](episodes/15-loading-and-manipulation-data.md)

- 

### [Documentation and Finding Help](episodes/16-documentation-and-finding-help.md)

- 
