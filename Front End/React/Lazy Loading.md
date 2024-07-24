only to render certain components if needed, so that when we have a big site and we first run it, it won't load those components, but only after clicking on them or reacting to them, this is good for speed:

```jsx
import {lazy} from "react"

const BlogPage = lazy(()=>import('./pages/Blog'))
```

the lazy function convert our `js` file into a `jsx` functional component, and the import function takes a string that will gets the path, it is an `async` function so the lazy handle that part

and then because this code will take some time to load, we can wrap our components with the `Suspnse` to show a fallback message, or an element:

```jsx
{
	path:"/blogs",
	element:(
		<Suspnse fallBack={<p>Loading...</p>}>
			<BlogPoge />
		<Suspnse>
	)
}
```