---
layout: post
title:  "Using Makefile for LaTeX"
date:   2019-10-27 18:00:00
categories: wiki
tags: [latex]
lang: en
ref: latex-makefile
description: Automate your report workflow using Makefile
img: https://images.unsplash.com/photo-1518331334341-85b0b2f4781a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
img-ref: https://unsplash.com/photos/dDppsuM_UpE
---

Makefile are not just for C projects. You can virtualy use for automate almost any workflow. Due to its [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming) style, it enables depence management between generated files from several diferent sources. You can just put the command to generate the output file and the input files needed. Everything else it solved for you. So I decided to use it to automate my report generation workflow using LaTeX. 

# LaTeX Compilation

The basic idea is simple. Fist set a makefile for compilation. I use the following template. Then you can just open a terminal and use **make** to compile everything. The best side of this is that the compiler will only be called when the source files changed or the output file is missing.

<script src="https://gist.github.com/akafael/6283346.js"></script>

Then you can integrate it with anything that you can call from terminal. Ex. You can use python inside your reports, let pandoc generate the .tex file from a markdown source, generate charts using gnuplot, ...  Lets try for instance to integrate an odd depence with the lastest image version from media wiki:


We can just add the new recipe
```
simulation.jpg:
	wget -c -N --output-document==simulation.jpg https://upload.wikimedia.org/wikipedia/commons/6/67/Curved_Heatsink_Image.jpg

```

Then add the dependence to the report recipe:

```
# Generate PDF output
$(NAME).pdf: $(NAME).tex simulation.jpg
	$(CC) $(CCFLAGS) $< &&	$(CC) $< && $(CC) $< &&\
	xdg-open $(@)&
```

Simple as that! Now everytime you try to compile the report the makefile will download the image from media wiki first then run the pdflatex. This enable a complete automated pipeline for your complete workflow.

## Go Bewond

 * https://sylvaindeville.net/2015/01/04/the-automated-academic/
