/ = search for text
? = search backwards

'*' = search the text under cursor
'#' = search text under cursor backwards

Note: they are in quotes because its markdown.

f = search for letter

we can continue search for letters using `;`

```
/[1-5]
```

to search number between 1 and 5.

```
:s/oldword/newword
```

> substitution (find and replace)

```vim
:%s/old/new
```

this will do substitution for all the file.

s stands for substitution.

```
:s/\<./\U&/g
```

to capitalize a whole line.

```vim
/\vhello|hola
```

to search for either hello or hola.
