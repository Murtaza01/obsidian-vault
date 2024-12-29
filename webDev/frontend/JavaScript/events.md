# onKeyDown

when you have a dialog, and you want it to not be closed using "Esc" because you want to only be closed via (icon) so that the effect of your DOM take place:

in this case, we need to add an event listener to the element, so that we prevent the default behavior of the dialog element:

```jsx
<dialog onKeyDown={(e) => e.preventDefault()}>

{/*better version is only to stop the Esc key*/}

function handleKey(e) {
    if (e.key === "Escape") e.preventDefault();
  }
```

# keypress

to add an event listener to keyboard we simply use the `keypress` event, and take that event and use the `.key` to extract the the key being pressed, see the example below:

