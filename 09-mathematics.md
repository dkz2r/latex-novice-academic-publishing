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

::::::::::::::::::::::::::::::::::::: keypoints 

- Inline math mode is marked with `$ ... $` or `\(...\`
- Display math mode is marked with `\[ ... \]`

::::::::::::::::::::::::::::::::::::::::::::::::

