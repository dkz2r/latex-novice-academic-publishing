---
title: 'Mathematics'
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I add mathematical expressions to a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create Inline and Display Math Mode expressions in LaTeX

::::::::::::::::::::::::::::::::::::::::::::::::

## Math Mode

Typesetting mathematical expressions in LaTeX is one of its greatest strengths. We can mark up
mathematical content in a logical way in what is known as *math mode*.

There are two kinds of math mode in LaTeX:

- **Inline math mode**: for typesetting math within a line of text
- **Display math mode**: for typesetting math on its own line

### Inline Math Mode

Inline math mode is marked using a pair of dollar sign symbols (`$ ... $`). It is also possible to
use the notation `\(...\)` to mark inline math mode. Simple expressions are entered without any
special markup, and you'll see that the math is spaced out nicely and has letters in italic.

```latex
\section{Mathematics}

There are two kinds of math mode in LaTeX: inline and display. Inline math mode is marked with
a pair of dollar signs, whereas display math mode is marked with a pair of square brackets.

\subsection{Inline Math Mode}

The Pythagorean theorem is $a^2 + b^2 = c^2$.
```

There are a lot of symbols and specialist math mode commands available in LaTeX:

- Superscripts: `x^2`
- Subscripts: `x_1`
- Greek letters: `\alpha`, `\beta`, `\gamma`, etc.
- Operators: `\times`, `\div`, `\sin`, `\log`, etc.
- Fractions: `\frac{numerator}{denominator}`
- Roots: `\sqrt{expression}`
- Sums and integrals: `\sum`, `\int`, `\oint`, etc.
- Brackets: `()`, `[]`, `{}`, `\langle`, `\rangle`, etc.

::: callout

You can also enter inline math mode using the `\(...\)` notation, which is equivalent to using
the dollar sign notation.

:::

### Display Math Mode

Display math mode uses the exact same commands as inline math mode, but it is centered by default
and is intended for larger equations that are "part of a paragraph". It is also started and ended
with a pair of square brackets (`\[ ... \]`).

::: callout

