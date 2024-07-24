- [x] # bookReading (old name)

- [x] site features 

1. [x] user can add books he want to read/currently reading/read 
2. [x] user can have timer sessions for books currently reading and to register what his mind through each session and track the time of the book


# preDev

- [x] playing around with backend/mongoDB
- [x] working on routes/CURD using mongoDB
- [x] learning to upload files into backend (in memory)


# handling file upload

when you want to upload file to the backend with the front end you need a from with the following attributes:

```html
 <form method="post" encType="multipart/form-data"></from>
```

these will ensure that the data is send has a file (with input of type file).

next you will need a function that handle the submit, which would look like this:

```jsx
function handleSubmit(e: SyntheticEvent) {
    e.preventDefault();
    const target = e.target as HTMLFormElement;
    const formData = new FormData(target);
    fetch(`${URL}/new`, {
    method: "POST",
    body: formData,
  });
  }
```

because the `fromData` object only takes a `fromElement` we need to type the target as the above, so that we make the form data we are getting as a send-able form.

the target in here refers to all the inputs that was inside the from, making it as a from element and transforming it as a from data object

then we send that  `fromData` to the backend, because it is not an regular object but rather a from object that is usually sent by default, we are just mimicking that behavior

# changing input type file style

in order to do that we need to first hide the input element, then style the label that is connected to it, however that will remove the file name, so we need to extract it using the following code:

```jsx
function handleChange(e: SyntheticEvent) {
    const target = e.target as HTMLInputElement;
    if (target.files) {
      const name = target.files[0].name;
      setFileName(name);
    }
  }
```

this will extract the file name from the input whenever its changed, we need to type the target as above because it is an input, and we are setting the name to a state that we render each time its changed, the if checks whether the file exist or not, because sometimes the user clicks (changes) but doesn't provide a file, this will result in error if not handled


# peer (floating label)

this refers to styling the sibling (the element next to the element im trying to style), `tailwindcss` provide an easy way of doing that:

```html
<input className="peer block h-8 w-64 border-b-2 border-black/50 bg-transparent placeholder-transparent outline-none"
type="text"
name="name"
id="name"
placeholder="Name"
        />
 <label htmlFor="name"
  className="absolute -top-4 start-0 cursor-text text-sm transition-all peer-placeholder-shown:top-1 peer-placeholder-shown:text-base">Your Name</label>
```

im connecting the two elements, now if the input change the state the following styles will be applied

all i need to do is make the upper sibling has the name `peer` then start providing some condition to my other element `peer-foucs:do something`

# using block and inline

a better way to add style especially if you want to add multiple languages, is to use `inline-padding/inline-margin` this will add padding or margin or anything to the start or end depending on the writing mode.

in tailwind there is some utility classes that provide that `ps/pe`

in CSS

block =   refers to the height depending on the writing mode
inline = refers to the width depending on the writing mode

``` css
h1{
  inline-size: 100%;
  block-size: 100%;
}
```

# randomizing a giving length

we can randomizing a number length with the random method on `Math` using the following:

```js
const number = 9
const isEven = Math.floor(Math.random() * number);
```

this will give us a number between 0 and 9

# images as `base64`

if we want to send our images to the backend or save them in our database, we can make the image as `base64` which is an *string* encoding that makes it smaller to save in the database, or to send to the backend.

every image has a buffer or an encoding that makes it easier to transform through computers instead of sending the whole file.

you can use the `base64` in your image tag like this:

```html
<img src=`data:img/png;base64, ${base64}` >
```

in the backend with node and `multer` it would look something like this:

```js
const base64 = file.buffer.toString("base64");
const image = "data:" + file.mimetype + ";base64," + base64;
```

where file is the image and the `file.mimetype` is the type of image (it could be png or jpg) 

# catch block typescript

when you want to type the error object in typescript, you should use something like this:

```js
catch(error){
if(error instanceof Erorr) retrun error
}
```

this will make the (after if statement) returns a error object that has the three properties like (message,name..)

because the error that gets in the catch block will be unknown (it could be anything really so it is of type unknown)

# deleting folder from git

we can do that using the command below:

```bash
// with the folder full path

~ git rm -r --cached src/test
```

# Object.values && Object.keys

to retrieve either the keys or the values as an iterable  (array) we can use Object constructor with these two methods
