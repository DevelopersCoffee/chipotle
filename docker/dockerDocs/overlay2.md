## Overlay2

OverlayFS layers two directories on a single Linux host and presents them as a single directory. 

These directories are called **layers** and the unification process is referred to as a union mount. 

OverlayFS refers to the lower directory as **lowerdir** and the upper directory a **upperdir**. 

The unified view is exposed through its own directory called **merged**