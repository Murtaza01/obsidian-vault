> why we use `useState()`

the reason why we can't update a variable inside jsx, is because react components are functions, and functions are only executed once, so when we try the following code:

```JSX
let num = 1;

<button onClick={num+1}>
{num}
</button>
```

this will only show the initial num (1), but won't update it, because in order to update it we have to execute the function (component) again

when we use `useState()` the function of `useState` will change that behavior, it will **render** the component function, thats why we are allowed to use `const` when storing the initial value of `useState` 

`useState()` will re-execute the function (component) that it is used in, if there is a component inside that parent component, it will re-execute that function too !

> Updating State

when we update state, you should use this syntax:

![[Updating State.png]]

> state is scheduled

the state function we get from `useState` doesn't update right away, but rather it scheduled the update, consider this example:

```jsx
function handleClick(newCount){
	setCount(newCount)
	console.log(count) {/* this will log the old count */}
}
```

in this case the old count is consoled, and not the newly set one `newCount` because 