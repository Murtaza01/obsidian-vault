 >displaying an images
 
 we should display an image by importing it instead of give a specific path, because this way it won't be lost when we deploy our site, and the `src` code of our image will be dynamic:
 
```JSX
import image from "./assets/image.png"

<img src={image} alt="" />
```

> using CSS import 

when importing a CSS into our `jsx`, this  CSS  won't be only scoped to this `jsx` component only, but rather to the whole page, so if you make a CSS file for the header, that CSS  will be global to your whole page, unless you change the name of the classes and ids you use in your CSS

> Styling conditionally

when we style an element conditionally, we don't use the `&&` (and operator), we use the ternary operator, because when we use the `&&` operator, the default value would be the function, not undefined:

```jsx
<h1 style={{color:isClicked ? "red": "blue"}}>hello world</h1>
```

> Ternary Expression Shortcut

if we have an expression, where we want to check if the value is true then output it, and if its not then output something else, we would use this shortcut:

```jsx
{isClicked ? isClicked : "not Clicked"}

==> {isClicked ?? "not Clicked"}
```

this is saying, if `isClicked` is true, output it, if its false, then output the string

> sending a prop to a higher component

usually we would send a prop from a parent component to a child component, but what if we wanted to send a prop to a parent component from a child component ? 

in this case we use a function that will take the value we need, we need to put that function into the parent component, and then use it in the prop, executing it will return the value to the parent component:

```jsx
function App(){

function handleCount(value){
	{/* value would be the count,  */}
}

return <>
	<Child handleCount={handleCount}></Child>
</>
}
```

the child component would look like this:

```jsx
function Child({handleCount}){
const [count,setCount]= useState(0)

return <>
	<button onClick={()=>hanldeCount(count)}></button>
</>
}
```
