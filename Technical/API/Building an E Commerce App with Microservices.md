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