Creating QEMU Virtual machines for building

创建QEMU虚拟机完成编译

==============================================

See the README-macos.rst and README-windows.rst files for initial instructions
for creating the macOS and Windows Virtual machines.

macos和windows虚拟机的创建初始化说明查看相应的 /bypy/virtual_machine/README-macos.rst 和 /bypy/virtual_machine/README-windows.rst
文件描述。

Once you have these working, you just need to put them in a form bypy will
recognize. To do so create the directories
(inside the root directory of the project you want to build)::

一旦完成上述创建工作，你就可以把他们放入calibre和kitty的bypy目录当中，程序会自动识别。在calibre和kitty项目的
根目录下面创建如下对应目录
（放置到你的项目的根目录当中用于编译）

    bypy/b/windows/vm

    bypy/b/macos/vm

Put the qcow2 and other files needed for each VM in its respective
directory.

将qcow2映像文件和其他VM所需要的文件一起放入对应的目录。


Then create a machine-spec file in each directory that
contains the qemu command line used to launch the VM. For instance,
for Windows, one would have::

在各自相应的目录创建一个虚拟机文件，里面存放qemu启动虚拟机的命令。一个例子，比如对于windows平台
你应该包含。



    # Number of processors
    -smp cores=2,threads=4
    # RAM
    -m 8G

    -cpu host,hv_relaxed,hv_spinlocks=0x1fff,hv_vapic,hv_time
    -drive file=SystemDisk.qcow2,index=0,media=disk,if=virtio
    -nic user,model=virtio-net-pci,hostfwd=tcp:0.0.0.0:0-:22
    -rtc base=localtime,clock=host
    -usb -device usb-tablet


You can run the VM by running the following command in the project root
directory::

在项目的根目录可以运行如下的命令启动虚拟机。

    python ../bypy windows shell
    python ../bypy macos shell

And shut it down with::

并且运行如下命令会关闭虚拟机。

    python ../bypy windows shutdown
    python ../bypy macos shutdown
