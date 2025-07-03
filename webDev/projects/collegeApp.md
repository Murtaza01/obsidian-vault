# favicon

to add favicon (the tab icon) we simply put an image inside the public folder then use a <link> tag that target it, example:

```html
<link rel="icon" type="image/png" href="/education.ico"/>
```

note you can add an image or svg or a favicon extension

# Object.keys()

is a method that turns an object into an array, it takes the object and returns a new array of that object

```javaScript
const obj = {name:"mertda",age:"age"}

object.key(obj) // [name,age]
```

this will only gets the keys of that object and not the values, to get the values there is `object.values()` function

# underline Effect

if you want to do some quick underline effect with your accent color you simply box shadow your color:

```CSS
.ele{
	box-shadow: inset 0 -0.4em 0 -0.1em --color;
}
```

this will effectively add a line behind your text, note 
`-0.1em` to remove the left shadow that we get from the inset

# `window.onpopstate`

this function is fired when the back button is clicked, in my project i used it to unauthorized when the user click the back button so there is no problems.

```js
window.onpopstate = () => {
	setAuth(false)
} 
```


# [linearGradient](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/linearGradient)


the `<linearGradient>` html element used only in svg tags, it is used to style svg element with gradient, we can use that with react-icons

# cover to images

first you add isolate to div (parent) of an image, then you add mix-blend-multiply and you need the text to be absolute around a different parent (relative).

```jsx
<section className="relative">
      <figure className="isolate">
        <img
          className="mix-blend-multiply"
        />
      </figure>
      <h1 className="absolute">some text</h1>
</section>
```


# create bash alias

open the `.bashrc` file and write your commands, then everytime you open the command write `source .bashrc` so that it knows the source of the command, then you are good to go

```bash
cdn = cd desktop/collegeApp;pnpm dev
```

# react-router in [Netlify](https://docs.netlify.com/routing/redirects/rewrites-proxies/#history-pushstate-and-single-page-apps) 

when publishing a react-router app in Netlify you need to create a file in the public folder that has the name `_redircts` with the following code:

```js
/*  /index.html  200
```
# concat

an array method that will help you join multiple arraies together  

```js
const array3 = array1.concat(array2);
```

# GitHub [Merge](https://stackoverflow.com/a/18137512)

in GitHub site, you can open GitHub editor with . in your keyboard, to edit your `repo`, useful when changing names and others.

when adding  changes this way  instead of the local way, i created a whole new commit, then i had to merge those commits, merge the change made on another PC (or another browser) using:

```bash
git fetch origin main
git merge origin/main
```

to check the git tree visually:

```bash
gitk --all
```

# Scroll to top with react-router

when you go through pages in react-router, the page doesn't go to the top and instead the scroll saves the last position, in order to fix that we can add a helper function component that will listen to the path and execute a function on each change, we can do that with the following code:

```js
import { useEffect } from "react";
import { useLocation } from "react-router-dom";

export default function ScrollToTop() {
  const { pathname } = useLocation();
  
  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);
 
  return null;
}
```

`window.scrollTo` is a js function that is executed everytime the `pathname` is changed, we put this above our parent component 
# small notes

1. loader works for both the main route and the children too, so when i redirect the route from my parent route to the child it caused an infinite loop.

2. `pnpm dlx === npx`
