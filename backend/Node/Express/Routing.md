# .router

we can add a folder for routing (controller), that will help us arrange our file structure with the `.router` method in our app (express) js:

```js
import express from "express"

const router = express.router()

router.get((req,res))...
router.post((req,res))...

export default router
```

using the routes normally, the router will function like the `app` , then in our main server file we can import it and add it as a middleware  or rather a route:

```js
import router from './router'

const app = express()

app.use(router)
```

we can add different routers and different paths to the routers:

```js
app.use(shopRuter)
app.use('/admin',adminRouter)
```

# using `__dirname`

when using a sub folder and we want to use `__dirname` we can do that with the following code:

```js
import path from 'path'

router.get((req,res)=>{
res.sendFile(path.join(__dirname,'..','views','shop.html'))
})
```

`..` this will get back one level because we are currently in the `router` folder and we need to access a folder in our main tree `views`:

![[__dirname.png]]