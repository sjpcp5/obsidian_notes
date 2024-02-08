![[Pasted image 20240131165412.png]]

In a monolithic Server  we would have 
![[Pasted image 20240131165512.png]]

In a microservice we would design each feature as a service like this
![[Pasted image 20240131165658.png]]

If we wanted to add a service that showed orders made by a customer 
- the feature would need access to the customer's user id in the user collection, the list of products associated by id would be a copy of the products listed on the order in the orders collection associated by the user's id. The data is communicated between microservices via an encrypted async service like pulsar created by yahoo
### Passing data and messages between microservices
#### Strategies
Synchronous - services communicate with each other using **direct requests**
Asynchronous - services communicate with each other **using events**

Example of synchronous, Service D, might use HTTP or JSON to send a request to the services it needs data from. 
![[Pasted image 20240131171048.png]]

#### Pros
Synchronous communication is easy to understand conceptually
Service D does not need a database
#### Cons
Introduces a dependency between services 
If any of the inter-services requests fail the overall request fails
The entire request is only as fast as the slowest request
We can easily introduce webs of requests
- ![[Pasted image 20240208173351.png]]Example of web of requests
## Asynchronous Communication
Event bus handles all the notifications from the services. The Event bus like (which SaaS offers this?) needs to be resilient bc if it goes down it crashes all the services. Not likely a commonly practiced. On top of it having downsides like Synchronous communication it additional downsides like conceptual easy to understand.
![[Pasted image 20240208173952.png]]

Best thing to do is define the exact goal of the service your wanting to build.
