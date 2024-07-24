# Inline 

when we set the *display: inline* we cant edit the **height and width** of the element, however setting it to inline-block will allow us to edit the width/height and be inline, consider the code below:

```css
span{
  background-color:green;
  width:100px;
  height:100px;
}
```

the width and height are ignored !

# float 

float is used to warp your text around an image or an element, it is used on the exact image/element that you want the text to be floated upon:

```css
img{
float:left;
}
```

using [Clear](https://developer.mozilla.org/en-US/docs/Web/CSS/clear) will stop the float of an element, but you have to target that float !

```css
p {
clear:left;
}
```

in the above code we are clearing the floating left that we did on the image so our paragraph is not effected anymore.

