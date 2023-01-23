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
#### Handling Errors 
	- create an error class
	- validate data
#### Methods to filter data
