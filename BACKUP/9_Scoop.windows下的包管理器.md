# [Scoop windows下的包管理器](https://github.com/haoz0x139/myblog/issues/9)

# Scoop 安装
## 环境需求
- PowerShell 5 +
- .NET Framework 4.5 +
![scoop-01](https://user-images.githubusercontent.com/124132611/216545926-1d034692-d7ae-491a-9237-04065711e7e6.jpg)
# 安装
## 指定安装位置（配置环境变量）
以管理员身份打开PowerShell
```yml
$env:SCOOP='D:\Applications\Scoop'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
$env:SCOOP_GLOBAL='F:\GlobalScoopApps'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
```
# 安装Scoop
首先确保你能访问 raw.githubusercontent.com
```yml
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
# 或者
iwr -useb get.scoop.sh | iex
irm https://cdn.jsdelivr.net/gh/duzyn/scoop-cn/install.ps1 | iex
irm https://ghproxy.com/raw.githubusercontent.com/duzyn/scoop-cn/master/install.ps1 | iex
```

# Scoop 使用
## Scoop官方维护的仓库
- main - 默认仓库
- extras - 默认仓库的补充超级强大
- games - 看名字就知道啦
- nerd-fonts - Nerd Fonts
- nirsoft - A subset of the 250 Nirsoft apps
- java - Installers for Oracle Java, OpenJDK, Zulu, ojdkbuild, AdoptOpenJDK, Amazon Corretto, BellSoft Liberica & SapMachine
- jetbrains - Installers for all JetBrains utilities and IDEs
- nonportable - Non-portable apps (may require UAC)
- php - Installers for most versions of PHP
- versions - Alternative versions of apps found in other buckets

可以直接通过scoop bucket add <repo_name>安装

由于某些原因，每次更新仓库的时间奇慢，所以还是换为国内镜像仓库来增加使用体验

# 镜像仓库
- [main](https://mirror.nju.edu.cn/git/scoop-main.git)

- [extras](https://mirror.nju.edu.cn/git/scoop-extras.git)

- [dorado](https://gitee.com/scoop-bucket/dorado.git)

# 执行以下命令安装必装软件
```yml
scoop install aria2 git 7zip
```
反正你肯定要用到！
或者
```
scoop install https://ghproxy.com/raw.githubusercontent.com/duzyn/scoop-cn/master/bucket/7zip.json
scoop install https://ghproxy.com/raw.githubusercontent.com/duzyn/scoop-cn/master/bucket/git.json
scoop install https://ghproxy.com/raw.githubusercontent.com/duzyn/scoop-cn/master/bucket/aria2.json
```
或者
```
scoop install https://cdn.jsdelivr.net/gh/duzyn/scoop-cn/bucket/7zip.json
scoop install https://cdn.jsdelivr.net/gh/duzyn/scoop-cn/bucket/git.json
scoop install https://cdn.jsdelivr.net/gh/duzyn/scoop-cn/bucket/aria2.json
```
# 对aria2进行设置
```
scoop config aria2-split 3 
scoop config aria2-max-connection-per-server 3 
scoop config aria2-min-split-size 1M
```
# 对scoop_repo进行更改
```
scoop config SCOOP_REPO https://gitee.com/scoop-bucket/scoop
```
# 执行以下命令订阅软件仓库
```
scoop bucket rm main
scoop bucket add main https://mirror.nju.edu.cn/git/scoop-main.git
scoop bucket add extras https://mirror.nju.edu.cn/git/scoop-extras.git
```
以上两个是官方bucket的国内镜像，所有软件建议优先从这里下载。
```
scoop bucket add dorado https://gitee.com/scoop-bucket/dorado.git
```
# 每次添加完仓库记得更新一下！
```
scoop update
```
# 另外附上常用命令
```
scoop update  #更新仓库
scoop update *  #更新所有软件
scoop list  #列出已安装的软件
scoop bucket list  #列出已订阅的仓库
```
