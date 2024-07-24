install react-route using the package `react-router-dom`

# createBrowserRoute

a function which takes an array of objects, each  object will have a path key and element, the path will refer to the path of the route, and the element will refer to the element that will show:

```jsx
import {createBrowserRoute} from "react-route-dom"
import Home from "./pages/Home"

createBrowserRoute([
{path: "/" ,element: <Home> }
])

```

# RouterProivder

a component that will serve our routes and check which route is currently is on the screen (on the browser) and change the element accordingly:

```jsx
import {createBrowserRoute,RouterProvider } from "react-route-dom"
import Home from "./pages/Home"

const router = createBrowserRoute([
{path: "/" ,element: <Home> }
])
function App(){
	return <RouterProvider router={router}/>
}
```

# Link

to navigate through our routes we can't use the `<a>` tag because it will refresh (re-render) our entire page (all of our JavaScript) using the `href` attribute, instead we use the `Link` component provided by `react-route-dom` and the to attribute instead of the `herf`

```jsx
import {Link} from "react-route-dom"

funtion Home(){
return <Link to="/About">Click to see about</Link>
}
```

# Component wrapper

sometimes we have constant components that show on all pages like navigation bar, we can't put it next our `RouterProvider` because then the links won't work, since they need to be nested inside that provider.

in this case we define a route that will have a `children` proberty and will act as a wrapper to our pages:

```jsx
const router = createBrowserRoute([
{path: "/",
element: <RootLayout />,
children:[
	{path: "/" ,element: <Home /> },
	{path: "/about", element: <About />}
] 
 }
])
```

children is a property (key) that will take an array of object of the paths that will be served as children, in our `RootLayout` we add the `Outlet` component that will act as children:

```jsx
import {Outlet} from "react-route-dom"

function RootLayout(){
	return <>
	<Nav />
	<Outlet />
	</>
}
```

# errorElement

a property that we can add to our main root wrapper that will get trigger only when the slash `/` have an unsupported route `/abc` , we simply put this key property and then the page we want to serve in case of an erorr:

```jsx

const router = createBrowserRoute([
{path: "/",
element: <RootLayout />,
erorrElement: <ErorrPage />
children:[
	{path: "/" ,element: <Home /> },
	{path: "/about", element: <About />}
] 
 }
])
```

# navLink

`react-route-dom` provide a way to indicate on which page we are on using the `navLink` component, which is similar to `Link` but has special properties that we can use to indicate current page

it has the `className` attribute that is different from the `className` that takes a string, this property or attribute takes a function that, in that function it provide an object that has a key we are interested in, the `isActive` key which we can destruct from that function

`isActive` is a boolean that we can compare whether it is true or not to show a class on our link:

```jsx
import {navLink} from "react-route-dom"

function Nav(){
	return <navLink to="/" 
	className={({isActive})=> isActive ? "active:text-decoration" : undefined }
	end
	>
	</navLink>
}

```

there is special property called `end` which will make our `/` link not be mixed with other routes, so when we have a link that goes to the `/` we want to give that property to it so it will understand that this `/` is the last thing it reads

# useNavigate

we use this to navigate with our code instead of links, we can trigger that after a form is submitted or after a timer or something else:

```jsx
import {useNavigate} from "react-route-dom"

function HomePage(){
	const navigate = useNavigate()

	function handleSubmite(){
	navigate("/content")
	}

	return <form onClick={handleSubmit}>
		<button>Click To Submit</button>
	</form>
}
```

# dynamic route

if we different products and we want to show the details based on those products that was clicked, we can use a one page with different details, we can do that with dynamic routing, we simply add `:` after the route:

```jsx
const router = createBrowserRoute([
{path: "/",
element: <RootLayout />,
erorrElement: <ErorrPage />
children:[
	{path: "/" ,element: <Home /> },
	{path: "/products", element: <Products />},
	{path: "/products/:id", element: <ProductsDetails />}
] 
 }
])
```

inside our component  `ProductsDetails` we can use a function provided by `react-route-dom` called the `useParam` which will return an object that we can get the id from (of that exact id):

```jsx
import {useParam} from "react-route-dom"
function ProductsDetails(){

const param = useParam();

param.id // shows you the id from the given route
}
```

in this case we can use this id to show different details:

![[dynamic route.png]]

# relative vs absoulte path

when we define our routs with the `/` that means they are absolute, we can use the relative paths with the lack of `/` in our children for example:
![[relative vs absoulte.png]]
this will only show the children using the absolute path then their decedent children `/root/products`

we should always use relative path so that they append to the current path instead of overriding to an absolute path 

# index

when we have a relative path that is the home page this would usually be empty (because it takes the path of the parent) in this case we can simply add a property that will say that this should be rendered as the `index` or the home page:

```jsx
const router = createBrowserRoute([
{path: "/",
element: <RootLayout />,
erorrElement: <ErorrPage />
children:[
	{index: true ,element: <Home /> },
	{path: "products", element: <Products />},
	{path: "products/:id", element: <ProductsDetails />}
] 
 }
])
```

# loader

is a property in the `createBrowserRoute` object that have a function and return that data into the page:

```jsx
const router = createBrowserRoute([
{path: "/",
element: <RootLayout />,
children:[
	{index: true ,element: <Home />,loader:()=>{
	return //something
	} },
] 
 }
])
```

