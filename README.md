# Linux-Container-For-Android

本项目用于在Android上创建Linux容器，基于chroot方式。

## 条件
已安装`magisk`软件且已`root`的Android系统
仅适用于`x64/arm64`架构（新手机平板基本都是`arm64`架构）

## 使用方式
1. 在release页面中下载本项目的`release.zip`模块
2. 打开magisk并安装模块
3. 重启后即可运行

## 登陆方式
1. 开机自启时默认会运行`wolfsshd`，绑定`0.0.0.0:7022`, 可通过ssh连接，密码为`12345678`
2. 通过shell（以adb/termux等方式打开手机终端）方式进入`/data/linux-ubuntu`文件夹,敲`./enterpoint.sh`进入容器

## 异常处理
若登陆方式1、2均失败，请检查`/data`是否存在`linux-ubuntu`，再检查`/data/linux-ubuntu`是否存在`_chroot.pid`文件。若不存在，表明容器启动失败。可尝试重启手机，如果还是失败，也许该模块不支持您的系统。

## 注意
1. root初始密码薄弱易于泄漏，建议进入容器后修改root密码, 修改`/etc/wolfsshd/sshd_config`关闭密码登陆并开启证书登陆
2. 建议修改`/etc/wolfsshd/ssh_host_rsa_key`中的私钥
3. 容器内部的`/sdcard`已经映射好Android系统的`/sdcard`目录
4. 容器使用`se-boot`进行初始化
5. 对于容器内部缺少常用的命令，可使用容器内部已经编译好`busybox`或直接通过`apt`安装
6. 容器内部`/script`提供快速换源脚本[LinuxMirrors](https://github.com/SuperManito/LinuxMirrors)
7. 更多关于容器的信息请查询`https://github.com/hvhghv/chroot-container`


## 引用
[se-boot](https://github.com/hvhghv/se-boot)
[chroot-container](https://github.com/hvhghv/chroot-container)
[magisk-module-installer-translated-chinese-simplified](https://github.com/fenildf/magisk-module-installer-translated-chinese-simplified)