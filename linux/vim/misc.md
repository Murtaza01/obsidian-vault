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

# Uppercase/Lowercase

We can use the gU/u operator:

guw = lowercase the word.
gU$ = uppercase the rest of the line.
gUl = uppercase current letter
~ = to toggle between cases.

# Using Mark

We can mark a line using:
```vim
m$letter
```
to go to the marked line:
```vim
'$letter
```

# copy to register

"ay$ = copies the whole line to register

Note that a could be any letter.

Then in insert mode:

Ctrl+R $letter = paste the copied line

# write a external command to a file

We can do that using double Exclamation mark `!!` while in **normal mode**.

>!!pwd

would write the current directory in the file.

# dot command

We can repeat actions using the `.` command.

# Global command

The global command is designed to do `:` commands to your file

for example you can delete a word using:

```
:g/consloe/d
```

g = line
console = the word that you want to target
d = delete

This command will delete all lines with the world console

```
:g/word/m $
```

This command will move all the lines with the containing words
to the end of the file, you can use `t` instead of `m` to copy.

# tabs 

you can open a new tab using:

:tabnew filename

to exit

:tabclose


you can naivagate through tabs using:

:tabnext or gt
:tabpervious or gT
3gt === go to 3rd tab 

# windows

to open mulitple windows we can use:

:split filename

:vsplit filename == opens virtically

we can close a window by using:

:quit
or 
ctrl-w + c 

to switch between windows if we split them we can use:

ctrl-w k == upper window
ctrl-w j == lower window
ctrl-w h == left window

> ctrl-w o

closes all other windows and keep current.

# Views 

We can save our folds and local settings in a particular file
using a view

> mkview

To create a new view.

> loadview

To load a view with.

> set viewoptions?

To see what is saved in the view with.

you can save different views and load different ones

> mkview 1

> loadview 1 

You can automate this process with these commands

```
autocmd BufWinLeave *.txt mkview
```

To mkview before leaving the buffer.

```
autocmd BufWinEnter *.txt silent loadview
```

To loadview when you enter a buffer.

# viminfo

Vim saves all the registers and other stuff in viminfo by 
default, we can create multiple viminfo for use cases.

> 1+Ctrl+g 

to display full path of the current file

