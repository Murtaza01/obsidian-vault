> why we use `useState()`

the reason why we can't update a variable inside jsx, is because react components are functions, and functions are only executed once, so when we try the following code:

```JSX
let num = 1;

<button onClick={num+1}>
{num}
</button>
```

this will only show the initial num (1), but won't update it, because in order to update it we have to execute the function (component) again

when we use `useState()` the function of `useState` will change that behavior, it will **render** the component function, thats why we are allowed to use `const` when storing the initial value of `useState` 

`useState()` will re-execute the function (component) that it is used in, if there is a component inside that parent component, it will re-execute that function too !

> state is scheduled

the state function we get from `useState` doesn't update right away, but rather it scheduled the update, consider this example:

```jsx
function handleClick(newCount){
	setCount(newCount)
	console.log(count) {/* this will log the old count */}
}
```

in this case the old count is consoled, and not the newly set one `newCount` because 

# using states with form

consider the following form:

```html
<form>
	<input type="text" name="title" />
	<textarea name="content" />
	<button>Add item</button>
</form>
```

the way we do this is first to keep track of the form value using `useState()` which in this case will track both of the `input` and the `textarea`, see below:

```JSX
const [note,setNote]= useState({
	title:'',
	content:''
})
```

where *title* will represent the input and *content* represent the textarea, second we control those values using the value property and use `onChange()` to keep track of the changes and store the value in the const above:

```jsx
	<input type="text" name="title" value={note.title}  
	onChange={handleChange}/>
	
	<textarea name="content" value={note.content}
	 onChange={handleChange} />
```

the `handleChange()` function will store two constant, one is the actual value of the input and textarea, the second will differentiate between which value goes to where, then we need to add those constant to our initial object stored in `Note`, using the `setNote()` function and accessing the previous object so we can update it and render it using the function

```jsx
function handleChange(event){
	const {name,value}= event.target

	setNote((previousNote)=>{
	return {...previousNote,
		[name]:value
	}
	})
}
```

the first line we are destructing our name and values that comes from the `event` which will trigger depending on the event we are using (input or textarea), so that it will take the name of that event and the value of it, and store it in a new variable

the second using `setNote()` which we acess the previous object so we can update it using our new variables, using the `setNote()` we return an object, and we spread our `previousNote` which is an object, and when we spread it, we are updating the name and value, which will correspond to *(title: what ever value the user enters)* and that will goes for both of the input and textarea


