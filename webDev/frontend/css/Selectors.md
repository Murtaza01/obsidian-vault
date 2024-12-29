# direct children and children

there is difference between those codes:

```css
.container *{
	/* select all the children */
}
.container > *{
	/* select only the direct children */
}
```

# valid

we can check Wether an input is valid or not and add
style to it depending on the validity using the vaild selector:

```css
input:valid{
background-color:green;
}
```

we can chain it with the `not:()` pseudo class to warn user
that the input is not valid, it is really good with validtion:

```css
input:not(:valid) {
background-color:pink;
```

**note** that it needs the `type=""` inside the html tag in order 
for this to work
