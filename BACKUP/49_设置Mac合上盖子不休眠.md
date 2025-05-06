# [设置Mac合上盖子不休眠](https://github.com/goohugo/myblog/issues/49)

Mac默认情况下合上盖子就会进入休眠状态，正在进行的任务也会停止。

我们在终端执行两条命令来将Mac设置为合盖不休眠。

打开Terminal，执行如下两条语句：

```
sudo pmset -b sleep 0
sudo pmset -b disablesleep 1
```

**若需要恢复原有合盖自动休眠的设置，则执行如下两条语句：**

```
sudo pmset -b sleep 5
sudo pmset -b disablesleep 0
```

关于pmset命令更多的用法可以在终端执行man pmset来查看。