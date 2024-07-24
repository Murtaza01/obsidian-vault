- [x] learn how to add and delete items using `useState()`



# saving the values of our input

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

# adding items

now in order to pass the note we stored to our `app.jsx` there needs to be a maneuver, first we need a function that will trigger when we hit the button, this function first will prevent the default behavior of the form, and it will also take another function coming from the `app.jsx` via props, and we will use it to trigger an action inside our `app.jsx` look at the example:

```jsx
function onSubmit(event){
	event.preventDefaluted();
	props.onAdd(note)
}

{/*in our app.jsx we will add a function that will be triggerd on this function call (the function above)*/}

function addItems(note){
	
}
function App(){
return <CreateNote onAdd={addItems}/>
}
```

the function `onSubmit()` will trigger another function from the `app.jsx` to add a new item, and we are using the props to give that function to our `<CreateNote /> `component

# saving the items into an array

in order to keep the items and adding them one by one we need an array that will store the values we get from the input, we can do that using `useState()`, so in our `app.jsx` where our function that will be triggered, we can add new notes using it:

```jsx
function App(){
	const [notes,setNotes]= useState([])

	function addItem(note){
		setNotes((previousNotes)=>{
			return [...previousNotes,note]
		})
	}
}
```

the `setNotes` function will return an array that will be saved in the const notes, and it will function as our database that we will use to add items using the map function:

```jsx
function App(){
	return <>
	{notes.map((item)=>{
		<Note
		title={item.title}
		content={item.content}		
/>
	})}
	</>
}
```

# removing items

to remove something, we use the same method we used to add things, we create a new function in our `app.jsx` that will be passed down to our component `<Note />` which will have a button that will trigger a function that will trigger our main function inside `app.jsx`:

```jsx
function App(){
 function deleteNote(id){
	setNotes((previousNote)=>{
		previousNote.filter((item,index)=>{
			return index !== id
		})
	})
 }

return <Note onDelete={deleteNote} />
}

{/* now in our Note compoenent we have a function inside our props object that we can trigger using another function that is triggered using onClick event !*/}

function Note(props){
	function HandleClick(){
	props.onDelete()
	}

	return <>
	<h1>props.title</h1>
	<button onClick={handleClick}>Delete</button>
	</>
}
```

to break `deleteNote` function, lets look at it separately:

```jsx
function deleteNote(id){
	setNotes((previousNotes)=>{
		return previousNote.filter((item,index)=>{
			return index !== id
		})
	})
```

so we are accessing the `previousNotes` which is an array that we want to filter based on a condition, this condition will filter items based on the ones that doesn't look like the id, so in turn we would get returned an array that doesn't have that id (index)

the only thing left is to add the id in our function, so we simply use the map function to give an id and a key as the inedex:

```jsx

{notes.map((item,index)=>{
	<Note
	key={index}
	id={index}
	title={item.title}
	content={item.content}	
/>
})}
```

then because these are sending to the `<Note />` component, we need to capture them and send them back using our function `handleClick`

```jsx
function Note(props){
	handleClick(){
	props.onDelete(props.id)
	}
}
```

on order to empty the `input` and `textarea` we can use the `setNote` function and give it the same empty object that we give it in the inital state:

```jsx
function sumbitNote(){
	props.onAdd(note)
	setNote({
	title:"",
	content:""
	})
}
```
