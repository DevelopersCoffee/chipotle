# overlay filesystems

## What’s an overlay filesystems

Overlay filesystems (also called union filesystems) allow creating a union of two or more directories: a list of lower directories and an upper directory. The lower directories of the filesystem are read only, whereas the upper directory can be used for both reads and writes.

## Overlay filesystems example:

## Create a directory as :
- mount : which will contain the union of all the other directory. 
- layer-1, layer-2, layer-3, layer-4 bunch of folders. 
- workdir : which is needed by the overlay filesystem

        # cd /tmp && mkdir overlay-example && cd overlay-example
        # mkdir mount layer-1 layer-2 layer-3 layer-4 workdir
        # ls

## Create some files into layer-1, layer-2 layer-3.
layer-4 (our upper folder) =  empty.

    # echo "Layer-1 file" > ./layer-1/some-file-in-layer-1
    # echo "Layer-2 file" > ./layer-2/some-file-in-layer-2
    # echo "Layer-3 file" > ./layer-3/some-file-in-layer-3

## mount the filesystem:

    # mount -t overlay overlay-example \
    -o lowerdir=/tmp/overlay-example/layer-1:/tmp/overlay-example/layer-2:/tmp/overlay-example/layer-3,upperdir=/tmp/overlay-example/layer-4,workdir=/tmp/overlay-example/workdir \
    /tmp/overlay-example/mount

## Inside the mount folder:

As expected the content of the folders layer-1, layer-2 and layer-3 have been mounted/combined in the mount folder.
Sure enough if we look at the content of the files, we’ll find what we have written in the previous step.
    
    # cat mount/some-file-in-layer-3
    Layer-3 file


## Creating a file in the mount folder:

    # cd /tmp/overlay-example/mount
    # echo "new content" > new-file
    # ls

## In the upper layer, which in our case is the folder called “layer-4”:

    # cd /tmp/overlay-example
    # tree

## Delete a file:

    # cd /tmp/overlay-example/mount
    # rm some-file-in-layer-2 
    # ls

## Original file in the “layer-2”:

    # cd /tmp/overlay-example
    # tree 


A new file called “some-file-in-layer-2” was created in “the layer-4”. The weird thing is that the file is a character file. These kinds of files are called “**whiteout**” files and are how the overlay filesystem represents a file being deleted:

    # cd /tmp/overlay-example/layer-4
    # ls -la

unmount the filesystem and remove the folder we created: 

    #  umount /tmp/overlay-example/mount && rm -rf /tmp/overlay-example

# Overall overlay filesystems:

The overlay filesystem allows to create a union of directories. 

-  the union was created in the “mount” folder and it was the result of combining the “layer-{1, 2, 3, 4}” folders. 
- Changes to files, deletion or creation will be stored in the **upper dir**, which in our case is “layer-4”. This is why this layer is also called “diff” layer.

- Files from upper layer shadow the ones in lower layers, i.e. if you have a file with the same name and relative path in layer-1 and layer-2, the layer-2 file is going to end up in the “mount” folder.

