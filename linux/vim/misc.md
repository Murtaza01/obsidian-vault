# Operator and motions

Similar to English grammar, vim has a similar structure:

Verbs + Nouns => Phrase

Operator + Motions => Action

> Operator 

Operator in vim are things that do stuff, for example:

y = yank text.
d = cut text.
c = cut text and enter insert mode.

> Motions

Those control how you move and navigate:

$ = end of the line
{ = jump to next paragraph

you can combine Operator and Motions:

y$ = yank from cursor to end of the line.
d{ = cut paragraph.

# Text Objects 

Text objects are a way to group text, they include "",'',(),<>,{}...

We can target them and do an operation to them using:

Operator + i/a + Text Object.

i = inner (inside parentheses).
a = outer (parentheses included).

ci) = cut text inside parentheses and enter insert mode.

Note_1:The same applies for [],{},"",'',``

Note_2: we can use this command in the same line where the parentheses exist
it will just jump to the place of the parentheses.

### dat/dit

To do operations on html elements:

```html
<h1>header<h1>
```

dit = cut inside the element.
dat = cut the whole element.

# Uppercase/Lowercase

We can use the gU/u operator:

guw = lowercase the word.
gU$ = uppercase the rest of the line.
gUl = uppercase current letter

# num%

we can go to different places of our current window using:

50% == goes to the middle.

# Window Jumps

H = jumps to top of current window
L = jumps to bottom of current window

Ctrl+d = jumps some lines (not sure how many)
Ctrl+u = jumps backwards.

[[ == goes to the next section (h1 in Markdown).

# search

/ = search for text
? = search backwards

'*' = search the text under cursor
'#' = search text under cursor backwards

Note: they are in quotes because its markdown.

f = search for letter

we can continue search for letters using `;`

# Using Mark

We can mark a line using:
```vim
m$letter
```
to go to the marked line:
```vim
'$letter
```

# insert

A = insert mode in the end of the line.
s = delete charactor under cursor and enter insert mode.

10o = will insert the same text to the next 10 lines.

This is only possible when you exist with Esc or Ctrl+[ 

# mapping

We can map the Esc key using:

```vim
inoremap jj <Esc>
```

# copy to register

"ay$ = copies the whole line to register

Note that a could be any letter.

Then in insert mode:

Ctrl+R $letter = paste the copied line

# sub mode

you can enter sub mode in insert mode using:

Ctrl+x

### autocomplete

You can autocomplete with sub mode using:

Ctrl+p

# execting terminal command

We can do that using double Exclamation mark `!!` while in normal mode.

for example:

!!pwd = would print the current directory

# sub-normal mode

We can enter normal mode while in insert mode with:

> Ctrl+o

This will only allow one command.

# dot command

We can repeat actions using the `.` command.


