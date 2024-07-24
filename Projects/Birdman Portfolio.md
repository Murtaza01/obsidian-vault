
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

# typeof with ternary

you can type check something with ternary like this:

```js
typeof icon === "string" ? do something
```