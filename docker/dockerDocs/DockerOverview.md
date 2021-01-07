# Docker Concepts and Interactions


- On Infrastructure Plumbing

    - To build a platform like Docker you need a lot of infrastructure plumbing; 
Infrastructure plumbing is made of small software tools which perform basic fundamental tasks in the most reliable and simple way possible. 

    - To build Docker we have re-used large quantities of plumbing: **Linux, Go, lxc, aufs, lvm, iptables, virtualbox, vxlan, mesos, etcd, consul, systemd…** the list goes on.
    - Docker has plumbing for interacting with both Linux and Windows native capabilities; it has plumbing for networking; service discovery; master election; security; and more.

- Infrastructure Plumbing Manifesto

How we create and reuse infrastructure plumbing is fundamental to the Docker project. Our approach boils down to 3 fundamental principles which we call “the Infrastructure Plumbing Manifesto”:


- Whenever possible, re-use existing plumbing and contribute improvements back.
    - When you need to create new plumbing, make it easy to re-use and contribute improvements back. This grows the common pool of available components, and everyone benefits.
    - Follow the unix principles: several simple components are better than a single, complicated one.
    - Define standard interfaces which can be used to combine many simple components into a more sophisticated system.

Docker is a platform to build, ship and rundistributed applications – meaning that it runs applications in :
- Distributed fashion across many machines
- Variety of hardware and OS configurations. 

- **portability:** it needs a sandboxing environment capable of abstracting the specifics of the underlying host. 

- **ubiquity:** without requiring a complete rewrite of the application.

- **scale:** without introducing excessive performance overhead.


# Docker Components

* Host: the machine that is running the containers.
* [Docker Image](dockerimages.md) a hierarchy of files, with meta-data for how to run a container.
* [Docker Container ](dockercontainers.md): a contained running process, started from an image.
* Docker Registry: a repository of images.
* Docker Volume: storage outside the container.
* [Dockerfile](sampledockerfile.md): a script for creating images.



