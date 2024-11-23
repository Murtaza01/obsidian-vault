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


