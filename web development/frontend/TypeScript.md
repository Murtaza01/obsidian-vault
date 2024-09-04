
is a programming language built on top of JavaScript as a way to have a better JavaScript, because JavaScript runs only on the browser, it doesn't show you any errors unless you use the browser, with typescript you can see errors before hand because it doesn't depend on the browser

you can add types to your variables and functions, instead of declaring a variable without any type, the type option will save more memory and will prevent errors, this is also called *static typing*

# static typing vs dynamic typing 

a static typing is where you have to declare the type of your variables and functions, it checks the type `at compile-time` 

the dynamic one like in JavaScript and python, you don't have to mention the type of your variables, they check the type `at run-time`

# Types

there are three types in JavaScript:
1. primitive (strings, number...)
2. array and objects
3. functions and parameter
4. type `never` which means the array or object must be empty

> primitive 

```ts
const age:number = 12;
const name:string = "mike";
const isNice:boolean = true
```

> array and objects

```ts
const hobbies:string[]= ['hobby1','hobby2']

// this is not defining an object but rather assigining  
const person:{
name:string,
age:number
}

person = {
name:"mike",
age:21
}
// array of objects
const people:{
name:string,
age:number
}[];
```


you can change the type of a string into a number using the `+` sign 
# Type Inference

`TypeScript` will try to guess the variable you used, without the need of you explicitly assigning it:

```ts
let name = "mike"
// name is of type string

name = 21
// error, cannot assing number to type string
```

# Union Types

when you want to assign different types to a variable you can do that with the `|`:

```ts
let hours: numbers | string = 2
hours = "two"
// no error !
```

# Type Aliases

sometimes you repeat yourself because you define the same types with different modification, in this case we can use an aliases, using the type keyword that is provided by typescript to have a type definition:

```ts
type Person = {
name:string,
age:number
}

const person:Person = {
name:"mike",
age:21
}

const people:Person[]=[
{name:"mike",
age:21
}
]
```

# Functions Types

parameter and the return value of function do get types:

```ts
function add(a:number,b:number){
return a + b
// this will infer to number type by defualt
}

// we can change that and add return defiention:
function add(a:number,b:number): number | string {
return a + b
}
```

# Generics

when we want to generically add types to functions, so that the two parameter take strings at one time, and numbers at another, we can use the generics syntax:

```ts
function add<T>(a:T,b:T){}
```

![[Typescript generics.png]]

if we didn't define a generic on the function, typescript wouldn't type our `updatedArray` into a number of array, rather it would type it as any, the same with the `stringArry` thus losing the safety of typescript


# type casting

when you know that the variable hold a certian type you can simply cast that type using the `as` keyword:

```tsx
const input = document.getElementById("1") as HTMLInputElement
```

this type `HTMLInputElement` is a default typescript type, because typescript doesn't know which element im using with the `getElementById` i end up typing it explicitly

```tsx
function onSubmit(event:React.SynthaticEvent){
// 
	const target = event.target as HTMLInputElement
	setValue(target.value)
}
```

in the code above i cant use `event.target.value` because typescript doesn't know what is the target. this is why i need to type it first then use it.
# React

when using it with react i simply define the props parameter:

```tsx
type items = {
	string[]
}
function App({items}:Items){}
```

# using it with class

we can use typescript along side classes (in javascript) that will act as a type model for our data.

consider having a posts object, that object will be a key value pair of id comments likes, in this case we would make a model for this data, we create a folder name model in it we create a typescript file that would hold these:

```ts
class Post{
id:string;
commnets:string;
likes:number;

constructor(commnets:string,likes:number){
	this.id = uuid();
	this.comments = commnets;
	this.likes = likes
}
}
```

our constructor will initiate these (id, comments..) with the type already there, in order to make a new posts in our post array, we simply use the `new`:

```jsx
import post from "./models/post"
function Posts(){
	const posts = [
	new post('this is comment',4),
	new post('hi',7)
// this will be {id:randomly genrated,commnts:hi,likes:7}
	]

	return <>
		<NewPosts posts={posts} />
	</>
}
```

we can then use this class as a definition for our class:

```tsx
import post from "./models/post"
function NewPosts({posts}:post[]){}
```

this class will act as a way to tell typescript which shape our data will be

# with refs

when we use refs with typescript we need to do additional things:

```tsx
const input = useRef<HTMLInputElement>(null)
```

we need to provide the generic type and a default value to it

> ! in typescript

sometimes the `?` mark is used to indicate that a value might be null:

```tsx
function handleSubmit(){
input.current?.value
// type will be either string | undefined
}
```

if we know that this will never be the case (that the value will always exist after the user hit submit) we can use the `!` mark :

```ts
function handleSubmit(){
input.current!.value
// type will be string
// this tells typescript that the value will never
// be null 
}
```

# type as a function 

if we have a prop and its type is a function we can set it like this:

```tsx
function child({onSelected:()=> void}){}
```

this `onSelected` is a function that is coming from a parent function and will not return anything (hence the keyword void)


# notes 

we can ignore the error on `this element/object could be null` by adding an `!` in-front of our variable:

```tsx
const button = document.querySelecter("button")!;

button.addEventListener(...)
// 
```

if we didn't add the `!` typescript will raise an error saying that this button might not exist, because it doesn't really look into html, it just sees this line and evaluate it

