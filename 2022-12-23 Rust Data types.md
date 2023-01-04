

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
	
}

main()
```

Once we have defined an array we can't change it's size

The syntax for initializing a large array is very similar to how we declared and array, except rather than declaring the data type,
we set the default value for each element in the array and then how many elements there are going to be in the array.

```
#![allow(unused_variables)]

fn main(){

	let location: [f64;10000] = [0.0; 10000]
	
}

main()
```

What if we wanted the coordinates to be associated with the name of the location? An Array can't handle that, so we will use a tuple. Rust will automatically recoqnize we have different data types and adjust the data types declaration.

from this 
```
#![allow(unused_variables)]

fn main(){

	let location: [f64;2] = ( "KCLE", 41.4094069; -81.8546911)
	
}

main()
```

to this

```
#![allow(unused_variables)]

fn main(){

	let location: (%str, f64,f64) = ( "KCLE", 41.4094069; -81.8546911)
	
}

main()
```

how do we write and array or tuple out to the console???

With scalar data types, a variable held a single value and we just referenced that variable and got the value back, but with compound data types we have multiple values. 

There are a couple of ways we can do this? 
The first way is to use the index postion in the array or the tuple to tell Rust which value we want  and we do this by putting a dot after the variable

```
#![allow(unused_variables)]

fn main(){

	let location: (%str, f64,f64) = ( "KCLE", 41.4094069; -81.8546911)
	println!("Location name")
	
}

main()
```
