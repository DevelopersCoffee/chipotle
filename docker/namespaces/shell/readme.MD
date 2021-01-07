The UTS namespace is used to isolate two specific elements of the system that relate to the uname system call. The UTS(UNIX Time Sharing) namespace is named after the data structure used to store information returned by the uname system call.


```$ sudo su                   # become root user
$ hostname                  # check current hostname
chauhanuday-Vbox 
$ unshare -u --fork --pid --mount-proc /bin/sh # create a shell in new UTS namespace
$ pidof /bin/sh
$ pidof /bin/sh  # on host machine
$ hostname my-new-hostname  # set hostname
$ hostname                  # confirm new hostname
$ exit                      # exit new UTS namespace
$ hostname                  # confirm original hostname unchanged
dev-ubuntu
```



7 namespaces to rule them all

The above example demonstrates the UTS namespace, but the fun doesn’t end there. At the time of writing there are 7 namespaces available:

    - Mount - isolate filesystem mount points
    - UTS - isolate hostname and domainname
    - IPC - isolate interprocess communication (IPC) resources
    - PID - isolate the PID number space
    - Network - isolate network interfaces
    - User - isolate UID/GID number spaces
    - Cgroup - isolate cgroup root directory