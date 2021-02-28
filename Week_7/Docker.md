# Docker
A tool for running applications in an isolated environment
#### Benefits:
- same environement >> always acts the same
- get around os or dependancy differences
#### Containers:
- not a virtual machine, but a container
- virtual mahcines are resource heavy, since they each get an os and kernal and divide the mahcine resources
- containers share the same kernal as host machine so it is lighter
#### Workflow:
- create a docker file to build an image
    - or pull an image from the clod
    - use a virtual environment for requirments if making the image form scratch
- run a containter using the image
    - develop on the docker container and share

<img src='https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/11/1.png'>

---
### Basic docker commands

| command                            | output                                      |
|------------------------------------|---------------------------------------------|
| docker version                     | version of docker                           |
| docker pull image_name             | pull image from docker cloud                |
| docker run --name <name> image     | run a container with image and given <name> |
| docker ps                          | running containers                          |
| docker ps -a                       | all containers                              |
| docker images                      | available images                            |
| docker run image                   | run a container of image                    |
| docker stop container (id \| name) | stop running container                      |
| docker rm container id             | remove the container                        |
| docker rmi image_name              | remove image                                |