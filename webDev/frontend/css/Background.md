# Background-image:

if you do deiced to use {background-image} to import an image, in a div, you should give it a padding so there is space for the image, like this:

<h3>div class={img}></h3> 

here we have a simple empty div, when we go and add background image to css:

<h3>.img{background-image: url('imge.jpg')} </h3>

because the div is an empty element, it wont show the image, because there is nothing to show, but when you add **padding**, you give a space for that div to have an image, because you are adding the image in the CSS


# background-position:

to position an image using background-position, we have two options, either using **units** or using **a wording position** for example:

```css
background-position: 10%  X axis  50px  Y axis 
background-position: left top
```

you can even combine the two options like this:
background-position: left 10px top 10%

# [Object Fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)

used to resize images to fit their containers, example:

```css
img{
object-fit:cover
object-position:80%
}
```

the first line will resize the image to cover the whole container, the second line will control its position


# [linear-gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/linear-gradient)

is a way to add gradient to your colors, it creates an image that will display the different colors you set, see the example below:

```css
linear-gradient(gradientDirection, color1, color2, ...);
```

`linear-gradient` function needs at least two color arguments to work

Color-stops allow you to fine-tune where colors are placed along the gradient line. They are a length unit like `px` or percentages that follow a color in the `linear-gradient` function, see the example below:

```css
linear-gradient(90deg, red 75%, green, blue)
```

this will make the red takes up 75% of the background color

if no `gradientDirection` argument is provided to the `linear-gradient` function, it arranges colors from top to bottom, or along a 180 degree line, by default.


> multiple background property

you can put multiple background images using the `,` to separate between them, see syntax below:

```CSS
.header{
	background-image:
	linear-gradient(rgba(255,255,255,0.7)),
	url('./images/house.png')
}
```

