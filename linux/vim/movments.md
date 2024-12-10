# movements

you can move around in the text editor normal mode with 
j = down
k = up 
l = left
h = right

you can move to the end of word or begining by:

e = end of word
b = begining of the word
w = next begining of the word

you can move to parantheses or braces by:
 
shift + 5 === %

to move to the end or beginig of the file:

gg = begining of file
G = end of file
number+G = specfic line 


> indent 

we can indent lines automatically using:

= which will indent our lines, 
we can indent the whole file using

=G

# open file/links 

we can `click` to another file if we have a path using:

gf == open file

> ctrl+w ctrl+f

Open file in a new window

>ctrl+6

Jump to previous buffer.

to a link using:

gx == open link (using xdg)

# num%

we can go to different places of our current window using:

50% == goes to the middle.

# Window Jumps

H = jumps to top of current window
L = jumps to bottom of current window

Ctrl+d = jumps some lines (not sure how many)
Ctrl+u = jumps backwards.

[[ == goes to the next section (h1 in Markdown).
