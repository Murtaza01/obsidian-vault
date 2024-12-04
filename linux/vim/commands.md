# commands

:h for help you can also chain it with something
:h write-quit

you can use `TAB` for vim to suggest you things after the h

:wq to quit and save
:conf q to quit with conformation of changes
:qall == to quit all buffers 
:wqall == to quit and save all buffers
:qall! == to quit all buffers without saving

> :set path

we can use that to set a current working directory to our path so that we can navigate through our project with :find command easily instead of giving a full path to vim everytime we want to open a file.

```vim
:set path+=src/components
```

# using inv to toggle commands

we can use the keyword inv infornt of a boolean command that will function
as a toggle, its useful for keymaps for example this:

```vim
:set invspell
```

this will toggle on and off spell check

# :w 

we can excute a command using the :w for example with node:

```
:w !node
```

this will excute a command on the whole current buffer using node.

```
:37w !node
```

this will execute a command only on the 37 line of the current buffer.

# execute a command

we can easily execute any command using this synatx

```
:!ls 
```

will print us the list of files inside vim.

# Folds

we can fold a text or a paragraph using:

```
zfj
```

this will fold two lines

```
zf10j
```

ten lines below

we can open and close the folds

```
zo
zc
```


