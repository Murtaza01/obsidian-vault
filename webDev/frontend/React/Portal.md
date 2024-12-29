CreatePortal is a function that changes where the element is render inside the tree component, we can choose whatever place we want, this is beneficial for modals, it takes two parameters, the first is the element that we want to change its place, and the second is the place:

```JSX
function Modal(){
return CreatePoral(
<>
	<dialog>
	<div>
	<p>hello world</p>
	</div>
	</dialog>
</>, document.getElementById('Modal')
)}
```

in our html we would have a div next to our root div that we would call the same as the element we want to change position:

```html
<div id="modal"></div>
<div id="root"></div>
```

[see](https://semaphoreci.com/blog/react-portals) for more info