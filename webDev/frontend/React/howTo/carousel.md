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

