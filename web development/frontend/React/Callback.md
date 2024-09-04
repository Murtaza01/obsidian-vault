useCallback is a react hook that works to prevent functions from re-creating on every render, this is not only good for optimiztion, but sometimes needed when using a function as a dependency, because function are re-created on every render, we can't use them with dependency unless we use `useCallback` function

it works by saving the function you give it in memory, so that it doesn't need to re-create it everytime, and so that it can be used as a dependency because its place won't change in memory 

it takes two arguments, the first is the function that you need to store in memory, the second is the dependency, just like the useEffect dependency, its an array, that will execute based on changes that happen to that dependency

> syntax

```jsx
const handleClick = useCallback(function handleClick(){
	setIsopen(false)
},[])
```

here we are wrapping our function with a the hook `useCallback` and getting the value of this as a function, but this time this function that we get as a value is stored in memory and not re-created 

there is an easier syntax with the anonymous function:

```jsx
const handleClick = useCallback(() => {  
console.log('Clicked!');  
}, []);
```