
# Pandoc assignment kit

## Command

~~~console
$ pandoc in.md  -o out.pdf --pdf-engine=lualatex  -V mainfont="Palatino" -H header.tex
~~~

- `in.md` is the source file
- `-o ...` is the output file (`out.pdf` here)
- `--pdf-engine=lualatex` is the latex plugin
- `-H` is the latex header file (`header.tex` here) that contains latex commands that are prepended to your input file (in.md)

## Latex header file 

~~~tex file
\usepackage{fancyhdr}
\usepackage{lastpage}

\newcommand\hffont{\fontsize{08pt}{08pt}\selectfont}

\pagestyle{fancy}
\fancyhf{}
\lhead{\hffont{Unit 3.7: Assessment for feedback}}
\rhead{\hffont{SBI4U}}
\lfoot{\hffont{Jeffrey Shevlen 99419720}}
\fancyfoot[R]{\hffont{\thepage\ of \pageref{LastPage}}}
\renewcommand{\headrulewidth}{0.3pt}
\renewcommand{\footrulewidth}{0.3pt}
~~~

- `\usepackage{...}` loads latex relevent packages
- `newcommand` is a user/me generated thing called `hffort` where I specify the header and fooder size
- no idea what `pagestyle{fancy}`, `fancyhf{}` do
- left head, right foot are `\lhead{}` and `\rfoot{}`
- `\fancyfoot[R]{...}` is like `\rfoot`, the `[R]` for right
- `\renewcommand` is a bit of a mystery to me
- `\headrulewidth{}` sets header line width

## Markdown header

You don't need to add anything in Obsidian anyway.  The `-H ...` pandoc arg is enough.

You may see something like this on the web.  

~~~
---
output:
  pdf_document:
    includes:
      in-header: header.tex
---
~~~

Didn't work for me in this context.

## References

- `\newcommand` comes by way of [https://latex-tutorial.com/changing-font-size/](https://latex-tutorial.com/changing-font-size/)
- the *fancyheader* manual [http://distrib-coffee.ipsl.jussieu.fr/pub/mirrors/ctan/macros/latex/contrib/fancyhdr/fancyhdr.pdf](http://distrib-coffee.ipsl.jussieu.fr/pub/mirrors/ctan/macros/latex/contrib/fancyhdr/fancyhdr.pdf)
- markdown header reference [https://stackoverflow.com/a/40992929](https://stackoverflow.com/a/40992929)
