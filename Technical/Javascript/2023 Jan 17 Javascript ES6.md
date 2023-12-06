# ES6 Object-oriented Programming Javascript

- Classes - stands for classification its a way define an object
	- inheritance - example drone or car might share some functionality 
	- Create an abstract class called Vehicle
- All objects derived from Object
- Modules - Data service class will consolidate everything. Inside the service we will have a list of cars and a list of drone objects. With functions to access the data. Functions are called methods within a class example `getCarByLicense()` &`sortCarsByMake()`
	- Having a data service keeps things simple and easy to test and won't have your data scattered all throughout your source code.
- Business Objects - This is where we create classes to model the user interface
	- we will create a button class to use buttons such as `SELF DRIVING CARS` & `DRONES`
	- We will be using Material Design Lite *(interface user framework similar to Bootstrap)*
	- Create an image class to show images
	- Create a title bar class to show the title bar
	- Create a class to create a data grid
	- Create a class to work with google maps

### Dev environment
- In the Browser Chrome or Firefox: Use F12 to open dev tools and to refresh
- To support older browsers we need to be working with transpilers and poly-fills
- To check compatibility use Kangax.github.io : http://kangax.github.io/compat-table/es6/ 
- Typscript/Babel Compiler Transpliers on't allow subclassing
- Rapid ES6 Training pluralsight course to quickly get up to speed with ES6

### Class Basics
- Classes are fundamental to object-oriented programing
- Think of a class as a blue print or a stamp in order to stamp out objects and create objects
#### What is a Module ?

#### Defining Classes
- Representation or sometimes an abstraction
- commonly known as a model
- A classs is not an object and can be thought of as a blueprint. This is where most of the programming happens.
- The class contains properities like amt of flight time left for a drone, the number of rotors, the maximum speed of the drone, and it's current GPS.
- The class can also contain actions to perform. We can program methods that would send it to a given GPS coordinate, start or stop the rotors.

#### Classes Creation
- always use captilize your class by using pascal casing
```
class Drone {
// details here
}
// new keyword of a new instance 
let drone = new Drone();
```

```
class Drone {

}

let drone = new Drone();
// this will tell us at runtime that whether a variable or not is an instance of //a class
console.log(drone instanceof Drone);
```
#### Constructors and Properties
- Keep the class simple and be able to test easily
- Normally we don't wanna do any heavy processing in a constructor.
- We want to create instance variables
- We `this.` keyword to refer to the instance being created
- 
```
// This is a very familiar pattern, you pass info into the constructor and you //save it on the instance variable this
class Drone {

	constructor(id, name){
	// id and name are going to be attached to the instance drone
		this.id = id;
		this.name = name;
	}

}

let drone = new Drone('A123', 'Flyer');

console.log(drone instanceof Drone);
console.log('drone: ' + drone['id'] + ' ' + drone['name']);
```

#### Static Properties
- It's very important to understand the difference between instance variables at the instance level those would instance properties  or properties at the class level. which are called class properties.
- Each instance of drone will have its own set of properties
- We can have properties directly on Drone the class these are *static properties* or *class properties*

```

class Drone {

	constructor(id, name){
	// id and name are going to be attached to the instance drone
		this.id = id;
		this.name = name;
	}
	// put a property directly on drone below here
	Drone.maxHeight = 2000

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

console.log(drone instanceof Drone);
console.log('drone: ' + drone['id'] + ' ' + drone['name']);
console.log(drone.id + ' ' + drone2.id);
console.log(Drone.maxHeight);
// there is currently not a maxHeight on the instance // only on the class. So the following won't work its // undefined
console.log(drone.maxHeight);

```


- **Recap** instance properties only get placed on the instance of the class when it gets instantiated and created as an object.
- We also add properties to the class itself aka Static properties
```
class Drone {

	constructor(id, name){
		this.id = id;
		this.name = name;
	}
	Drone.maxHeight = 2000

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

console.log(Drone.maxHeight);
// there is currently not a maxHeight on the instance // only on the class. So the following won't work its // undefined
console.log(drone.maxHeight);
```

