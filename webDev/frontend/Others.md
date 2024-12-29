# chaining classes
you can use Chaining to apply a specific style to an element consider the code below

h1.heading{
color:blue
}

Chaining takes no spaces and will select that specific element with the class of heading

# [Visibility](https://developer.mozilla.org/en-US/docs/Web/CSS/visibility)

is a way of showing/hiding an element instead of using display:block, which doesn't have transition, instead using this with opacity will give some transition, consider the code below

```css
div > ul {
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s, opacity 0.5s linear;
}
div:hover > ul {
  visibility: visible;
  opacity: 1;
}
```


you can center things using the code below
```css
.container{
display:grid;
place-items:center;
}
```


place-items= this property is shorthand for **justify items** and **align items** 

# [Outline](https://developer.mozilla.org/en-US/docs/Web/CSS/outline)

you can use outline to remove the input default *outline*, the outline [differs](https://stackoverflow.com/questions/1158515/what-is-the-difference-between-outline-and-border-css-properties)from border

# type Selector 

you can use type to select an element in CSS, which would look like this:

```css
input[type="radio"]:hover {
    cursor: pointer;
}
```

# Global variables 

if we don't want to use global variables, instead there is a really good [way](https://stackoverflow.com/questions/407048/accessing-variables-from-other-functions-without-using-global-variables)of accessing values

which is to use an **empty object** that will serve as a container, then we can add to the container from our functions.

# Refreshing the Page

you can refresh the page via JavaScript using this 
[code](https://www.freecodecamp.org/news/refresh-the-page-in-javascript-js-reload-window-tutorial/):

```js
window.location.reload();
```

this would reload the current window, a good way to use it with buttons, is to add the onclick method in your html then use this as a parameter:

```html
<button onclick="window.location.reload()">Fill Again</button>
```
# Open a Link in a New Tap 

you can do that by adding the attribute target to you anchor tag, it would look like this:

```html
<a href="https://freecatphotoapp.com" target='_blank'>cat photos</a>
```

# Window.open()

We can open links pragmatically using the open method on
the window object:

```Javascript
Window.open(url)
```

# Button as link

We can create a button that will act as a link using 
[this](https://stackoverflow.com/a/2906611):

```html
<button onclick="location.href='http://www.example.com'" type="button">
         www.example.com</button>
```

