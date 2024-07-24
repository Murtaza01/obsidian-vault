we use context to pass down a state or data into our components without the need for props, why you might ask ?

because sometimes we don't want to pass data to our nested components, this is called prop drill: which is when we pass our state for example that is needed by all components, into every component and nested component

> convention

it is the convention to make a folder called "store" that has a jsx file, which at the end would have context, for example `shopping-card-context.jsx`

we also start  the constant with a capital letter, because it would be a component wrapper inside our app component

and whenever we add something to the object inside our app function, we should write it in our createContext file, so that we get auto completion

```jsx
import {createContext} from "react"

export const CartContext = {
	items:[],
	addItemsToCart:()=>{},
	updateQuantiy:()=>{}
}
```

note that these are the default values, and cannot be changed, so they are used just as an indicator

> createContext

we use this syntax to create a new context for our app components:

```jsx
import { createContext } from "react"

export const Context = createContext({
	item:[]
})
```

inside our app component we use the createContext like this:

```jsx
import {Context} from "./store/shopping-card-context.jsx"
function App(){

const [shoppingItems,setShoppingItems] = useState({items:[]})

return <Context.provider value={shoppingItems}>
	<Header>
	<Shop>
</Context.provider>
}
```

we need the value property inside our wrapper component, the default value would be helpful in providing an auto complete, the default value is the value we give to the initial object

inside our children component, we can access the object we provided using the `useContext` hook, which we will give the object of `createContext` that we import from our file 

```jsx
import {useContext} from "react"
import {Context} from "./store/shopping-card-context.jsx"

function Shop(){
	const {items}= useContext(Context)
}
```
items is the value i gave inside the value property of my wrapper, i then im able to use the items (which is a state) whenever i would like, on whatever component

> linking state to context

when we link our state to our create context wrapper, we can only read it and not edit the state, if we want to edit the state provided by our wrapper, we use this syntax:

```jsx
function App(){

const [showAccordion,setShowAccordion] = useState(false)

function handleClick(){
	setShowAccordion((prev)=> !prev)
}

const ctxvalue = {
	show:showAccordion,
	onClick:handleClick
}
return <Context.provider value={ctxvalue}>
	<Header>
	<Shop>
</Context.provider>
}
```

this is the way of linking a state to a context, we add an object that will has the value of our state, and the functions that is related to our state, and then we simply send that object into our provider so it can be used anywhere

> creating separate component for context

if we have a bloated App component, we should create a separate component with all the logic that the App component has, it would be a context component that pass down all the states/function that the site need

so in the same file we create our context, `/store/context.jsx` we create the component:

```jsx
import {createContext} from "react"

const context = createContext({
	items:[],
	addItemtoCard:()=>{},
})

function contextProvider({childern}){

{/* all the logic from App component here */}

const contextValue= {
	items:shoppingList,
	addItemtoCard:handleClick,
}
return <context.provider value={contextValue}>
	{childern}
</context.provider>
}
```
this component will function as a wrapper for our context value, we are doing the same thing for the context creating, but we are simply doing it in separate component