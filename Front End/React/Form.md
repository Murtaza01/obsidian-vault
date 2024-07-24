we can derive from data in a different ways:

1. using state and two way binding
2. using ref
3. using the FormData native JavaScript object


# FormData

is a native JavaScript  constructor function that helps you deal with more complex form data, it uses the `name` attribute on the inputs to derive the information of such an input, here is the syntax:

```jsx
function handleSubmit(event){
	event.preventDefault();
	const fd new FormData(event.target)
	const email = fd.get('email')
}

<from onSubmit={handleSubmit}>
...
</from>
```

in order to get all the forms data we use: 

> [Object.fromEntries](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)

used to make an iterable data into key value pairs we used it with FromData, because when we create a new FromData constructor it returns an iterable:


```jsx
function handleSubmit(event){
	event.preventDefault();
	const fd new FormData(event.target)
	const data = Object.formEntries(fd.entries())
}

<from onSubmit={handleSubmit}>
...
</from>
```

we are using the method `entries()` on our  FromData to get all the entries in our from.

# event.target.reset

to reset our form, we simply use the reset method on our target:

```js
function handleSubmit(event){
	event.preventDefault();
	event.target.reset();
}
```

# Validation  

we want to indicate to the user that the given input is not valid, we can do that in combination with state and some helper property called `onBlur`:

```jsx
function App(){

const [entredInput,setEntredInput]=useState({
email:'',
password:''
})

const isValid = entredInput.email.includes("@")

hanldeChange(event){
	setEntredInput(event.target.value)
}


return <form>
	<input onChange={handleChange}/>
	{!isValid && <p>please enter a correct email</p>}
</from>
}
```

we are using a variable in this case to check whether the entered email is valid or not, but this is not enough for good user experience

> onBlur

adding to the code above, we can add the message when we lose focus on the input:

```jsx
const [didEdit,setDidEdit]=useState({
email:false,
password:false
})

const isValid=didEdit.email && entredInput.email.includes("@")

handleInputBlur(identifer){
	setDidEdit(prv=>{
	...prv,
	[identifer] : true
	})
}

return <form>
	<input onBlur={()=> handleInputBlur("email")}/>
</from>
}
```

here we are combining our function `onBlur` to check whether the user lost focus and our condition `includes("@")` to give best user experience

we can combine both of these with the `onChange`: 

```jsx
function App(){

const [entredInput,setEntredInput]=useState({
email:'',
password:''
})

const [didEdit,setDidEdit]=useState({
email:false,
password:false
})

const isValid=didEdit.email && entredInput.email.includes("@")

handleInputBlur(identifer){
	setDidEdit(prv=>{
	...prv,
	[identifer] : true
	})
}
hanldeChange(identifer,event){
	setEntredInput(prv=>{
	...prv,
	[identifer] : event.target.value
	})
	setDidEdit(prv=>{
	...prv,
	[identifer] : false
	})
}


return <form>
<input 
	onChange={handleChange} 
	onBlur={()=> handleInputBlur("email")} 
	/>
	{!isValid && <p>{!isValid ? "please enter a correct email" : ""}</p>}
</from>
}
```

in this case in the `handleChange` function, we say that when the user start typing the message `of validition` disappears, but when he loses focus, it comes back again.

note that the states here are for both password and email, so we are checking both.

# [validation using browser built-in](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation#using_built-in_form_validation)

in the above code we did validation using our code, but there is an easier version where we use the browser built-in propitiates like `requried` and `minlength`:

```jsx
return <form>
<input 
	type="email" required
	/>
</from>
```

we need that `type` attribute because the browser will validate this input based on the type.