using tailwindcss and react to create dark mode we need the following:

1. variables in advance for the light and dark colors
2. style the button of toggle (with icons)
3. make a custom hook that will have both state and effect

# making a custom hook

consider the [code](https://javascript.plainenglish.io/how-to-create-light-and-dark-mode-toggle-in-next-js-with-tailwind-61e67518fd2d) below:

```js
import { useEffect, useState } from "react";

function useDarkMode() {|
const [theme, setTheme] = useState(
typeof window !== "undefined" ? localStorage.theme : "dark"
);
const colorTheme = theme === "dark" ? "light" : "dark";

useEffect(() => {|
const root = window.document.documentElement;

root.classList.remove(colorTheme);
root.classList.add(theme);

if (typeof window !== "undefined") {|
localStorage.setItem("theme", theme);
}
}, [theme]);
return [colorTheme, setTheme];
}

export default useDarkMode;
```
we are going to take this code step by step:

```js
const [theme, setTheme] = useState(
typeof window !== "undefined" ? localStorage.theme : "dark"
);
```

the check will always be true on browsers (this is only necessary for `nextjs`), and it will return `undefined` because `localStorge.theme` still doesn't exist

```js
const colorTheme = theme === "dark" ? "light" : "dark";
```

this will have the opposite of my theme so i can remove the class later

```js
const root = window.document.documentElement;

root.classList.remove(colorTheme);
root.classList.add(theme);
```

because i want to add the class to my html i need to use the `documentElement` method on `document` , and im removing the opposite class and adding the new class (so that they don't clash)

```js
if (typeof window !== "undefined") {
localStorage.setItem("theme", theme);
}
```

as we said this will always return true on browsers, so that im setting the theme to local storage variable

```js
[theme];
return [colorTheme, setTheme];
```

of course i will need to put the `theme` as a dependency, and im returning the color theme and `setTheme` because it is a custom hook that i want to use in my app 

# useTheme

```js
import { useEffect, useState } from "react";

function useDarkMode() {|
const [theme, setTheme] = useState(
localStorage.theme ? localStorage.theme : "light"
);
const colorTheme = theme === "dark" ? "light" : "dark";

useEffect(() => {
const body = window.document.body;

body.classList.remove(colorTheme);
body.classList.add(theme);


localStorage.setItem("theme", theme);

}, [theme]);
return [colorTheme, setTheme];
}

export default useDarkMode;
```