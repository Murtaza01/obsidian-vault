# gradient text

we can have gradient text with this code:

```css
h1{
background-image:linear-gradient(to right,#ccc,#3737);
-webkit-background-clip:text;
color:transparent;
}
```

in the above code, we give a gradient background and then we make the image clipped as the text, then i need to make the color transparent so that the background appears

*this works for images too!*

# [ellipsis](https://developer.mozilla.org/en-US/docs/Web/CSS/text-overflow) ...

we can set a minmal size of the text so that we show ellipsis in the end,
instead of showing the actual text, it is done by using three properties:

```css
p{
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
}
```

# adding background effect with shadows

you can add text background effect using the box-shadow property, with the inset value, see code:

```CSS
.Header{
	box-shadow:inset 0 -0.5em 0 0 rgba(0,0,0,0.7);
}
```

