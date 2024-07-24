there is three components i need to know before i build this site

1. Carousel
2. navbar
3. Drop-down menu


# 1. Carousel 

- [x] Using Bootstrap
- [x] Using Slick 
- [x] Using React Slick

Fail !

>  **Building it from the ground**

using React, im going to build it from the ground up, there is few steps to this:

1. i need to make the Carousel in CSS.
```html
    <div class="container">
      <div class="slider">
        <div class="slide">
        </div>
      </div>
    </div>
```
where we define the width and height in the `container` class, so our slider would take that width and height, then our slider would be the container of each slide, our slider 

2. i need to make  an array of the slides, which i will only show one based on the index of that one, using the map function, i also need a state which will control which index i show if i click a button:
```JSX
const [slideIndex,setSlideIndex]= useState(1)

{data.map((item,index)=>{
	<div className={slideIndex === index + 1 ? "slide active" : "slide"}>
	</div>
})}
```
the code above will show one slide that will give it the active class only when the `slideIndex` is matched, that means i can control that `slideIndex` using a function and an `onClick` property

3. i need a function to go to the next index in the array each time i click the next button:
```jsx
function nextSlide(){
	if(slideIndex !=== data.length){
		setSlideIndex(slideIndex + 1)
	} else{
		if (slideIndex === data.length){
		setSlideIndex(1)
		}
	}
}

<NextButton onClick={nextSlide}/>
```
the code above will check if the `slideIndex` didn't hit the length of the array, then it will add each time the button is clicked, once it get (handled by the else statement) it will rest it back to 1 (the first slide) which will make it infinite

4. i need a function that will go to the previous slide each time i click the previous button:
```jsx
function prevSlide(){
	if(slideIndex !== 1){
		setSlideIndex(slideIndex - 1)
		}
	else if (slideIndex === 1){
		setSlideIndex(data.length)
	}
}
```
in the code above, am checking if the slider is not on the first slide, then i can go back to the previous slide, if its is on the first slide, then i would give it the last index which is (data.length)

# 2. Accordion

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

>lowering the opacity of a background image

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