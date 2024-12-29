# localStorage

local Storage is a way to save data into our browser so we don't lose them after a refresh or after we close the tab, its really good with dark mode or data that need to persist inside our page, for example a to do list app

> adding items

we use the method, `.setItem` which takes two parameters, the first one is the name of the item, the second is the actual data that we want to store, note that the data must be a string, we can use JSON:

```js
function getItems(id){
const StoredData = JSON.parse(localStorage.getItem("data")) || [];
localStorage.setItem("data",JSON.stringify([id,...StoredData]));
}
```

this really good example, where we get the items from our storage data that we create, and then spreading this array when we are adding the new items (which is the id), and because at first it will be undefined, we use the `||` or operator, to say that if we don't have that then we use an empty array

> checking if items exist

we can add an extra code to check wether that id already exist in our array or not using the array method `indexOf` which will return if true the index of an element, otherwise it will return `-1`:

```js
function getItems(id){
const StoredData = JSON.parse(localStorage.getItem("data")) || [];
if(stroedData.indexOf(id) === -1){
	localStorage.setItem("data",JSON.stringify([id,...storedData]));
}
}
```

so here im only adding if i don't have the index (id) of that array (storedData), so if it does exist, this will return false and won't exeucte

> deleting item

we can delete item from our local stroage using the filter array method:

```js
function deleteItem(id){
localStorage.setItem(
"data",
JSON.stringify(storedData.filter((item)=> item !== id))
}
```

the filter array method will return false, and that will make the item be removed

