# runC: a lightweight universal container runtime

Collection of features which make this kind of abstraction possible. 
Those individual features have esoteric names like "**control groups”, “namespaces”, “seccomp”, “capabilities”, “apparmor**" and so on. But collectively, they are known as “OS containers” or sometimes “lightweight virtualization”.

Containers are actually an array of complicated, sometimes arcane system features, we have integrated them into a unified low-level component which we simply call **runC.** And It is spinning out runC as a standalone tool, to be used as plumbing by infrastructure plumbers everywhere.

**runC** is a lightweight, portable container runtime. It includes all of the plumbing code used by Docker to interact with system features related to containers. 

## runC principles:

- Designed for security.

- Usable at large scale, in production, today.

- No dependency on the rest of the Docker platform: just the container runtime and nothing else.

# Features:

- Full support for Linux namespaces, including user namespaces
- **If Linux can do it, runC can do it:** Native support for all security features available in Linux: Selinux, Apparmor, seccomp, control groups, capability drop, pivot_root, uid/gid dropping etc. .
- **it’s a real standard:**  A formally specified configuration format, governed by the Open Container Project  under the auspices ofthe Linux Foundation.

**The goal of runC is to make standard containers available everywhere**

## references:
https://www.docker.com/blog/runc/ 

https://github.com/opencontainers/runc

https://github.com/cri-o/cri-o