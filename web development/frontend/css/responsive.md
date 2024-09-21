# rem

rem is the Font size of the root element, it is `16px` by default, using rem makes it easy to have responsive design, when we set the font size to a fixed number (pixels) in our html element, we then have the ability to inherit that size using rems:

```css
html{
	font-size:10px;
}

header{
	margin:2rem /* 20px */
}

p{
	font-size: 2.5rem; /* 25px */
	width: 12rem /* 120px */
}
```

when we change the font-size on the html element, the whole document will change size, because its depending on that size

> allowing user to change size

when we put the html element as 10px, we run into a problem, the user can't change the browser font-size, because its always fixed at 10px, so a good way is to put a percentage

```css
html{
	font-size:100%; /*16px, because thats the default */
	
	/*we want 10px so we use percentage*/
	font-size:62.5%;
	
	/*if we want 20px we use this*/
	font-size:125%;
}
```
