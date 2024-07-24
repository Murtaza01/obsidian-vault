# Constructor function

a constructor function is a function that create other functions or objects, it start with a capital letter and we use the keyword New with it, example:

```javascript
// constructor function
function Person (name, age, gender) {

   // assigning  parameter values to the calling object
    this.name = name;
    this.age = age;
    this.gender = gender;

    this.greet = function () {
        return ('Hi' + ' ' + this.name);
    }
}

// creating objects
const person1 = new Person('John', 23, 'male');
const person2 = new Person('Sam', 25, 'female');

// accessing properties
console.log(person1.name); // "John"
console.log(person2.name); // "Sam"

//excuting the method greet, we are consloing it because the function only returns a value
console.log(person1.greet())

```

in the above example, greet is a method that we can use to the person1 to execute the function, the the example in the end
# switch statement

consider having an array, that you want to check to do a specific action depending on the element, you can use *else if* but it is better to use the switch statement, here is an example:

![[Switch Statement.png]]

in the above example we have an array, and we are using a for loop to access each element and giving it and event listener, we are taking the `innerHTML` of the element that gets clicked, and using `switch` we are checking for what button got clicked and making an action likewise

note that we need the `break;` after every case, and inside the switch parentheses, we button the value that we wanna check, and the `case` is to check whether this is the value, if it is do the this !

if we didn't put a `break;` in our switch, the code will continue running to the next line that has `break;`


# Ternary Operator

is a shorthand way of adding a condition to a giving code, see the code below for more understanding:

```javascript
function sum(a, b) {
  return a + b;
}

const result = sum(10, 10) > 1 ? sum(5, 5) : sum(1, 1);

console.log(result); // 👉️ 10
```

the first line after the function sum, is the compare operator that will work with our condition *(1)*, basically we are saying if the result of this function is bigger then 1, then `sum(5,5)` else `sum(1,1)` but here the if is represented as `?` and the else as  `:` and the condition is before the actually code

you can also use this syntax with else if statement, see the code below:

```JS
const getTime = () => {
  return (time >= 0) & (time < 12)
    ? "morning"
    : (time > 12) & (time < 18)
    ? "noon"
    : time > 18
    ? "eveing"
    : console.log(time);
};
```

in the above way we need the else statement, this is the same example as the [docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_operator#conditional_chains) its only has a better syntax (kinda)


there is another way to a shortcut if statement, which is by using the code below:

![[shortcut if.png]]

no else or brackets is needed, just the if and the condition and the followed action in the same line !

# [Geolocation](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation)

to find out the location of the user, we use geolocation, a method inside the `navigator` object, to get the current position we use the following code:

```js
navigator.geolocation.getCurrentposition((position)=>{
	position.coords.longitude
})
```

`getCurrentPoision` is a function that takes a callback function, that function returns an object, an object which have the longitude and latitude of the current position of the user, see [example](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/getCurrentPosition#examples)

# localStorage

local Storage is a way to save data into our browser so we don't lose them after a refresh or after we close the tab, its really good with dark mode or data that need to persist inside our page, for example a to do list app

> adding items

we use the method, `.setItem` which takes two parameters, the first one is the name of the item, the second is the actual data that we want to store, note that the data must be a string, we can use JSON:

```js
function getItems(id){
const StoredData = JSON.parse(localStorage.getItem("data")) || [];
localStorage.setItem("data",JSON.stringify([id,...StoredData]));
}
```

this really good example, where we get the items from our storage data that we create, and then spreading this array when we are adding the new items (which is the id), and because at first it will be undefined, we use the `||` or operator, to say that if we don't have that then we use an empty array

> checking if items exist

we can add an extra code to check wether that id already exist in our array or not using the array method `indexOf` which will return if true the index of an element, otherwise it will return `-1`:

```js
function getItems(id){
const StoredData = JSON.parse(localStorage.getItem("data")) || [];
if(stroedData.indexOf(id) === -1){
	localStorage.setItem("data",JSON.stringify([id,...storedData]));
}
}
```

so here im only adding if i don't have the index (id) of that array (storedData), so if it does exist, this will return false and won't exeucte

> deleting item

we can delete item from our local stroage using the filter array method:

```js
function deleteItem(id){
localStorage.setItem(
"data",
JSON.stringify(storedData.filter((item)=> item !== id))
}
```

the filter array method will return false, and that will make the item be removed

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

# accessing a property in an object with a dash -

if we want to access a property in an object that has a dash in it, for example `person-name` we can do that using the following syntax:

```js
const object = {
'person-name':'ahmed',
age: 8
}

object['person-name']
```

i don't use dot with it and the object key have to also be wrapped in quotes 

# [turn string into number](https://perals.io/posts/63/)

we can easily do that using the `+` operator in-front of the variable:

```js
let num1 = '1'

+num1 + 1 // 2
```