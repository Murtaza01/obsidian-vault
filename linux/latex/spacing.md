# Vertical Space

## Line breaks

There is different ways to add line breaks, we can use:

### `\\`

this will sometimes cause an error of fill box, it
will force the line break to go over the hbox (beyond the box
of text).

We can add how much break we can have using an argument:

```tex
Text\\[2cm]
Another text 2cm far
```

### \smallbreak,\medbreak,\bigbreak

These works better by not creating an error, although they
are limited.

# Horizontal Space

## Line Break

We can add that with `\,`

# hspace{num}

This is the better way if we want to control the spacing


# Margins 

We can add magins to our document using the geometry package:

```tex
\usepackge[vmargins=1in,hmargins=1in]{geometry}


```

vmargins = top and bottom
hmargins = left and right

Or we can define it separately:

```tex
\usepackge{geometry}
\geometry{top=0.6in}
```


