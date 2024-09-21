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
