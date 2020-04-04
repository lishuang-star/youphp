
**在Virtualbox下对Ubuntu18.04虚拟机进行根目录扩容**

### 一、virtualbox操作

- 首先**关闭**需要扩容的虚拟机，复制一个新的虚拟机，对新虚拟机进行操作。（这是我怕操作失误进行的一次备份）

- 设置-存储，发现虚拟硬盘是**动态分配存储**，确定存储硬盘的位置，对硬盘进行**备份**，然后将挂载的硬盘**移除**。
`C:\Users\dell\VirtualBox VMs\ubuntu18.04-1\ubuntu18.04-1.vdi`

  ![](pic\设置.png)

- 确定virtualbox的安装位置，在安装位置打开**cmd**窗口。

- 在cmd窗口中运行命令进行扩容
 **`vboxmanage modifyhd /location-of-your-virtual-disk --resize size-in-MB`**
比如：`vboxmanage modifyhd /C:\Users\dell\VirtualBox VMs\ubuntu18.04-1\ubuntu18.04-1.vdi --resize 81920`
将我的虚拟硬盘扩容至80G。
  ![](pic\进度条.png)

- 扩容命令结束之后，选择设置-存储，在刚刚的界面内，将扩容后的硬盘挂载回去。此时还不能使用新增的空间，需要使用**GParted**分区工具进行操作。

### 二、使用GParted分区工具

- 对挂载扩容后硬盘的机器重启。安装并启动分区工具。
   ```
   sudo apt-get install gparted
   sudo gparted
   ```

- 参考[对于分区软件的使用](https://blog.csdn.net/LEON1741/article/details/56494797)中，使用分区工具部分以及重启，可以实现扩容。

- 即可完成在virtualbox上对虚拟机的扩容。

 [操作参考](https://www.cnblogs.com/xueweihan/p/5923937.html)