# Offensive Security Exam Report Template in Markdown
It's noraj's modified templates but with support for code block highlighting

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
