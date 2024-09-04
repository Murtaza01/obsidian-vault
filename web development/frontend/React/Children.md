we use children in react to have nested components, in order to do that, we simply nest a component inside a parent component that has a children prop:

```JSX
<Parent>
	<Child />
</Parent>

function Parent({children}){
	return <div>
	{children}
	</div>
}
```

we can use multiple children inside a parent component, and this will create an array of objects, we can select based on the index:

```jsx
<Parent>
	<Child1/>
	<Child2 />
</Parent>

function Parent({children}){
	return <div>
	{children[0]}
	<p>
		{children[1]}
	</p>
	</div>
}
```

# React.Children
