# using isolation

when we have an background image and we have text on it, and the text is not clear, we can add a pseudo element which will represent a new background, and we reduce that pseudo element opacity

```CSS
.background{
	position:relative;
	isolation:isolate;
}

.background::after{
	content:"";
	position:absoulte;
	background-color:pink;
	opacity: .3;
	inset:0;
	z-index:-1;
}
```

isolation will create a stacking content, where the pseudo element will be on top of the image, where the z-index will put it in the background, yet not hide it because it has a position of absolute and the isolate property.
