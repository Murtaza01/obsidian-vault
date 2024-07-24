# Training

- [x] test useEffect
- [x] test localStorage

> setInterval to stop at a fixed number

we can do that with the following code:

![[setInterval x useEffect.png]]
for some reason there is an issue putting an if statement inside the setCount function, so i had to use the `question mark` and another problem i faced was putting curly braces which seemed to crash the code, so i did it inline

> adding and resting localStorage

i did that using the following code:

![[localStorageExample.png]]

# what i learned

> filter an array using query 

we can filter an array based on the query the user give, and make it dynamic so as every key stroke would give result

```jsx
const [searchQuery, setSearchQuery] = useState("");

  function handleQuery(e) {
    const query = e.target.value;
    setSearchQuery(query);
  }
	return <>
<input type="text" value={searchQuery} onChange={handleQuery}/>

{data.filter((item) => {
    const name = item.name.toLowerCase();
    const value = searchQuery.toLowerCase();
    return name.startsWith(value);
}).map(()=>{
	return <Data></Data>
})}
</> 

```

in the above example, we have a state that manage the `searchQuery`,  we take advantage of the two-key binding, that update the UI on every key stroke, and filter the array data with `array.filter` 

what will it do is this: loop through the array for `names` using the first value (from our query) and use it to filter the array, then it returns every `name` with the query the user put

>  show a fixed amount of an array

we can do that using the slice method, with the ability to increase, see this code:

```jsx
 const [shownItems, setShownItems] = useState(10);

data.slice(0,shownItems).map(()=>{...})
```

this would only map (and return) the first 10 items, ideally there would be a button that will increase that amount, it won't cause an error if the amount goes beyond the array length.


> disable a button based on a condition

we can do that using the disabled property and button the condition:

```jsx
disabled={ShownItems >= data.length}
```
this will only disable it if the condition is true, otherwise it is enabled

> style dialog component

when styling the dialog component, we need to be careful, putting a parent element will block its functionality , so it must be the first element, because it has a width of `100vw` and a height of `100vh`

> using || 

we can use the `OR` symbol to effectively render on condition:

```jsx
const [cartItems, setCartItems] = useState(storedItems || []);
```

> show/hide nav on scroll 

we can do that using the following [code](https://stackoverflow.com/a/71356027/20940799):

```jsx

const [showHeader, setShowHeader] = useState(true);
const [lastScrolledY, setLastScrolledY] = useState(0);

function onScroll() {
    if (window.scrollY > lastScrolledY) {
      setShowHeader(false);
    } else {
      setShowHeader(true);
    }
    setLastScrolledY(window.scrollY);
  }
  useEffect(() => {
    addEventListener("scroll", onScroll);

    return () => {
      removeEventListener("scroll", onScroll);
    };
  });
```

