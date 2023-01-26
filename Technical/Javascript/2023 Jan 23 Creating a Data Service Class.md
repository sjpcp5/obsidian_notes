# Creating a Data Service Class

#### The data service class
	 - retrieving information
	 - create file `fleet-data-service.js`
```
// cars and drones collection the purpose is to manage them from the
// data feed

import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
	}
};
```

#### Data in JSON file
	- create data file `fleet-data.js`
```
export let fleet = [
	{
		license: 'ABC123',
		type: 'drone',
		model: 'Amazon 1250',
		airTimeHours: '6050',
		base: 'New York',
		latLong: '40.775596 -73.974615'
	},
	{
		license: 'XYZ456',
		type: 'drone',
		model: 'Amazon 1550',
		airTimeHours: '2100',
		base: 'New York',
		latLong: '40.771956 -73.978531'
	},
	{
		license: 'QRS678',
		type: 'drone',
		model: 'Google 3800',
		airTimeHours: '300',
		base: 'New York',
		latLong: '40.779423 -73.969411'
	},
	{
		license: 'AT9900',
		type: 'car',
		make: 'Tesla',
		model: 'Quick Transport',
		miles: '15600',
		latLong: '40.773272 -73.968875'
	},
	{
		license: 'AT2000',
		type: 'car',
		make: 'Uber',
		model: 'Auto Taxi Plus',
		miles: '400',
		latLong: '40.778878 -73.968435'
	},
	{
		license: 'AT2020',
		type: 'car',
		make: 'Uber',
		model: 'Zip Trip',
		miles: '12200',
		latLong: '40.778984 -73.962266'
	},
	{
		license: 'AT4000',
		type: 'car',
		make: 'Lyft',
		model: 'Pick U Up',
		miles: '400',
		latLong: '40.774036 -73.967319'
	}
];
```
 
#### Constructors
- _Instantiation_ is **the creation of a real instance or particular realization of an abstraction or template**, such as a class of objects or a computer process.
- in the file `app.js` instantiate the data service
```
import { Car } from './classes/car.js';
import { Drone } from './classes/drone.js';
import {fleet} from './fleet-data.js'
import { FleetDataService } from './services/fleet-data-service.js';

//instanitiate the data service  
let dataService = new FleetDataService();

dataService.loadData(fleet);

console.log(dataService.cars);
```
- Next we will parse the fleet data object in the `FleetDataService` in order to organize it, validating the data and seeting up methods to query it, sort it and filter it.
- In the file `fleet-data-service.js` 
	- `fleet` is a big array and we can loop through it with `for of` statement
	- set a variable called `data` bc we don't know if its a car or drone
	- we will use a switch statement to check the `type`
	- create methods to `loadCar` data and `loadDrone` data
```
import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
	}
	loadData(fleet){
		for (let data of fleet){
			switch(data.type){
				case 'car':
					this.cars.push(data);
					break;
				case 'drone':
					this.drones.push(data);
					break;
			}
		}
	}
	loadCar(car){
		let c = new Car(car.license, car.model, car.latlong);
		c.miles = car.miles;
		c.make = car.make;
		return c;
	};
	loadDrone(drone){
		let d = new Drone(drone.license, drone.model, drone.latlong);
		d.airTimeHours = drone.airTimeHours;
		d.base = drone.base;
		return d;
	};
};
```
- add constructor to the `Vehicle` class in the `Vehicle.js` file
-  add the common properties license, model, latlong
```
export class Vehicle {
	constructor(license, model, latlong){
		this.license = license;
		this.model = model;
		this.latlong = latlong;
	}
}
```
-  add a constructor to the drone class
```
import { Vehicle } from './vehicle.js'

export class Drone extends Vehicle{
	constuctor(license, model, latlong){
		super(license, model, latlong);
		this.airTimeHours = null;
		this.base = null;
	}
}

```
#### Instanitiaing Objects
	-Arrays
