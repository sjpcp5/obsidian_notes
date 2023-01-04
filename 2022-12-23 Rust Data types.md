

#### #Characters and booleans true or false

characters Letters 
common size C# and Java byte size 2

* 1 byte 255 characters in ASCII

* 2 bytes 65535 characters in Unicode-16 table

* 4 bytes 4294,967,296 characters in unicode-32 table. 
	* Rust has a 4 byte character type. A character in Rust can be any letter or symbol in any language or alphabet. 
	* Does this make Rust very adaptable in translating to any language or complied language?

**biggest thing to rememeber in Rust about booleans and characters you use a single quote to define a character literal rather than the double quotes user for strings.**


#### #Compound Data types- single variable holding multiple values

Arrays- multiple values of a single data type

Tuples - mulitple values, but can be different data types

They are both very fast at runtime but are fixed sized.

latitute and longitude in degrees

Before an array is used it must be initialized, most of the time we will initialize an array in line with our declaration.  

```
#![allow(unused_variables)]

fn main(){
	##declare the variable and data type then the value [41.4094069, -81.8546911]
	let location: [f32;2]= [0.0, 0.0];

	let location: [f64;10000] = 
	
}

main()
```

Once we have defined an array we can't change it's size

The syntax for setting 
