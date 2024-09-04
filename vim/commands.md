
# commands

:h for help you can also chain it with something
:h write-quit

you can use `TAB` for vim to suggest you things after the h

:wq to quit and save
:conf q to quit with confieration of changes
:qall == to quit all buffers 
:wqall == to quit and save all buffers
:qall! == to quit all buffers without saving

> :set path

we can use that to set a current working diractory to our path so that we can navigate through our project with :find command easily instead of giving a full path to vim everytime we want to open a file.

```vim
:set path+=src/components
```


