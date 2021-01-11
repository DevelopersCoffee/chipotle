# Creating a chroot Environment

    chr=/home/chauhanuday/chrootexample

    mkdir -p $chr

create directories to hold the portions of the operating system our chroot environment will require including the touch, rm, and ls commands. 
That will allow us to use all Bash’s built-in commands and touch, rm, and ls. 

List the directories you need to create within the {} brace expansion.

    mkdir -p $chr/{bin,lib,lib64}

    cd $chr



Copy the binaries that we need in our minimalist Linux environment from your regular “/bin” directory into our chroot “/bin” directory.

    cp -v /bin/{bash,touch,ls,rm} $chr/bin

These binaries will have dependencies. We need to discover what they are and copy those files into our environment as well, otherwise bash, touch, rm, and ls will not be able to function. The __ldd__ command will list the dependencies for us.


    ldd /bin/bash



    list="$(ldd /bin/bash | egrep -o '/lib.*\.[0-9]')"

__ldd:__ to list the dependencies 

__egrep:__ is the same as using grep with the -E (extended regular expressions) option. 

__-o:__ (only matching) option restricts the output to the matching parts of lines. 


    echo $list

## For touch command: 

    for i in $list; do cp -v --parents "$i" "${chr}"; done

    list="$(ldd /bin/touch | egrep -o '/lib.*\.[0-9]')"

## For ls command:

    for i in $list; do cp -v --parents "$i" "${chr}"; done

    list="$(ldd /bin/ls | egrep -o '/lib.*\.[0-9]')"

##  For rm command:


    list="$(ldd /bin/rm | egrep -o '/lib.*\.[0-9]')"

    for i in $list; do cp -v --parents "$i" "${chr}"; done

## Dependencies are copied into our chroot environment
    # sudo chroot $chr /bin/bash

    # ls	

    # ls /home/chauhanuday/Desktop

    # touch sample_file.txt

    # ls

    # rm sample_file.txt

    # ls

    # help

    # exit

    # rm -r chrootexample/

__.so__ files are dynamic libraries. The suffix stands for "shared object", because all the applications that are linked with the library use the same file, rather than making a copy in the resulting executable.


## jail 
    cd /tmp
    wget https://olivier.sessink.nl/jailkit/jailkit-2.21.tar.gz
    tar -zxvf jailkit-2.21.tar.gz
    cd jailkit-2.21/
    ./configure
    make
    su -
    make install

uday:x:1002:1002:uday chauhan,305,0987654321,1234567890:/jail/./home/uday:/usr/sbin/jk_chrootsh