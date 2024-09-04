# Constructor function

a constructor function is a function that create other functions or objects, it start with a capital letter and we use the keyword New with it, example:

```javascript
// constructor function
function Person (name, age, gender) {

   // assigning  parameter values to the calling object
    this.name = name;
    this.age = age;
    this.gender = gender;

    this.greet = function () {
        return ('Hi' + ' ' + this.name);
    }
}

// creating objects
const person1 = new Person('John', 23, 'male');
const person2 = new Person('Sam', 25, 'female');

// accessing properties
console.log(person1.name); // "John"
console.log(person2.name); // "Sam"

//excuting the method greet, we are consloing it because the function only returns a value
console.log(person1.greet())

```

in the above example, greet is a method that we can use to the person1 to execute the function, the the example in the end
