# Template for writing a PhD thesis in Markdown [![Build Status](https://travis-ci.org/tompollard/phd_thesis_markdown.svg?branch=master)](https://travis-ci.org/tompollard/phd_thesis_markdown)  

[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.58490.svg)](http://dx.doi.org/10.5281/zenodo.58490)

This repository provides a framework for writing a PhD thesis in Markdown. I used the template for my PhD submission to University College London (UCL), but it should be straightforward to adapt suit other universities too.

## Citing the template

If you have used this template in your work, please cite the following publication:

> Tom Pollard et al. (2016). Template for writing a PhD thesis in Markdown. Zenodo. http://dx.doi.org/10.5281/zenodo.58490

## Are there any reasons not to use Markdown?

There are some minor annoyances:
- if you haven't worked with Markdown before then you'll find yourself referring to the style-guide fairly often at first.
- it isn't possible to add a short caption to tables ~~and figures~~ ([figures are now fixed](https://github.com/tompollard/phd_thesis_markdown/pull/47), thanks to @martisak). This means that /listoftables includes the long-caption, which probably isn't what you want. If you want to include the list of tables, then you'll need to write it manually.
- the style documents in this framework could be improved. The PDF and HTML (thanks [@ArcoMul](https://github.com/ArcoMul)) outputs are acceptable, but ~~HTML and~~ Word needs work if you plan to output to this format.  
- ~~there is no straightforward way of specifying image size in the markdown right now, though this functionality is coming (see: https://github.com/tompollard/phd_thesis_markdown/issues/15)~~ (Image size can now be specified. Thanks to @rudolfbyker for [highlighting this](https://github.com/tompollard/phd_thesis_markdown/issues/15)).
- ... if there are more, please add them here.

## How do I get started?

1. Install the following software:
    - A text editor, like [Sublime](https://www.sublimetext.com/), which is what you'll use write the thesis.  
    - A LaTeX distribution (for example, [MacTeX](https://tug.org/mactex/) for Mac users).
    - [Pandoc](http://johnmacfarlane.net/pandoc), for converting the Markdown to the output format of your choice.  You may also need to install [Pandoc cite-proc](http://pandoc.org/demo/example19/Extension-citations.html) to create the bibliography.
    - Install @martisak's shortcaption module for Pandoc, with `pip install pandoc-shortcaption`
    - Git, for version control.
2. [Fork the repository](https://github.com/tompollard/phd_thesis_markdown/fork) on Github  
3. Clone the repository onto your local computer (or [download the Zip file](https://github.com/tompollard/phd_thesis_markdown/archive/master.zip)).  
4. Navigate to the directory that contains the Makefile and type "make pdf" (or "make html") at the command line to update the PDF (or HTML) in the output directory.  
**In case of an error** (e.g. `make: *** [pdf] Error 43`) run the following commands:  
    ```
    sudo tlmgr install truncate
    sudo tlmgr install tocloft
    sudo tlmgr install wallpaper
    sudo tlmgr install morefloats
    sudo tlmgr install sectsty
    sudo tlmgr install threeparttable
    sudo tlmgr update l3packages
    sudo tlmgr update l3kernel
    sudo tlmgr update l3experimental
    ```
    
5. Edit the files in the 'source' directory, then goto step 4.  

## What else do I need to know?

Some useful points, in a random order:
- each chapter must finish with at least one blank line, otherwise the header of the following chapter may not be picked up.
- add two spaces at the end of a line to force a line break.
- the template uses [John Macfarlane's Pandoc](http://johnmacfarlane.net/pandoc/README.html) to generate the output documents. Refer to this page for Markdown formatting guidelines.
- PDFs are generated using the LaTeX templates in the style directory. Fonts etc can be changed in the TeX templates.
- To change the citation style, just overwrite ref_format.csl with the new style. Style files can be obtained from [citationstyles.org/](http://citationstyles.org/)
- For fellow web developers, there is a Grunt task file (Gruntfile.js) which can be used to 'watch' the markdown files. By running `$ npm install` and then `$ npm run watch` the PDF and HTML export is done automatically when saving a Markdown file.
- You can automatically reload the HTML page on your browser using LiveReload with the command `$ npm run livereload`. The HTML page will automatically reload when saving a Markdown file after the export is done.

## Word Counting

You can use the [`wc` utility](https://www.freebsd.org/cgi/man.cgi?wc) to perform a word count of the thesis' contents. Simply run `wc -w chapters/*.md` to gather an approximate. Running it on the Markdown sources should omit words generated by pandoc/LaTeX and give a better approximation.
