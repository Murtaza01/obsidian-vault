To ignore case while searching.

```vim
set ignorecase
```

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

# mapping

We can map the Esc key using:

```vim
inoremap jj <Esc>
```

