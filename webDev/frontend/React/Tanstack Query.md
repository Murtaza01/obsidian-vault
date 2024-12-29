a way to manage and simplify the fetching code you write, it has many features like caching (saving the fetched data so that you don't need to re-fetch) 

it simplify the code you write, instead of writing and managing the fetched code you have with (`isLoading` and `IsError`) states and `useEffect`.

however it does not send an HTTP request it only manage that request


# Query Client

in order to use react query we should wrap our parent component with the query client provider and use the client we get from instantiating a new client:

```jsx
import {QueryClient,queryClientProvider}
const queryClient = new QueryClient()

return <queryClientProvider client={queryClient}>
	<App />
</queryClientProvider>
```

# useQuery 

a hook that takes an object, this object is our configuration of how to manage the fetching:

```jsx
useQuery({
	queryKey:["posts"],
	queryFn: fetchPosts
})
```

> queryKey

is a key that will function as an identifier for our caching behavior, it is an array, that can be a string of a simple identifier

if we have a search term or a content that is dynamic (that changes every time a user interact) we should use it in our `queryKey`:

```jsx
useQuery({
	queryKey:["posts",searchTerm],
	queryFn: fetchPosts
})
```

so that when ever the search term is different a new query is instantiated


> queryFn

the fetching function that we use to fetch the data, note that we need to also manage the errors coming from that fetching function, and we are doing that in the `fetchPosts`

the `queryFn` sends some default object to our function, so that when we use a parameter in our function we should destruct that parameter and send it as an object, next to the abort parameter:

```jsx

useQuery({
	queryKey:["posts"],
	queryFn: ({signal})=> fetchPosts({searchTerm,signal}),
})
```

this signal property helps with the abortion of the fetch function, when we have two components, one that use the `searchTerm` and one that not, we need to use this syntax:

```jsx
function fetchPost({signal,searchTerm}){
if(searchTerm){
// do something
}

const res = await fetch("localhost:8080",{signal:signal})
}
```

note that you do get the `queryKey` inside your `queryFn`  so if you need it, you can pull it instead of providing it manually:

```jsx
useQuery({
queryKey:["posts",param.id],
queryFn:({signal,qureryKey})=> fetchPosts({...qureryKey[1]}),
})
```

im spreading the array of the `queryKey` then im accessing the second index `param.id` instead of repeating myself
# `staleTime,gcTime,enabled`

```jsx
useQuery({
	queryKey:["posts"],
	queryFn: fetchPosts,
	staleTime:5000,
	gcTime:10000
	enabled: false,
})
```

> staleTime

is the time that react query waits before sending another behind the scene request to update the data, by default its `0` but you can change that to prevent unnecessary  re-fetching

> gcTime 

is the time that react query wait before clearing the cache, by default its 5 minutes (50000) but we can change that

> enabled

is a way to stop react query from running on the go but instead whenever you like, when set to false it will be set as `pending`, if you don't want your loader to show when enabled is false, you can use the `isLoading` instead of `isPending` because the latter does check whether the query is enabled or not

# useMutation 

a hook that sends a post request to the backend, instead of using `useQuery` we use this because it is optimized for sending a post request, it takes a post request function and give back an object which has a mutate function that we can call to send the request:

```jsx
const {mutate,isPending,isError,error} =useMutation({
	mutateFn:createNewPost
})

function handleSumbie(data){
	mutate(data)
}
```

im simply passing the data into my mutate function which will send that data to the backend, with the request

> isPending, isError, error

we also get these with `useMutation` to check if the request is pending or not, and to check if we get back an error or not.


```jsx
const queryClient = new QueryClient()

const {mutate,isPending,isError,error} =useMutation({
	mutateFn:createNewPost,
	onSuccss:()=>{
	queryClient.invlidateQueries({queryKey:["posts"]})
	navitgate("/")
	}
})
```

> onSuccss

when the data request  finishes we often want to show something, or navigate to somewhere in this case, we use `onSuccss` which takes a function that execute after success.

> queryClient

the `queryClient` that we use as wrapper, we use a method called `invlidateQueries` which will re-execute our query to update the data that has been added, or to re-fetch the data that we have

this is useful when a user add new (post) and we need to include that new post without the need of refreshing the page

we give this the `queryKey` that we assigned to our query that we want to update