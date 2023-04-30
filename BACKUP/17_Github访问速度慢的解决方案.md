# [Github访问速度慢的解决方案](https://github.com/haoz0x139/myblog/issues/17)

作为国内的用户，我相信绝大多数的家人们都遇到过一个问题，那就是访问github的时候非常非常慢。甚至有的时候访问网站页面直接死掉。这个时候该有人说了，我有梯子我不怕，上网速度嗖嗖的。

但是如果我们不使用梯子的情况下该怎么办呢？毕竟使用github也是我们的日常。

# Github打开慢的原因：
      GitHub的CDN(Content Delivery Network,即内容分发网络)域名遭到DNS污染，无法连接使用GitHub的加速分发服务器，
      所以国内访问速度较慢。 

      DNS解析的问题；服务器在国外。


# 方案一：
方案一：修改本地host文件
修改本地host文件，增加配置内容，绕过域名解析，达到加速的目的。

## 获取方式1:

github.global.ssl.fastly.net.ipaddress.com/#ipinfo 访问这个网址。会得到CDN和IP地址，对应github.com

github.com.ipaddress.com/#ipinfo 访问这个网址，会得到CDN和IP地址，对应github.global.ssl.fastly.net。然后再host中添加配置：

```
140.82.114.4 github.com
199.232.69.194 github.global.ssl.fastly.net
```

## 获取方式2:

访问链接：https://raw.hellogithub.com/hosts（ps：这链接定时更新），获取对应的host配置。

如果需要工具自动更新的话，点击链接：https://github.com/oldj/SwitchHosts

特别说明

Github的IP地址是不断变化的，如果发现网站打不开了，可以获取新的IP地址修改hosts里面的内容，方式如下：

在网站https://www.ipaddress.com/ 输入你要解析的域名。例如：github.com的IP获取方式，在输入框输入以下内容：

![ipaddress.com/](https://user-images.githubusercontent.com/124132611/235336020-8fde6d5e-6e72-4628-bf19-cf61573a4deb.png)


敲击你最爱的回车键，你会得到：

![ip](https://user-images.githubusercontent.com/124132611/235336030-b969a911-bb42-44a4-bf99-93312430bd28.png)


要的就是红框框里的内容。获取了相关信息后，可以替换hosts里的内容即可。

## 修改HOSTS文件的方法：

### 1、Mac OS系统

1）、直接打开终端

2）、输入：sudo vim /etc/hosts

3）、输入本机的开机密码

### 2、Windows系统

1）、打开c盘，按照这个路径C:\Windows\System32\drivers\etc\hosts找到hosts文件

2）、用文本编辑器打开文件

# 方案二：Github镜像或加速网站
通过GitHub 镜像访问。这里提供几个最常用的镜像地址：
```
https://hub.fastgit.xyz/ 
https://gitclone.com/ （此镜像是直接搜索相关仓库，然后克隆）
https://ghproxy.com/ （GitHub 文件 , Releases , archive , gist , raw.githubusercontent.com 文件代理加速下载服务）
https://toolwa.com/github/ （GitHub 加速下载）
```
也就是说上面的镜像就是一个克隆版的 GitHub，你可以访问上面的镜像网站，网站的内容跟 GitHub 是完整同步的镜像，然后在这个网站里面进行下载克隆等操作。

注意是否已失效，当然也可搜索其他的镜像网址或加速网站。