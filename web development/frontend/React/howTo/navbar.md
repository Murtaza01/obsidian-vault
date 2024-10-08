the simple markup for a navBar is:

```Html
<nav>
	<a>Logo</a>
	<ul>
		<li><a>Home</a></li>
		<li><a>Contact</a></li>
		<li><a>About</a></li>
	</ul>
</nav>
```

to show the hamburger menu and hide it we can use `useState()` like this:

```JSX
function NavBar(){
const [isClicked,SetisClicked]= useState(false)

function handleClick(){
	SetisClicked(!isClikced)
{/* the (!) will set it as a toggle button rather then a static one that only changes once, because it will be the oppsite of its state each time the button is clicked ! */}
}
return <>
	<i className={isClicked ? "fas fa-time" : "fas fa-bar"}
		onClick={handleClick}
></i>
{/* simply saying if clicked show X icon, if not show the bar*/}
</>
}
```
where `<i>` is an icon element, that we add with the `cdn` of font awesome, it is a great way to add icons, because we only need to add classes to add the icon

to make the navBar on small screen we add a `fixed` position, look at the example:

```css
.navBar{
	flex-direction:column;
	position: fixed;
	right:-300px;
/* so we can hide our navBar*/
	top: 30px;
	height:100vh;
}
.navBar.active{
	right:0;
}
```

to add a way to display it and remove it, we can use the same state of our icons to work with it:

```JSX
<ul  className={isClicked ? "navBar active" : "navBar"}></ul>
```

with the `CSS` above, we can hide show the navBar with our the icon that we can click


# show/hide nav on scroll 

we can do that using the following [code](https://stackoverflow.com/a/71356027/20940799):

```jsx

const [showHeader, setShowHeader] = useState(true);
const [lastScrolledY, setLastScrolledY] = useState(0);

function onScroll() {
    if (window.scrollY > lastScrolledY) {
      setShowHeader(false);
    } else {
      setShowHeader(true);
    }
    setLastScrolledY(window.scrollY);
  }
  useEffect(() => {
    addEventListener("scroll", onScroll);

    return () => {
      removeEventListener("scroll", onScroll);
    };
  });
```
