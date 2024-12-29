# Ternary Operator

is a shorthand way of adding a condition to a giving code, see the code below for more understanding:

```javascript
function sum(a, b) {
  return a + b;
}

const result = sum(10, 10) > 1 ? sum(5, 5) : sum(1, 1);

console.log(result); // 👉️ 10
```

the first line after the function sum, is the compare operator that will work with our condition *(1)*, basically we are saying if the result of this function is bigger then 1, then `sum(5,5)` else `sum(1,1)` but here the if is represented as `?` and the else as  `:` and the condition is before the actually code

you can also use this syntax with else if statement, see the code below:

```JS
const getTime = () => {
  return (time >= 0) & (time < 12)
    ? "morning"
    : (time > 12) & (time < 18)
    ? "noon"
    : time > 18
    ? "eveing"
    : console.log(time);
};
```

in the above way we need the else statement, this is the same example as the [docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_operator#conditional_chains) its only has a better syntax (kinda)


there is another way to a shortcut if statement, which is by using the code below:

![[shortcut if.png]]

no else or brackets is needed, just the if and the condition and the followed action in the same line !

