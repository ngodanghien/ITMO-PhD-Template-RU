# Шаблон кандидатской диссертации в Университете ИТМО

This is not an official $\LaTeX$ template. This template is based on [toftul/itmo-phd-thesis-template-ru](https://github.com/toftul/itmo-phd-thesis-template-ru) and [ITMO Шаблон LATEX для диссертации](https://dissovet.itmo.ru/index.php?main=110 )

In addition, there is a repository of thesis templates for English [ngodanghien/ITMO-PhD-Template-EN](https://github.com/ngodanghien/ITMO-PhD-Template-EN)

There is an official template on the [ITMO Dissertation Council](https://dissovet.itmo.ru/index.php?main=110) website, which is a fork of the well-known template [AndreyAkinshin/Russian-Phd-LaTeX-Dissertation-Template](https://github.com/AndreyAkinshin/Russian-Phd-LaTeX-Dissertation-Template).

## Why does this exist
The above templates are configured with many things, for many platforms, so they are quite complicated to fully understand. In addition, there are some packages that are outdated and currently (2024) will report an error, for example on [Overleaf](https://www.overleaf.com/).

This form has been rewritten more neatly and fully complies with ITMO's regulations on writing doctoral dissertations, such as: paper size, margins, images, tables, citations, references, table of contents. , ...
 
## What has changed

1. Take advantage of all the strengths found in [toftul/itmo-phd-thesis-template-en](https://github.com/toftul/itmo-phd-thesis-template-en)
2. Remove the file `biblio/own.bib`. I think I should design in my own style to highlight my work (no need to be too strict according to `GOST 7.0.100`). 
Create your own style at `biblio/author`
3. Use only the necessary packages, leaving out the complicated stuff. Move your settings to the corresponding packages for easy management and future updates.

## How to use

### Online compilation
* Download the `zip` of this repository;
* Upload it to [Overleaf](https://www.overleaf.com/) (tested March 2024).
### Offline compilation
Recommended uses: [TexStudio](https://www.texstudio.org/) and [TexLive](https://tug.org/texlive/)
- Make sure you have `biber` installed
- Change the bibliography engine from `bibtex` to `biber`

## Notes
1. Check biber is installed or not
    ```cmd
    > biber --version
    biber version: 2.19
    ```
    Note that the `biber version` must match the `biblatex version`. The simple way is to update both versions to the latest.

2. `MikTex` is much lighter than `TexLive`, installation time is also very fast. However, when using `\usepackage[T1,T2A]{fontenc} `, the Russian font when rendering the PDF file is blurry and not sharp. Because it cannot call modern fonts. `TexLive` in `Windows` is installed with `fonts-extra`. If `texlive-full` version is not installed in Linux, you need to install it via the command:
    ```cmd
    > sudo apt install textlive-fonts-extra
    ```
3. Citing references using the `biblatex` package with `backend=biber` requires converting the Bibliography Tool to `biber`.
The file contains references added in the following way: `\addbibresource{biblio/references.bib}`