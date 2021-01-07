## Supported dokerfile Commands :

### BUILD Commands
* FROM – The image the new image will be based on.
* MAINTAINER – Name and email of the maintainer of this image.
* COPY – Copy a file or a directory into the image.
* ADD – Same as COPY, but handle URL:s and unpack tarballs automatically.
* RUN – Run a command inside the container, such as apt-get install.
* ONBUILD – Run commands when building an inherited Dockerfile.
* .dockerignore – Not a command, but it controls what files are added to the
* build context. Should include .git and other files not needed when building
* the image.

### RUN Commands
* CMD – Default command to run when running the container. Can be overridden
* with command line parameters.
* ENV – Set environment variable in the container.
* EXPOSE – Expose ports from the container. Must be explicitly exposed by the
* run command to the Host with -p or -P.
* VOLUME – Specify that a directory should be stored outside the union file
* system. If is not set with docker run -v it will be created in
* /var/lib/docker/volumes
* ENTRYPOINT – Specify a command that is not overridden by giving a new
* command with docker run image cmd. It is mostly used to give a default
* executable and use commands as parameters to it.
### Both BUILD and RUN Commands
* USER – Set the user for RUN, CMD and ENTRYPOINT.
* WORKDIR – Sets the working directory for RUN, CMD, ENTRYPOINT, ADD and COPY.





ls /var/lib/docker/overlay2/44ec9df71a44cb00ee9f4125209a13717e293cf5be773bf9caa10676dfc06726/diff/ls /var/lib/docker/overlay2/44ec9df71a44cb00ee9f4125209a13717e293cf5be773bf9caa10676dfc06726/diff/ls /var/lib/docker/overlay2/44ec9df71a44cb00ee9f4125209a13717e293cf5be773bf9caa10676dfc06726/diff/


### Sample dockerfile
    FROM debian:jessie
    RUN apt-get update && \
      apt-get install gcc -y


### To build the image from dockerfile 
    $ cd <path to dockefile>
    $ sudo docker build .
    $ sudo docker container ls -a