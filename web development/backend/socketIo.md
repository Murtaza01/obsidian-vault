sockets are a way for the server to push data to other clients, it is used for real time messages and other real time application, because we don't want to load our server with request, we use a socket which will manage that for us.

# using it (node)

you can use it by writing the below code:

```js
import io from "socket.io"
const server = app.listen(3000)
io(server)
io.on("connction",()=>{
    consloe.log("client conntcted")
})
```
this is the way of max in the video

