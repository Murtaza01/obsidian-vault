# statment

a javascript statment is a set of code that is ended with a semicolon

```Javascript
 alert('hello');
```

> implict semicolon

when we don't put a semicolon, it will be implict

```Javascript
alert('hello')
//same as alert('hello'); 
```

although sometimes the javascript compiler doesn't know how to infer
a semicolon so that you need to put it manually.

# varaibles

when we write this code:

```Javascript
 let name = "ali";
```

we are actually decalraing and assgining at the same time
the compiler is actually doing this behind the scenes:

```Javascript
 let name;
 name = "ali";
```

> UpperCase const

it is a convention that we uppercase constant that are hard coded,
for example birthdays or colors:

```Javascript
const COLOR_GRAY = #ccc 
```

> let

let unlike var, makes a block scoped level varaible, it red us of the
hoisting thing that comes from var, but it restrict us to use varaibles
inside blocks only

block can include if statments/ loops and functions..

```Javascript
if (something){
    let name = "mariam"
}

console.log(name) // undifiend
```

you can say that let binds to the local scope 

# Model Windows in Browser

We can use three things to show pop up windows:

+ alert: shows a message to the user.
+ prompt: similar to alert but with input.
+ confirm: returns true or false, used to ask questions.

# Type Conversion

We can type convert using three functions:

+ String()
+ Number(): shorter version is `+` before the string
+ Boolean()

