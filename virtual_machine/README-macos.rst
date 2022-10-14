Create a VM using https://github.com/foxlet/macOS-Simple-KVM (for Catalina)

通过开源项目macOS-Simple-KVM完成创建一个macos的Catalina虚拟机系统。

With a SystemDisk::

创建一个系统硬盘

    qemu-img create -f qcow2 SystemDisk.qcow2 240G

Install the OS:

安装系统

* Create a single HFS+ (dont know if APFS works well) partition to install to

创建一个HFS+格式的文件系统分区用于安装系统(APFS格式不知道是否可用)


* Create a user account named: ``kovid`` during OS installation
安装系统时候创建一个``kovid``名字的账户。


After the OS is installed:

安装完成系统以后：

* Change the two network related lines in the launch script, which use an obsolete
  syntax to::

修改两个网络相关的启动脚本的命令后，使用一个过时的语法。

    -nic user,model=e1000-82545em,mac=52:54:00:0e:0d:20,hostfwd=tcp:0.0.0.0:0-:22

* Change the number of CPUS and RAM to::

修改CPU和内存数量

    -smp 4,cores=2
    -m 8G

* enable automatic login for the ``kovid`` user in Preferences->Users->Login
  options

设置``kovid`` 账户可以自动登陆：系统偏好设置->用户和组->登陆选项

* turn on SSH, install vimrc and zshrc and ssh authorized_keys.

打开SSH，安装vimrc、zshrc、ssh authorized_keys

* Edit /etc/ssh/sshd_config and set the following to allow only key based login,
  UsePAM yes is needed to use ``screen``::

编辑/etc/ssh/sshd_config 并且设置如下选项。

    PermitUserEnvironment yes
    PasswordAuthentication no
    ChallengeResponseAuthentication no
    UsePAM yes

* Create the file ~/.ssh/environment::

创建如下环境变量

    PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

* Copy over kitty terminfo using ssh kitten

覆盖kitty终端，使用ssh kitten

* Turn off sleep, screensaver, auto-updates.
关闭休眠、屏幕保护程序、自动更新。

* Mount the EFI partition that contains
the clover bootloader, look for config.plist and change DracoHD
to LastBootedVolume. You can also decrease the timeout if you prefer::

挂载EFI分区，其包含：bootloader

    sudo mkdir /Volumes/efi
    sudo mount -t msdos /dev/disk0s1 /Volumes/efi
    sudo vim `find /Volumes/efi -iname config.plist`

* Install Xcode from https://developer.apple.com/download/more/
Download the version of Xcode (at least 12.4) you need as a .xip archive. Run::
安装Xcode(版本大于12.4)

    open Xcode*.xip
    mv Xco*.app /Applications
    sudo xcodebuild -license

* Install an up-to-date rsync::
安装更新rsync到最新版

    curl -L https://github.com/kovidgoyal/bypy/raw/master/virtual_machine/install_rsync_on_macos.sh | /bin/zsh /dev/stdin
