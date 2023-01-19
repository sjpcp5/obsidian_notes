
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
// c is also an instance of vehicle
console.log(c instanceof Object);

```