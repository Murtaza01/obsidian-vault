> spreading props

we can use props to access all the data inside an array of data that we have on a separate file using the syntax below:

```JSX
import appData from "../appData.js"

<Header 
{...appData[1]}
/>
```

in this case we only getting the first index, which is an object, that we are spreading into the curly , which gets all the keys out and send them as props, this will name them exactly like they are named in the object

> props.children

we can put elements/text into our components and rendering them using the props.children parameter:

```JSX
<Header>Hello Wrold</Header>

{/* the Header.jsx */}

function Header({children}){
	return <div>
	<h1>children</h1>
	</div>
}
```
we can't do this normally without using the pros.children, so when using the opening and closing tag of a component and we want to nest elements or text inside them, we must use children to render them

> naming functions as props

to name functions that we pass as props and that handle an event, such as clicks and change (value), we simply use on in-front of the event ex: onClick / onSelect

> sending a function as prop

we can send parameters with the functions as props, we can access those parameters inside our component props, here is an example:

![[props functions.png]]

we are sending a different parameter each time we click a different button, these parameters will serve as an identifier, so we know which button is clicked

> spreading props

we can use spread operator for objects to spread the content and not repeatedly name the same name of the prop and key, here is an example:

```JSX
{data.map(()=>{
return <Header
	key={item.key}
	title={item.title}
	image={item.image}
/>
})}

{data.map(()=>{
return <Header
	{...item}
/>
})}
```

the names will remain the same as the object name, and we can access every key from that object in our `Header` component

>key as string

we can give the prop `key` a string that is unique and it will work the same as giving it an id, but it must be unique

> forwarding props

using the rest operator (seen in the parameter list) we can group the remaining props and then spreading them inside our element to be used:

![[forwarding props.png]]

> sending a dynamic element (using a component identifier)

using props, we can send elements or components, that we can use in our function (component), so that for each time we use this components, we can render a different element or a custom element:

```jsx

function Section(){
return <Tab 
	buttonContainer="menu"
	Container="main"
/>
}

function Tab({buttonContainer,button,Container}){

const ButtonContainer = buttonContainer;

return <>
	<Container>
	<ButtonContainer>{button}</ButtonContainer>
	</Container>
</>
}
```

we have to put that `string` into a new const that will make it as a custom component, if we didn't, it won't render anything because react won't recognize that element `menu` without it being upper cased, or we can simply name the prop as an uppercase element like for the `</Container>` element

> default props

we can set default props in our function component to display whatever element we want without sending a prop, here is an example from the above:

```jsx
function Tab({button , buttonContainer = "menu"}){

return <>
	<ButtonContainer>{button}</ButtonContainer>
</>
```

here `buttonContainer` would be a menu element by default

> two way binding

this is used with inputs, when you want to save the value of the input, we can use state and `onChange` function, see the code below:

```JSX
const [playerName,setPlayerName] = useState("Player 1")

function handleChange(event){
	const {value} = event.target
	setPlayerName(value)
}

return <>
	<input type="text" value={PlayerName} onChange={handleChange}>
</>
```

> all other props

when we don't know how many props you get from a certain element, we use the spread operator in our parameter, and use them inside the function:

```JSX
function Input({label,...props}){
	return <p>
	<label>{label}</label>
	<input {...props}>
	</p>
}
```

in this spread operator, everything is send to the input function is put inside the input element