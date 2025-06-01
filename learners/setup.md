---
title: Setup
---

This workshop will demonstrate how to use [TeX Live](https://tug.org/texlive/) in order to write
and render LaTeX documents. TeX Live is a comprehensive TeX system that includes all of the
necessary tools to compile and render LaTeX documents. It is available for Windows, macOS, and
Linux, and can be installed on your local machine.

## Software Setup

You can find installation instructions for TeX Live on the
[TeX Live website](https://tug.org/texlive/).


### Windows Installation

1. Download the TeX Live installer from the [TeX Live website](https://tug.org/texlive/windows.html).
2. Run the installer and select "Install" from the dialog that appears, then click "Next".
3. Click "Install" to begin the installation process. This will unpack some files, before opening
   a new window called the "Tex Live Installer".
   a. If desired, you can change the installation directory by clicking on the "Change" button.
   b. The default installer will install the full TeX Live distribution, which is recommended for
      most users, however this can take a long time and requires a lot of disk space. If you would
      like to install a smaller subset of TeX Live, you can select "Advanced" to bring up the
      custom installation options. For this workshop, you can customize the Collections to include
      only the "US and UK English" collections, then ensure that the "Install TeXworks front end"
      option is selected.
4. When the installation is complete, you can close the installer windows.
5. Open a command prompt and type `tex --version` to verify that TeX Live is installed correctly.
   You should see the version number of TeX Live printed to the console.
   a. If you did a mimumum installation, you may need to install additional packages. Run
      `tlmgr info latex` to check if the `latex` package is installed. If you see "installed: no",
      you should install it now by running the following command:
      `tlmgr install latex scheme-small collection-latex collection-latexrecommended`.
6. Ensure that everything is working:
   a. Open a command prompt and enter `pdflatex --version` to check that the PDFLaTeX
      compiler is installed correctly. You should see the version number of PDFLaTeX printed to the
      console.
   b. Open TeXworks, which is a simple LaTeX editor that comes with TeX Live and paste the following
      code into a new document:
      ```latex
      \documentclass{article}
      \begin{document}
      Hello, \LaTeX!
      \end{document}
      ```
      Then click on the green "Typeset" button (or press `Ctrl+T`) to compile the document. If you
      see a PDF preview of the document with the text "Hello, LaTeX!" then everything is working
      correctly.