# Noraj's OSCP Report Template in Markdown with code block highlight
It's noraj's modified templates but with support for code block highlighting

## Requirements
First get Stack with

`curl -sSL https://get.haskellstack.org/ | sh`

Install the other requirements

`apt install texlive-latex-recommended texlive-fonts-extra texlive-latex-extra pandoc p7zip-full`

Build Pandoc-Emphasize from source

```
git clone https://github.com/owickstrom/pandoc-emphasize-code
cd pandoc-emphasize-code
stack setup
stack install
```

Add `/root/.local/bin` to your PATH

## Hightlight Config

On your MD file add the following headers
```
header-includes:
  - \usepackage{listings}
  - \lstset{basicstyle=\ttfamily}
  - \newcommand{\CodeEmphasis}[1]{\textcolor{red}{\textit{#1}}}
  - \newcommand{\CodeEmphasisLine}[1]{\textcolor{red}{\textit{#1}}}
```

Then you can proceed to highlight your code blocks

```
```{.haskell emphasize=2-2,4:6-4:9}
I am pasting a lot of code
but this line is the one
that maybe seems important
also THIS part only is good

The rest is ok```

```

The `2-2` will cause the whole 2nd line to be highlighted

The `4:6-4:9` will cause the 4th line to be highlighted from the 6th character until the 9th




## Report generation

Same old way, just add `--filter pandoc-emphasize-code` in some point

```

pandoc src/OSCP-exam-report-template_whoisflynn_v3.2.md \
-o output/OSCP-OS-XXXXX-Exam-Report.pdf \
--from markdown+yaml_metadata_block+raw_html \
--template eisvogel \
--table-of-contents \
--toc-depth 6 \
--number-sections \
--top-level-division=chapter \
--highlight-style breezedark \
--filter pandoc-emphasize-code

```