this return will be available inside our `home` page, we can get that data from the component using `useLoaderData`:

```jsx
import {useLoaderData} from "react-router-dom"

function Home(){
	const data = useLoaderData();
}
```

we can use the data from the loader inside the elements and its children
# loader with fetch

when you fetch data with loader you can only return the response without using the `.json()` becuase the loader support it:

![[loader function.png]]

here we are outsourcing the loader function and importing it in our route, then we are using it in our component, we are defining the loader function there because it belongs there.

# useNavigation

a hook in the react-router package that can tell the state of the transition from one route to another, because sometimes the backend data that you put in one route might take a little time to load, when using the loader:

```jsx
import { useNavigation } from "react-router-dom"

function Page(){
const navigation = useNavigation();

return <>
	{navigation.state === "loading" && <p>loading...</p>}
</>
}
```

we use the `state` property inside that navigation object to know what the state of that transition is.

# Error handling with loader

we can handle errors with loader like this:

```jsx
export async function loader(){
	const response = fetch("http//...")
	if(!respnse.ok){
	return {isError: true, message:"Error Happend"}
	} else{
	return response;
	}
}
```

However there a better way to invoke the **Error Elements** inside our route, when we throw a new error in our loader:

```jsx
export async function loader(){
	const response = fetch("http//...")
	if(!respnse.ok){
	throw { message:"Error Happend" }
	} else{
	return response;
	}
}
```

this will invoke the error Element inside our route (it will pick the closest one)

> throwing more specific errors 

in order to set the status of our error, we can use the constructor Response() to throw a new error response, this we can chain with the `useRouteError` to get hold of it inside our child routes:

```jsx
export async function loader(){
	const response = fetch("http//...")
	if(!respnse.ok){
	throw new Response(JSON.Stringify({message:"Error accord"}),{status:500})
// we need the json becuase we are using it in the browser, and the status is an object.
	} else{
	return response;
	}
}
```

now we can simply use this in our route children of that parent using the `useRouteError` hook:

```jsx
function Child(){
	const error = useRouteError()
	error.status // 500
}
```

the default error status for not finding the page is **404** so we can do this check:
![[Route Error Handling.png]]
# using the json() function

we can use json() function from `react-route-dom` instead of throwing a Response, this remove the parsing and stringify step of our previous method:

```jsx
import {json} from `react-route-dom`

export async function loader(){
	const response = fetch("http//...")
	if(!respnse.ok){
	throw json({message:"Error happend"},{status:500})
	} else{
	return response;
	}
}
```

# action

an action is a route property that we can use to send data to our backend easily, it works just like loaders:

```jsx
export async fucntion action(){
fetch("http//..",{
	method:"POST",
	body:
})
}
```

we can use action with a from submitting data, using the `Form` element inside our from (instead of a regular from element):

```jsx
import {From} from `react-route-dom`
function From(){

return <Form method="post">
//....
</From>
}
```

then in our action function we get the request using a request object, with the `formData` method:

```jsx
export async fucntion action({request}){

const data = await request.fromData();

fetch("http//..",{
	method:"POST",
	body:
})
}
```

then we can get the from data that we entered in the from using the `name` attribute inside our input elements:

```jsx
const data = await request.fromData();
data.get("title")
```

and if we have multiple from input we simply create an object:

```jsx
const dataFrom = {
	title:data.get("title")
	name:data.get("name")
}
```

then its that dataFrom that we want to send as a Post request to our backend:

```jsx
fetch("http//..",{
	method:"POST",
	body:JSON.Strigify(dataFrom)
	header:{
	"Content-Type":"application/json"
	}
})
```

# useSearchParams

a hook provided by react-router that helps you take the query from your route `url`, a query is the route parameter that starts with `?` example (`/auth?mode=login`) 

in this case we are using the query parameter to show a different component:

```jsx
function Auth(){
	const [searchParams,setSearchParams] = useSearchParams()
	const isLogin = searchParams.get('mode') === "log in"
}
```

here we are destructing the hook because it returns an array, we then use a method that gets the query, and comparing it to the string to render elements based on that condition:

```jsx
<Link to={`?mode=${isLogin ? "login" : "sign up"}`}>
{isLogin ? "log in" : "sign up"}
</Link>
```

this way we are managing the url with a button click, that when i click that button it will show me the login button, and if it is already login in it will show sign up, sort of like a toggle.

# Log out

to add a log out we can create page that will have a path of `logout` that i will target using a react router from element, which will have an action method that will send to `logout`:

```jsx
{
	path:"logout",
	action:logoutAction
}
```

this `logoutAction` is simply a function that do a certain  thing, in this case it removes the special token that allow a user to delete and edit posts:

```jsx
function logoutAction(){
localStorage.removeItem("token")
return rederict("/")
}
```

now in order to apply this we simply add this route to a button inside a from in our UI:

```jsx
import { From } from "react-router-dom";

<Form action="/logout">
	<button>Logout</button>
</Form>
```

# Route Protection 

we can create a protection to using a loader that will redirect if the user is not logged in and add that loader to any route that needs protection:

```jsx
function checkLoader(){
	const token = localStorage.getItem("token")

	if(!token) redirect("/auth")
}
```

