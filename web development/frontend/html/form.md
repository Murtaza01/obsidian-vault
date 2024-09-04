why use the form element ? for [_semantic markup_ !](https://stackoverflow.com/questions/31066693/what-is-the-purpose-of-the-html-form-tag), also because it sends requests to the backend of choice automatically

to use input and label together, consider the code below:

```html
<form>
	<label for="firstName">First Name</label>
	<input type="text" id="firstName">
</form>
```

to have an options input, we use the select + options elements:

```html
<form>
	<label for="age">Age</label>
	<select name="age" id="age">
	<option value="18-19">18-19</option>
</form>
```

to pervent the default behavior of a form we use this:

```javascript
document.querySelector('#form-1').addEventListener('submit', (e) => {
    e.preventDefault()
})
```

you have to add it to a an event listener, because the form is triggered as an event.

# Radio

in order to have a radio elements, we need a [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) which will be a container to those radios, note that you need a label for your radio input, and you need a name that will group them together 

to change the color of the radio we use [accent-color](https://developer.mozilla.org/en-US/docs/Web/CSS/accent-color)

```css
input[type=radio]:checked {
    accent-color: red;
}
```

when using radio, people can ignore your radio and not pick any option, if we give it the attribute required, we will make them select one from the other, so in this case, we give one radio an attribute of checked, so they can't ignore it

```html
<label for="personal-account"><input id="personal-account" type="radio" name="account-type" checked />
```

# floating placeholder

to add a floating effect to your input, like [this](https://codepen.io/Murtaza-Alkabue/full/VwgrdRY) you need a few things.

1. you need to have a separate label, that will function as your placeholder
2. position your label as the placeholder, give it a transition
3. give your input a psudo class that will move your label up when foucs

![[floating placeholder.png]]

the [~](https://developer.mozilla.org/en-US/docs/Web/CSS/Subsequent-sibling_combinator#using_the_combinator_with_simple_selectors) is a CSS selector that select an element that descent from the same parent *(meaning the first selector in this case input, is in the same line with the label and has the same parent)*

# input::before X

you can't use pseudo elements on inputs because they are not containers elements

# formaction

you can use `fromaction` to an input or a button that will go to the desired link you give it, see the example below:

```html
<input type='submit' formaction='/about'>
```

