 in this example i have an action that is connected to a Form react router element

```jsx
export async function action({ request }) {
  const searchParams = new URL(request.url).searchParams;
  const mode = searchParams.get('mode') || 'login';

  if (mode !== 'login' && mode !== 'signup') {
    throw json({ message: 'Unsupported mode.' }, { status: 422 });
  }

  const data = await request.formData();
  const authData = {
    email: data.get('email'),
    password: data.get('password'),
  };

  const response = await fetch('http://localhost:8080/' + mode, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(authData),
  });

  if (response.status === 422 || response.status === 401) {
    return response;
  }

  if (!response.ok) {
    throw json({ message: 'Could not authenticate user.' }, { status: 500 });
  }

  // manage token

	const resData = response.json()
	const token = resData.token

	localStorage.setItem("token",token)

  return redirect('/');
}
```

# Retrieving Param

```jsx
export async function action({ request }) {
  const searchParams = new URL(request.url).searchParams;
  const mode = searchParams.get('mode') || 'login';
```

the action function returns an object which im destructing here to retrieve the object request.

which im using with the URL constructor that expect a url which im getting from the `reqeust.url` and searching the param of that url to know whether its login or sign up

# Checking Param

```jsx
if (mode !== 'login' && mode !== 'signup') {
    throw json({ message: 'Unsupported mode.' }, { status: 422 });
  }
```

here im check if the param is not login or signup (it was entered manually), i want to send an error, this json function is a helper function by react router that im using here to send an error to my closest error element defined in my react router tree

# Getting From Data

```jsx
const data = await request.formData();
  const authData = {
    email: data.get('email'),
    password: data.get('password'),
  };
```

this action function is used  with the `From` react router component, the Form sends that data to that action function, and here im retrieving that data with the method `formData`

# Sending Data to Backend

```jsx
const response = await fetch('http://localhost:8080/' + mode, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(authData),
  });
```

using the dynmaic mode that i get from the code above, i use it to send a post request to my backend that will handle both the `login` and `sign up` to show and do different things

plus im using my data which i get from my `fromData` method which i get from the `From` element provided by react router.

# Checking For Errors

```jsx
if (response.status === 422 || response.status === 401) {
    return response;
  }

  if (!response.ok) {
    throw json({ message: 'Could not authenticate user.' }, { status: 500 });
  }

  return redirect('/');
```

here im checking for errors in two cases, if it is `422 and 401` which i send a special error message defined in my backend, and im sending that response to the action function which can be handled because react router action and loader function support json response without the need to use `response.json()` on them

or it is `not ok` in this case im sending a generic error message

if the code passes all these check, redirecting the user (which means success)

# Managing a Token

when we want to add authentication, we have to attach every user with a token, that token will serve as an id for the user, or a way to add a special privileges (for example anyone could see the site, but only users with the token can interact with the site)

```jsx
	const resData = response.json()
	const token = resData.token

	localStorage.setItem("token",token)
```

in this code we are getting a token from the backend, we then put it into the `localStorage` to store it, we can alternatively store it in a global state.
 
then in order to use it we must use it in our fetch function when a user make that request, for example when a user want to delete a post, we must include that token in there, and manage the backend accordingly:

```jsx
const token = localStorge.getItem("token")

fetch("localhost:8080/events/" + eventId,{
	method:"DELETE",
	headers:{
	'Authorization': "bearer " + token
	}
})
```

we are getting the token from the `localStorage` then we are using the header `authorization` which is used for token and authentication, and using the token next to the type `bearer` is a type of authentication that takes a token

# Showing Errors in the From

we can retrieve the response we get from our backend using the `useActionData` hook in our form, and then show that data if it exist.

```jsx
function AuthForm() {
const data = useActionData();
{data && data.message && <p>{data.message}</p>}
}
```

this data is coming from our action function, specifically from our return responses:

```jsx
if (response.status === 422 || response.status === 401) {
    return response;
  }
```