Remember that `[` and `]` are special characters in LaTeX, which is why we have to "escape" it with
a backslash(`\`) here.

:::

```latex
\subsection{Display Math Mode}

Einstein's famous equation is:

\[
E = mc^2
\]
```

::: spoiler

Math Mode in LaTeX is not just for LaTeX users! It is also used other tools like Jupyter Notebooks,
R Markdown and many markdown processors. There are even extensions for Google Docs and Microsoft
Word that allow you to use LaTeX math mode.

:::

### Math in Enviroments

We can include math in an environment called `equation` to number the equations:

```latex
\subsection{Math in Environments}

The quadratic formula is:

\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\label{eq:quadratic}
\end{equation}

This will allow us to refer to the equation later in the document with \cmd{ref} like this:
Refer to Equation \ref{eq:quadratic}.
```

We can now refer to this equation using the `\ref` command, just like we did in the previous
section:

```latex
The quadratic formula is given in Equation~\ref{eq:quadratic}.
```

### Captions for Equations

We can also add captions to equations, just like we do for figures and tables. This is done by
wrapping the equation in a `figure` environment and using the `\caption{}` command:

```latex
\subsection{Captions for Equations}

\begin{figure}[h]
\centering
\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\label{eq:quadratic}
\end{equation}
\caption{The quadratic equation}
\end{figure}
```

## The `amsmath` Package (Optional)

Mathematical notation is very rich, and the tools in the LaTeX kernel are sometimes not enough to
cover everything. The `amsmath` package extends the capabilities of LaTeX for more complex
mathematical typesetting. Let's try it out:

Add the following to your document:

(In the preamble)
```latex
\usepackage{amsmath}
```

(In the body)
```latex
\subsection{The `amsmath` Package}

Solve the following recurrence for $ n,k\geq 0 $:
\[
Q_{n,0} = 1   \quad Q_{0,k} = [k=0];
\]

\[
Q_{n,k} = Q_{n-1,k}+Q_{n-1,k-1}+\binom{n}{k}, \quad\text{for $n$, $k>0$.}
\]
```

That look ok, but we really want the equations to be aligned vertically, not centered on the page.
We can use the `align` environment from the `amsmath` package to do this:

```latex
\usepackage{amsmath}
```

```latex
\subsection{The `amsmath` Package}

Solve the following recurrence for $ n,k\geq 0 $:
\begin{align*}
  Q_{n,0} &= 1   \quad Q_{0,k} = [k=0];  \\
  Q_{n,k} &= Q_{n-1,k}+Q_{n-1,k-1}+\binom{n}{k}, \quad\text{for $n$, $k>0$.}
\end{align*}
```

The `align*` environment makes the equations line up on the amperstand (`&`)

There's far too many options to cover here, but the `amsmath` User Guide contains many more
examples.

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Can you do it?

See if you can write the following mathematical expression in LaTeX:

- Special Relativity: t' = t / sqrt(1 - v^2 / c^2)

:::::::::::::::::::::::: solution

## Output

```latex
\[
t' = \frac{t}{\sqrt{1 - \frac{v^2}{c^2}}}
\]
```

:::::::::::::::::::::::::::::::::


## Challenge 2: What's wrong with this?

What's wrong with the following LaTeX code?

```latex
\(F = G * (m_1 m_2) / r^2 \)
```


:::::::::::::::::::::::: solution

The code is missing the `\frac` command to create a fraction. The correct code should be:

```latex
\(F = G \frac{m_1 m_2}{r^2} \)
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 3: The `amsmath` package and referencing equations


Add the following equation to your document: E = mc^2.
For this, use the `amsmath` package and a numbered `align` environment.
Label the equation using `\label`. Then, use the `\ref` command to refer to the equation in the text.
You may find the following LaTeX template helpful:

```latex
\documentclass{article}
\usepackage{amsmath} % For better equation formatting

\begin{document}

\section{Referencing Equations}






\end{document}
```


:::::::::::::::::::::::: solution

```latex
\documentclass{article}
\usepackage{amsmath} % For better equation formatting

\begin{document}

\section{Referencing Equations}

We can include a numbered equation as follows:

\begin{equation}
  E = mc^2
  \label{eq:energy}
\end{equation}

Now, we refer to the equation in the text. The famous equation is \ref{eq:energy}.

\end{document}
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

## Scientific Units

To write numbers with their scientific unit you can use the package `\siunitx`.
This provides various commands, so that instead of writing

```latex
The road is about 934.54 m long.
```

you write

```latex
The road is about \qty{934.54}{\m} long.
```

You load the package in your preamble

```latex
\usepackage{siunitx}
```

Using the specifically provided macros of the package has several benefits.

- **Consistent formatting**  
  All numbers and units are printed with the correct spacing and font shape.

- **Locale and digit grouping**  
  You can automatically switch decimal markers (comma vs. point, depending on
  your current language/locale of the section) and group digits:

 ```latex
  \num{12345.678}      % prints “12 345.678” or “12 345,678” depending on locale
  \numlist{11;33;55;77}
  \numproduct{11 x 33}
  \numrange{11}{33}
 ```

- **Unit parsing**  
  Composite units are built from predefined macros:

 ```latex
  \qty{9.81}{\metre\per\second\squared}
  \qty{1}{\kilo\gram\metre\per\second\squared}
  \qty[per-mode = symbol]{1}{\kilo\gram\metre\per\second\squared}
```

- **Uncertainties, lists and ranges**  
  Express measurement errors and intervals:

  ```latex
  \qty{1.23(4)}{\metre} 
  \qtylist{0.13;0.67;0.80}{\milli\metre} 
  \qtyrange{20}{25}{\celsius} 
  ``` 


- **Tables with aligned numbers**  
  Use the `S` column specifier in `tabular` environments to align on decimal
 markers:
 
 ```latex
  \begin{tabular}{S[table-format=3.2] c}
  \toprule
  {Distance} & {Time} \\
  \midrule
  123.45 & \unit{\second} \\
  7.8    & \unit{\minute} \\
  \bottomrule
  \end{tabular}
```

::::::::::::::::::::::::::::::::::::: challenge

- Write the following quantities using ``\qty` or `\num=` and `\ang``:
  1. Speed of light: \(c = 2.99792458 x 10^8\)\,m/s  
  2. Standard atmospheric pressure: 1013.25 hPa  
  3. A right angle is 90° but navigating is done in the direction 1°2′3″ SSW.


:::::::::::::::::::::::: solution
% 1. Speed of light
\qty{2.99792458e8}{\metre\per\second}

% 2. Standard atmospheric pressure
\qty{1013.25}{\hecto\pascal}

% 3. A right angle
\ang{90}; \ang{1;2;3} SSW

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::




::::::::::::::::::::::::::::::::::::: keypoints

- Inline math mode is marked with `$ ... $` or `\(...\)`
- Display math mode is marked with `\[ ... \]`
- Use `\qty{}{}` or `\unit{}` for properly writing numbers with their scientific unit.
::::::::::::::::::::::::::::::::::::::::::::::::

::: spoiler

After this episode, [here is what our LaTeX document looks like](files/document_state/ep-09.tex).

:::
