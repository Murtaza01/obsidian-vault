
# Usage

the full `tailwindcss` with prettier extension 

```
pnpm -D tailwindcss postcss autoprefixer prettier prettier-plugin-tailwindcss

pnpm dlx tailwindcss init -p
```

# adding custom style

we can normal CSS in our CSS file even with `tailwindcss`, and we can use the `@layer` function to add `tailwindcss` components, which would look like this:

```CSS
@layer components {
  .center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
```
# Mobile First


in tailwind it uses the `min-width` function of media queries, because its designed to be mobile first, so in order to style your element, you need to apply the styles to mobile then start changing the styles, here is an example:

```HTMl
<h1 
	className="w-full text-cyan-500 sm:w-2/4 text-gray-500 md:w-1/5 text-red-500"
	>
hello world
</h1>
```

in the example above, it will start as full width, then it will be 50% at small screens `(640px)` then it will be 20% at mid screens `(768px)` if we stop and not define the large screens, it will use the mid screen width as the rest

# Conditional with React

in order to use conditional we need to use `template literals (``) ` and add styles using the tailwind classes, see the example below:

```JSX
<nav
        className={`mobile bg-violet-400 sm:tablet md:desktop md:bg-transparent ${
          isClicked
            ? "translate-x-[0] sm:right-0 w-1"
            : "translate-x-[-100%] sm:right-[-100%] md:right-0"
        }`}
```

here we are saying that if *isClicked* is true, then apply `translateX(0)` which will show the nav, because when its false it will be `translateX(100%)` and this is only for mobile screens, which is the first thing to style

second the small screens, such as tablet, we use the `right:-100%` when the function is false, so its hidden by default

third, we need to set the default (when false) of the mid screens and above, so we don't have the default of small screens

# adding custom fonts

you can add custom fonts by adding the fonts import in the CSS file where your tailwind is, then going to the config and edit as below:

```JS
theme: {
  extend: {
    fontFamily: {
     customName: ['Custom Font', 'serif'],
    },
  },
}, 
```

and then using font-`customName` inside classes

# peer & group

we can use `group` to have some styles to the child element based on whats happening on the parent element, for example when i hover on this parent element i want to add some style to the child element, we can do that using the group

`peer` on the other hand is equal to the `~` which will style the sibling elements, and it should be after the element we give peer to, see the examples below:

```JSX
<input className="peer"/>
<label className="peer-focus:translate-y-[-80%]">Email</label>

// for group, it must be on a parent element
<div className="group">
	<h1 className="group-hover:bg-black"> Hello World</h1>
</div>
```

# adding classes conditionally 

![[tailwind adding classes.png]]

in the above example, we add a variable that contain the base class, and only add a class (background color) if a certain condition is true, using string concatenating, note that we need the space so it doesn't mix the class 

# darkMode 

to apply dark mode we have two main ways:

> using class dark

in our tailwindcss config, we add this property:

```js
darkMode:"class";
```

that will track a class called `dark` and if that class exist, it will apply dark mode, we put this in our `html` element so the whole document is effected, we also use the `dark:` to change between styles, and we add transition to the color so that the switch is smooth:

```css
html{ @apply transition-color duration-400 }
```

we only need to add that class using `useState` whenever there is click, we can save that class in our `localStorge` and apply it so that it is saved 

