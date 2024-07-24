
# JSON

JSON comes as a string, so you can't really use it to extract information unless you first turn it to javascript object using the `parse` method
# JS to JSON

you can transform JS object to JSON using the code below:

```javascript
const jsonData = JSON.stringify(data)
```

where data is the JavaScript object

# JSON to JS

to turn a JSON object into a JavaScript object, we use the code below:

```javascript
const data = JSON.parse(jsonData)
```


# `axios`

to make a request to an api, we can use `axios` using the code below:

```javascript
import axios from 'axios'
const respone = axios.get('the api url')
// because when we get the api, we don't only get the data, so we should abstract that (data) object from the respone object
const data = respone.data 
```

and data is an object that contain the information you need, this is also called `fetching`

a good way is to use object destruction to only get the data so it minimize your code, here is an example:

```javascript
const { data } = await axios.post(API_URL + '/secrets')
```

# using await with `axios`

sometime you want to make multiple request to an api, so you should use the `async`  function

```javascript
async function randomApi(){
    const response = await axios.get("api/random");
    const result = response.data;
}

async function filterApi(){
    const response = await axios.get("api/filter");
    const result = response.data;
}
```

so it would go in the first function and try to reslove it, if it didn't it will throw an error, so a good idea is using  the `try and catch`:

```javascript
async function filterApi(){
	try{
		const response = await axios.get("api/filter");
	    const result = response.data;
	} catch(error){
		consloe.log(error)
}    
}
```

note that the error is an object, and it has a value of `.message` that you can use to show the actual message of the error 

# using GET with basic authentication

to request data from an api that has some basic authorization, we need to specify the username and password using an object called `auth` as a second parameter in the `axios.get()` function, here is an example:

```javascript
axios.get('my-url', {
    auth: {
        username: 'my-username',
        password: 'my-password'
    },
    params: { username }
})
```

# using GET with Bearer Token

to request data from an api that has a bearer token authorization, we put the object of the second parameter as a header, and put the `bearer` name before out token, look below:

```javascript
const respone = await axios.get('URL', {
    headers: {
      Authorization: `bearer ${yourBearerToken}`
    }
  })
```

# promise API

we can use two different methods to the promise we get from an api, for example when working with `axios` we can either use `async` or `.then`, they both do the same thing, they return the specified object as soon as it finishes

when using the keyword then, we simply chain `.then` into our function, would look like this:

```javascript
axios.get('/user?ID=12345') 
	.then(function (response) {
		console.log(response); })

	.catch(function (error) {
		console.log(error); })
```

using the `async` function, we should use try and catch for error handling, see the example below: 

```javascript
async function getUser() {
	try {
	 const response = await axios.get('/user?ID=12345');
	console.log(response);
	}catch (error) {
	 console.log(error.respone.data)
	  }
}
```

usually when catching an error its inside the path `error.respone.data` when using `axios`



