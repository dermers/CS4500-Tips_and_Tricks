Docker
======
The following instructions can be used with the given [Dockerfile](./Dockerfile "Dockerfile")

### In order to build a docker image:
`docker build -t <desired image name> .`

eg `docker built -t soft-dev .`

### In order to run a docker image:
`docker run -it -v <full path to local soft-dev directory>:<desired path on container> <desired image name>`

eg `docker run -it -v (pwd):/soft-dev soft-dev`

### Add this to your Makefile:
```
docker:
	docker run -ti -v `pwd`:/soft-dev soft-dev bash -c "cd soft-dev; g++ -std=c++11 -Wall main.cpp"
```

eg

```
docker:
	docker run -ti -v `pwd`:/soft-dev soft-dev bash -c "cd soft-dev; g++ -std=c++11 -Wall main.cpp"
```
