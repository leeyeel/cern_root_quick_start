##ROOT的安装与运行
&emsp;若要安装ROOT,可以直接去官网[root.cern.ch](https://root.cern.ch/downloading-root)查看，这里提供部分操作系统的安装教程。另外，我以前写过一个ROOT安装的教程，里面附带了常见的错误的解决方法，
可以[点此](https://www.douban.com/note/455214073/ "linux下安装CERN ROOT全过程")查看. 
以下是ROOT安装教程: 
&emsp;在安装ROOT之前，先安装ROOT的依赖包.    
&emsp;Fedora 18, 19 and 20; Scientific Linux 5, 6; CentOS 6, 7系统使用如下命令.  
&emsp;必需安装包：
```sh
$ sudo yum install git make gcc-c++ gcc binutils \ 
libX11-devel libXpm-devel libXft-devel libXext-devel 
``` 
&emsp;可选安装包：  

```sh 
$ sudo yum install gcc-gfortran openssl-devel pcre-devel \
        mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel \
        mysql-devel fftw-devel cfitsio-devel graphviz-devel \
        avahi-compat-libdns_sd-devel libldap-dev python-devel \
        libxml2-devel gsl-static
        ``` 

&emsp;Ubuntu 10, 11, 12 14 and 16系统使用如下命令.  
&emsp;必须安装包：  

```sh
$ sudo apt-get install git dpkg-dev make g++ gcc binutils\
        libx11-dev libxpm-dev libxft-dev libxext-dev
        ``` 
&emsp;可选安装包：  

```sh 
$ sudo apt-get install gfortran libssl-dev libpcre3-dev \
        xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
        libmysqlclient-dev libfftw3-dev cfitsio-dev \ 
        graphviz-dev libavahi-compat-libdnssd-dev \
            libldap2-dev python-dev libxml2-dev libkrb5-dev \
            libgsl0-dev libqt4-dev
            ```

&emsp;然后，你需要在官网下载ROOT程序并解压，进入解压后的root文件夹依次运行如下命令：

```sh
$ ./configure -all
$ make -j4
```
&emsp;上面的-j4表示使用4个核心同时编译.安装时间视你计算机性能而定，几分钟到几小时不等。
出现成功安装的提示内容后，需要运行一下配置脚本，输入如下命令即可:
```sh
source /myROOTdir/bin/thisroot.sh
```
&emsp;其中myROOTdir表示你root的根目录，比如我的root是在我家目录下编译的，则在终端输入:
```sh
source ~/root/bin/thisroot.sh
```
&emsp;注意，上面这个命令只在当前终端有效，如果你打开多个终端，需要重新执行一遍此命令。一种解决方法是将其写入用户家目录下的.bashrc文件(或者系统配置文件),这样每次使用ROOT时就不需要每次都执行上面的source操作了。

## 启动ROOT

&emsp;安装成功ROOT之后，你可以在终端使用如下命令打开ROOT：
```sh
$ root
```
&emsp;若不希望每次启动都看到ROOT的启动画面，可以输入
```sh
$ root -l
```
##其他问题
&emsp;启动ROOT时,有些Linux发行版可能会出现包含xfonts XFree86 xorg 100dpi等关键字的相关错误提示。这是因为系统没有相关字体导致.  
对于Scientific Linux等系统.  
```sh
yum search xorg-x11 | grep -E "100dpi|75dpi" |sudo yum install -y
```
对于Ubuntu等系统  
```sh
apt-cache search xfonts|grep -E "100dpi|75dpi"|sudo apt-get install -y
```
&emsp;一般即可修复。思路就是查找相关字体然后安装.下面一节我们正式开始ROOT的学习.

