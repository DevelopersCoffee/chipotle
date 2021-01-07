# Docker containers

    $ docker container ーhelp
    $ docker container run -it  testimage_1 bash
    $ docker container run -it  testimage_1 bash

diffs re empty as we have not saved anything inside a container.

**-init** : are trailing ids directories this are nothing but container specify readonly layers created to initialise some mandatory files and directories for each container like hostfile , hostname,etc 
till the time we launch the containers there layers are nothing but individual directories stored on native Linux fs
Only at the time of launching the containers the overlay drivers kicks in to create a unified merged view of there layers to be mounted inside the containers 

**/merged** directory contains merged view of all its underlying layers