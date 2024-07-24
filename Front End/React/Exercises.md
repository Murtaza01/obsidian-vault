> Section 4 / 19 
![[Exersice 1.png]]

> My Solution

```JSX
function Player(){
const [isEditing,setIsEditing]= useState(false);

function handleClick(){
	setIsEditing(!isEditing)
}

return <>
{!isEditing ? <span>{name}</span> : <input />}
<button onClick={handleClick}>Edit</button>
</>
}

```

> His Solution

![[Exercise 1 solution.png]]