
# Inheritance and Code Organization

Extening a class

```
class Vehicle {
// properties and methods here to be inherited
}

  

class Drone extends Vehicle {

}

  

class Car extends Vehicle {

}

  

let c = new Car();

  
// example of implied inheritance
// c is also an instance of vehicle and object
console.log(c instanceof Object);

```

```
class Vehicle {
	constructor(){
		console.log('construcing Vehicle');
	}

}

class Drone extends Vehicle {

}

class Car extends Vehicle {

//derived constructor must call super it makes sure vehicle's contructor gets called first.
	constructor(){
		// super();
			console.log('constructing Car');
			}
}

let c = new Car();
console.log(c instanceof Vehicle);

```
![[Pasted image 20230119171556.png]]