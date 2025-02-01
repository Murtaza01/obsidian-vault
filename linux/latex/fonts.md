We can either use babel or polyglossia for fonts and other 
languages.

# Multiple Fonts

To use multiple fonts:

```tex
\usepackage{polyglossia}

\setmainfont{Philosopher}
\newfontfamily\fontpar{BespokeSerif}

{\fontpar
...
}

```

Where the main font is the default for the document
and the new font would need to wrap all the text.

When using bold with fonts, make sure you have the bold font
of that specific font.

# Multiple Languages

To use multiple fonts we:

```tex
\usepackage{polyglossia}

\setotherlanguage{arabic}
\newfontfamily\arabicfont[Script=Arabic, Scale=1.2]{Amiri}

\begin{otherlanguage}{arabic}
Arabic text
\end{otherlanguage}
```

We need to set the script so that our environment can 
recognize the language set in curly braces.

# Phonemes

We can add Phonemes transcription using:

```tex
\usepackage{tipa}

\textipa{A, N} % these will render as phonemes, see doc for chart.
```


# Symbols

We can use symbols in our documents:

```tex
$\Rightarrow$
```

We use $ because its a math symbol and only works 
in math environment.


