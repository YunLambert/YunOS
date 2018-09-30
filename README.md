# YunOS
操作系统学习，自制一个实现基本功能的OS

## boot部分
1.下载Bochs虚拟机  
2.bximage创建虚拟硬盘  
3.nasm -o对汇编文件进行编译，生成.bin文件  
4.将.bin文件通过dd if=  of= bs=512 count=1 conv=notrunc写入到创建的虚拟硬盘当中  
5.在bochsrc.disk文件中加入虚拟硬盘的信息，然后通过bochs启动即可  

## MAKEFILE
为了方便编译，集中写在了makefile里面了，下面介绍一下我工作环境的项目目录结构：
```
/home/yun/YunOS/YunOS/src:boot   command  fs       kernel  makefile  thread
build  device   helpdoc  lib     shell     userprog

/usr/local/bin:hd80M.img yunos.img

/usr/local/share/bochs:bochsrc.disk
```
文件放的有些松散，不过需要注意的只有`/usr/local/bin/`,因为我的makefile指定的都是将编译好的文件写入此文件夹下的两个.img文件中，bochsrc.disk中设置的启动盘的目录也是这个，大家下载的时候记得将这两个变化点更改为自己相应的目录。

## 如何使用
`git clone本项目`  
确保自己的电脑（linux）已经安装了bochs虚拟机  
如果不想自己编译的话，只需将bochsrc.disk文件中的启动盘目录更改为存放有两个.img文件的位置即可
如果想自己编译的话，需要更改makefile中的编译地址，同样式存放有两个.img文件的位置
项目中yunos.img是启动引导盘+系统盘，hd80M.img为文件系统盘，其中有主逻辑分区与扩展逻辑分区，当时分的时候并没有注意，但能用就好。

## 关于项目
这个项目还会持续更新，由于当前的OS有些笨重而且实现方式都是为了理解的，所以舍去了一些很好或者说更优的实现方式，日后会重新从零开始实现一个OS，并会在自己的博客中同步更新相应的进度

2018.10.1
