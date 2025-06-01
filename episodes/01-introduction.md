---
title: "Introduction to the LaTeX Workflow"
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- What do I need to do to write and edit a LaTeX document?
- How can I render a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Demonstrate how to create a new LaTeX Document.
- Become familiar with the TeXworks interface.
- Compile a LaTeX document with the TeXworks editor.
- Compile a LaTeX document with the command line.

::::::::::::::::::::::::::::::::::::::::::::::::

## What is LaTeX

LaTeX is a typesetting language, useful for combining text with mathematical equations, figures,
tables, and citations, among other things.

Unlike common word processors like Microsoft Word or LibreOffice Writer, LaTex is a *markup
language*, meaning that formatting (including bold text, bullet points, and changes in font size)
is indicated by the use of commands, special characters, or *environments*.

In order to produce the actual document, this mark-up text must be *compiled*. Errors in the
mark-up can either be non-fatal, meaning the document will compile with some warnings; or fatal,
meaning the document will fail to compile.

## Our First LaTeX Document

To begin with, we will create a new directory to hold our files for this workshop. Call it
`latex-workshop`, and make a note of the path to this directory.

Start the TeXworks editor and immediately "save" the file. This will prompt you for a location to
save the file, so navigate to the `latex-workshop` directory you just created, and save the file
as `main.tex`.

## The TeXworks Interface

The TeXworks interface is divided into three main sections:
- The **Editor**: This is where you write your LaTeX code. It supports syntax highlighting and
  basic code completion.
- The **Preview Pane**: This shows the compiled output of your LaTeX code. This window will appear
  whenever we compile the document.
- The **Menu Bar**: This contains various options for managing your document, such as saving,
  compiling, and printing. You can also access the preferences and settings from here.

The overall interface is designed to be simple and intuitive, focusing on the essential features
of a LaTeX editor. Note the large green triangle button in the top left corner of the interface.
This is the "Typeset" button, which compiles your LaTeX document and updates the preview pane with
the rendered output. Next to the "Typeset" button is a drop-down menu that allows you to select
the typesetting engine you wish to use. For this workshop, we will use the default engine,
PDFLaTeX.

## Compiling a LaTeX Document

Type the following code into the editor:

```latex
\documentclass{article}
\begin{document}
Hello, \LaTeX!
\end{document}
```

Now click the green "Typeset" button in the top left corner of the interface. This will compile
the document and update the preview pane with the rendered output. You should see a PDF preview
of the document with the text "Hello, LaTeX!".

::: callout

When you click the "Typeset" button, TeXworks will run the PDFLaTeX compiler on your document. You
will see a window appear on the bottom of the interface called "Console output". This window
contains the output of the compiler, including any warnings or errors that may have occurred
during the compilation process. We will talk about this in more detail in a later episode.

:::

## Compiling a LaTeX Document from the Command Line

The TeXworks editor is a convenient way to write and compile LaTeX documents, but you are not
limited to using it. Any program that can edit text files can be used to write LaTeX, which we can
then compile from the command line.

