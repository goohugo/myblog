# [Ubuntu分区方案](https://github.com/haoz0x139/myblog/issues/24)

# Ubuntu分区方案
- swap: 4G(跟你自己内存一样大)；主分区；空间起始位置；用于交换空间
- /boot: 300M(太小会导致软件无法升级)；逻辑分区；空间起始位置；EXT4；/boot
- /: 30G；主分区；空间起始位置；EXT4；/
- (可不分)/usr: 软件安装位置，大小剩下的1/3 - 1/2空间；逻辑分区；空间起始位置；EXT4；/usr
- /home:** 文件存放位置，剩下的所有空间给它；逻辑分区；空间起始位置；EXT4；/home
 
# Ubuntu单系统分区方案(1T)

- swap: 12G(跟你自己内存一样大)；主分区；空间起始位置；用于交换空间
- /boot: 500M逻辑分区；空间起始位置；EXT4；/boot
- /: 100G；主分区；空间起始位置；EXT4；/
- /usr: 100G；逻辑分区；空间起始位置；EXT4；/usr
- /home: 剩下所有空间减去200M；逻辑分区；空间起始位置；EXT4；/home
- efi: 逻辑分区；空间起始位置；EFI系统分区
- 安装启动引导器的设备选择efi那个分区

已经使用 Ubuntu 快一年了，贴一张各分区使用情况图：

![image](https://github.com/haoz0x139/myblog/assets/124132611/bdf837bd-f326-4af7-a4a2-0e3a957ee0bc)
