
# memo

memo is a react hook that is used to prevent unnecessary executing of a component function

it works by checking if the prop we are sending to this child function changed, and if it is then and only then the function re-executes

we use it by wrapping our component with the function memo, we shouldn't use it a lot because it then hinder performance

# useMemo

just like memo, it is used to prevent unnecessary executing of a **Function** instead of a component function

it works by checking wether the function has a state that changes so we could pass it as an array dependencies, if we didn't put any dependency, the function will never get executed

```jsx

function isPrime(value){
	if (value % 2 !== 0){
	return true
	} else return false;{/*or nothing because thats falsy*/} return;
}

function App(){
const [count,setCount]=useState(0);

memo(()=> isPrime(count),[count])
}
```

this function `isPrime` will only get executed when the count is changed
