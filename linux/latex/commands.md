# Basic Commands

> \section{}

This command is used for a heading, there is also 
`\subsction{}` and `\subsubsection{}`.

> \textbf{}

To make a text bold.

> \emph{}

To make italic text.

> \footnote{}

To make a footnote.

# Lists

There is three different types of lists that you can make

* enumerate
* itemize
* description

Written all with a begin and end command:

```tex
\begin{enumerate}
\item text here.
\end{enumerate}
```

# \newcommand

To make a new command that you can use repeatedly:

```
\newcommand{\bolden}[1]{\emph\,\textbf{#1}}
```

We just use the `\,` to sepreate commands.


