# Commands and arguments

> {}

In latex the curly braces are a way to express mandatory
arguments to the commands.

> \

Every command starts with the backward slash sign.

> []

Braces are uses to express optional arguments.

> \\

The two backward slashes are used to give space, you should
only use it in very speical cases.

```tex
this is normal text\\and this is another
```

> \medbreak , \smallbreak , \bigbreak

Used to make line breaks, we should use this instead of `\\` 

> %\usepackage

To comment a command we use the `%`

# Body

Every document has a body, and to begin a body we need the 
following command:

```tex
\begin{document}
\end{document}
```

> get rid of the indition in the begining of the paragrpahs

By default latex indent all words in the beginning of the
paragraphs, we can change that by using this package:

> \usepackage[parfill]{parskip}

Or we can use this on one line:

> \noindent

# Space

We can add space either horizontal or vertical using these
commands:

```tex
some text \hspace{1cm} other text

\vspace{10cm}

other other text.
```

# Text Shape

We can change the font using three commands

> \texttt{text}

this will change the font to a `monospaced` font

> \textsf{text}

this will change the font to `sans serif`.

>\textrm{text}

this will change the font to `roman`.

> \textsc{text}

will make the text all caps the text.

> \textit{text}

italic

> \textbf{text}

bold

# Environment Group

We can group multiple text to an enviroment so that all
text inside will have an effect, for example we can
italize text in an environment.

```tex
{\itshape

some text

and its italic all the way

}
```

# Paragraph

Every paragraph ends with a space, we can either force 
space using `\\` or use normal space, we can end paragraphs
using:

> \par

# Using lualatex engine

Lualatex is the modren engine for latex, it supports using multiple fonts
from your local device, it has many features, to use it we first need
to add this line to our config located in `~\.latexmkrc`

```
$pdf_mode = 4; ## sets lualatex to default engine.
$dvi_mode = 0;
$postscript_mode = 0;
```

# maketitle

You can make a title inside your document by using the `\maketitle` which
goes only inside the document, however you need 3 **mandatory** commands:

```
\title{}
\author{}
\date{}
```

If date is not set the current date will be set.

> \usepackage{xcolor}

To color our text, the command takes two argument one 
for the color and the other for the text.

```
this is normal colored text
\textcolor{blue}{and this is blue}
```

# \newcommand

To make a new command that you can use repeatedly:

```
\newcommand{\bolden}[1]{\emph\,\textbf{#1}}
```

We just use the `\,` to sepreate commands.


