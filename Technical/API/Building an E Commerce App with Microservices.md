![[Pasted image 20240131165412.png]]

In a monolithic Server  we would have 
![[Pasted image 20240131165512.png]]

In a microservice we would design each feature as a service like this
![[Pasted image 20240131165658.png]]

If we wanted to add a service that showed orders made by a customer 
- the feature would need access to the customer's user id in the user collection, the list of products associated by id would be a copy of the products listed on the order in the orders collection associated by the user's id. Most likely communicate between an encrypted service that all the services use to talk to each other. 