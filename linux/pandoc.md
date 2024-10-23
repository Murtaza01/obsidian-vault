# pandoc

a tool that can convert file types, such as pdf epub and md.

it needs lateX as a dependences [tex_live](https://wiki.archlinux.org/title/TeX_Live) in order to work.

#### convert md to pdf

``` zsh
pandoc MANUAL.md -o example13.pdf
```

#### Add title 

in order to add title and author inside the pdf we put 
title and author inside three **dashes** in our md file.



>title: Book.
>
>author: Bob.

#### Change size

possible sizes: (8pt, 9pt, 10pt, 11pt, 12pt, 14pt, 17pt, 20pt)

>documentclass: extarticle.
>
>fontsize: 14pt.

#### Change margin

in order to change the margin inside the pdf we use:

```zsh
pandoc file.md -V geometry:margin=1in -o file.pdf
```

Or use the [yaml headers](https://zsmith27.github.io/rmarkdown_crash-course/lesson-4-yaml-headers.html).

>geometry: margin=3cm
