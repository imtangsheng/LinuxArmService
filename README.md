# 开发环境搭建

- ## 安装 VMware Tools

启动虚拟机 打开 VMware Workstation 或 VMware Player，选择需要配置的虚拟机并启动。

挂载 VMware Tools 安装包 点击菜单栏的 “虚拟机” > “安装 VMware Tools”。 如果未自动挂载，尝试重新安装或重启虚拟机。

解压并安装 在虚拟机中打开挂载的光盘，复制 .tar.gz 文件到主目录。 解压文件： tar -xzvf VMwareTools-*.tar.gz 进入解压后的目录并运行安装脚本： cd vmware-tools-distrib sudo ./vmware-install.pl 按提示完成安装，默认选项直接回车即可。

- ## [主机与VMware虚拟机共享文件夹](https://zhuanlan.zhihu.com/p/650638983)

1. 在虚拟机设置中:打开 “设置 -> 选项 -> 共享文件夹”

2. 挂载操作,具体命令如下：
```
$ sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```
/mnt/hgfs/ 是挂载点，我们也可以修改为其它挂载点
-o allow_other 表示普通用户也能访问共享目录。

3. 再次进入 /mnt/hgfs 查看 ,此时可看到共享的本地文件
4. 附开机自动挂载：追加到/etc/fstab即可
```
echo '.host:/ /mnt/hgfs fuse.vmhgfs-fuse allow_other,defaults 0 0' >> /etc/fstab
```

- ## Qt Creator 开发
    - 设备添加通用的Linux设备
    - Kit 选择对应的配置,设备,gcc等路径
    - CMake ,部署,构建(tmp路径,其他路径失败)

- ## 使用 x86_64 版本的 GDB 来调试 ARM64/aarch64 架构的 (待验证)
安装交叉编译 GDB（推荐 工具 → 选项 → 调试器 → GDB
```
# Ubuntu/Debian 系统
sudo apt-get update
sudo apt-get install gdb-multiarch

# 或者安装特定架构的 GDB
sudo apt-get install gdb-aarch64-linux-gnu

为什么需要交叉编译 GDB？
x86_64 GDB：只能调试 x86_64 架构的程序

gdb-multiarch：支持多种架构（x86, ARM, MIPS, RISC-V 等）

aarch64-linux-gnu-gdb：专门用于 ARM64 架构
```

- ## [ROS2安装](https://docs.ros.org/en/rolling/Installation/Windows-Install-Binary.html)
**执行才可以使用ros2的指令**

    call C:\pixi_ws\ros2-windows\local_setup.bat 
