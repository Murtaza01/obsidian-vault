# Specificity

a more specific selector, is the one that gets to win the battle of styling, if we have styled an element multiple times, ID are the most specific selectors, comes after classes:

![[specifity.png]]

> :hover also need specificity

pseudo elements when used also need specificity if we are changing something we already declared  with a high specificity, see the example below:

![[specificity&hover.png]]

the hover won't work because its not specific enough to override the first declaration, that's why we need a more specific hover selector, in this case this:

```CSS
#nav div.pull-right a.button:hover{
 background-color:green;
}
```

this will add more specificity since pseudo classes are classes and this can override the original selector. 

# block and inline

inline elements are elements that stay in line, they don't occapy the whole width, some of the common inline elements are: 

```html
<button></button>
<a></a>
<img />
<video></video>
```


# Centering

> using absolute

when you want to center an element, you can use the absolute property:

```css
.text-header{
	position:absolute;
	top:50%;
	left:50%;
	transfrom:translate(-50%,-50%)
}
```

> Centering with margin 

you can center an element using the margin property, see the code below:

```css
element{
margin: 0 auto;
}
```

this will set the top and bottom to 0 and the left and right to auto, which will center the element

# Positioning

> Relative

we can use relative position to shift our element or move it using this code:

```css
.element{
position:relative;
left:50px;
top:50px;
}
```

in here we are moving the element 50px to the left and top, *from where its originally has been !*  

> Absolute 

this will set the element relative to its parent element *(that has a relative positioning)* if no parent found to a relative positioning, the element will be set to the web page left top position.

