# Button effect

when you want to add effect to your Button, we use Pseudo elements, we add the Content:'' and a position of absolute so we can pick where the color will start from, and we use <b>opacity</b> or <b>scale()</b> to hide show the hover effect on the button, then we add the button hover with the pseudo element

the order of your pseudo element and hover should look like this:
# .btn-1:hover::before

this translate to (when you hover on my button, i want to do something to the before pseudo element)

in order to make the element show, we need to set the left and right and top and bottom to 0, so that they have room

then we can either use scale or opacity to hide our element then show it when hovering


```css
btn-1 hover::before {
	content: '';
    position: absolute;
    background-color: #000;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 1s ease;}
```

# keyframes

To Rotate an element you just need to use Rotate and turn, like this:

```css
@keyframes Name {
    to {
        transform: rotate(1turn);
    }
}
```

a more advance way of using keyframes is from animation, we simply define a keyframes and then use it in our element using the `animation` property 

```css
.header-text{
	animation-name:moveToLeft;
	animation-duration:1s;
}


@keyframes moveToLeft {
	0%{
	opacity:0;
	transfrom:translateX(-100px);
	}
	100%{
	opacity:1;
	transfrom:translateX(0);
	}
}
```

# [@starting-style](https://www.youtube.com/watch?v=TTPuNolpaDI&ab_channel=NetNinja)

starting style gives a style to a specific element before any changes applies to it, for example when we have a dialog element, which we want to transition from its normal state (display:none) to a different state, we use the @starting-style:

```CSS
/* when the dialog is open transtion this ! */
dialog[open]{
	opacity:1;
	scale:1;
}
/* adding a transtion to our dialog */
dialog{
	opacity:0;
	scale:0;
	transition:all 1s ease;
}

@starting-style{
	dialog[open]{
	opacity:0;
	scale:0;
	}
}
```

because its the same element im trying to add a transition to, i have to have an initial state of style, which is why i use @starting-style, the initial state will represent the first state of the element, then if i had a transition in the same element, it would go from the initial state to that of which i put under the @starting-style:

```CSS
.card{
	rotate:0deg;
	opacity:1;
	transition:all 1s ease;
}

@starting-style{
	.card{
	rotate:180deg;
	opacity:0;
	}
}
```

> [animation-fill-mode](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode)

this property of animation is used to apply the animation before or after the execution of the animation