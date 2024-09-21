# adding overlay

we can add overlay just like [this](https://codepen.io/t_afif/embed/vYbdVjb?default-tab=result)
with the boder-image property like this:

```css
.overlay {
  border-image: linear-gradient(#0003,#000) fill 0; 
}
```

> border-image

the border-image takes five values, we are only interested in two 
in this use case:

border-image-source == which is the source of the image we want to use,
it could linear-gradient, just like our example

border-image-slice == which is the place that the border going to start,
we use fill in our example to fill the whole image, and 0 because idk its
like that :)



