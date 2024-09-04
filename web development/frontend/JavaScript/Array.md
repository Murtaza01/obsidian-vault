# array.find()

an array method that will return the first matching element inside that array, you can use it to abstract some strings, here is an example:

```javascript 
jokes.find((joke)=>{
	const joke =joke.jokeType === 'Puns'
	console.log(joke)
})
```

this will return the first matching string, it will loop through the array and takes the first value that matches the condition you gave, and return it !

note that it has a callback function like the `forEach`  method, that will be used to loop through the array, so the argument will function as the index.

# array.filter()

this is a similer method to the `array.find()`, however it returns all the matching results back to you unlike the find method, see the example below:

```javascript
jokes.filter((joke)=> joke.jokeType==='Puns')
```

this is a strict down version that looks cleaner, because its one line


# array.findIndex()

an array method that returns the index of an element inside the array, it takes a callback function which will work as a way to check if the giving value matches the value you want to find, look the code below:

```javascript
jokes.findIndex(e => e.id === id)
```

here i am basically saying, that inside the array jokes, there is an element, in this case the element is an object that has an id, so im asking if that id is the same id on the right, if yes, it will return the object index, or the element index, if not it will return `-1` 

# Array.map()

the map method takes a callback function, it will go over every element of the array, and run that function on it, here is two examples:

```JSX
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map((x) => x * 2);

// Expected output: Array [2, 8, 18, 32]
-------------------------------
function createCard(contact){
	return <Card 
	name={contact.name}
	img={contact.img}
	/>
}

contacts.map(createCard)
```

in our second example, we are taking each element (which in this case is an object) of the array as a parameter in our function `contact` and using it to access our value in our object

we can create an object from an array using the `map` function using the code below:

```JS
array.map((item)=> ({text:item}))
```
