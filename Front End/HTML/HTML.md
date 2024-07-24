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

# table

table is used for semantic purposes, but they also makes things easier to handle, to use tables we need the following html elements:

```html
<table>
	<caption>Name of the table</caption>
	<colgroup>
		<col>
	</colgroup>
	<thead>
	<tr>
		<th colspan="2">table head</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>table data</td>
	</tr>
	</tbody>
</table>
```

here is some information:
```html
<colgroup> <!-- to style groups -->
<col> <!-- we can add border and style different col based on how much cols we have, if we put one, it will style all of them -->
<tbody> <!-- for sematinc purposes -->
<thead> <!-- for sematinc purposes -->
<tr> <!-- needed to form a row -->
<td> <!-- table data, is a cell -->
<th> <!-- also a cell but its bold -->
<th colspan="2"> <!-- how much the cell takes space, two cells in this case -->
```

> styling tables

we need to put those styles to change the default behavior of tables:

```css
table{
	table-layout: fixed;
	border-collapse: collapse;
}
```

# [Figure](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure)

use to add caption to your image