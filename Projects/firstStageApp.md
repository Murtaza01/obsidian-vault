# download 

the download property on the a tag is used to download files from a directory , you need the access of the route it will get to, if you provide a local href, it will redirect you to a route with the filename:

```html
<a href='images/pic.jpg' download>download image<a>
```

# deploying via Vite

1. copy your github repository name and add `/` in the beginning and end and put it inside the vite.config:
![[viteConfig.png]]
2. build the app using:
`pnpm build` / `npm run build`
4. adding the dist folder into our github repository, using:
`git add dist -f`
5. we then commit our changes with the command:
`git commit -m "adding dist"`
6. we push our dist folder into our repository in a subtree called gh-pages
`git subtree push --prefix dist origin gh-pages`

this also work when we update something, we simply repeat the process

> deploying fails (!rejected)

if you can't push your build to gh-pages, you can simply delete the branch (gh-pages) and re push it, if there were some errors, with this [code](https://stackoverflow.com/a/52105454):

```Bash
git push origin --delete gh-pages
git subtree push --prefix dist origin gh-pages
```

# transitioning accordion 

when we want to transition height to use for accordion, we can use grid in our element:

```css
.container{
	display:grid;
	grid-template-rows:0fr;
	transition: grid-template-rows 0.5s ease-out;
}
.container.show{
	grid-template-rows:1fr;
}
.innerElement{
	overflow:hidden;
}
```
the container elements are hidden using the `0fr` value, then to not overflow, we use hidden on the element itself (or row in this case), then if we want to show it, we simply have a show class that will be added on click

# [Cloning a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)

if you decided to come back to an old project, you simply need to clone it to your local computer


# transitioning from display

when you want to transition the display, we can use the `@starting-style` this way:

```css
.element{
transition: opacity 1s, display 1s;
display:none;
opacity:0
}

.showElement{
	opacity:1;
	display:flex;
}

@starting-style{
	.element{
	opacity:0;
	}
}

```

when we add the `.showElement` class, it will show the element, but without transition, instead it needs 


# minor things

> save an array using map in a variable

consider this example:

![[map example.png]]

Scores would  be an array of the two arrays inside my student array, whats happening is that im going through each object, and im destructing the scores object, which is an array, then im returning it and saving it inside `Scores`

i can further destruct each of the scores into an individual array using this syntax: 

```jsx
const [Scores1,Scores2]= students.map(({scores})=> scores)
```

# some notes

1. the project needed a planing instead of just doing whatever works for the moment
2. the project orientation was a bit messy, instead in the future i should focus on one thing at a time, JavaScript, then CSS
3. i got too excited and put a lot of energy and time on the project, which i ended up not doing a good work on, and resulted in a messy code and not much energy for other activity
4. i should prepare the needed files/icons in my project before i start working on it, this way, it is much cleaner
5. not having much breaks and continuously working on the project was also a mistake that i need to not repeat 

