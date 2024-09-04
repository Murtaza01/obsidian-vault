
to delete every document in our collection we use:

```js
db.collcectionName.deleteMany({})
```


> removing one item from collection 

we can do that using the `updateOne` and `$unset` like this:

```js
updateOne(id, {$unset:{name:"bob"}})
```

this will first fine the object that has that id and remove the property with key name and value bob

> using find returns a cursor 

when you want to display a lot of items or all of your data, you can use `find`, however find will returns a cursor and not an array, in order to make it return all the items you need you need to give it the `toArray` method:

```js
db.users.collection.find().toArray()
```

