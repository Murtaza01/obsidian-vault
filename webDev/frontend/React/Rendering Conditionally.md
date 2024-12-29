>using if / variable 

we can use an alternative to rendering a element conditionally, see the code below:

```jsx
fucntion App(){
const [element,setElement] = useState(false)

let content = <h1>hello world</h1>;

if (element){
	content = <div>
	<h1> bye abbys </h1>
	</div>
}

return <>
	<button onClick={()=> setElement(true)}>click me</button>
	{content}
</>
}
```

this by default will return the first content, if element is true it will update the content value and return a different `jsx`, this is allowed since we are not changing variable itself 