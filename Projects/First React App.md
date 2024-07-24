- [x] learn how to do the flip animation
- [x] make the Card component
- [x] render one dynamic card with props 
- [x] expand more on the react component !



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