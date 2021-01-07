# docker images

![dockerfilecommands](img/docker-image.png)

An image is a file structure, with meta-data for how to run a container. The image is built on a union filesystem, a filesystem built out of layers. Every command in the Dockerfile creates a new layer in the filesystem.
When a container is started all images are merged together into what appears to the process as unified. When files are removed in the union file system they are only marked as deleted. The files will still exist in the layer where they were last present.


- It is used for creating our own docker image
- It is a text file contains a list of instructions how to build a docker image.
- It is written in layered format. Each instruction is converted into overlay filesysytem in the backend.
- Overlayfs driver will build the unified view

## Interesting Image Inspect Results
* ID This is the unique identifier of the image.
* Parent A link to the identifier of the parent image. It is very common for an image to have a defined parent.
* Container A container identifier is interesting because this is meta-data for an image not a container. This container identifier is a temporary container created when the image was built. Docker will create a container during the image construction process, and this identifier is stored in the image data.
* ContainerConfig This data again is referring to the temporary container created when the Docker build command was executed.
* DockerVersion The version of Docker used to create the image is stored in this value. It could be very useful as the Docker ecosystem continues to advance.
* Virtual Size The size of the image reported in bytes.


        FROM centos:7    
        RUN mkdir /test1 && echo “Hello” > /test1/file.txt


## Commands for interacting with images

    # docker images  # shows all images.
    # docker import  # creates an image from a tarball.
    # docker build   # creates image from Dockerfile.
    # docker commit  # creates image from a container.
    # docker rmi     # removes an image.
    # docker history # list changes of an image.



## Repository path
    cat /var/lib/docker/image/overlay2/repositories.json
