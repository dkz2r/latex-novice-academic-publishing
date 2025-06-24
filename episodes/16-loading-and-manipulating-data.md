---
title: 'Loading and Manipulating Data'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- Why would I want to load data into my LaTeX document?
- How can I incorporate data analysis into my LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Load a csv file into a LaTeX document and display it as a table
- Manipulate the data to get summary statistics in another table
- Create a simple plot using the data

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

To start with we need to use the `datatool` package. We can find information about the package on
CTAN: [https://ctan.org/pkg/datatool](https://ctan.org/pkg/datatool), including a readme.

We can install the package using the following command in the terminal:

```bash
tlmgr install datatool
```

We can then load the package in our LaTeX document using the following command:

```latex
\usepackage{datatool}
```

We'll also need some data to work with. We'll use some simple CSVs that contain data about GDP
per capita and life expectancy from the past 50 years. You can download the data from
[here](/files/gapminder_data_tidy.zip). Unzip the file and place the contents in you project directory.

Your directory should look like this:

```
project/
├── data
│   ├── gapminder_tidy.csv
│   ├── gapminder_gdp_africa.csv
│   ├── gapminder_gdp_americas.csv
│   ├── gapminder_gdp_asia.csv
│   ├── gapminder_gdp_europe.csv
│   └── gapminder_gdp_oceania.csv
├── main.tex
├── other files...
```

## Loading Data

First things first, we want to load the data into our LaTeX document. We can do this with the
`\DTLread` command from the `datatool` package. This command takes two arguments: the name of the
database and the path to the CSV file.

```latex
\section{Loading and Manipulating Data}

We are using the datatool package to load and manipulate data in our LaTeX document.

\subsection{Loading Data}

We can \kw{load} the data from the CSV file with the \cmd{DTLread} command:

\DTLread[name=gapminder]{data/gapminder_gdp_oceania.csv}
```

## Displaying Data

We can display the data in a table using the `\DTLdisplaydb` command. This command takes the name of
the database as an argument and displays the data in a table.

```latex
\subsection{Displaying Data}

\DTLdisplaydb{gapminder}
```

We can see the data now, but we have way too much data to show in a single table. Let's filter
the data to only show the GDP per capita data.

## Filtering Data

We can filter the data by adding the `row-condition-inline` option to the `\DTLdisplaydb` command.
This option takes a condition that is applied to each row of the database. If the condition
evaluates to true, the row is displayed in the table.

```latex
\subsection{Filtering Data}

% Create a table with only the GDP per capita data
\begin{tabular}{lll}
\textbf{Country} & \textbf{Year} & \textbf{Value} \\
\hline
\DTLforeach{gapminder}{%
  \metric=metric,%
  \country=country,%
  \year=year,%
  \datavalue=value% % we have to use `value` here because `value` is a reserved word in LaTeX
}{%
  \ifthenelse{\equal{\metric}{gdpPercap}}{%
    \country & \year & \datavalue \\
  }{}
}
\end{tabular}
```

## Data Aggregation

```latex
\subsection{Data Aggregation}

\DTLgetuniquevaluesforkey{\countrylist}{gapminder}{country}

\begin{tabular}{lr}
\textbf{Country} & \textbf{Average GDP per Capita} \\
\hline
\DTLforeach*{\countrylist}{\thiscountry=country}{%
  % Calculate mean for this country
  \DTLmeanforkey{gapminder}{value}{country}{\thiscountry}{\meanvalue}%
  \thiscountry & \meanvalue \\
}
\end{tabular}
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

## Figures

You can use pandoc markdown for static figures with the following syntax:

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

