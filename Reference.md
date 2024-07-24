 
```js
function reducerFn(state,action){
	return {
	counter: state.count + 1
	}
}
const counterReducer = reducerFn();

// OR

const counterReducer = function reducerFn(state,action){
	return {
	counter: state.count + 1
	}
}
```