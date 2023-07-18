# Long AppMotor

优化启动LongOS应用程序的速度。

## 依赖包

Debian/Ubuntu 依赖包:

```shell
sudo apt install cmake qtbase5-dev qtdeclarative5-dev qtquickcontrols2-5-dev libsystemd-dev libcap-dev libdbus-1-dev
```

## 构建

```shell
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr ..
make
sudo make install
```

##引言

Applaunchard是一个守护程序，通过以下方式帮助更快地启动应用程序
预加载动态链接的库和缓存内容。
它还节省了内存，因为所有启动的应用程序都共享某些资源。
Applaunchard还支持快速单实例启动。
下面将解释一些技术细节。
为基于Doxygen的用户文档安装platenchunder文档。
有关如何构建压平器和文档，请参阅INSTALL。
Booster守护程序（使用提供的库编写）作为
用户会话。助推器负责分叉将要应用的应用程序
在知道下一个要启动哪个应用程序之前。可能有
针对不同类型的
例如Qt或QML。
在当前架构中，助推器被实现为单独的过程，
使用提供的支持库。每个助推器进程等待发射
命令。
用户总是通过特殊的调用程序使用启动器。这个
invoker（/usr/bin/invoker）告诉booster进程加载应用程序
二进制文件。
通过鼓掌器启动的应用程序应编译为
共享库或位置无关的可执行文件（-pie）
始终导出main（）。还有一个适用于所有应用程序的“助推器”。
在这种情况下，将使用exec（）。

## License

GPL-2.1.
