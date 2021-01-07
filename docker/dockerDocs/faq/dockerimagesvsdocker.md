# Docker imges vs containers

- Both elements are closely related and are part of a system defined by the Docker platform.

- Images can exist **without** containers, whereas a **container needs to run an image to exist**. Therefore, containers are dependent on images and use them to construct a run-time environment and run an application.

- The two concepts exist as essential components (or rather phases) in the process of running a Docker container. Having a running container is the final “phase” of that process, indicating it is dependent on previous steps and components. That is why docker images essentially govern and shape containers.