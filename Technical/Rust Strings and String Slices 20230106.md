- Strings are complex in Rust as compared to many other languages

- This trade off that Rust has made to support its core principles.
	- Speed
	- Concurrency- Concurrency means **multiple computations are happening at the same time**. Concurrency is everywhere in modern programming, whether we like it or not: Multiple computers in a network. Multiple applications running on one computer.
	- Memory Safety or Memory Management - 

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
