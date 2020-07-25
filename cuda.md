# cuda

01 前期工作
1.1 禁用nouveau

ubuntu 16.04默认安装了第三方开源的驱动程序nouveau，安装nvidia显卡驱动首先需要禁用nouveau，不然会碰到冲突的问题，导致无法安装nvidia显卡驱动。指令如下

sudo gedit /etc/modprobe.d/blacklist.conf  打开文件，在最后添加如下两行：

blacklist nouveau

options nouveau modeset=0

1.2 更新系统修改

sudo update-initramfs -u      ，输入指令后重启系统（一定要重启），确保到位。

1.3 验证nouveau是否已禁用

lsmod | grep nouveau

02 下载驱动文件并指令安装
 2.1 、在英伟达的官网上查找你自己电脑的显卡型号然后下载相应的驱动： https://www.geforce.cn/drivers，  下载后的run文件拷贝至home目录下，   文件为：NVIDIA-Linux-x86_64-xxx.run

2.2 、 在ubuntu下按ctrl+alt+f1进入命令行界面，此时需要login：电脑账户名称，password：密码，登录到命令行界面。 有时会出现登录失败，报错incorrect login ，此时可以按下ctrl+alt+F2(F4)等进入，重新login,即可。

2.3、   sudo service lightdm stop      //这个是关闭图形界面，必须关闭

2.4、 sudo apt-get remove nvidia-*    //卸载系统中存在的驱动，默认有安装的，一定要执行这个

2.5 sudo /usr/bin/nvidia-uninstall

---
# cannot find -lCUDA_cublas_device
安装更新的cmake即可