#### Methods
* A method is a function that gets attached to the instance
* when working with the instance of class you need to always use the `this` keyword with a property name  example `this.id`

```
class Drone {

	constructor(id, name){
		this.id = id;
		this.name = name;
	}
	fly(){
	// remember we need to access the instance by using the this keyword //otherwise id will be undefined
		console.log('Drone ' + this.id + ' is flying');
	}

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

// call the method as an instance
drone.fly();
drone2.fly();

```

#### Static Methods
- Static methods belong directly on a class not on an instance
- Static methods can't access instance variables or properties 

```
class Drone {

	constructor(id, name){
		this.id = id;
		this.name = name;
	}
	static getCompany(){
		console.log('in getCompany')
	}
	
	fly(){
	// remember we need to access the instance by using the this keyword //otherwise id will be undefined
		console.log('Drone ' + this.id + ' is flying');
	}

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

// correct way of calling a static class
Drone.getCompany();
// incorrect way of calling a static class
drone.getCompany();
```


- If we tried to call a property using `this.id `in static `getCompany()` we would get undefined because it doesn't exist on class Drone. It only exists on drone instances.
* Be aware if a method belongs as a static method or as an instance of the class which would not use the static keyword.
```
class Drone {

	constructor(id, name){
		this.id = id;
		this.name = name;
	}
	static getCompany(){
		console.log(this.id)
	}
	
	fly(){
	// remember we need to access the instance by using the this keyword //otherwise id will be undefined
		console.log('Drone ' + this.id + ' is flying');
	}

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

// correct way of calling a static class
Drone.getCompany();

```
#### Getters and Setters
- Getters and setters let us execute some code when we access or set a property,
-  When a variable begins with an underscore its a convention that usually means it's private. It's a variable that symbolizes it should not be toyed with
- How to make javascript variables private with closures:  https://dev.to/somedood/emulating-private-variables-in-javascript-with-closures-and-factory-functions-2314
- There are no private variables in classes yet...
- We want to create a new property that behaves somewhat like a function 
- This getter example is for validation, logging, or any case where you need to execute a function when all you need is a property.
```
class Drone {

	constructor(id){
		this._id = id;
	}
// get id() looks like a function but it's not we can access //it like a property as in drone.id without closing and //opening parenthesis
	get id(){
		// you can do validation, checking or alter the result here
		console.log('in id getter');
		return this._id + ' TEMPORARY';
	}

}

let drone = new Drone('A123')
console.log('drone id: ' + drone.id);



```

- We can also have setters 
-  Just like a getter a **setter** is used to execute an function when we set a value. So we can have any kind of error checking, validation, or change the data on how we want.

```
class Drone {

	constructor(id){
		this._id = id;
	}
// get id() looks like a function but it's not we can access //it like a property as in drone.id without closing and //opening parenthesis
	get id(){
		// you can do validation, checking or alter the result here
		console.log('in id getter');
		return this._id + ' TEMPORARY';
	}
	set id(value){
		this._id = value
	}

}

let drone = new Drone('A123')
drone.id = 'B456';
console.log('drone id: ' + drone.id);



```
**results in**
```
in id getter
drone id: B456 TEMPORARY
```

- By setting `drone.id = 'B456'` our setter `set id(value)` was invoked and `this._id` was set to the new value. And when we console logged out `drone.id` it needed to execute the getter function for id in order to print it out. So this is why we got `B456 TEMPORARY`.
	- Remember the underscore in front of  `id` is just a convention and it's not required at all.
	- But normally when you see a underscore before a variable in a class you can think of it as private and thats probaly what the programmer intended like below: 
```
class Drone {

	constructor(id){
		this._id = id;
	}
}
```

A module can be simply a file.