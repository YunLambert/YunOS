# YunOS
操作系统学习，自制一个实现基本功能的OS
## boot部分
1.下载Bochs虚拟机
2.bximage创建虚拟硬盘
3.nasm -o对汇编文件进行编译，生成.bin文件
4.将.bin文件通过dd if=  of= bs=512 count=1 conv=notrunc写入到创建的虚拟硬盘当中
5.在bochsrc.disk文件中加入虚拟硬盘的信息，然后通过bochs启动即可