You can use any text editor to write your LaTeX code. Some popular text editors for LaTeX include:
- [Visual Studio Code](https://code.visualstudio.com/)
- [Emacs](https://www.gnu.org/software/emacs/)
- [Vim](https://www.vim.org/)
- Notepad++ (Windows only)

We will continue to demonstrate with TeXworks, but you can use any text editor you prefer.

To compile a LaTeX document from the command line, you can use the `pdflatex` command. Open a
console or terminal window, then navigate to the directory where you saved your `main.tex` file.

::: spoiler

Useful commands for navigating the command line:
- `cd <directory>`: Change directory to `<directory>`.
- `ls` (Linux/macOS) or `dir` (Windows): List the files in the current directory.
- `pwd` (Linux/macOS): Print the current working directory.

:::

Once you are in the correct directory, run the following command:

```bash
pdflatex main.tex
```

You should see output similar to the following:

```
This is pdfTeX, Version 3.141592653-2.6-1.40.28 (TeX Live 2025) (preloaded format=pdflatex)
 restricted \write18 enabled.
entering extended mode
(./main.tex
LaTeX2e <2024-11-01> patch level 2
L3 programming layer <2025-04-29>
(e:/texlive/2025/texmf-dist/tex/latex/base/article.cls
Document Class: article 2024/06/29 v1.4n Standard LaTeX document class
(e:/texlive/2025/texmf-dist/tex/latex/base/size10.clo))
(e:/texlive/2025/texmf-dist/tex/latex/l3backend/l3backend-pdftex.def)
(./main.aux)
[1{e:/texlive/2025/texmf-var/fonts/map/pdftex/updmap/pdftex.map}] (./main.aux)
)<e:/texlive/2025/texmf-dist/fonts/type1/public/amsfonts/cm/cmr10.pfb><e:/texli
ve/2025/texmf-dist/fonts/type1/public/amsfonts/cm/cmr7.pfb>
Output written on main.pdf (1 page, 21048 bytes).
Transcript written on main.log.
```

In the directory where you ran the command, you should now see a new file called `main.pdf`, as well
as some other files that were created during the compilation process. The `main.pdf` file is the
rendered output of your LaTeX document, and you can open it with any PDF viewer to see the result.

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Create a new project, then delete it

See if you can create a new project in Overleaf. Name it "A test project". Then close the project
and reopen the "LaTeX Workshop" project. Finally, delete the "A test project" project.

:::::::::::::::::::::::: solution

## Answer

Creating a new project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- Click the "New Project" button.
- Select "Blank Project" from the drop-down menu.
- Enter in "A test project" as the project name.
- Click "Create".

Closing and reopening the "LaTeX Workshop" project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- Click on the "LaTeX Workshop" project to reopen it.

Deleting the "A test project" project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- Click the "trash can" icon next to the "A test project" project.
- Confirm that you want to delete the project.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Copy your current project, then delete it

See if you can create a copy of your current project "LaTeX Workshop" in Overleaf. Name it "A copy project". Then close the project
and reopen the "LaTeX Workshop" project. Finally, delete the "A test project" project.

:::::::::::::::::::::::: solution

## Answer

Creating a copy project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- For the "LaTeX Workshop" project, navigate to the right column "Actions".
- Click on the first button, the "copy" button, in the "Actions" column for the "LaTeX Workshop" project.
- Enter in "A copy project" as the project name.
- Click "Copy".

Closing and reopening the "LaTeX Workshop" project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- Click on the "LaTeX Workshop" project to reopen it.

Deleting the "A copy project" project:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- Click the "trash can" icon next to the "A copy project" project.
- Confirm that you want to delete the project.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 3: Three ways to download your project as pdf

See if you can download your new project "LaTeX Workshop" in Overleaf as a pdf file.
In your current project "LaTeX Workshop", navigate to the *Preview Pane* on the right.
At the panel bar for the *Preview Pane*, find the button to download a pdf.
If you have figured out the described way for downloading the pdf, try to find two alternative options on how to save your project as a pdf.

:::::::::::::::::::::::: solution

## Answer


Option A as described in the task:

- In "LaTeX Workshop", navigate to the *Preview Pane* on the right.
- At the panel bar for the *Preview Pane*, there is a button with an arrow pointing downwards.
- If you hover over this button, it displays "Download PDF".
- Click on that button and a pdf of your current project "LaTeX Workshop" will be downloaded.

Option B:

- In "LaTeX Workshop", click on the top left icon which contains the Overleaf symbol with the word "Menu".
- The Menu sidebar will open on the left.
- In the first paragraph "Downloads", click on the "pdf" button on the right to download your current project "LaTeX Workshop".

Option C:

- Click the "house" icon on the top menu bar to return to the main Overleaf page.
- In "All projects", you can find your project "LaTeX Workshop".
- Navigate to the column "Actions" on the right side.
- If you hover over the third button, it says "Download PDF".
- Click on this button to download your current project "LaTeX Workshop".

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- We can use Overleaf to edit and render LaTeX documents.
- An Overleaf project can contain many files.

::::::::::::::::::::::::::::::::::::::::::::::::


