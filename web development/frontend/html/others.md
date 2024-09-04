# menu 
// search for it and write !
# Progress

is an html element that help you make a progress bar, it takes two property to function, one is the max value, and the other is the actual value of the progress bar:

```jsx

const time = 3000
function ProgressBar(){
const [timer,setTimer]useState(time);

useEffect(()=>{
	const interval = setInterval(()=>{
	setTimer(prevTime => prevTime-10)
	},10)

	retrun ()=>{
	clearInterval(interval)
	}
},[])

return (
	<progress max={time} value={timer} ></progress>
)
}
```

# [Figure](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure)

use to add caption to your image
