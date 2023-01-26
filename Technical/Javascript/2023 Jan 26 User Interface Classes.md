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
- An element, before it becomes part of the DOM is just a string so need to create a method that 