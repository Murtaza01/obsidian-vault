
# why use it?

redux is similar to react context, it provides states the whole app.

we use it because sometimes we have a complex state, and we do not want to split that state into multiple react context, and we care about performance, because react context is not meant for high render appliactions.


# how it works

redux stores data in one state for the whole app, components do not directly interact with that data, they subscribe to the store (redux), and whenever a state changes, the store notify and send the data to components

> how does the state change

in redux we use the reducer function.

in JavaScript a reducer function reduce the input and spit our a different output, for example the native array reducer function, which takes numbers and give the sum of those numbers.

that reducer function will mutate our data and change it, and send those changes to our store.

> Actions

because our components have no direct contact with the store, the only way to interact with our data in the store is with reducer.

to trigger the reducer function the components send a `dispatch` to it, then the reducer will mutate the old data in store and change it according to the `dispatch`

then and only then the data in our store is changed, and the store sends the new data to the component.

![[How Redux works.png]]

# how to use it

we use redux by importing it, and then creating a function for the reducer which will act as the value for our store, so that the changes made to the store via the reducer function, i will divide the steps for how to use redux:

> createStore

```js
import redux from "redux"

redux.createStore();
```

> create reducer function and pass it to the store

```js
import redux from "redux"

const counterReducer = (state,action) => {
	return {
	counter: state.count + 1
	}
}

redux.createStore(counterReducer);
```

here im using a anonymous function because i want the value of that function, instead of making this syntax [[Reference]], i will need a default for the state on the first run of the code:

```js
const counterReducer = (state = {counter:0},action) => {
	return {
	counter: state.count + 1
	}
}
```

> create subscription


```js

const store = redux.createStore(counterReducer);

const counterSubscriber = ()=>{
store.getState()
}
```

this will give us the latest state snapshot after it is being updated, however we need to tell redux aware of this function, using the subscriber method on the store:

```js
const counterSubscriber = ()=>{
store.getState()
}

sotre.subscribe(counterSubscriber)
```

i simply reference the function i made which in turn will get the latest state snapshot.

> dispatch 

in order to update the state in our store we need actions (dispatch meaning sending something) we use the dispatch method, which takes an object and a key of `type` that describes what this action will do:

```js
store.dispatch({type:"incremnt"})
```

we can use the type to determine which action we are going to take in our reducer function:

```js
const counterReducer = (state = {counter : 0},action)=>{
	if(action.type === "increment"){
	return { counter: state.counter + 1 }
	}

	if(action.type === "decrement"){
	return { counter: state.counter - 1 }
	}

	return state
}

store.dispatch({type:"incremnt"})
store.dispatch({type:"decrement"})
```

> All steps above

```js
import redux from "redux"

const counterReducer = (state = {counter : 0},action)=>{
	if(action.type === "increment"){
	return { counter: state.counter + 1 }
	}
	return state;
}

const store = redux.createStore(counterReducer)

const counterSubscriber = ()=>{
store.getState();
}

store.subscriber(counterSubscriber)

store.dispatch({type:"increment"})
```

# using it in react

> providing the store

to use redux in react we need to download another package along side redux, which is `react-redux` package that can link react and redux.

then we create a folder named `store` in that folder we create a file `index.js`, inside that file we write and export our store.

in our highest level component (usually the index.js) we want to import provider from `react-redux` and then wrap this provider with our app:

```jsx
import Porivder from "react-redux"
import store from "./store/index.js"

ReactDOM.createRoot(document.getElementById('root')).render(
  <Provider store={store}><App /></Provider>
)

```

> useSelector

in order to get the data from the store, in our components we use a hook provided by `react-redux` package called `useSelector` to get a specific data in our store

using this hook will automatically subscribe our component and get the latest state snapshot:

```jsx
import { useSelector } from "react-redux"
function Counter(){
	useSelector( state => state.counter )
}
```

the `useSelector` hook will get back a state, and we are selecting which property of that state we want (in this case it is counter):


```jsx
import { useSelector } from "react-redux"
function Counter(){

const counter = useSelector( state => state.counter )

return <>
	<h1>{counter}</h1>
</>
}
```

> useDispatch

we can also send actions from our component to the store to execute a certain code, using another hook from the `react-redux` package, and using it in our component:

```jsx
import { useSelector,useDispatch } from "react-redux"

function Counter(){

const counter = useSelector( state => state.counter )

const dispatch  = useDispatch()

function handleIncrement(){
	dispatch({type:"Increment"})
}

function handleDecrement(){
	dispatch({type:"Decrement"})
}
return <>
	<h1>{counter}</h1>
	<button onClick={handleIncrement}>Increment</button>
	<button onClick={handleDecrement}>Decrement</button>
</>
}
```

> action payload

usually we use dispatch action like this:

```jsx
function handleIncrease(){
	dispatch({type:"increase", amount:5})
}
```

and in our store file we have the following code:

