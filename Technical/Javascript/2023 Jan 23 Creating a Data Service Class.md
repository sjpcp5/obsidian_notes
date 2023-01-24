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


#### Instanitiaing Objects
	-Arrays
#### Handling Errors 
	- create an error class
	- validate data
#### Methods to filter data
