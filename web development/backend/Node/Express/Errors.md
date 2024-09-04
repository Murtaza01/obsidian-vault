# catch all route

we can handle a catch all route that will be used if the user entered an incorrect route, using the following code:

```js
app.use((req,res)=>{
	res.status(404).send("Error Page Not Found")
})
```

we use this code in the end 