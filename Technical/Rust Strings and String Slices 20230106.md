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

main()
```