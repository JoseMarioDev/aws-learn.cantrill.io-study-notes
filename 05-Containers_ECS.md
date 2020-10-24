### Introduction to Containers and Demo

#

- virtualization runs multiple OSs on same hardware
- causes the problem of using same resource over and over. in pic, the Guest OS is the same on each VM
- why do we need multiple copies then?

  ![Alt text](img/virtualization.png 'problem of virtualization')

- solution is to use containers (ex: Docker)

  - container runs as a process within OS, only need one installation of OS

  ![Alt text](img/containerization.png 'difference with container')

- container is a running copy of a docker image

  - made up of multiple layers
  - stacks of layers
  - docker file creates image
  - file has lines that creates layers of image

    ![Alt text](img/dockerimage.png 'layers of docker image')

- images are used for creating docker containers
  - container has read/write layers
  - allows containers to run
  - images can create multiple containers
  - only difference between containers is the read/write layer
- containers registry are hubs of container images
  - can be private/public
  - download/upload images
- key concepts

  ![Alt text](img/containerkeyconcepts.png 'layers of docker image')

### ECS - Concepts

#

testing

### ECS - Cluster Mode and Demo

#

testing
