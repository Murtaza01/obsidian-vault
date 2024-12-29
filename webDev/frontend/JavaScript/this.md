This is a reference value to whatever its bound to, so in
order to understand this, we need to know what it is bound 
to, there is four bindings to this:

* default binding
* implicit binding
* explicit binding
* hard binding

# default binding

By default, this will refer to the global object, in the browser
its the window object:

```javascript
function hello(){
    console.log(this) // window
}
```


# implicit binding

When its used on objects, this will refer to the object

```javascript
const obj = {
 fn(){
    console.log(this) // obj 
 }
}
```

# explicit binding

We can put an object manually that `this` will refer to using one of
the function method `.call` `.apply`

```javascript
function greet(){
    console.log(this.name,'says hi');
}

const person = {
    name:"ali"
    age:21
}

greet() // undefined says hi
greet.call(person) // ali says hi
```

> fn.apply 

Does the same thing but it can take an array as a second argument.

# hard binding 

Hard binding will make `this` always refer to one object, so that
the reference of `this` is predictable but less flexible:


```javascript

function greet(){
 console.log(this.name "says hello")
}

const person = {
 name:'ali',
 age:21
} 

const greeter1 = greet.bind(person)
console.log(greeter1) // ali says hi

```

this greeter1 constant will always refer to the person object,
this is hard binding to the object
