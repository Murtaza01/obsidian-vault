# onKeyDown

when you have a dialog, and you want it to not be closed using "Esc" because you want to only be closed via (icon) so that the effect of your DOM take place:

![[useImperativeHandle.png]]

in this case, we need to add an event listener to the element, so that we prevent the default behavior of the dialog element:

```jsx
<dialog onKeyDown={(e) => e.preventDefault()}>

{/*better version is only to stop the Esc key*/}

function handleKey(e) {
    if (e.key === "Escape") e.preventDefault();
  }
```

# dialog

> animating dialog

when you want to animate dialog, we need to use a special CSS property called @starting-style, which is used when we want to either transitioning from block to none, or when we want to transition on element on place (when we want to have an initial state of style)

> styling dialog

when styling a dialog, we need to use the pseudo selector [::backdrop](https://developer.mozilla.org/en-US/docs/Web/CSS/::backdrop)  which would give style to the back of the element that is rendered upfront,  to the whole view-port,  

# others

> adding background text effect

you can add text background effect using the box-shadow property, with the inset value, see code:

```CSS
.Header{
	box-shadow:inset 0 -0.5em 0 0 rgba(0,0,0,0.7);
}
```

> accessing body in react

when you want to access the body inside react, we use the normal way of accessing it using the query selector 

# some notes

1. never skip a component without finishing it, completely !
2. don't use crappy CSS methods, always make room for some changes 
3. when planning, consider the mobile and desktop version
4. always, ALWAYS, get data and icons first
5. Plan Plan plan !