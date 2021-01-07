# Control groups 
1. Create a process 


        $ cat hello.sh
        #!/bin/sh

        while [ 1 ]; do
                echo "hello world"
                sleep 60
        done
2. Creating a cgroup name under the memory subsystem

        $ sudo mkdir /sys/fs/cgroup/memory/foo
        $ echo 50000000 | sudo tee /sys/fs/cgroup/memory/foo/memory.limit_in_bytes
        $ sudo cat memory.limit_in_bytes
        $ sh ~/test.sh &
        $ cat cgroup.procs
        $ echo 11213 > /sys/fs/cgroup/memory/foo/cgroup.procs
        $ ps -o cgroup 11213
