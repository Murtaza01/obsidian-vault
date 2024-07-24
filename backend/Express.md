
# getting the body that sent using POST `Middleware`

when the user post something (send something to the server) we must have a way to extract this information, we can't without using the `body-parser` module, we need to install it since it doesn't come bundled with express, we will use the module to get the body of the POST request, here is an example:

```javascript

import bodyParser from 'body-parser'

// the urlencoded is the type of the request, it could be JSON, the extended option will return a JSON like object
app.use(bodyParser.urlencoded({extended:true}))

// in our POST request we can use the following code to reqest the body (extract it), we can either log it or save it to a variable, note that this sends back an Object
req.body
```

this is what is called to be a `middleware`, we need to use the `app.use()` method since it allows use to use this before handling any request

# `morgan`

is a `middleware` that sent us data about what request the user is requesting, for example when the user request our homepage, the module will sent us a `consloe.log` saying whether it was successful or not, below is an example of the syntax 

```javascript
import morgan from 'morgan'

//there is different kind of options regarding the output we get 
app.use(morgan('combined'))
```

# `Middlewares`

"**a set of functions that execute during the processing of HTTP requests received by an Express application**"

it is what happens before the user send any kind of request, take a look at the code below, it is a way of creating a `middleware` 

![[middlware.png]]

the first line of code is creating your own `middleware` that will request the method and console log it whenever a user makes a request, the `next()` function basically says that after this code, move to the next line *(in our example here is the app.get)*

here we are doing the exact same thing but with an independent function:

![[your own middleware.png]]

# sending a file with GET

in order to send a file as GET request *meaning when the user request something we display a certain file* we use the following code:

```javascript

app.get('/',(req,res)=>{
res.sendFile(__dirname + '/public/index.html')
})
```

where `__dirname `is the function we get from combining `path` and `url` modules

# `res.redirct()`

we can use redirect to redirect a user to a specific route, especially when we are handling a post request and want to send the user to somewhere after the form submit, here is an example:

```javascript

app.post('/submit',(req,res)=>{
res.redirect('/')
})
```

in this case it will redirect to the home page


# serving static files

in order to serve static files in your project, you need to use the `express.static` method, showing in the below example:

```javascript
app.use(express.static('public'))
```

when linking your files to the public folder, you don't name the public folder, only a slash will do, example:

```html
<link rel='stylesheet' href='/styles/layout.css'>
```

# Creating a dynamic route

to create a dynamic route that will function as an id, which you can take as a parameter, you can simply put a `:` before the name, and it would return as an object when you call `req.params`, see the example below:

```javascript
app.get('/jokes/:id',(req,res)=>{
	const id = req.params.id
	res.json(jokes[id])
})
```

this `jokes/:id` is what called, a path parameter, it is distinguished from the query which will looks like this `jokes?id=2`   

`res.json()` will return a json object to the desired route, no need of rendering a site, it would look like this:

![[Pasted image 20231123184158.png]]
# Route with Query

in order to get the query of the route you have, you use `req.query`, note that you shouldn't add the query to the route, and only take the query with the callback function, see the code below:

```javascript
app.get('/filter',(req,res)=>{
	const query = req.query.type
	
})
```

in this case, type is what im trying to match with my object that contains a type of jokes, other quires will not be considered because they won't match that line `req.query.type`


# cors

All requests made from the front end of a different origin or to a back end of a different origin will be blocked by the browser. `CORS` allows us to bypass this policy **in case of scenarios where accessing third-party resources becomes necessary**

`cors` helps us bypass an error that occurs when we try to reach our server from a domain, because the browser default will not accept that, so `cors` helps us with that, it will make it possible to fetch data from any domain

it is a third party *Middleware* 