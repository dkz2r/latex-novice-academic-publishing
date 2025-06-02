---
title: Setup
---

This workshop will demonstrate how to use [TeX Live](https://tug.org/texlive/) in order to write
and render LaTeX documents. TeX Live is a comprehensive TeX system that includes all of the
necessary tools to compile and render LaTeX documents. It is available for Windows, macOS, and
Linux, and can be installed on your local machine.

## Software Setup

You can find installation instructions for TeX Live on the
[TeX Live website](https://tug.org/texlive/). We include a brief overview of the installation
on this page for convenience, but we recommend that you refer to the official documentation for
the most up-to-date instructions.

## Windows Installation

Visit the [TeX Live website](https://tug.org/texlive/windows.html) for the latest version of the
TeX Live installer for Windows. Click the link to "install-tl-windows.exe."

The full TeX Live installation is recommended for most users, as it includes all of the necessary
packages and tools to compile and render LaTeX documents. However, if you have limited disk space
or a slow internet connection, you can install a minimal version of TeX Live that includes only the
commonly used packages.

::: tab

### Windows Installation (Full)

Run the installer and select "Install" from the dialog that appears, then click "Next".

Click "Install" to begin the installation process. This will unpack some files, before opening a new window called the "Tex Live Installer".

*If desired, you can change the installation directory by clicking on the "Change" button.*

When the installation is complete, you can close the installer windows.

### Windows Installation (Minimal)

Run the installer and select "Install" from the dialog that appears, then click "Next".

Click "Install" to begin the installation process. This will unpack some files, before opening a new window called the "Tex Live Installer".

*If desired, you can change the installation directory by clicking on the "Change" button.*

Select "Advanced" to bring up the custom installation options.

Under "Selection", select "Scheme: small" to install a minimal set of packages.

Ensure that the "Install TeXworks front end" option is selected.

When the installation is complete, you can close the installer windows.

:::

## macOS Installation

Visit the [MaxTeX Download Page](https://tug.org/mactex/mactex-download.html) for the latest
version of the MacTeX installer for macOS. Click the link to download the "MacTeX.pkg" file.

Double click the downloaded "MacTeX.pkg" file to start the installation process. Follow the
prompts to complete the installation. The default installation options are recommended for most
users.

Open a terminal and type `tex --version` to verify that TeX Live is installed correctly. You
should see the version number of TeX Live printed to the console.

Open a terminal and enter `pdflatex --version` to check that the PDFLaTeX compiler is installed
correctly. You should see the version number of PDFLaTeX printed to the console.

## Unix/Linux Installation

```bash
cd /tmp
wget https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
zcat < install-tl-unx.tar.gz | tar xf -
cd install-tl-2*
perl ./install-tl --no-interaction --scheme=small
```

This process will download and install TeX Live in the `/usr/local/texlive` directory by default.
Note that the download may take several hours.

Finally, prepend `/usr/local/texlive/2023/bin/x86_64-linux` to your `PATH` environment variable in
order to use the TeX Live binaries from the command line. You can do this by adding the following
line to your `~/.bashrc` or `~/.bash_profile` file:

```bash
export PATH="/usr/local/texlive/2023/bin/x86_64-linux:$PATH"
```

## Verify Installation

Open a command prompt or terminal and type `tex --version` to verify that TeX Live is installed correctly.  You should see the version number of TeX Live printed to the console.

Open a command prompt or terminal and enter `pdflatex --version` to check that the PDFLaTeX compiler is installed correctly. You should see the version number of PDFLaTeX printed to the console.

::: tab

### TeXworks

Open TeXworks, which is a simple LaTeX editor that comes with TeX Live and paste the following code into a new document:

```latex
\documentclass{article}
\begin{document}
Hello, \LaTeX!
\end{document}
```

Then click on the green "Typeset" button (or press `Ctrl+T`) to compile the document. If you see a PDF preview of the document with the text "Hello, LaTeX!" then everything is working correctly.

:::
