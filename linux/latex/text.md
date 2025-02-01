> \section{}

This command is used for a heading, there is also 
`\subsction{}` and `\subsubsection{}`.

> \textbf{}

To make a text bold.

> \emph{}

To make italic text.

> \footnote{}

To make a footnote.


# Remove indention

We can remove indention using:

```tex
\setlength\parindent{0pt}
```

# Size

To control text size we use

* \large
* \Large
* \huge

Note that these needs to be before the text:

```tex
\textbf{\LARGE{Title}}
% not
\Large{\textbf{title}} % this is wrong
```

# underline

Because the default `\underline` does not wrap and does not
allow force wrap, we can use an alternative:

```tex
\usepackage{lua-ul}
\underLine{...}
```

With Captial L so that it won't clash with the default.


# Verse Package

We can use verse Package to add poems in our document
it makes things easier and add semantics:

```tex
\usepackege{verse}

\poemtitle{Sonnet 116}
\settowidth{\versewidth}{Let me not to the marriage of true minds}
\begin{verse}[\versewidth]
hich alters when it alteration finds,\\ 
Or bends with the remover to remove.
\end{verse}
```

Where `\settowwidth{\versewidth}` Is the width that will be assigned in our poem
using the `[]` next to the verse environment.

