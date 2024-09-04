# Containers

you can add a container in bootsrap using the code below:

```html
<div class="container"></div>
<!-- to add a responisve contianer that will fill on all screens-->
<div class="container-fluid"></div>
```

to add content you need to add a row and a col, bootsrap containers are a row based system that has 12 column:

```html
<div class="container">
	<div class='row'>
		<div class='col-6'></div>
	</div>
</div>
```


# sizes on different screens

using the col-sm-2.. we can have different sizing on different screens, consider the code below:

```html
<div class='col-sm-2'></div>
```


this is basically saying "when the screen is small and above i want this col to take up 2 spaces (out of 12)" this will result to giving them at (at smaller then small screens) a 100% width, by this it means it will function as a block element (taking the whole row)

you can combine different size screen to set a limit between each one so that your website response to different screen size using the code below:

```html
<div class='col-lg-6 col-md-4 col-sm-2'></div>
```