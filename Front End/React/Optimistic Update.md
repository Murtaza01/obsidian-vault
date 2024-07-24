when we have a `PUT` method and we edit a post, we want to reflect those changes immediately, so that the user doesn't have to refresh the page to see those changes, plus there is an additional problem, that the backend might fail to provide those data so we must put the old post back instead of  giving an error

we can do that with a couple of steps using the `onMutate` which takes callback function that will have the `queryClient` object to allow us to manipulate our query and cache: 

```jsx
const {mutate} = useMutate({
mutateFn:updatePost,
onMutate: async (data)=>{
	const newPost = data.formData
	await queryClient.cancelQueries({queryKey:["posts",id]})

	const oldPost = queryClient.getQueryData(["posts",id])
	queryClient.setQueryData(["posts",id],newPost)

	return {oldPost}
},
onErorr:(data,error,context)=>{
	queryClient.setQueryData(["posts",id],context.oldPost)
},
onSettled:()=>{
	queryClient.invaildateQueries(["posts",id)
}
})

function handleClick(formData,id){
	mutate({id,formData})
}
```

> onMutate

a function that takes a callback function and is executed while the request `mutation` happens, it has the data that we pass on the `mutate` function that we get from the `useMutate` 

> setQueryData

because we want to control the query behavior manually, we need to use this method to update the our query, it expect two arguments, the first is the id that we want to update, the second is the data, which we are getting from the `onMutate` function

> cancelQueries

in order to manipulate the query manually we need to cancel the other query running, so that it doesn't clash, this will not stop the mutate function but only the `useQuery` function, that is involved with getting data

it returns a promise so we need to use await in front of it, and it expect the `queryKey` that we need to stop

> getQueryData

if the mutation fails, we don't want to display an error, we want to give the old data back, in order to do this we can use this method that will return the old data to the `onMutate` function which we will use on the `onError` function

> onError

triggered when there is an error, in this case we are updating the data to our previous data using the argument provided by the `onError` function, which in this case is the `context`

> onSettled

a function that will trigger whether the mutate fails or succeed, this step will insure that the data from the backend is in sync with our data in the front end