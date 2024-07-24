# Cookies

we use cookies to store states or the data, it is used in the backend to save the user data for example (login data), it is used in the front end, and can be modified in the browser under the `dev` tools

it function the same as `localStorage`, the only difference is that it send a request and that it has a specific time

# usage

we can use it in our express app using the code below:

```js
app.post('/login',(req,res)=>{
	res.cookie('login','true')
	// or 
	res.setHeader('Set-Cookie','login=true')
})
```

this route which is connected to from that sends a post request will be used as a way to save that login data with the help of cookies

# session

unlike cookies which is used in the client side, session is a way to store unique data from the user to be kept in the backend, it cannot be modified in the browser

# usage

to use session in our express app, we should download a package called `express-session` and import it and use it as a middleware:

```js
import session from "express-session"

app.use(session(
	secret:"shop",
	resave:false,
	saveUninitialized:false,
))
```

then we use this with our request:

```js
app.post('/login',(req,res)=>{
	req.session.login = true
})
```

this will uses a cookie to save this value, we can then use it just like with our cookie, it will however be encrypted so the user cannot modify it.

# with [mysql](https://www.npmjs.com/package/express-mysql-session)

its bad idea to save a session locally (using our cookie storage) because every user visiting our site will create a new session and our cookie storage is limited

instead we should use session with our database, there is a session guide for every database, to use it with `mysql2` we need the package `express-mysql-session`