- in the file `app.js` loop through the cars and drone array using `for of`  statement and a local varible to represent each unique object in the specific arrays
* don't add a semi-colon after the `for of ` statement that will give you an undefined error and will make the local variable unreachable in the scope.
_working example below_
```
import { Car } from './classes/car.js';
import { Drone } from './classes/drone.js';
import {fleet} from './fleet-data.js'
import {FleetDataService} from './services/fleet-data-service.js';

let dataService = new FleetDataService();
dataService.loadData(fleet);

// for of statement for cars
for (let car of dataService.cars)
console.log(car.license, 'cars');


// logs to check if the dataService is working
console.log(dataService.cars);
console.log(dataService.drones);

// for of statement for drones
for (let drone of dataService.drones)
console.log( drone.license, 'drones');
```

#### Handling Errors 
- When working with data feeds they're usually prone to errors and your going to get values your don't expect or maybe entire objects
###### Next steps
- create an error class
- validate data
- create an array to store errors in the `fleet-data-service` class constructor
- when we find an error we want to continue processing the data feed that way the user of the  will have the option to check the errors or ignore them and work with the data that did load properly
```
import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
		// as we get errors we will dump them in this array
		this.errors = [];
	}
```
- create a DataError class its a simple class holding message and the data error
```
export class DataError{
	constructor(message, data){
		this.message = message;
		this.data = data;
	}
}
```
- import DataError into the `fleet-data-service.js`
- looking at this file one thing can go wrong if our switch statement doesn't have a default
- add a default  to the switch statement 
- create a local variable `e` and instaniate a new `DataErrors` 
- we will give it the message "Invalid vehcle type" and pass it `data` then push this to the errors array
```
import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';
import { DataError } from './data-error.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
		// as we get errors we will dump them in this array
		this.errors = [];
	}
		loadData(fleet){
		for (let data of fleet){
			switch(data.type){
				case 'car':
					this.cars.push(data);
					break;
				case 'drone':
					this.drones.push(data);
					break;
				default:
					let e = new DataError('Invalid vehicle type', data)
					this.errors.push(e)
					break;
			}
		}
	}
	loadCar(car){
		let c = new Car(car.license, car.model, car.latlong);
		c.miles = car.miles;
		c.make = car.make;
		return c;
	};
	loadDrone(drone){
		let d = new Drone(drone.license, drone.model, drone.latlong);
		d.airTimeHours = drone.airTimeHours;
		d.base = drone.base;
		return d;
	};
};
```
- another place things can go wrong is load car, an exception can get raised
- we can watch for it and store it in the error's array with a `try` statement do this for drone as well
```
import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';
import { DataError } from './data-error.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
		// as we get errors we will dump them in this array
		this.errors = [];
	}
		loadData(fleet){
		for (let data of fleet){
			switch(data.type){
				case 'car':
					this.cars.push(data);
					break;
				case 'drone':
					this.drones.push(data);
					break;
				default:
					let e = new DataError('Invalid vehicle type', data)
					this.errors.push(e)
					break;
			}
		}
	}
	loadCar(car){
		try {
			let c = new Car(car.license, car.model, car.latlong);
			c.miles = car.miles;
			c.make = car.make;
			return c;
		} catch(e){
			this.errors.push(new DataError('error loading car', car));
			}
		return null;
	};

	loadDrone(drone) {
		try {
			let d = new Drone(drone.license, drone.model, drone.latlong);
			d.airTimeHours = drone.airTimeHours;
			d.base = drone.base;
			return d;
		} catch (e) {
		this.errors.push(new DataError('error loading drone', drone));
		}
		return null;
	};
};

```
- lets loop through the error messages in app.js and change a value in feet-data.js so we'll produce an error.  Remove the 'd' from "drone" and save.
```
import { Car } from './classes/car.js';
import { Drone } from './classes/drone.js';
import {fleet} from './fleet-data.js'
import {FleetDataService} from './services/fleet-data-service.js';

let dataService = new FleetDataService();
dataService.loadData(fleet);

// for of statement for cars
for (let car of dataService.cars)
console.log(car.license, 'cars');

// for of statement for drones
for (let drone of dataService.drones)
console.log( drone.license, 'drones');

// loop through error messages
for (let e of dataService.errors)
console.log(e.message, e.data);
```

