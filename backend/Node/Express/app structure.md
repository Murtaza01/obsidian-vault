
to make a great express app we can use the following folders for our app structure:

# routes

where we keep all the routes logic and nothing else, we use the router method in express:

```js
import express from "express"
import {getPosts} from "./controller/feed"

const router = express.Router();

router.get('/posts', getPosts);

```

# controller
 
where we keep all the route logic:

```js
export const getPosts = (req, res, next) => {
  res.status(200).json({
    posts: [{ title: 'First Post', content: 'This is the first post!' }]
  });
};
```

# app / server 

then we can use the above folder with `app.use`:

```js
import feed from "./routes/feed"

app.use('/feed', feedRoutes);
```