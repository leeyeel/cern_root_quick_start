ROOT的安装与运行
若要安装ROOT,可以直接去官网[root.cern.ch](https://root.cern.ch/downloading-root)查看，这里提供部分操作系统的安装教程。另外，我以前写过一个ROOT安装的教程，里面附带了常见的错误的解决方法，
可以[点此](https://www.douban.com/note/455214073/ "linux下安装CERN ROOT全过程")查看. 
以下是ROOT安装教程: 
首先，ROOT使用了很多软件包，你需要在安装ROOT之前就将所需的软件包安装成功：
Fedora 18, 19 and 20; Scientific Linux 5, 6; CentOS 6, 7系统使用如下命令.  
必需安装包：
```sh
$ sudo yum install git make gcc-c++ gcc binutils \ 
libX11-devel libXpm-devel libXft-devel libXext-devel 
``` 
可选安装包：  

```sh 
$ sudo yum install gcc-gfortran openssl-devel pcre-devel \
        mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel \
        mysql-devel fftw-devel cfitsio-devel graphviz-devel \
        avahi-compat-libdns_sd-devel libldap-dev python-devel \
        libxml2-devel gsl-static
        ``` 

Ubuntu 10, 11, 12 14 and 16系统使用如下命令.  
必须安装包：  

```sh
$ sudo apt-get install git dpkg-dev make g++ gcc binutils\
        libx11-dev libxpm-dev libxft-dev libxext-dev
        ``` 
可选安装包：  

```sh 
$ sudo apt-get install gfortran libssl-dev libpcre3-dev \
        xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
        libmysqlclient-dev libfftw3-dev cfitsio-dev \ 
        graphviz-dev libavahi-compat-libdnssd-dev \
            libldap2-dev python-dev libxml2-dev libkrb5-dev \
            libgsl0-dev libqt4-dev
            ```

然后，你需要在官网下载ROOT程序并解压，进入解压后的root文件夹依次运行如下命令：

```sh
$ ./configure -all
$ make -j4
```
-j4表示使用4个核心同时编译.安装时间视你计算机性能而定，几分钟到几小时不等。
出现成功安装的提示内容后，需要运行一下配置脚本，输入如下命令即可:
```sh
source /myROOTdir/bin/thisroot.sh
```
其中myROOTdir表示你root的根目录，比如我的root是在我家目录下编译的，则在终端输入:
```sh
source ~/root/bin/thisroot.sh
```
注意，上面这个命令只在当前终端有效，如果你打开多个终端，需要重新执行一遍此命令。一种解决方法是将其写入用户家目录下的.bashrc文件(或者系统配置文件),这样每次使用ROOT时就不需要每次都执行上面的source操作了。

## 启动ROOT

安装成功ROOT之后，你可以在终端使用如下命令打开ROOT：
```sh
$ root
```
若不希望每次启动都看到ROOT的启动画面，可以输入
```sh
$ root -l
```

