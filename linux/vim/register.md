# numbered Register 

"+num+p = get to the history of yanked or deleted items.

Ex: "1p

# copy to a named Register

We can do that using the following command

"+letter+yank = yank to a specific letter.

Ex: "ayy


Then to use that yanked word we use `"a`, or under
insert mode CTRL+R a.

"%p = get the name of the file 

```
set clipboard=unnamed
```
this allow copying from and out to vim.

```
"_dd
```
delete without saving to register.

```
:register
```

to view all the register.

```
:register 1 a
```

to view register with that letter/number.


```
:put 1 a
```

to paste from register using a number/letter.



