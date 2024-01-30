REST created around 2005 
SOAP created by microsoft fallen out of popularity but used in enterprises
GraphQL a later development 2017 popular to use.
gRPC

REST - For creating distributed APIs that are going to work with communication between apps and servers or websites and servers or even business to business servers, REST still represents a great percentage of the kind of work that's being done.

Why build an API and do we really need one?
- you don't need one if you have desktop clients that need to reach data
- You want to build an API if you have clients that want to call into your service
- If you need to go across different networks 
- If you need to be able to easily cross things like proxies and firewalls

HTTP protocols 
- client (laptop) request data from a server which is a text document. This text document contains three pieces.
	- a verb what action to take aka GET or POST ( create something) PATCH ( please update the address of a customer), DELETE (delete an object I mistakenly made )
	- headers- info or metadata about the request
		- content type: is the data binary, XML, JSON,
		- content length: size of content
		- Authorization: who is making the call, (server checks if they have read write  access )
		- Accept: when you send me a response what kind of data can I accept
		- Cookies: state or data that is passed that the client should expect 
	- content- optionally asked for
- the client receives a response back with status code back and a body
- the server is typically stateless because request to the server is very short lived unlike a game server or a database programming. The stateless server  connection is short lived it doesn't know if your going to send another request.