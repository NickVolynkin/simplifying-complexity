---
title: Instructions
permalink: /instructions.html
published: false
---

## Kindle

1. serve_kindle.sh
2. new tab: build_kindle.sh
3. move.sh (moves docnav.mobi file to mobi folder)
4. open Kindle Previewer and select the docnav.mobi file in the mobi_files directory.

details:
- config file is \_config_kindle.yml
- use format: kindle for targeting kindle
- no tables allowed. take images of tables instead
- tocstart.html is the beginning page that lists the chapters
- docnav.ncx is used for the built-in navigation in kindle
- not necessary to have a more robust toc b/c the ncx file provides the nav built-in
- build_pdf.sh runs this:

```
/Users/tomjoht/projects/kindlegen/kindlegen _site/docnav.opf
```

the first is kindlegen, the next is the location of the docnav.opf file

- run move.sh to move this file into /mobi in the regular doc directory
- docnav.opf contains the master content used to build your output
- you can preview in kindle previewer
- to test manually, plug in micro usb cable, then simply drag the .mobi file into documents

there's no need to convert to another ebook format b/c kindle has a reading app on every device aleady.
but if you want to convert to ebook: http://www.online-convert.com/result/0d8a7494-041a-4e88-b71a-b646bc178660

- css: css/kindle.css
- layout: kindle.html

to test on kindle fire:
- plug in with micro usb
- launch android file transfer app (android.com/filetransfer)
- put in books folder
- restart


## PDF
- not really necessary to generate this except if someone wants to print out the entire book
- look into offering a paperback version of the kindle version
- if so, you prob. need to generate the full TOC

- if you run into issues, look at prince-list.txt in the output. make sure all paths are valid. they should all have an absolute URL going to them.
- filter out the swagger demos.
- the PDF frontmatter are served from the pdf_frontmatter folder in \_docs but these paths are hard-coded into the toc page.

1. run ". serve_pdf.sh"
this file uses the \_config_pdf.yml. in this file, two important properties are defined:
baseurl: /Users/tomjoht/projects/learnapidoc/\_site
format: pdf

2. run " . build_pdf.sh"

it builds from the local, so it's not necessary to have serve_pdf running

3. see pdf/docnav.pdf

- no need to swap in images for tables
- format: pdf
- css: assets/css/pdf/printstyles.css
- css: assets/css/pdf/theme-blue.css
- layout: printpdf.html

## Web

1. bundle exec jekyll serve
2. format: web
3. uses the default.html layout
layout: default.html
css: main.css (compiles from sass)
