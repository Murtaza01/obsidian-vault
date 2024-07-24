a site where i ask people questions based on the SOS-10 scale found in the book (the imp of the mind, p.164), putting these  question on a separate back-end so use them from there, to both apply my knowledge and have a better site, and append the answers they give to a separate JSON file in my back-end, only send the data if they provide a name

i will need to learn these things first:

- [x] how to write without overwriting in `fs` (the backend)
- [x] how will the app function
- [x] dark mode with tailwindcss
- [x] learn how to use figma for basic design 
# preDev

> learning append data without losing info

we use the function [appendFileSync](https://nodejs.org/api/fs.html#fsappendfilesyncpath-data-options):

```js
import { appendFileSync } from 'node:fs';

appendFileSync('message.txt', 'data to append');

```

> [post vs put](https://stackoverflow.com/a/630475/20940799)

an easy way to think about it is this: put for putting new contact, post is for posting a whole new thing (i think this is the summary)

> sync vs async in node

in node there is [three](https://nodejs.org/api/fs.html#promise-example) ways of using the `fs` module

1. using the callback method
2. using the promise method
3. using the sync function method

the sync function method will block the code below until it finishes from doing what we want, this is optimal in my case

> adding new data to the "database"

in my "fake" database, which is basically a `JSON` file i can add new data from the sent data that i get from the front end using the write/read sync function, like [this](https://stackoverflow.com/a/61474383/20940799):

```js
wrieFileSync("pathOfFile",JSON.stringify([]))
//in this case i will have an empty array, otherwise i can simply just put an empty array in my file, so this is not really needed
const newData = req.body;
cosnt fileData = JSON.parse(readFileSync("pathOfFile"))
fileData.push(newData)
wrieFileSync("pathOfFile",JSON.stringify(fileData,null,2))
```

first i read the file to extract the array, and i must use `JSON.parse` so it is a valid JavaScript array, then i push the new data that i extract from the `body` and push it to my array, then i simply write this change to my json file

a good trick to make some intention is using the second and third parameter in the `JSON.stringify` function, like the code above

# postDev


# adding smaller screens in tailwincss

in order to add smaller screen i can't just extend the screens object, rather i would want to import `defaultTheme` and spread the old screens besides the new screen (this will override the default screens) here is [how](https://tailwindcss.com/docs/screens#adding-smaller-breakpoints).


# [@font-face](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face)

is a way to add local fonts with almost any kind of extension:

```css
@font-face {
  font-family: "Amulya";
  src: url(./assets/fonts/Amulya-Bold.ttf) format("opentype");
}
```

# darkMode & tailwindcss

in order to add darkMode using tailwindcss we need to do the following:

1. define our classes (light/dark), and in these classes we put our bg-colors and colors:
```css
@layer base {
  .light {
    --background: 0, 0%, 99%;
    --primary: 0, 0%, 9%; 
  }
  .dark {
   --background: 0, 0%, 1%;
   --primary: 220, 14.3%, 95.9%;
  }
}
```

it must be `hsl` or `rgb` and without the function names (that will allow us to edit the opacity of the colors in `tailwindcss`)

2. extend those colors using the variable names:
```js
extend: {
	colors: {
		background: "hsla(var(--background))",
		primary: "hsla(var(--primary))"}
 }
```

we are using this syntax because we want to be able to add opacity.

3. in our classes we can simply call those colors
4. we add those classes (light/dark) to our body using state [[Dark Mode]] 

```html
<body class="bg-background/50 transition-colors duration-300">
```

# all decedent in tailwindcss

we can use the `*` to style all direct children:

```jsx
className="*:bg-background/85"
```

# render one element instead of the whole component

we can do that using the if statement to check whether a condition is true and if it is we can simply obstruct the return of our functional component and instead return one element (for example error element):

```jsx
if (error) {
    return <Error />
}
```

# using environmental variables

we can do that by first downloading a package named `dotenv` then use the method `config()` on it, and create a file with `.env` that will have our environmental variables, this file won't ship to GitHub and is needed for sensitive information:

```js
import dotenv from "dotenv";
dotenv.config();

mysql.createPool({
    host: process.env.DB_host,
    user: process.env.DB_user,
    password: process.env.DB_password,
    database: process.env.DB_database,
})
```
# others

1. `StrictMode` in react render the the components twice 

