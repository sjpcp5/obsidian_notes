Manual development, Build by hand
cut by hand MVP infrastructure
a box running docker 

blue green strategy
merge into dev deployment
then have a branch tagged to be deployed to production
frontend docker
backend pip

make artifact in docker container images
a seperate repo to pull seperate versions of the builds or code

- make a new repo for the code (empty)
- navigate politics derek is having teeth drilled
- turn on sass (keys) should be no keys in this
- security injected through env variable public keys
	- manage it from a secret store
	- client secret
	- configuration file or overwritten in env variable
	- .home deck manages that on the command line
	- ports in docker are internal
	- docker will kill the container and restart itself 
	- expose the API seperately?
	- AWS API Gateway generate and rotate keys
	- makeshift 
	- best and breed project for 
	- when bringing technical solutions for devOps or deployment we don't want to code ourselves into a corner for infrastructure when we are scaling up
		- its okay its  infrastructure your suppose to be able to throw it away and build anew
	- Containers
		- run pthyon app in one
		- engine x
		- traffic reverse proxy route a di