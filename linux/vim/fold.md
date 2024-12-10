We can fold text using `zf`

> zfj

this will fold a line below.

> zo

To open a fold

> zc 

To close a fold

> zfG

To fold to the end of the file.

> zM

close all folds.

> zR 

open all folds.

# make folds permanent

Folds gets lost when we end the session, in order to make it 
save the folds we can use `mkview` before quitting the file and
`loadview` when we open it again.

> mkview

save folds.

> loadview 

load the folds.
