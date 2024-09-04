# :active

when the user click on something, this is triggered

# :not & last-child

we can combine these tow to select everything expect the last child:

```css
container *:not(:last-child){
	margin-bottom:10px;
}
```
