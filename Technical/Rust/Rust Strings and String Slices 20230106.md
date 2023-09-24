# Rust Topic: Strings
#Strings
- Strings are complex in Rust as compared to many other languages

- This trade off that Rust has made to support its core principles.
	- Speed
	- Concurrency- Concurrency means **multiple computations are happening at the same time**. Concurrency is everywhere in modern programming, whether we like it or not: Multiple computers in a network. Multiple applications running on one computer.
	- Memory Safety or Memory Management - 
	
### String Types
Strings
- Vector of u8 data
- Mutable
- Stored on the heap

&str
* Vector of u8 data
* immutable
* Can be stored on the heap, stack or embeded in the compiled code.

Its hard to cover one topic in Rust because much of the topics in it overlaps. 
It would be good to reference this in the future when we talk about variables and variable immutability.

**A String is stored on the heap because it can grow and shrink in size. The size is not constant so it cannot be stored on the stack.**

A string slice is more complex and can be stored on the heap, on the stack, or as a string literal embedded in the code itself depending on how its created and how it's used.

### Converting data between String Types
Each string type will serve an important role. 
This is how you can convert data between the two string types.

```
#![allow(unused_variables)]

fn main(){
let person_name_slice:&str = "Donald Mallard";
// create a string type and not string slice type
// all we need to do is use the string slice to_string() method

let person_name_string:&str = person_name_slice.to_string();
}


```

String literals are embeded in code versus being stored in the stack or on the heap but they are also a string slice. 
If we want to assign a string literal to a type of string we need to call the to_string method on the string literal.

Just one way to do it
```
#![allow(unused_variables)]

fn main(){
let person_name_slice:&str = "Donald Mallard";

let person_name_string:String = "Donald Mallard".to_string();
}

```
 Another way we can create a string from a string slice is by using the String::from method
```
#![allow(unused_variables)]

fn main(){
let person_name_slice:&str = "Donald Mallard";

let person_name_string:String = String::from(s:"Donald Mallard");
}
```

Converting a string to a string slice
```
#![allow(unused_variables)]

fn main(){
let person_name_string:String = String::from(s:"Donald Mallard");
let person_name_slice = &person_name_string;

// you can also use the as_str() method
let person_name_slice2 = person_name_string.as_str();
}
```

When we store the memory on the heap we note the address of where we stored the data then we use the pointer, which is a special variable that holds the memory address on the heap so that we can find that data again later. 
There are some special symbols that we use with pointers which are asterisks `*` and ampersands`&`, and gross over simplification of the subject an ampersand tell us the memory address where the data lives.
So in this scenario the string data isn't copied to the string slice, rather the string slice is effectively holding the memory address where the data lives and it's this scenario where the sting slice is working with a string that is stored on the heap. This might also be called derefferencing the variable.