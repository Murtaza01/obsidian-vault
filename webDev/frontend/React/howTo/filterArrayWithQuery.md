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

