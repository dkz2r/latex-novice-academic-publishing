---
title: 'Mathematics'
teaching: 10
exercises: 2
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

\subsection{Inline Math Mode}

The Pythagorean theorem is \(a^2 + b^2 = c^2\).
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

### Display Math Mode

Display math mode uses the exact same commands as inline math mode, but it is centered by default
and is intended for larger equations that are "part of a paragraph":

```latex
\subsection{Display Math Mode}

The quadratic formula is:

\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]
```

### Math in Enviroments

We can include math in an environment called `equation` to number the equations:

```latex
\subsection{Math in Environments}

The quadratic formula is:

\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\label{eq:quadratic}
\end{equation}
```

We can now refer to this equation using the `\ref` command, just like we did in the previous
section:

```latex
The quadratic formula is given in Equation~\ref{eq:quadratic}.
```

## The `amsmath` Package

Mathematical notation is very rich, and the tools in the LaTeX kernel are sometimes not enough to
cover everything. The `amsmath` package extends the capabilities of LaTeX for more complex
mathematical typesetting. Let's try it out:

Add the following to your document:

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


::::::::::::::::::::::::::::::::::::: keypoints

- Inline math mode is marked with `$ ... $` or `\(...\`
- Display math mode is marked with `\[ ... \]`

::::::::::::::::::::::::::::::::::::::::::::::::

