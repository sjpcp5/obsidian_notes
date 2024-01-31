
There is monolithic server would be characterized as containing
all routing, middlewares, business logic, database access to implement **all the features** of our app. 

versus 

A single microservice contains all the routing, middlewares, business logic, database access to implement **one feature** of our app

An app with four microservices. Each service is standalone. 
![[Pasted image 20240131161959.png]]

**Biggest challenge with microservices**
Data management between services 
How is data stored and accessed 
- each service has it's own database if required. 
- we will never access data from reaching from one microservice into the database of another microservice 
example![[Screenshot from 2024-01-31 16-25-52.png]]
Microservices use the 
Database-Per-Service Pattern
- Each service will run independently of other services
- database schema/structure might change unexpectedly
- some services might function more efficiently with different types of DB's (sql vs nosql)
#### Why each microservice has its own DB and is autonomous  
If we used one database for all our services and it crashed our services would go down.
If we ever needed to scale up our database we may need to adjust the schema to serve all the services of our app therefore more app downtimes.
If service A is designed to reach to service B's database and that database goes down then both services go down.

A single database shared between many services would be a single point of failure which would limit the reliability of the app.

SO microservices are designed to function autonomous so that one service does not take down an entire application it also helps organize an application to isolate bugs, and for more developers or teams organize work responsibilities.

