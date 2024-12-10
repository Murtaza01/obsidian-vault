# insert 

to insert in new line or before we use:

o = insert after line
O = instert before line

A = insert mode in the end of the line.
s = delete charactor under cursor and enter insert mode.

10o = will insert the same text to the next 10 lines.

This is only possible when you exist with Esc or Ctrl+[ 

> Ctrl+w

Insert mode you can delete before the cursor words.

> Ctrl+u

for deleting a whole line before the cursor 

## Text Objects 

Text objects are a way to group text, they include "",'',(),<>,{}...

We can target them and do an operation to them using:

Operator + i/a + Text Object.

i = inner (inside parentheses).
a = outer (parentheses included).

> ci)

Cut text inside parentheses and enter insert mode.

> di(

Delete text inside parentheses.

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

# sub mode

> Ctrl+x

you can enter sub mode in insert mode using:

> Ctrl+p

You can autocomplete with sub mode.

We can enter normal mode while in insert mode with:

> Ctrl+o

This will only allow one command.
