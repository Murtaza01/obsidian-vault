To create a table we use the array package

> \usepackage{array}

Then we use the `tabular` environment:

```
\begin{tabular}{cc}
Animals & Humans\\
Dog & Jack\\
\end{tabular}
```

`\\` = represent a new row
`&` = represent a new column
`{cc}` = Mandatory argument controls position of the column

# Position

We can put different positions possible arguments 
are (l,r,c,p).

> \begin{tabular}{position}

We can use number and a string to repeat the position of
the column.

> {num}{string}

```
\begin{tabular}{*{3}{c}}
```

# Lines

We use the booktabs package instead of regular lines

> \usepackage{booktabs}

There is few lines you can chose

> \toprule
> \midrule 
> \bottomrule

Where midrule is a bit thiner than the rest.

We can also add space in our rows using:

> \addlinespace


# merge cells

We can merge two cells togther using:

> \muticolumn{num of cells}{position}{contant}

We can also use this as a trick to center on cell

```tex
\begin{tabular}{*{3}{l}}
Animals & \multicolumn{1}{c}{Plants} & Humans\\
Dog & Flower & Jack\\
\end{tabular}
```

Here Plants  is centered where Humans and Animals 
are left aligned.


