we use `useRef()` hook, when we want to store a variable that won't be changed every time the function (component) render

when we use `useState()` to store variables, we are rendering the function (re-executing it) every time the state changes, instead of this behavior, we use `useRef()`

for example when we have an `onChange` prop that we are handling on an input, and we only want the end value of that input, we can use `useRef()` to store the value and not render (re-executing) the function on every key stroke

```jsx
function Player(){
const playerName= useRef();
const [enteredName,setEnteredName]= useState('')

function handleClick(event){
	setEnteredName(playerName.current.value)
}
reutrn <>
<input ref={playerName} />
<button onClick={handleClick}>Submit</button>
</>
}

```

in the example above, we are storing the value of our input inside the ref, then updating that state using our new value that is entered through the click of the button

`useRef()` always return an object with `current` as property, and what we are doing essentially, is connecting our ref and our input

because of the functionality of `useRef()` we can't update our UI using it alone, because it doesn't re-execute our function (component)

![[state vs refs.png]]
 > `forwardRef()`

another usage of `useRef` is to store elements and change them, see the below example:

```jsx
function Button(){
const changeColor = useRef()

function handleClick(){
	changeColor.current.style.color= 'red'
}

return <>
<h1 ref={changeColor}>hello world</h1>
<button onClick={handleClick}>Change Color</button>
</>
}
```

in the above example am taking the `h1` element, and putting it inside a variable (sort of like accessing it using the `querySelecter`) and then im accessing it using the `current` and giving it a color of red

However if we need to do that but with another component, so we take an element and change it inside another component based on an event, we need to use the `forwardRef`:

```jsx
import {forwardRef} from "react"

const Button = forwardRef(function Button(props,ref){

})

export defualt Button
```

the above is how we use `forwardRef` we have to wrap it with our component function, we can access the ref using the second parameter in our component function.

you can think about it as; our component function will return some JSX, `fowardRef` is going to take that JSX, and adjust it so that the refs work, then the variable `const Button` is going to store that returned data coming from the `forwardRef` function and its going to be exported 

> `useImperativeHandle()`

is a hook that is used with the `forwardRef` function so that the ref coming from another component is controlled inside our component, this is good if multiple developer working on one component and you want to make your refs accessible inside one component, synatx:

```jsx
import {forwardRef,useRef,useImperativeHandle} from "react";

const Header forwardRef(function Header(props,ref){

	const dialog = useRef();
	useImperativeHandle(ref,()=>{
	return {
		open(){
		dialog.current.showModel()
		}
	}
	})
	return <dialog ref={dialog}>
	<h1>hello world</h1>
	</dialog>
})

```

in the above code, we are getting a ref, i use that ref inside my `useImperativeHanlde` hook, which takes two arguments, the first is the ref, and the second is a callback function, this returns a method we call whatever, in here we are calling it `open`

in that method we are manipulating the ref we created above inside this function (so we are not using the other ref)

then because of the connection we have from the ref we are getting, the other component handling the ref that wrap our function will have access to the `open()` method we defined in our function

```jsx
function App(){
	const dialog = useRef();

	function handleClick(){
	dialog.current.open();
	}

	return <ShowResult ref={dialog}/>
}
```

so we are taking the element `showResult` and manipulating it, adding the `open` method, but how does it know what is `open()` ?

it will know because we manipulating the ref we are sending into that element, adding a method to it, then we are accessing it inside this function

an easier explanation would be, am sending a dialog element, am adding a method to it, then because of the connection of the ref, the method will be stored and can be accessed inside my App component