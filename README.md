# PhD Thesis template (English) for ITMO University

This is not an official $\LaTeX$ template. This template is based on [toftul/itmo-phd-thesis-template-en](https://github.com/toftul/itmo-phd-thesis-template-en) and [ITMO Шаблон LATEX для диссертации](https://dissovet.itmo.ru/index.php?main=110 )

In addition, there is a repository of thesis templates for Russian [ngodanghien/ITMO-PhD-Template-RU](https://github.com/ngodanghien/ITMO-PhD-Template-RU)

There is an official template on the [ITMO Dissertation Council](https://dissovet.itmo.ru/index.php?main=110) website, which is a fork of the well-known template [AndreyAkinshin/Russian-Phd-LaTeX-Dissertation-Template](https://github.com/AndreyAkinshin/Russian-Phd-LaTeX-Dissertation-Template).

## Why does this exist
The above templates are configured with many things, for many platforms, so they are quite complicated to fully understand. In addition, there are some packages that are outdated and currently (2024) will report an error, for example on [Overleaf](https://www.overleaf.com/).

This form has been rewritten more neatly and fully complies with ITMO's regulations on writing doctoral dissertations, such as: paper size, margins, images, tables, citations, references, table of contents. , ...
 
## What has changed

1. Take advantage of all the strengths found in [toftul/itmo-phd-thesis-template-en](https://github.com/toftul/itmo-phd-thesis-template-en)
2. Continue using the file `biblio/own.bib` and automatically calculate the number of articles and automatically print them out in the appropriate locations. Check everything in `biblio/author` and `biblio/counter`. Citations still comply with style [GOST 7.0.100-2018](https://ctan.org/pkg/biblatex-gost?lang=en).
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
    > biber -v
    biber version: 2.19
    ```

    Note that the `biber version` must match the `biblatex version`. The simple way is to update both versions to the latest.

2. `MikTex` is much lighter than `TexLive`, installation time is also very fast. However, when using `\usepackage[T1,T2A]{fontenc} `, the Russian font when rendering the PDF file is blurry and not sharp. Because it cannot call modern fonts. `TexLive` in `Windows` is installed with `fonts-extra`. If `texlive-full` version is not installed in Linux, you need to install it via the command:
    ```cmd
    > sudo apt install textlive-fonts-extra
    ```
3. Citing references using the `biblatex` package with `backend=biber` requires converting the Bibliography Tool to `biber`.
The file contains references added in the following way: `\addbibresource{biblio/references.bib}`
4. Maybe the numbering and printing of references is incorrect, please do: `Tools/Clean Auxiliary Files ...` then rebuild. Or you can press `F8` (rebuild `*.bib` only, **Attention** to executing the command on the TEX file) and press `F5` (rebuild `*.TEX`).
5. Reference style: При наличии 4-х и более имён авторов, редакторов, переводчиков и пр. ГОСТ позволяет на выбор либо выводить их полный список, либо сокращать его до одного имени с добавлением [et al.], [и др.] и пр.
    > see more: [GOST 7.0.100-2018](https://ctan.math.illinois.edu/macros/latex/contrib/biblatex-contrib/biblatex-gost/doc/biblatex-gost.pdf), page 20.

    ```tex
    \usepackage [
        ...
        style=gost-numeric, %GOST 7.0.100-2018
        giveninits=true, % = true -> print full authors, don't use [et al.]
        maxbibnames=99,
        movenames=false, % = false -> put the author's name first.
    ]{biblatex}
    ```
    In `*.bib` file, if @article has 4 authors, it will look like `[1]`, otherwise if it has less than 4, it will look like `[2]`. It looks very messy and inconsistent. so I will put all authors first and write all the authors (do not use et al. - GOST allows this)
    > `[1]` Adaptive control of LTV systems with uncertain periodic coefficients / D. Gerasimov [et al.] // ...
    >
    > `[2]` Gerasimov D., Hien N., Nikiforov V. Direct Adaptive Control of LTV Discretetime Systems with Uncertain Periodic Coefficients //

    **After all, it will be like this.** I like it :) And it is similar rules to writing the article (Оформление списка литературы) of Институт проблем управления им . В.А. Трапезникова РАН.
    > _*Gerasimov D., Popov A., Hien N., Nikiforov V.*_ Adaptive control of LTV systems with uncertain periodic coefficients // IFAC-PapersOnLine. — 2023. —
    Vol. 56, no. 2. — P. 9185–9190. — URL: [https : / / doi . org / 10 . 1016 / j .ifacol.2023.10.160.](https://doi.org/10.1016/j.ifacol.2023.10.160)

6. In the file `biblio/own.bib`, if you only care about which article is {scopus/wos, vak}, add the line `keywords = {scopus}`, or `keywords = {vak}`. As for other articles that are not indexed above, you don't need to pay attention to them. They will be automatically printed in section: other articles.
    ```bib
    @article{Gerasimov2023a,
        keywords = {scopus, wos},
        author = {Gerasimov, D and Popov, A and Hien, N.D. and Nikiforov, V},
        journal = {IFAC-PapersOnLine},
        issue = {2},
        number = {2},
        pages = {9185--9190}, 
        title = {Adaptive control of LTV systems with uncertain periodic coefficients},
        url = {https://doi.org/10.1016/j.ifacol.2023.10.160},
        volume = {56},
        year = {2023}
    }
    ``` 