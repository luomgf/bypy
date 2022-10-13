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
