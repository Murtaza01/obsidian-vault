to use jQuery we simply use the `$` 

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
```

# addClass()

we can select multiple classes in the same string using the addClass method, example:

```javascript
$('h1').addClass('big-title margin-50')
```
# css()

to add CSS we can simply use the CSS method:

```javascript
// where the first is the property and the second is the value
$('h1').css('color','red')
```

but it is not recommended to add CSS inside our JavaScript, so we can simply refer to a class inside our CSS

# text()

to change text in jQuery, we simply use the text function, to change the `innerHTML` we use the html method, example:

```javascript
$('h1').text('New Text')
$('h1').html('<em>New html</em>')
```

Note that when using jQuery on an array, the change applies for all the elements inside our list, without needing to use for loop

# attr()

to change an element attribute we simply use the `attr()` method:

```javascript
$('a').attr('href','http//www.google.com')
```

# Adding events with jQuery

to add events we simply use the name of the event in our selected element, example:

```javascript
$('h1').click(function(){
	$('h1').css('color','red')
})
```

we can better add event with jQuery using the `on()` method and it takes two parameters, the first for the event, the second for the call back function, example:

```javascript
$('h1').on('mouseover',function(){
	$('h1').css('color','red')
})
```

# adding elements with jQuery

to add elements we have mulitple methods we can use:

1. `before()`
2. `after()`
3. `prepend()`
4. `append()`

see the example below:

```javascript
$('h1').after('<button>new</button>')
```

to delete an element we simply use the remove() method on it:

```javascript
$('h1').remove()
```

you can add classes and `attr` with that element inside the quotation, here is an example:

```javascript
$('div').append('<input type="checkbox">')
```

# showing and hiding elements

we have muliple methods that can show/hide our elements:

1. `show()`
2. `hide()`
3. `toggle()` *toggles the show/hide method*
4. `fadeOut() `
5. `fadeIn()`
6. `fadeToggle()` *toggles the `fadeOut/fadeIn` method*
7. `slidDown()`
8. `slidUp()`
9. `slidToggle()`

for the `fadeout` it will lower the opacity to 0 with transition
for the `slidDown()` it will collapses our element, this can be useful for drop-down menu

# animate()

is a method that takes two CSS values and animate them *meaning they get animation applied to them*, it takes a property and a value like CSS, look the example below:

```javascript
$('h1').animate({margin: 20px})
```

this will give the `h1` a margin, but it will do it with animation, note that the animation method only takes properties that accepts numbers like padding or opacity...


# Chaining methods together

we can simply chain methods together, and they will run in order, exmaple:

![[chaining methods.png]]

# variables with jQuery

you can add an element or a value to a variable easily with jQuery, see the example below:

```javascript
//val() takes the value of the input
const name = $('input').val()
```

