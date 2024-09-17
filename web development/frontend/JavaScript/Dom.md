# Combining Selectors Using The DOM

you can combine class and elements using the querySelector in the DOM, example:

```javascript
document.querySelectorAll('a.new-window')
```

where a is a an *element* and new-window is a *class*

# Adding CSS

to Add CSS using The DOM, there is a really good way of doing so, in JavaScript we write this function:

```javascript
let counter = 0

const addCss = ()=>{
	counter++
	if(counter %2 !== 0){
		docment.queryselector('head').innerHtml = '<link src='style.css'>'
}
}
```

and in the Html, we should have a button that will run this function when clicked, so the number of counter would equal to 1 which in this case will add in the head the innerHtml that i picked !

button onClick='addCss()'

# adding style

consider this [site](https://appbrewery.github.io/flexbox-sizing-exercise/), it uses a function that adds style which are given by the user via textarea, look below:

![[Pasted image 20231107175022.png]]


# [toggle()](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/toggle#toggling_a_class_on_click)

is a method that you can use it to remove/add class to a specific element, if the class doesn't exist, it will add it, if it does it will remove it, example:

```javascript
element.classList.toggle('the class name')
```

# Change the opacity in one element

im trying to figure out the best way to do this, maybe i add a function that will get rid of the  nested loops, but so far this is what I've done:

![[opacity in one element.png]]

# keypress

to add an event listener to keyboard we simply use the `keypress` event, and take that event and use the `.key` to extract the the key being pressed, see the example below:

![[keypress event.png]]

# function (event)

to know which event triggered your `addEventListener` we can simply add a parameter to the anonymous function (or the callback function) so we get the exact event that triggered our function, example:

```javascript
element.addEventListener('click',function(event){
// this will give you the mouse event
	console.log(event)
})
```

# adding styles and removing it after a specific time

consider the code below:

![[Pasted image 20231114004136.png]]

where `pressed` has some styles in the style sheet, this will add the animation and remove it after few seconds (or whatever time you would like it to be)
