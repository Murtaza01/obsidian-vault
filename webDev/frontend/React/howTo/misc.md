#  show a fixed amount of an array

we can do that using the slice method, with the ability to increase, see this code:

```jsx
 const [shownItems, setShownItems] = useState(10);

data.slice(0,shownItems).map(()=>{...})
```

this would only map (and return) the first 10 items, ideally there would be a button that will increase that amount, it won't cause an error if the amount goes beyond the array length.

# disable a button based on a condition

we can do that using the disabled property and button the condition:

```jsx
disabled={ShownItems >= data.length}
```
this will only disable it if the condition is true, otherwise it is enabled

