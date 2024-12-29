# [mysql2](https://sidorares.github.io/node-mysql2/docs)

we use the package mysql2 instead of the normal mysql because it is faster and more efficient, it is the same syntax with few improvements.

# creating connection

we create connection by either using the `pool` or the `createConncection`, pool is better because we can reuse and it closes by itself [further reading](https://stackoverflow.com/a/26432283) 

```js
import mysql from 'mysql2'

mysql.createPool({
// host:"localhost",
host:"127.0.0.1"
user:"mertda",
password:"1234567"
database:"nine"
})

```

because `localhost` will actually results in `127.0.0.1` and that sometimes it gives problems with connection we should put that ip number instead of `localhost`
# using env

because we don't want our password exposed in our javaScript, we should import  the information of the connection from another file using

how to use it:

1. we create a `.env` file in our project
2. we put those variables that we want to import
3. we install the `dotenv` package and import it into our project
4. we use the `dotenv.config()` 
5. note that we don't upload the `.env` file in our GitHub

the `.env` file will look like this:

```.env
host="127.0.0.1"
name="mertda"
password="1234567"
database="nine"
```

your `server.js` file will look like this:

```js
import mysql from 'mysql2'

import dotenv from "dotenv"
dotenv.config()

mysql.createPool({
// host:"localhost",
host:procces.env.host,
user:procces.env.user,
password:procces.env.passowrd,
database:procces.env.database
})
```

now instead of hard coding these values we simply use the variables found in `.env` file

# query 

in order 