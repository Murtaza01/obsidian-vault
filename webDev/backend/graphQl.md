graphQl is similar to rest in the way that it manages the server side logic with endpoints and sends back a response, it is here to solve one problem with Rest

# REST Problem

lets say we want to send request from the front end and get back only some data, for example if we have an endpoint `/posts` and we want only the name

Technically we can use query but it would be difficult, we can also get all of the data (post) and filter it in the front end, but that would be cumbersome

instead we use GraphQl, a way to query the data in the backend and sends only the required data to the front end

# how it works

GraphQl works by sending a request (POST) from the front end to the backend that will have a query (the data needed) to an endpoint /graphql which will manage that query and sends back only the data requested

note that the endpoint is always /graphql and the method is always POST

graphQl has three kind of `routes`:

query: which manages the GET method
Mutation: which manages the POST/PUT/DELETE methods
Subscription: which mananges the Socket (real time connection)

# working with graphQl

to work with graphQl you need a folder inside your server with
schema 
resolver

the schema file will have the data structure of your data, it would look something like this

```js
import {buildSchema} from "graphql"

export default const schema = buildSchema(`
    type Query {
    hello : string
}
`)
```

the buildSchema takes a string, we are using string literal to have multiple lines

the data inside will be objects with the keyword type, and the filed which is `hello` in this case would refer to the same name in the resolver file

in our resolver file we would have something like this:

```js
export const root = {
    hello(){
    return "hello world"
}
}
```

in our app or server js, we use this syntax to connect both the schema and reslover:

```js
import {createHandler}  from "graphql-http/lib/use/express";

app.all('/graphql',createHandler({
    schema: schema,
    rootValue:root,
}))
```

# using it in the front end

in order to use graphql and send the right data in the front end we need to send a POST request with the following code:

```js
const graphqlQuery = {
query: `
    mutaution{
    //the same code in the backend
    }
`
}

fetch("http//localhost:3000/graphql",{
    method:'POST',
    header:{
    'Content-Type':"applcation/json"
    },
    body:graphqlQuery
})
```

# method not allowed

you will get this error as a result of the options request being send from the front end to the backend, to fix this we can simply add a middleware that will handle the Options request and set them to 200:

```js
app.use((req,res,next),{
    if(req.method === "OPTIONS"){
        return res.statusCode(200)
}
    next()
})
```

