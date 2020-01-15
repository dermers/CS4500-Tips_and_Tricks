# Docker Compose

### What's that?

[Docker Compose](https://docs.docker.com/compose/) is a tool for managing your Docker containers.

Instead of running long, somewhat complicated Docker commands, like:

```bash
docker run -ti -v `pwd`:/test w2-gtest:0.1 make
```

Docker Compose enables you to accomplish the same task with shorter and easier syntax:

```bash
docker-compose run dev docker
```

### Getting Started

You'll need to [install Docker Compose for your system](https://docs.docker.com/compose/install/).

Once you've done that, you should create a `docker-compose.yml` file at the root of your project.

You should also create a `Dockerfile` there based on the
[course Dockerfile](https://piazza.com/class/k51bluky59n2jr?cid=130). For the sake of simplicity
when following these instructions, it may be helpful to add the following after the first line:

```Dockerfile
WORKDIR /test
```

For our specific purposes, your project folder should be whatever folder you're writing your homework in.
This file will be reusable across assignments.

In `docker-compose.yaml`, let's define a simple
[service](https://docs.docker.com/compose/gettingstarted/#step-3-define-services-in-a-compose-file)
called `dev`, which will use our Docker image for the course, `w2-gtest:0.1`:

```YAML
version: "3.7"
services:
  dev:
    image: w2-gtest:0.1
    build:
      context: ./
```

This creates a service named `dev` that uses `w2-gtest:0.1`. But what's this about a `build context`?

This provides the directory to use for building the Docker image. If you place both the `docker-compose.yaml`
and the `Dockerfile` at the root of your project directory, the `./` here will evaluate to that directory.

We can use the definition of `dev` in the `docker-compose.yaml` file to build the Docker image itself from any
subdirectory within your project using the following command:

```bash
docker-compose build dev
```

There are some other things we're going to be using whenever we run commands within our Docker container;
let's add them to our service definition.

```YAML
version: "3.7"
services:
  dev:
    image: w2-gtest:0.1
    build:
      context: ./
    volumes:
      - "${LOCAL_DIR}:/test"
    entrypoint: make
```

With these last three lines we've done two things. First, we've defined a mount point for our container,
which will use the value of the shell variable `LOCAL_DIR` to create a volume on our host system that's
shared with the container.

For example, on a MacOS or Linux system, you can run:

```bash
export LOCAL_DIR=`pwd`
```

From within your folder for Warmup 2, and any command you run with `docker-compose` in the current
shell session will mount that folder within the container at `/test`.

Second, we've created an entrypoint for the container; this is a value that
will be added to the beginning of any command we run using `docker-compose`.

Our command from earlier:

```bash
docker-compose run dev docker
```

Is equivalent to this with our new `entrypoint` definition:

```bash
docker-compose run dev make docker
```

And voila! With this as a starting point, you should be well on your way to managing
your Docker containers with Docker Compose.
