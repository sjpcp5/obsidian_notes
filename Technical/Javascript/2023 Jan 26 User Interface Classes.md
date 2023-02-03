# User Interface Classes

- create buttons
- create image class
- create responsive title bar
- data table
- map class
### Steps
- visit material design lite https://getmdl.io/started/index.html for button and layout
- `npm install -save material design lite`
- add links to index.html from the https://getmdl.io/started/index.html
```
<html>
	<head>
		<title>Drones</title>

		<link rel="stylesheet" href="https://fonts.googleapis.com/iconfamily=Material+Icons">
		<link rel="stylesheet" href="https://code.getmdl.io/1.3.0/material.indigopink.min.css">

		<script src="node_modules/traceur/bin/traceur.js"></script>
		<script src="node_modules/es6-module-loader/dist/es6-module-loader-dev.js"</script>

// material design lite scripts
		<script defer src="https://code.getmdl.io/1.3.0/material.min.js"></script>
	</head>
	<body>
		<script>
			System.import('src/app.js');
		</script>
	</body>
</html>
```
- `npm install save jquery`
- jquery will not recognize ES6 and above so systemjs needs to be added to the dependences
- SystemJS will load ES6 modules as well as CommonJS and RequireJS modules
- `npm install -save systemjs`
- replace the script es6 node modules with systemjs script `<script src="node_modules/systemjs/dist/system.js"></script>`
```
<html>
	<head>
		<title>Drones</title>

		<link rel="stylesheet" href="https://fonts.googleapis.com/iconfamily=Material+Icons">
		<link rel="stylesheet" href="https://code.getmdl.io/1.3.0/material.indigopink.min.css">

		<script src="node_modules/traceur/bin/traceur.js"></script>
// systemjs module
		<script src="node_modules/systemjs/dist/system.js"></script>

// material design lite scripts
		<script defer src="https://code.getmdl.io/1.3.0/material.min.js"></script>
	</head>
	<body>
		<script>
			System.import('src/app.js');
		</script>
	</body>
</html>
```
- Systemjs extends ES6 module loader so system.import stays the same
- Tell system that jquery is a loadable module
- Add `System.paths['jquery']= './node_modules/jquery/dist/jquery.js';` above `System.import('src/app.js')` in file `index.html`
- now we don't have to add the script tag for jquery since systemjs is handling it for us
### Create UI file system
- create class BaseElement
- An element, before it becomes part of the DOM is just a string 
- Each componet is going to have its own string that has the tag and any classes any attributes. So we want to make sure this gets overwritten. We'll throw an exception so if it doesn't get overwritten we will leave the developer a nice message
`base-element.js`
```
import $ from 'jquery';

// default export for jquery

export class BaseElement{

constructor(){

this.element = null; // jQuery object and not a DOM element, storing the element in a jquery object wrapper

}

getElementString() {

throw 'Please override getElementString() in BaseElement';

}

}
```
- The base element is all setup. When we create a any kind of element which is simply a DOM tag we could have that class extend the base element and we'll get access the all this functionality
```
import $ from 'jquery';
// default export for jquery

export class BaseElement{
	constructor(){
		this.element = null; 
	// jQuery object and not a DOM element, storing the element in a jquery object wrapper
	}

	appendToElement(el) {
		this.createElement();
		el.append(this.element);
	}
	
	createElement() {
		const s = this.getElementString();
		this.element = $(s);
	}

	getElementString() {
		throw 'Please override getElementString() in BaseElement';
	}
}
```

#### Create and render a button
- It is a hassle to be working with imports for everything but it does solve the big namespace problem in Javascript.
- It means we can work with lots of different libraries that have buttons and if there was ever a conflict we could just give an alias to button we could say `import {Button as MyButton} from './ui/button.js'`
- app.js ![[Pasted image 20230126172930.png]]
- button.js ![[Pasted image 20230126173009.png]]
#### Create and render an Image component
- Use straight up HTML
- if you run into errors with loading systemjs 
	- delete node modules 
	- make sure your package.json matches whats in the follwoing image
	- ![[Pasted image 20230201152454.png]]
	- then `npm intall` && `npm run dev`
	- if the drone image doesn't load make sure the images folder exists under .vscode 
	- ![[Pasted image 20230201152708.png]]
	- if not copy and paste from `javascript-es6-object-oriented-programming/6-javascript-es6-object-oriented-programming-m6-exercise-files/final-working/after/images`
#### Create and Render a titlebar


- Make a `title-bar.js` file. Then copy and paste the image class into it. Change the class name to `TitleBar` 
- Go to https://getmdl.io/components/index.html#layout-section copy the fixed header layout and paste within template literals 
- to fix the menu bar being off the html.index doesn't know we are using html5 so we need to write in the `<!DOCTYPE html>` tag  at the top the `index.html` file. Or if your in visual code just type !!! and press `enter` in the first line of the `index.html` 
- ![[Pasted image 20230203160855.png]]