# ES6 Object-oriented Programing Javascript

- Classes - stands for classification its a way define an object
	- inheritance - example drone or car might share some functionaility 
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
- To support older browsers we need to be working with transpilers and polyfills
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
- We can have a 

```

class Drone {

	constructor(id, name){
	// id and name are going to be attached to the instance drone
		this.id = id;
		this.name = name;
	}

}

let drone = new Drone('A123', 'Flyer');
let drone2 = new Drone('B456', 'Twirl');

console.log(drone instanceof Drone);
console.log('drone: ' + drone['id'] + ' ' + drone['name']);
console.log(drone.id + ' ' + drone2.id);
```

#### Methods

#### Static Methods
- Static methods belong directly on a class not on an instance

#### Getters and Setters
- Getters and setters let us execute some code when we access or set a property,