```js
const counterReducer = (state = {counter:0},action)=>{
	if(action.type=== "increase"){
	return {
		counter: state.counter + action.amount;
		}
	}
}
```

usually we would have different data that we manage:

```js
const initalState = {counter:0, showCounter:true}

const counterReducer = (state = ,action)=>{
	if(action.type=== "increase"){
	return {
		counter: state.counter + action.amount,
		showCounter: state.showCounter
		}
	}
	if(action.type === "toggle"){
	return {
		showCounter: !state.showCounter,
		counter: state.counter,
		}
	}
}
```

we need to provide our state each time we return it, so if we have multiple state, we need to write them down with their default value `state.something` 

because redux will use those return values to replace the existing state, so it should be the same as the initial state.

# using [toolkit](https://redux-toolkit.js.org/) 

redux toolkit make a lot of things easier, it first better manages our states and reducer function, lessen the code we have to write, and it helps with our dispatch action names,

> using it

we first need to install it via package manager, `@reduxjs/toolkit`, then we can simply import function in it.

> createSlice

this function allows us to slice our state, to keep our reducer function more organized

it take a name (for the slice) this name will serve as a handler for one state (if we have different states, and two or more connected with each either, they should be sliced), and it takes the state that we want to slice, and it takes the actions that are going to be in the reducer 

```js
import { createSlice } from "@reduxjs/toolkit"

const initalState = {counter: 0, showCounter:true}

createSlice({
name:"counter",
initalState,
// same as initalState = initalState
reducers:{
	increment(){},
	decrement(){},
	increase(){},
	toggle(){}
}
})
```

this reducers object can take our old state and manipulate it, here it is allowed to mutate our state because the toolkit does copy the state behind the scenes:

```js
reducers:{
	increment(state){
	state.counter++
	},
	decrement(state){
	state.counter--
	},
	increase(state,action){
	state.counter = state.counter + action.payload
	},
	toggle(state){
	state.showCounter = !state.showCounter
	}
}
```

> configureStore

we can use that to combine multiple reducers, because store takes only one reducers, this function will replace our `createStore` and we simply put an object of `reducer` that will take an object of reducers, the function will merge our reducers into one reducer function:

```js

const counterSlice = createSlice({
name:"counter",
initalState,
// same as initalState = initalState
reducers:{
	increment(){},
	decrement(){},
	increase(){},
	toggle(){}
}
})


const store = configureStore({
reducer:{counter: counterSlice.reducers, //anotherSlice: ...}
})
```

> dispatch with toolkit

now if we want to dispatch action, our `createSlice` handle this for us, it has a method called `actions` that we will export to our component and from there we can use the method that we defined in our reducers object.

```js
const counterSlice = createSlice({
name:"counter",
initalState,
// same as initalState = initalState
reducers:{
	increment(){},
	decrement(){},
	increase(){},
	toggle(){}
}
})

export const counterActions = counterSlice.actions
```

and in our component we simply use that with the methods:

```jsx
import { useDispatch } from "react-redux"
import { counterActions } from "../store/index"

const dispatch = useDispatch()

function handleIncrement(){
	dispatch(counterActions.inreacment())
}
```

this method will automatically add an action type.

if we have an action that we want to dispatch, we can use the method parameter, however the name of the object that is send through the dispatch will always be `payload`:

```jsx
function handleIncrease(){
	dispatch(counterActions.increase(10))
// {type: Uniqe_idenitfier, payload: 10}
}
```

this `10` will always be the value of the key `payload` so when we want to extract it inside our slice we use payload:

```js
increase(state,action){
	state.counter = state.counter + action.payload
	}
// this code is from above example
```

# [Thunks](https://redux.js.org/usage/writing-logic-thunks#what-is-a-thunk) 

when we want to write async logic using redux we usually use `thunks` actions, it is a function that returns an async function with a dispatch action:

```js
export function sendCartData(cart){
	return async (dispatch)=>{
		dispatch(uiActions.showNotifictions())
	}

	const response = await fetch('http//...')
	const data = await response.json()
}
```

there is a better way to handle error is to wrap our fetch code with a function and use try and catch on it:

```js
export function sendCartData(cart){
	return async (dispatch) => {
		dispatch(uiActions.showNotifictions())
	}

	function async sendRequest(){
		const response = await fetch('http//...')
		const data = await response.json()
		// do something with data
		if(!response.ok){
		throw new Erorr('erorr')
		}
	}

	try{
		await sendRequest()
	}
	catch(err){
		//... error
	}
}
```

in order to use it we simply dispatch it in our component:

```js
import { sendCartData } from "./store/sendCartData"

function App(){
	dispatch(sendCartData(cart))
}
```

this will send an action to the logic we have in our function, it can also contain other dispatch action that will perform other dispatch actions

# using redux with localStorge

persisting data with redux is no easy job i learned, using either a  middle-ware or a package called `redux-persist` which will do that for you.