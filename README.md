# qntfs-driver
**来源**	[lintel](https://www.right.com.cn/forum/forum.php?mod=viewthread&tid=432734&ordertype=1 "悬停显示")


## 使用方法:
1. 下载解压,把qntfs-driver放到package/lean目录下。

2. make menuconfig选择Kernel modules  --->Filesystems  --->
<*> kmod-fs-qntfs........................... PandoraBox Quick-NTFS filesystem

3. 挂载ntfs分区.
参考:mount -t qntfs /dev/sda1 /mnt/sda1

4. 关于性能
读取比ntfs商业驱动不相上下，iops比商业版驱动稍强，大文件写入速度比ufsd稍差一些。
基本表现接近原生ext4,比ntfs-3g性能翻倍.

5. 已知问题：
   没有实现ACL，全部权限都是drwx，即0777.
   没有完整的splice接口，所以针对Samba的优化全部无效.
   没有实现fallocate/truncate接口，在部分应用上写入速度也会差一些.
   挂载不会检查文件系统完整性，需要确认文件系统没有损坏
