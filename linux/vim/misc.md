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
