# Node
#Node
Node is ideal for I/0 intensive apps 
Like building applications that require alot of disk or network access
because you serve the amount of clients without the need to throw in more hardware. Which means Node applicaions are highly scalable.

Node should not be used apps requiring CPU access or CPU intensive applications like video encoding or an image manipulation service. These kind of applications have alot of calculations that should be done by the CPU or GPU and few operations that touch the file system or the network.

Since Node applications are single threaded when performing the calculations ti serve one client other clients have to wait and that's why Node should not be used or for CPU instensive applications. It should only be used for building data intensive and real-time applications