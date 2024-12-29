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
