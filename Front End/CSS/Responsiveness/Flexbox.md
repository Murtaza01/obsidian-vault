[good resource for flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

when you set the display to flex, you have a row of elements that will fit to your content, the container (flexbox) will be the **Block** element, and it will be a 100% width

# Inline-Flex

![[1.png]]
inline-flex will function the same way, but with the addition that it will be inline, so you can have element besides your content 

# flex-basis 

controls the size of your content, it mainly controls the size along the main-axis, so if we have a flex-direction set to row it will increase its width, if we had column it will change the height.

we put the flex-basis on the element itself and not in the container, consider the code below

```css
.container{
display:flex;
}
.container > *{
flex-basis:100px
/* to set equal width to your elements */
flex-basis:0
}
```

what this does, it sets all the children of our container (flexbox) to have a flex basis of 100px, we can give flex-basis individually to each element

flex-basis have a default of auto, which will set the width of the element to the content (text), so **if you want equal width to your elements** you set it to 0 
# [Order](https://developer.mozilla.org/en-US/docs/Web/CSS/order)

used to change the order of your flex elements

# [align-self](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self) 

both change one element into your container to have a specific kind of flex, see the image below: 

![[Pasted image 20231107011500.png]]

# [There is no justify-self in Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_box_alignment/Box_alignment_in_flexbox#there_is_no_justify-self_in_flexbox)


# min-width & max-width

using the min-width with your flex items will make a point of your specified number that this items will shrink

# [flex-grow](https://css-tricks.com/almanac/properties/f/flex-grow/)

flex-grow controls how your flex items grows, if you specify (1) your items will grow to fill in the container, the [default](https://css-tricks.com/understanding-flex-grow-flex-shrink-and-flex-basis/#:~:text=That's%20the%20default%20behavior%20of,on%20the%20content%20inside%20it.) of it is 0, so the items will not grow to take up the space

you can use flex-grow into an individual item, for example:

```css
item{
flex-grow:2
}
```
this will grow your item to take up double the space that other items take, so if they take 50px this item will take 100px

![[Pasted image 20231107155736.png]]


# flex

take three values shorthand for grow and shrink and basis, note you need the write values (number, number, unit (30px,2rem..)) 

```css
item{
/* flex-grow flex-shrink flex-basis*/
flex: 1 1 0;
/* shorthand for the code above*/
flex:1;
}
```

this code above will make your items grow, and shrink, and distribute your space to an equal amount along all items (flex-basis:0)

note that flex-shrink default is 1 !