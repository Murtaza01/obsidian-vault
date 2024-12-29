the useEffect hook happens *after* every render of your functional component, every time the component is re-rendered it get executed, it makes it valuable choice when:

> asynchronous tasks 

which is tasks that needs time to happen, for examples; fetching data (getting data from an api, which might takes time)

> tasks that doesn't effect the render-cycle

- [x] for examples putting items into our local storage, this task doesn't require a re-render, because it won't effect our output, the returned `JSX` value, this is why its called a side effect, because it doesn't directly effect our `jsx` return value
Wrong !

for example using setTimeOut and setInterval functions

# dependencies

dependencies is way to control how much our function inside side effect execute, we can put a state that will execute each time the state is changed, or we can only execute the function once `onMount` leaving the dependencies empty:

```JSX
function App(){
	useEffect(()=>{
		navigator.geolocation.getCurrentPosition((pos)=>{
		return pos.cooreds.langitude
		})
	},[])
	}
```

for example the code above will execute only once the app is opened, `onMount`, the code above will ask for the location of the user, and return the longitude

if we didn't use an empty array, it will execute this function (asks for user location) every-time the app gets re-rendered, and if we didn't use `useEffect` we would run to the same problem, `useEffect` here makes this code execute only once the app is opened

> assigning functions as dependency

when we assign functions as dependency we might run into an infinite loop, because every time our time re-render, our functions are re-created and they would be new functions (different place in memory)

with this problem we can use a special hook `useCallback` to avoid re-creating the function that our useEffect hook depend on


# returning function

useEffect can return a function that will execute before the execution of our hook (useEffect) or before the component exit the DOM:

```jsx
function deleteConfirmation(){
	useEffect(()=>{
	const timer =setTimeout(()=>{
		onConfirm();
	},3000)
	return ()=>{
		clearTimeout(timer)
	}
	},[])
}
```

# stop effect from starting at the beginning

if you don't want your `useEffect` to run in the first render (when you open the app) but rather after one render (when the user interact with the ui), we can use a variable:

```jsx
let isInitial = true;

function App() {
  useEffect(() => {
    const sendCartData = async () => {
      const response = await fetch(
        'https://react-http-6b4a6.firebaseio.com/cart.json',
        {
          method: 'PUT',
          body: JSON.stringify(cart),
        }
      );
    if (isInitial) {
      isInitial = false;
      return;
    }
    sendCartData()
      
  }, [cart]);

```

using a variable that will change only after the second execution of the function !