##### Data Validation in our Data Service
- First we would create an if and else statement to bring in our data validator and push any errors in our else statement
example of what `fleet-data-service.js` looks like after we are done creating validation
```
import {Car} from '../classes/car.js';
import {Drone} from '../classes/drone.js';
import { DataError } from './data-error.js';

export class FleetDataService {
	constructor(){
		this.cars = [];
		this.drones = [];
		// as we get errors we will dump them in this array
		this.errors = [];
	}
		loadData(fleet){
		for (let data of fleet){
			switch(data.type){
				case 'car':
				if (this.validateCarData(data)) {
					let car = this.loadCar(data);
					if (car)
						this.cars.push(car);
				} else {
					let e = new DataError('Invalid car data', data);
					this.errors.push(e);
				}
				break;
				case 'drone':
					this.drones.push(data);
					break;
				default:
					let e = new DataError('Invalid vehicle type', data)
					this.errors.push(e)
					break;
			}
		}
	}
	loadCar(car){
		try {
			let c = new Car(car.license, car.model, car.latlong);
			c.miles = car.miles;
			c.make = car.make;
			return c;
		} catch(e){
			this.errors.push(new DataError('error loading car', car));
			}
		return null;
	};

	loadDrone(drone) {
		try {
			let d = new Drone(drone.license, drone.model, drone.latlong);
			d.airTimeHours = drone.airTimeHours;
			d.base = drone.base;
			return d;
		} catch (e) {
		this.errors.push(new DataError('error loading drone', drone));
		}
		return null;
	};
	validateCarData(car) {
		 requiredProps = 'license model latlong miles make'.split(' ');
		 let hasErrors = false;
		 for (let field of requiredProps) {
			 if (!car[field]) {
				 this.errors.push(new DataError(`invalid field ${field}`, car));
				 hasErrors = true;
				 }
			}
			if (Number.isNaN(Number.parseFloat(car.miles))) {
				this.errors.push(new DataError('invalid mileage', car));
				hasErrors = true;
			}
			return !hasErrors;
	}
};
```
##### Creating the validateCarData method
- We will define our data validator by naming it `validateCarData` 
- then we will set our properites to be loop through as an array by creating the local variable `requiredProps` an listing them in a string then spliting by an empty space
- This enables us to loop through them with an `for of` statement 
- We will call each property `field` and we want to make sure car has that field by it ensuring it has it by rasing an error. 
- We use an `if` statement checking if the argument car doesn't have the field then push errors with instance of DataError.
- We also need return true or false for `validateCarData` because we wrapped it in a `if` statement. 
- Create anoter local variable and we initialize it as `false` . So we can set it to true if there are errors 
- Validation here can check for required fields, have a check for each field itself, like checking a valid format for longitude and latitude, making sure the license number is something that would be valid
- Create validation that `miles` driven is acutally a number. We check for Not a Number when we parse `car.miles`. 
- We add an error if miles is not a number is true 
- For the final scope of `validateCarData` we return a negate `hasErrors` so if there are no errors we return `true` and if there are errors we will return `false` to fit the name of the function
```
	validateCarData(car) {
		 requiredProps = 'license model latlong miles make'.split(' ');
		 let hasErrors = false;
		 for (let field of requiredProps) {
			 if (!car[field]) {
				 this.errors.push(new DataError(`invalid field ${field}`, car));
				 hasErrors = true;
				 }
			}
			if (Number.isNaN(Number.parseFloat(car.miles))) {
				this.errors.push(new DataError('invalid mileage', car));
				hasErrors = true;
			}
			return !hasErrors;
	}
};
```
- Add an if statement before `this.cars.push(car)` this checks if an exception was thrown in the `loadCar` method
```
	switch(data.type){
		case 'car':
			if (this.validateCarData(data)) {
				let car = this.loadCar(data);
				if (car)
					this.cars.push(car);
```
#### Methods to sort and filter data
- In the file `fleet-data-service.js` write a find and sort method for license
```
getCarByLicense(license) {
	return this.cars.find(function (car) {
		return car.license === license;
	});
}

getCarsSortedByLicense() {
	return this.cars.sort(function (car1, car2) {
		if (car1.license < car2.license)
			return -1;
		if (car1.license > car2.license)
			return 1;
		return 0;
	});
}
```
- Write helpers with in the methods to prevent other devs creating infinite loops
- How do I write a helper what does it look like?

##### Filtering Data