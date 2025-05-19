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

- Demonstrate how to create a new project in Overleaf.
- Become familiar with the Overleaf interface.

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

## Our first Overleaf Project

There are several ways to write LaTeX documents, but we'll be using Overleaf, a cloud-based LaTeX
editor. This has the advantage of being accessible from any computer with an internet connection,
without the need to install any additional software. As part of the preparation for this workshop,
you should have registered for an account on Overleaf.

We'll start by creating a new, 'Blank', project in Overleaf by clicking on the large green button
that says 'New Project' in the top left corner of the screen. This will open a drop-down menu with
a number of options. We'll select 'Blank Project' from this menu. Name the project 'LaTeX Workshop'
and click 'Create'.

![The Overleaf Main Page](fig/01-introduction/overleaf-main-page.PNG){alt='The Overleaf main page.'}

## The Overleaf Interface
Once the project is created, you'll see that it isn't quite blank. There are four main panels when
you open a new project in Overleaf:

- 1. The *File Navigator* on the top left, which shows all of the files in your project.
- 2. The *File Outline* on the bottom left, which shows the structure of the current file.
- 3. The *Text Editor* in the middle, where you can write your LaTeX code.
- 4. The *Preview Pane* on the right, which shows a preview of the compiled document.

![The Overleaf Interface](fig/01-introduction/overleaf-interface.PNG){alt='The Overleaf interface.'}

You'll notice that our project isn't quite blank, as we have a file called `main.tex` open in the
text editor with some LaTeX code already written. This is a basic LaTeX document, with some of the
minimum requirements for a LaTeX document.

## The Main Menu

When we want to switch projects or create a new one, we can use the main menu at the top of the
screen, which is indicated by a small "house" icon. Clicking on this icon will take us back to the
main landing page for overleaf, where we initially created our project.

We can see now in the section "All Projects" that our new project, "LaTeX Workshop", is listed
there, that we are the owner, and that it was just recently modified. We can click on the project
name to open it again.

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


