# spread operator 

in order to add some element in the beginning of the array or an object, or at the end, this is a very useful and easy way of doing it, look the code below:

```javascript
const obj = {'b': 2, 'c': 3};

const startAdded = {'a':1 , ...obj};
// startAdded = { "a": 1, "b": 2, "c": 3 }
```

imagine it as if the three dots `...` where like a special syntax that open the array or the object to receive a new element, in this case we want it in the middle, so we put the first key/value pare followed by a comma

you can use the spread operator with babel to shorten you code, see the example below:

```JSX
function handleChange(e){
	const {name,value}= e.target

	setContact((prev)=>{
	return {
		...prev,
		[name]:value
	}
	})
}
```

see that we warp `name` with brackets, so that JavaScript won't consider it a new key but rather a variable, we are spreading the object `prev` and only changing the name key, here name would be dynamic, it would be different value depending, for example it might be `fname` or `lname`, check `angela react 40`

# Destructuring assignment

an expression in javascript that allow us to assign variables from objects or arrays using a simple syntax and a clean code, see the example below:

```javascript
const { jokeText, jokeType } = req.body
```

the values after the const is what you want your variables name to be, the second part after the equal sign is the array or the object

in our example, we are destructing an object, when doing so, its either you give a new name to the object by saying this:

```javascript
const { jokeText:text, jokeType:type } = req.body
```

or you only name the key, which will become the variable, because objects have named indexes  *(meaning that you can find an element using the key and not an integer)*

we can have nested Destruction when we have nested objects or array, consider the example below:

```JS
const animals= [
	{
		name:"cat",
		needs: {
			food:2,
			water:1.5
		}
	},
		{
		name:"dog",
		age: [1,2,3]
	}
]

const [cat,dog]=animals;
// here im taking the index of my array animals to assign them to cat and dog, same as (const cat = animals[0])

const {needs:{food,water}}= cat;
// here im destructing the needs object, then further taking the food and water objects from that need object as a sperate variable

const {age:[one]}=dog
// im taking the first index of the array (age) and puting it into a variable
```
