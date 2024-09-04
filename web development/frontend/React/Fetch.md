
in order to connect to a backend (a server) in react, we have to first create our server, using `node.js` usually with `express.js`, then after having the backend separate from our front end, we can connect the two

# [fetch()](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

is a JavaScript browser function, that helps you send a request to a server, it returns a promise, which is either true or false, it takes time, so we need to use `async`  function

in react we can't use async function on our components, so we either use `.then` syntax, which is an alternative, or we use it inside a function

in order to not make a loop in our react component, we have to use `useEffect`  hook, see the below example:

![[infininte react loop.png]]

when i fetch the data and get a response back, then i put that response inside my updating function, this will re execute the component, which in turn will send another request and then update the `places` which in turn will cause a re execution, which will create an infinite loop

# useEffect

i can't use the async function with my `useEffect` callback function, so instead we use this:

```jsx
useEffect(()=>{
	async function fetchingData(){
		const respones = await fetch("localhost:3000/home")
		const data = await respones.json()
		setData(data)
	}
	fetchingData()
},[])
```

in here im creating a new function that will fetch the data, then im calling it inside my useEffect hook, and this code will only run on the site start

# handling loading time

when we fetch data using the above method, we don't get an immediate response, so there will be a loading time, even though our front end is working, the data is not yet finished loading, so in this case, we need to create a state that will update the UI to say 'your data is loading', maybe even use a loading icon, to do that we use this:

```jsx
const [loading,isLoading]= useState(false)
useEffect(()=>{
	async function fetchingData(){
		isLoading(true);
		const respones = fetch("localhost:3000/home");
		const data = respones.json();
		setData(data);
		isLoading(false);
	}
	fetchingData();
},[])
```

in this function, i will put my state to be true when it is loading, and set it to false when it finishes fetching data, this function is an `async` function, *which means code will execute line by line* !

# handling Errors

when fetching data we should handle errors that might occur if the fetching fails, so in order to do this we have to use `try/catch` block to try a code and catch if an error exist.

using our code above, we simply need to teak it a bit so that we can handle the error:

```jsx
const [error,setError] = useState()

useEffect(()=>{
	async function fetchingData(){
		isLoading(true);
	
	try{
		const respones = fetch("localhost:3000/home");
		const data = respones.json();
		setData(data);
		if(!respones.ok)throw new Error("couldn't fetch data")
	} catch (error){
		setError(error)
{/* we can make it even better using this syntax*/}
	setError({meseage:error.message || "something wrong happend" })
	}
		isLoading(false);
	}
	fetchingData();
},[])
```

we will take the code line by line:

```jsx
if(!respones.ok)throw new Error("couldn't fetch data")
```

when we don't use the try/catch block, our `new Error` object will crash our application so we need to use try and catch with this, this is needed in the try block, for the catch to execute, it will need a condition, this is the condition, defined using the `throw` function

```jsx
setError({meseage:error.message || "something wrong happend" })
```

this will set our error message to either the error message in the object, or our custom message, because sometime the error is not recognized, then we can access it using the state (`error.message` in this case)

# outsource the fetch function

we can make a standalone file for the fetch function so we can reuse it in our application, the syntax would look like this

```jsx
{/* fetch.js */}
export async function fetchData(){
	const respones = fetch("localhost:3000/home");
	const data = respones.json();
	if(!respones.ok)throw new Error("couldn't fetch data")

	return data
}
```

then we can import this as a helper function in our components like this:

```jsx
import {fetchData} from "../fetch.js"

useEffect(()=>{
	async function fetchingData(){
		isLoading(true);
	
	try{
		const data = await fetchData()
	} catch (error){
		setError(error)
		}
},[])
```