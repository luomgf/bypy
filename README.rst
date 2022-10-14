bypy
========

Code to build the binaries for `calibre <https://calibre-ebook.com>`_ and
`kitty <https://sw.kovidgoyal.net/kitty>`_ with all their dependencies on
Linux, macOS and Windows.

为了完成`calibre <https://calibre-ebook.com>`_ 和
`kitty <https://sw.kovidgoyal.net/kitty>`的二进制安装程序，该项目代码完成所有他们的第三方依赖的安装
主要包括Linux, macOS and Windows三个平台.

Designed to run on Linux, building macOS and Windows binaries inside QEMU+KVM
based Virtual machines that run on a configurable build server.

设计实现均是在linux平台，对于macos和windows的二进制编译则是在QEMU+KVM的虚拟机中运行配置文件夹完成编译


在bypy的工程目录下面执行： python ../bypy   -h命令，可以获得该工程的使用方法帮助。


[root@localhost bypy]#  python ../bypy   -h
usage: bypy [-h] {vm,linux,macos,windows,win,export,worker-status,program,dependencies,deps,shell} ...

positional arguments:
  {vm,linux,macos,windows,win,export,worker-status,program,dependencies,deps,shell}
    vm                  Control the build Virtual Machines
    linux               Build in a Linux VM
    macos               Build in a macOS VM
    windows (win)       Build in a Windows VM
    export              Export built deps to a CI server
    worker-status       Check the status of the bypy dependency build worker
    program             Build the program
    dependencies (deps)
                        Build the dependencies
    shell               Run a shell with a completely initialized environment

options:
  -h, --help            show this help message and exit
[root@localhost bypy]#





