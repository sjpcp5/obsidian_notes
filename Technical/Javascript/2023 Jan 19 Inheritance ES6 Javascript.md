
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
#### Example of inheritence needing call super() first even if Vehicle has no constructor super() still needs to be called on class extending Vehicle. Javascript provides implied properties on a empty class
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
#### Correct example
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
		super();
			console.log('constructing Car');
			}
}

let c = new Car();
console.log(c instanceof Vehicle);
```
#### passing arguments into constructors to inherit
- we can store the license number on Car but we want it to be accessible on all vehicles. In order to do that the example below passes the license number through super to the constructor in Vehicle.
```
class Vehicle {
	constructor(licenseNum){
		this.licenseNum = licenseNum;

	}
}

class Drone extends Vehicle {

}

class Car extends Vehicle {

			//derived constructor must call super it makes sure //vehicle's contructor gets called first.

	constructor(licenseNum){
		super(licenseNum);
	}
}

let c = new Car('A123');

console.log(c instanceof Vehicle);

console.log(c.licenseNum);
```
#### In creating properties in classes and derived classes remember super() is always before this otherwise error messages.

```
class Vehicle {
	constructor(){
		this.gpsEnabled = true;

	}
}

class Drone extends Vehicle {

}

class Car extends Vehicle {

	constructor(){
		super();
		this.gpsEnabled = false;
	}
}

let c = new Car();

console.log(c.gpsEnabled);
```

#### Methods with Inheritance
- In constructors super() always had to be called first
- In methods when overriding 
```
class Vehicle {
	constructor(){
		this.gpsEnabled = true;

	}
}

class Drone extends Vehicle {

}

class Car extends Vehicle {

	constructor(){
		super();
		this.gpsEnabled = false;
	}
}

let c = new Car();

console.log(c.gpsEnabled);
```