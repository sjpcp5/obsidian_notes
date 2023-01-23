# Creating a Data Service Class

- The data service class
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

- Data in JSON file
- Constructors
- Instanitiaing Objects
	-Arrays
- Handling Errors 
	- create an error class
	- validate data
- Methods to filter data