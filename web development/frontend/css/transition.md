# transition display

you can transition the display property using `allow-discrete` see the below code:

```css
.card{
	display:none;
	transition:display 0.5s;
	transition-behavior:allow-discrete; 
}

.card.show{
	display:block
}
```

we can use the `@starting-style` this way:

```css
.element{
transition: opacity 1s, display 1s;
display:none;
opacity:0
}

.showElement{
	opacity:1;
	display:flex;
}

@starting-style{
	.element{
	opacity:0;
	}
}

```

when we add the `.showElement` class, it will show the element, but without transition, instead it needs 

# Flip Card

to do a flip card we need four `divs`, represent the container, the card, the front and the back

in CSS we need to put the card to relative and the front and back of absolute so they stack over each other, we need three CSS property

```CSS
backface-visibility: hidden;
/* and we put that over the front and back */
transform-style: preserve-3d;
/* which will make our card to have a 3d effects */
perspective: 1000px;
/* sort of like giving your element a place to have the 3d effect */
```

we also need to use `rotateY` for the back

# transition on enter

if you want to transition your element when it first enter you can use the rule `@starting-style` see example:

```css
@starting-style{
.card{
	height:0;
	opacity:0;
	}
}

.card{
	transition: height 0.7s,opacity 0.7;
	height:10rem;
	opacity: 1;
}
```

in this case the card will start as 0 and then transition to `10rem` 

