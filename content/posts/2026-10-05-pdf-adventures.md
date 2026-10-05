---
title: PDF adventures
date: 2026-10-05T11:52:18+08:00
---

My [PDF]({{< ref "2021-05-24-pdftk-combinining-pdfs-using-pdftk" >}}) [adventures]({{< ref "2020-06-24-extracting-pdf-page-ranges-using-pdftk" >}}) continue.

Like [Chloé-Agathe](https://cazencott.info/index.php/post/2015/04/30/Numbering-PDF-Pages), I too needed to create a large (30+ pages), single PDF file out of a combination of multiple other files, and page numbers -- i.e., re-numbering -- is really helpful. I already know of `pdftk`, and from her blog post -- and others, I learned that this was all still possible 11 years later on macOS 27.0.1.

Step 1: Combine the 1st two pages of `foo.bar`, and the 9th, 10th pages of `bar.pdf` as `baz.pdf`:

```text
pdftk A=foo.pdf B=bar.pdf cat A1-2 B9-10 output baz.pdf
```

After this step, `baz.pdf` consists of 4 pages to be re-numbered.

Note that I tried to replicate Steps 2/3 in Google Docs, and it didn't work, so I had to install LaTeX...

Step 2: Define a LaTeX document `numbers.tex`:

```text
 \documentclass[12pt,a4paper]{article}
 \usepackage{multido}
 \usepackage[hmargin=.8cm,vmargin=1.5cm,nohead,nofoot]{geometry}
 \begin{document}
 \multido{}{4}{\vphantom{x}\newpage}
 \end{document}
```

(4 is the total number of pages.)

Step 3: Generate `numbers.pdf`:

```text
pdflatex numbers.tex
```

Step 4: Combine the PDFs as `qux.pdf`:

```text
pdftk baz.pdf multistamp numbers.pdf output qux.pdf
```

Optional Step 5: Reduce filesize. My PDF was too large (13+ Mo). I used Ghostscript to reduce it by ~84%:

```text
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dBATCH -dQUIET -sOutputFile=quux.pdf qux.pdf
```

Happy PDF-ing!
