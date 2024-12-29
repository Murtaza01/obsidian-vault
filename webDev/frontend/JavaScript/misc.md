# switch statement

consider having an array, that you want to check to do a specific action depending on the element, you can use *else if* but it is better to use the switch statement, here is an example:

in the above example we have an array, and we are using a for loop to access each element and giving it and event listener, we are taking the `innerHTML` of the element that gets clicked, and using `switch` we are checking for what button got clicked and making an action likewise

note that we need the `break;` after every case, and inside the switch parentheses, we button the value that we wanna check, and the `case` is to check whether this is the value, if it is do the this !

if we didn't put a `break;` in our switch, the code will continue running to the next line that has `break;`

# [Geolocation](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation)

to find out the location of the user, we use geolocation, a method inside the `navigator` object, to get the current position we use the following code:

```js
navigator.geolocation.getCurrentposition((position)=>{
	position.coords.longitude
})
```

`getCurrentPoision` is a function that takes a callback function, that function returns an object, an object which have the longitude and latitude of the current position of the user, see [example](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/getCurrentPosition#examples)

# date

in order to get the date in JavaScript we simply use the `date()` instance, we can also get the exact day using the `getDay()` here is an example:

```javascript
const date = new Date()
console.log(date.getDay())
// number of the day ! 0-6 
```

to have the exact date of the current day, there is a [method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString)inside the date constructor that helps with that, it takes two parameters, the first is the language and the second is the options, which is an object with the exact year month and day format 

# using an empty return in if

when we do that we stop the execution of the below code:

```js
const isKind = true;

function checkKindness() {
	if (isKind) {
      console.log("he is kind");
      return;
    }
    console.log("he is unKind");
  }
```

in this case because we are in a function only the `he is kind` will execute

# [turn string into number](https://perals.io/posts/63/)

we can easily do that using the `+` operator in-front of the variable:

```js
let num1 = '1'

+num1 + 1 // 2
```

# calling an inner function

we can do that just by adding a second parentheses to the end:

```javascript

function hello(){
    return function(){
    console.log('hello world');
    }
}

hello()() // hello world
```

# typeof with ternary

you can type check something with ternary like this:

```js
typeof icon === "string" ? do something
```
