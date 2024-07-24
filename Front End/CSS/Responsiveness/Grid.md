a grid helps to build two dimensional responsive layouts, a row in grid is a vertical row, unlike flexbox, see the picture below:

![[Pasted image 20231108123340.png]]


fr is a unit-less value that helps creating a flexible gird, it uses the space available to distribute the width/height example:

![[Pasted image 20231108123825.png]]


# units with grid

using px/rems will not make your grid flexible, you can use **auto** for a flexible layout, it will take the remaining space that it finds to fill the whole container (100%) but only for the column, see the example below:

![[Pasted image 20231108141628.png]]

it will try to fit the content with the row, as you can see above

# minmax

using minmax will control how your item shrink and grow, consider the example below: 

![[Pasted image 20231108143739.png]]

the column will have a grow limit of 800px, and shrink limit of 400px

# not defining rows/column

when you don't assign a width and a height for your item, it will be automatically aligned, it will fit the content for the row, and fill with the previous column, see the example below:

![[Pasted image 20231108144921.png]]

in here we can use the **grid-auto-columns** and **grid-auto-rows** to control the auto behavior of an extra item/s

# [grid-column](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column)

a shorthand property for setting a position of your grid items and their size, it has two properties 

```css
item{
/* basically the first code is a shorthand for the other two properties if only one was giving*/
grid-column:2 => grid-column-start: 2, grid-column-end:auto;

/* to divide the two properties we use the slash, and this code below is saying start from the second column and end at the last*/
grid-column:2/-1 => grid-column-start: 2, grid-column-end:-1;
}
```

using the span value will give your grid cell size exactly the value you specify:

```css
item{
/*basically give two spans or places to that item, by defualt will start from 1 (auto) */
grid-column:span 2;

/* this is saying that i want you to start from the second column and span two*/
grid-column:2 /span 2 => grid-column-start: 2, grid-column-end:span 2
}
```
# order

using order in your grid will make your item be the last or at the last of your grid container

![[order-grid.png]]

# [grid-area](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area)

is a shorthand property for the four properties of grid-column/grid-row, look the example below:

![[grid-area.png]]

