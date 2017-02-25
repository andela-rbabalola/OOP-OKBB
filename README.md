# Object Oriented Programming (OOP)
 
This is the output for the OKBB skill Object Oriented Programming. In this markdown, we will implement the following concepts in OOP
- Abstraction
- Encapsulation
- Inheritance
- Polymorphism
- Methods
- Overloading

## Encapsulation & Abstraction
Encapsulation is the process of hiding relevant data about an object in order to reduce complexity and increase efficiency. It also protects the object from outside interference and misuse. This is done through the process of abstraction. An example is given below:
```javascript
const Video = (volume) => {
  
  const increaseVolume = (number) => {
    let loudness = volume
    loudness += number;
    console.log(loudness);
  };
  
  return {
    increaseVolume
  };
}

const videoPlayer = Video(10);
videoPlayer.increaseVolume(10);
```
In the example above, the variable `loudness` which alters the volume can only be accessed within the object. This variable can only be manipulated via the `increaseVolume` method keeping it safe from outside interference and ensuring that the volume can only be increased by calling the `increaseVolume` method.

## Inheritance
Inheritance allows new objects to take the properties of existing objects. This is done by defining a base class from which other child classes can inherit object and properties from. Inheritance helps to avoid code duplication and is one of the core tenets of OOP. 

In Javascript, inheritance can be done using the `prototype` key word. Here is an example:
```javascript
// We define the parent class entertainer
function Entertainer (name, age) {
  this.name = name;
  this.age = age;
}
// Give entertainer ability to perform
Entertainer.prototype.perform = function() {
  return `My name is ${this.name}, I am a ${this.age} year old entertainer
  and I am displaying my talent!!`;
}

// We define a subclass of Entertainer - Dancer
function Dancer (name, age, dance) {
  this.name = name;
  this.age = age;
  this.dance = dance;
}
// Inherit perform method from Entertainer class
Dancer.prototype = new Entertainer();

// Create objects of the Entertainer and Dancer classes
const entertainer = new Entertainer('Jack', 24); 
const dancer = new Dancer('Jane', 19, 'salsa');

console.log(entertainer.perform());
console.log(dancer.perform());
```
We see how the child class `Dancer` has access to the `perform` method of the parent class `Entertainer` without having to repeat the code for the `perform` method

## Polymorphism
Polymorphism is another important concept in OOP. It allows child classes to override specific behaviours of parent classes. It takes advantage of inheritance to make this happen. Carrying on from our previous example on Inheritance, we can make the `Dancer` child class override the behaviour of the `perform` method from the parent class `Entertainer`. This is shown below:
```javascript
// Override behaviour of perform method
Dancer.prototype.perform = function() {
  return `My name is ${this.name}, I am a ${this.age} year old dancer and I
  am performing the ${this.dance} dance`;
}

console.log(dancer.perform());
```
We can see how even though the `Dancer` class inherited the `perform` method from the `Entertainer` class it is able to override its behaviour and define its own custom behaviour for that method.

## Methods
Methods are basically functions that are defined within classes. Methods allow objects of a class to perform specific actions. For example, the `perform` method in the `Dancer` class allows an object of that class to perform a specific dance.

## Overloading
Overloading is the ability of one function to perform different tasks i.e. it allows creating several function with the same name which differ from each other in the type of the input and the output of the function. A simple example is shown below:
```javascript
const manipulateNumbers = function (...args) {
  if (args.length === 1) {
    return args * 2;
  } else if (args.length === 2) {
    return args[0] * args[1];
  } else {
    return 'You have passed in more than 2 arguments';
  }
}

manipulateNumbers(2);
manipulateNumbers(2, 4);
manipulateNumbers(2, 4, 5);
```
In the example above we can see that the behaviour of the function `manipulateNumbers` changes depending on the number of arguments we pass to it.
