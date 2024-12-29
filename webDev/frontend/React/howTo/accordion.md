for accordion, i simply create a class that by default is hidden (by height) and show it when i add an active class:

```JSX
const [showAcc,setShowAcc]=useState(false)

<button onClick={()=>setShowAcc(!showAcc)}>
</button>

<ul className={showAcc ? "content show": "content"}></ul>
```

the following CSS is needed to show the effect desired:

```CSS
  .content {
    max-height: 0;
    overflow: hidden;
    transition: all 0.5s cubic-bezier(0, 1, 0, 1);
  }

  .content .show{
    height: auto;
    max-height: 9999px;
    transition: all 0.5s cubic-bezier(1, 0, 1, 0);
  }
```

# better way to transition from height

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

